# Payments Canada (payments-canada)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
