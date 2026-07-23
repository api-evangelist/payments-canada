---
name: Send an RTR credit transfer and check its status
description: Send a single Real-Time Rail credit transfer (ISO 20022 pacs.008) to RTR Exchange and enquire on its payment status (pacs.028), on the Payments Canada sandbox.
api: openapi/rtr-inbound-participant-payment-api-openapi.yml
operations:
- POST /payments
- POST /payments/status
---

# Send an RTR credit transfer and check its status

Operate the Payments Canada Real-Time Rail (RTR) sandbox to send a credit
transfer and confirm its outcome. These are interbank ISO 20022 messages, not
card payments.

## Prerequisites
- Register on the developer portal and create an app subscribed to
  `rtr-sandbox-product`. Note the **Consumer Key** and **Consumer Secret**.
- Obtain an OAuth2 access token (client-credentials) from
  `https://api.payments.ca/accesstoken`. Tokens expire in 5 minutes.
- Base URL: `https://api.payments.ca/rtr-sandbox`.

## Steps
1. **Send the credit transfer** — `POST /payments`.
   - Body media type `application/vnd.api.v1+json`, schema `SendPayment`
     (a `business_application_header` + `fi_to_fi_customer_credit_transfer`,
     ISO 20022 pacs.008).
   - Required headers: `traceability-id` (UUID, per-call trace) and
     `x-jws-signature` (JWS of the request payload). Include `x-uetr` (UUID) as
     the end-to-end transaction reference.
   - A `200` returns a `PacsResponse` (pacs.002 status report). Inspect the
     transaction status: **RJCT** means the transfer was rejected; any other
     status is accepted. A malformed request instead yields an admi.002
     `message_reject`.
2. **Enquire on status** — `POST /payments/status`.
   - Body schema `SendStatusEnquiry` (ISO 20022 pacs.028) referencing the same
     UETR. Same required headers.
   - Returns a `PacsResponse` (pacs.002).

## Rules
- **No idempotency key.** Re-sending `POST /payments` is a new instruction — do
  not blindly retry a payment on a timeout; use `POST /payments/status` with the
  original UETR to determine the outcome first.
- Every request and response payload is JWS-signed; verify the response
  `x-jws-signature`.
- Handle `429` (rate limited) with backoff; `503` means temporary maintenance.
- See `conventions/payments-canada-conventions.yml` and
  `errors/payments-canada-problem-types.yml`.
