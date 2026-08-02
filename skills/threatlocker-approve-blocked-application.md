---
name: Approve a blocked application in ThreatLocker
description: Triage a pending ThreatLocker approval request for a blocked application, inspect what was actually blocked, and either permit it, reject it, or ignore it.
api: openapi/threatlocker-portal-openapi-original.json
operations:
  - "GET /portalapi/ApprovalRequest/ApprovalRequestGetCount"
  - "POST /portalapi/ApprovalRequest/ApprovalRequestGetByParameters"
  - "GET /portalapi/ApprovalRequest/ApprovalRequestGetById"
  - "GET /portalapi/ApprovalRequest/ApprovalRequestGetPermitApplicationById"
  - "POST /portalapi/ApprovalRequest/ApprovalRequestUpdateForTakeOwnership"
  - "POST /portalapi/ApprovalRequest/ApprovalRequestPermitApplication"
  - "POST /portalapi/ApprovalRequest/ApprovalRequestUpdateForReject"
  - "POST /portalapi/ApprovalRequest/ApprovalRequestUpdateForIgnore"
generated: '2026-08-02'
method: generated
source: openapi/threatlocker-portal-openapi-original.json + https://threatlocker.kb.help/api-documentation/
---

# Approve a blocked application

Use this when an end user has requested access to software ThreatLocker Application Control blocked.

## Setup

- Host: `https://portalapi.{INSTANCE}.threatlocker.com` — the instance is organization-specific; find it under the organization settings in the ThreatLocker Portal.
- Header `Authorization: <API User token>` — the raw token, **no `Bearer` prefix**. Create it under Users > API Users.
- Header `managedOrganizationId: <organization GUID>` — required when acting on a managed (child) organization.
- All bodies and responses are `application/json`.

## Steps

1. **Check the queue.** `GET /portalapi/ApprovalRequest/ApprovalRequestGetCount` with `includeChildOrganizations` to see whether anything is pending. Stop here if the count is zero.
2. **List the requests.** `POST /portalapi/ApprovalRequest/ApprovalRequestGetByParameters` with an `ApprovalRequestParametersDto` body. Set `requestTypeId` and `statusId` to filter, and page with `pageNumber` / `pageSize`.
3. **Read one request.** `GET /portalapi/ApprovalRequest/ApprovalRequestGetById?approvalRequestId=<guid>` for the request record, then `GET /portalapi/ApprovalRequest/ApprovalRequestGetPermitApplicationById` for the full `PermitApplicationDto` — the originating `actionLog`, `fileDetails` (including code-signing certificates), `matchingApplications`, `policyConditions`, `ringfencingOptions`, and `policyLevel`.
4. **Investigate before permitting.** Pull the file's history with `GET /portalapi/ActionLog/ActionLogGetAllForFileHistoryV2` (`hostname`, `fullPath`) and, if you need it, the application record with `GET /portalapi/Application/ApplicationGetById`. Never permit on the request alone — check what else that file did on the endpoint.
5. **Claim it.** `POST /portalapi/ApprovalRequest/ApprovalRequestUpdateForTakeOwnership` so a second operator does not act on the same request.
6. **Decide.**
   - Permit: `POST /portalapi/ApprovalRequest/ApprovalRequestPermitApplication` with the `PermitApplicationDto`. Set `policyLevel` deliberately — the narrowest scope that solves the problem (a single computer or computer group, not the whole organization) — and keep `ringfencingOptions` in place.
   - Reject: `POST /portalapi/ApprovalRequest/ApprovalRequestUpdateForReject`.
   - Ignore: `POST /portalapi/ApprovalRequest/ApprovalRequestUpdateForIgnore`.

## Rules

- **Not idempotent.** ThreatLocker publishes no idempotency key. A retried permit can create a duplicate policy — re-read the request with `ApprovalRequestGetById` before retrying anything that timed out.
- Permitting an application **writes a security policy**. Treat it as a human-approved action: an agent should propose the permit and its scope, not apply it unattended.
- Errors are bare HTTP status codes. `401` = bad or inactive token (expiry is inactivity-based). `403` = the token's roles or organization scope do not cover this request. See `errors/threatlocker-problem-types.yml`.
