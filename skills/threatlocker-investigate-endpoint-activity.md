---
name: Investigate endpoint activity in ThreatLocker
description: Search the ThreatLocker action log to work out what ran, was blocked, or touched the network on a managed endpoint, and pull the supporting file and audit detail.
api: openapi/threatlocker-portal-openapi-original.json
operations:
  - "POST /portalapi/ActionLog/ActionLogGetByParametersV2"
  - "GET /portalapi/ActionLog/ActionLogGetByIdV2"
  - "GET /portalapi/ActionLog/ActionLogGetAllForFileHistoryV2"
  - "GET /portalapi/ActionLog/ActionLogGetFileDownloadDetailsById"
  - "POST /portalapi/Computer/ComputerGetByAllParameters"
  - "POST /portalapi/ComputerCheckin/ComputerCheckinGetByParameters"
  - "POST /portalapi/SystemAudit/SystemAuditGetByParameters"
  - "POST /portalapi/UploadRequest/UploadRequestInsert"
  - "POST /portalapi/UploadRequest/UploadRequestGet"
generated: '2026-08-02'
method: generated
source: openapi/threatlocker-portal-openapi-original.json + https://threatlocker.kb.help/api-documentation/
---

# Investigate endpoint activity

Use this to answer "what happened on this machine" from the ThreatLocker action log.

## Setup

Same as every PortalAPI call: instance host, `Authorization` API-key header, `managedOrganizationId` for the target tenant, JSON in and out.

## Steps

1. **Find the endpoint.** `POST /portalapi/Computer/ComputerGetByAllParameters` with a `ComputerParameterDto`; page with `pageNumber` / `pageSize`. Keep the `computerId`.
2. **Search the action log.** `POST /portalapi/ActionLog/ActionLogGetByParametersV2` with an `ActionLogParamsDto`. The provider documents these coded values inline in the operation description:
   - `ActionType`: `execute | install | network | registry | read | write | move | delete | baseline | powershell | elevate | configuration | dns`
   - `SourceTableId`: `ActionLog = 1 | DenyActionLog = 2 | BaselineActionLog = 3 | EventLogActionLog = 4`
   - `ActionId`: `Permit = 1 | Deny = 2 | DenyOptionToRequest = 3 | InstallMode = 4 | MissingCoreFiles = 5 | Ringfenced = 6 | AnyDeny = 7`
   - `GroupBy`: `FullPath = path | Hash = hash | SourceIp = sourceip | Cert = cert | Hostname = hostname | Username = username | ProcessPath = process`
   Start with `ActionId: 7` (AnyDeny) scoped to the `computerId` to see what is being blocked.
3. **Open one entry.** `GET /portalapi/ActionLog/ActionLogGetByIdV2?eActionLogId=<id>` returns the `ActionLogDto` — `certificates`, `actionLogCreatedByProcesses` (the process chain), `threatLockerItem`, `engineRatings`.
4. **Follow the file.** `GET /portalapi/ActionLog/ActionLogGetAllForFileHistoryV2?hostname=<host>&fullPath=<path>` for everything that file has done across the estate.
5. **Confirm the endpoint is live.** `POST /portalapi/ComputerCheckin/ComputerCheckinGetByParameters` for recent check-ins before drawing conclusions from an absence of events.
6. **Get the sample if you need it.** `POST /portalapi/UploadRequest/UploadRequestInsert` asks the endpoint to upload the file, then poll `POST /portalapi/UploadRequest/UploadRequestGet`. Use `GET /portalapi/ActionLog/ActionLogGetFileDownloadDetailsById` for download details.
7. **Check who changed what.** `POST /portalapi/SystemAudit/SystemAuditGetByParameters` for the administrative audit trail around the same window.

## Rules

- Every read is safe to repeat. The upload request is a **write** that reaches out to the endpoint — do not fire it in a loop.
- The coded enums above are documented as prose in the operation descriptions, not as OpenAPI `enum`s. Do not invent additional codes.
- No rate limits are published. Back off on `500` and check https://threatlockerstatus.com for your instance before retrying.
