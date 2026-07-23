---
name: Retrieve RTR interest and balance reports
description: Query the Payments Canada clearing & settlement system for a participant's interest report and payment-capacity balance report (ISO 20022 camt.003 -> camt.004).
api: openapi/rtr-balance-report-api-openapi.yml
operations:
- POST /interest-report
- POST /payment-capacity-balance-report
---

# Retrieve RTR interest and balance reports

Pull account reports for an RTR participant from the clearing & settlement (C&S)
system. Both endpoints send an ISO 20022 camt.003 (Get Account) and receive a
camt.004 (Return Account) — or an admi.002 reject.

## Prerequisites
- Same OAuth2 client-credentials token as the RTR payment flow
  (`https://api.payments.ca/accesstoken`, 5-minute TTL).
- Base URL: `https://api.payments.ca/rtr-sandbox`.
- Required headers on every call: `traceability-id` (UUID) and `x-jws-signature`.

## Steps
1. **Balance report** — `POST /payment-capacity-balance-report`
   (spec `openapi/rtr-balance-report-api-openapi.yml`).
   - Body `BalanceRequest` = `get_account` (camt.003) + `business_application_header`.
   - `200` returns `BalanceResponse`: a `return_account` (camt.004 with balance
     data) or a `message_reject` (admi.002).
2. **Interest report** — `POST /interest-report`
   (spec `openapi/rtr-interest-report-api-openapi.yml`).
   - Body `InterestRequest` = `get_account` (camt.003) + `business_application_header`.
   - `200` returns `InterestResponse`: `return_account` (camt.004 with interest
     data) or `message_reject`.

## Rules
- These are read/query operations (no funds move); still JWS-sign the request.
- Branch on the `oneOf`: check for `message_reject` before reading account data.
- Handle `401`, `429`, `500` per `errors/payments-canada-problem-types.yml`.
