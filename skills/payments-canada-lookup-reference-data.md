---
name: Look up Canadian financial-institution and creditor reference data
description: Query the Payments Canada FIF (Financial Institutions File) and CCIN (Corporate Creditor Identification Number) reference-data APIs — master/updated extracts, branch and single-CCIN lookups.
api: openapi/fif-extracts-api-openapi.yml
operations:
- getMaster
- getUpdate
- getBranchById
- getMasterExtractUsingGET
- getUpdateExtractUsingGET
- getCcinByIdUsingGET
---

# Look up Canadian financial-institution and creditor reference data

Retrieve routing/reference data for Canadian financial institutions (FIF) and
corporate creditors (CCIN). These are read-only paginated REST APIs, distinct
from the ISO 20022 RTR rails.

## Prerequisites
- Register on the developer portal; these APIs authenticate with a **Bearer
  token** in the `Authorization` header (FIF) obtained via the portal.
- Host: `api.payments.ca`.

## FIF — Financial Institutions File
- **Master extract** — `getMaster` (`GET /extracts/master`, spec
  `openapi/fif-extracts-api-openapi.yml`, basePath `/fif-extracts`). Params:
  `asAtDate`, `limit`.
- **Updated extract** — `getUpdate` (`GET /extracts/updated`). Params:
  `startDate`, `endDate`.
- **Branch lookup** — `getBranchById` (`GET /branches/{dprn}`, spec
  `openapi/fif-branch-api-openapi.yml`, basePath `/fif-branch`). Path param
  `dprn`; query `asAtDate`.

## CCIN — Corporate Creditor Identification Number
- **Master extract** — `getMasterExtractUsingGET` (`GET /api/v1/extracts/master`,
  spec `openapi/ccin-extracts-api-openapi.yml`). Paginate with `page`, `limit`,
  `sortField`, `sortOrder`; `allRecords=true` for the full set; `asAtDate`,
  `filter`.
- **Updated extract** — `getUpdateExtractUsingGET` (`GET /api/v1/extracts/updated`).
  Params `startDate`, `endDate`, `page`, `limit`, `sortField`, `sortOrder`.
- **Single CCIN** — `getCcinByIdUsingGET` (`GET /api/v1/ccins/{ccin}`, spec
  `openapi/ccin-lookup-api-openapi.yml`). Path param `ccin`; query `asAtDate`.

## Rules
- Page through extracts with `page`/`limit` (see
  `conventions/payments-canada-conventions.yml`); prefer a date window
  (`startDate`/`endDate`) over full extracts for incremental sync.
- Handle `400/401/404/406/429/500` per
  `errors/payments-canada-problem-types.yml`.
