# Payments Canada (payments-canada)

Payments Canada (formerly the Canadian Payments Association) is the public-purpose organization created by federal statute (the Canadian Payments Act) that owns and operates Canada's core national payment clearing and settlement infrastructure, under the oversight of the Bank of Canada and the Minister of Finance. It operates Lynx (the high-value, ISO 20022 real-time gross settlement system), the Automated Clearing Settlement System (ACSS, Canada's retail batch/ACH rail), and is building the Real-Time Rail (RTR) — a 24/7/365 irrevocable faster-payments system fully based on the ISO 20022 messaging standard.

Payments Canada is payments infrastructure, distinct from Canada's Consumer-Driven Banking (open banking) framework, which is legislated but not yet operational and is overseen by the Financial Consumer Agency of Canada (FCAC). Payments Canada runs a real, publicly registerable API developer portal at [developer.payments.ca](https://developer.payments.ca/) (launched February 19, 2020) exposing member/registered-user sandbox and data-extract APIs — including downloadable RTR sandbox OpenAPI specifications — secured with OAuth2 client-credentials (Consumer Key/Secret via Apigee). Production access is license/agreement gated.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/payments-canada/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/payments-canada/refs/heads/main/apis.yml)

## Tags

- Financial Services
- Payments
- Canada
- Payment Infrastructure
- Clearing and Settlement
- Real-Time Rail
- ISO 20022
- Lynx
- Crown Corporation
- Faster Payments

## Timestamps

- **Created:** 2026-07-23
- **Modified:** 2026-07-23

## Open-Finance / API Posture

- **First-party developer portal:** Yes — [developer.payments.ca](https://developer.payments.ca/), live (HTTP 200), publicly registerable.
- **Downloadable specs:** Yes — four RTR sandbox OpenAPI 3.0.3 documents harvested verbatim (see `openapi/`).
- **Auth model:** OAuth2 client-credentials (Consumer Key / Consumer Secret) issued per registered app via Apigee.
- **Rails posture:** Operator of Lynx (RTGS, ISO 20022), ACSS (retail/ACH), and the in-progress Real-Time Rail (RTR, ISO 20022). This is the shared Canadian payments rail, not a consumer bank.
- **Consumer-Driven Banking (open banking):** Payments Canada is NOT the open-banking authority; Canada's CDB framework is overseen by the FCAC and is not yet operational. No FDX / 1033-style consumer-data API is exposed here.

## APIs

### RTR Sandbox - Inbound Participant Payment API

Real-Time Rail sandbox API for sending an RTR payment (ISO 20022 pacs.008 Customer Credit Transfer) to another RTR participant and enquiring on payment status (pacs.028).

- **Human URL:** [https://developer.payments.ca/rtr-sandbox-api/apis](https://developer.payments.ca/rtr-sandbox-api/apis)
- **Base URL:** `https://api.payments.ca/rtr-sandbox`
- **Properties:** [OpenAPI](openapi/rtr-inbound-participant-payment-api-openapi.yml)

### RTR Sandbox - Inbound Exchange Heartbeat API

Heartbeat requests between a participant and the RTR exchange (ISO 20022 admi.004 System Event Notification).

- **Human URL:** [https://developer.payments.ca/rtr-sandbox-api/apis](https://developer.payments.ca/rtr-sandbox-api/apis)
- **Base URL:** `https://api.payments.ca/rtr-sandbox`
- **Properties:** [OpenAPI](openapi/rtr-inbound-csp-heartbeat-api-openapi.yml)

### RTR Sandbox - Interest Report API

Clearing-and-settlement API generating an interest report (ISO 20022 camt.003 / camt.004).

- **Human URL:** [https://developer.payments.ca/rtr-sandbox-api/apis](https://developer.payments.ca/rtr-sandbox-api/apis)
- **Base URL:** `https://api.payments.ca/rtr-sandbox`
- **Properties:** [OpenAPI](openapi/rtr-interest-report-api-openapi.yml)

### RTR Sandbox - Payment Capacity Balance Report API

Clearing-and-settlement API generating a payment-capacity balance report (ISO 20022 camt.003 / camt.004).

- **Human URL:** [https://developer.payments.ca/rtr-sandbox-api/apis](https://developer.payments.ca/rtr-sandbox-api/apis)
- **Base URL:** `https://api.payments.ca/rtr-sandbox`
- **Properties:** [OpenAPI](openapi/rtr-balance-report-api-openapi.yml)

### Lynx Sandbox API

Member-gated sandbox APIs for Lynx, Canada's high-value ISO 20022 RTGS system. No public OpenAPI published.

- **Human URL:** [https://developer.payments.ca/lynx-sandbox-api/apis](https://developer.payments.ca/lynx-sandbox-api/apis)

### ACSS API

APIs for the Automated Clearing Settlement System, Canada's retail batch/ACH clearing rail. Member-gated.

- **Human URL:** [https://developer.payments.ca/acss-api/apis](https://developer.payments.ca/acss-api/apis)

### FIF Extracts API / FIF Branch API

Financial Institutions File extract and branch data. Registered-user access.

- **Human URL:** [https://developer.payments.ca/fif-extracts-api/apis](https://developer.payments.ca/fif-extracts-api/apis)
- **Human URL:** [https://developer.payments.ca/fif-branch-api/apis](https://developer.payments.ca/fif-branch-api/apis)

### CCIN Extracts API / CCIN Lookup API

Corporate Creditor Identification Number extract and single-lookup data. Registered-user access.

- **Human URL:** [https://developer.payments.ca/ccin-extracts-api/apis](https://developer.payments.ca/ccin-extracts-api/apis)
- **Human URL:** [https://developer.payments.ca/ccin-lookup-api/apis](https://developer.payments.ca/ccin-lookup-api/apis)

## Common Properties

- [Website](https://www.payments.ca/)
- [Developer Portal](https://developer.payments.ca/)
- [Documentation](https://developer.payments.ca/apis)
- [Getting Started](https://developer.payments.ca/getting-started)
- [GitHub Organization](https://github.com/paymentscanada)
- [LinkedIn](https://www.linkedin.com/company/payments-canada)
- [Twitter](https://twitter.com/paymentscanada)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
