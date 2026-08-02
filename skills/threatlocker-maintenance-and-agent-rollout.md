---
name: Run a ThreatLocker maintenance window and agent rollout
description: Put endpoints into maintenance/learning mode for a software install or upgrade, roll the ThreatLocker agent version, and close the window cleanly.
api: openapi/threatlocker-portal-openapi-original.json
operations:
  - "POST /portalapi/Computer/ComputerGetByAllParameters"
  - "GET /portalapi/ComputerGroup/ComputerGroupGetDropdownByOrganizationId"
  - "POST /portalapi/MaintenanceMode/MaintenanceModeInsert"
  - "GET /portalapi/MaintenanceMode/MaintenanceModeGetByComputerId"
  - "POST /portalapi/MaintenanceMode/MaintenanceModeUpdateEndDateTimeForSpecificDate"
  - "PATCH /portalapi/MaintenanceMode/MaintenanceModeEndById"
  - "POST /portalapi/Computer/ComputerUpdateToFinishMaintenanceMode"
  - "GET /portalapi/ThreatLockerVersion/ThreatLockerVersionGetForDropdownList"
  - "POST /portalapi/Computer/ComputerUpdateThreatlockerVersionByIds"
  - "POST /portalapi/Computer/ComputerUpdateBaselineRescan"
  - "POST /portalapi/ScheduledAgentAction"
  - "POST /portalapi/ScheduledAgentAction/GetByParameters"
  - "POST /portalapi/ScheduledAgentAction/Abort"
generated: '2026-08-02'
method: generated
source: openapi/threatlocker-portal-openapi-original.json + https://threatlocker.kb.help/api-documentation/
---

# Maintenance windows and agent rollout

Use this to install or update software on protected endpoints without generating a wall of denials, and to move endpoints onto a new ThreatLocker agent build.

## Setup

Instance host, `Authorization` API-key header, `managedOrganizationId` for the tenant. JSON in and out.

## Steps

1. **Pick the target set.** `POST /portalapi/Computer/ComputerGetByAllParameters` for individual endpoints, or `GET /portalapi/ComputerGroup/ComputerGroupGetDropdownByOrganizationId` to work by group.
2. **Open the window.** `POST /portalapi/MaintenanceMode/MaintenanceModeInsert` with a `MaintenanceModeInsertDto` — `computerId`, `maintenanceTypeId`, the `maintenanceModeConditions`, and either `existingApplication` or `newApplication` so the learned files land against the right application definition.
3. **Verify it took.** `GET /portalapi/MaintenanceMode/MaintenanceModeGetByComputerId?computerId=<guid>` before you touch the endpoint. Never assume the window is open.
4. **Extend if the work overruns.** `POST /portalapi/MaintenanceMode/MaintenanceModeUpdateEndDateTimeForSpecificDate`. Extend deliberately — an open window is reduced enforcement.
5. **Close it.** `PATCH /portalapi/MaintenanceMode/MaintenanceModeEndById`, then `POST /portalapi/Computer/ComputerUpdateToFinishMaintenanceMode` to finalize on the endpoint. Closing the window is the security-relevant step; do not leave it to the timer if you finished early.
6. **Rescan the baseline** after a significant install: `POST /portalapi/Computer/ComputerUpdateBaselineRescan`.
7. **Roll the agent.** List builds with `GET /portalapi/ThreatLockerVersion/ThreatLockerVersionGetForDropdownList`, then `POST /portalapi/Computer/ComputerUpdateThreatlockerVersionByIds` for the selected `computerId`s. Ring it — a pilot group first, then the estate.
8. **Schedule and supervise.** Queue work with `POST /portalapi/ScheduledAgentAction`, watch it with `POST /portalapi/ScheduledAgentAction/GetByParameters`, and stop a bad rollout with `POST /portalapi/ScheduledAgentAction/Abort`.

## Rules

- **Do not blind-retry.** No idempotency key exists. A retried `MaintenanceModeInsert` or `ScheduledAgentAction` can open a second window or queue a duplicate action — re-read with `MaintenanceModeGetByComputerId` or `ScheduledAgentAction/GetByParameters` first.
- `ComputerDisableProtection`, `ComputerEnableProtection` and `ComputerMoveToOtherOrganization` change the security posture of real machines. An agent should propose them; a human should approve them.
- `ScheduledAgentAction` is one of only three operations in the spec that declares `400/401/403/500` — everywhere else you get an undocumented status. Handle non-200 defensively.
