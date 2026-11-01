# ThreatLocker

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

ThreatLocker is a Zero Trust endpoint and cloud security platform used by enterprises and managed service providers to enforce least privilege across endpoints, networks, and cloud workloads. Its capabilities include Application Control (allowlisting), Ringfencing, Elevation Control, Storage Control, Network Control / ZTNA, Web Content Control, Patch Management, and ThreatLocker Detect (managed detection and response). The multi-tenant ThreatLocker Portal is exposed programmatically through the PortalAPI — a public OpenAPI 3.0 REST contract covering action logs, applications, approval requests, computers and computer groups, maintenance mode, organizations, policies, reports, saved searches, scheduled agent actions, system audit, tags, upload requests, and agent versions. The platform is deployed as regionally isolated instances (A–H plus AE1, AU1, CA1, EU1, SA1 and a FedRAMP instance), so both the portal and the API are addressed per instance.

**Areas:** Cybersecurity · Zero Trust · Endpoint Security · Application-Control · allowlisting · Ransomware Prevention · Privileged Access Management · Network Access Control · Managed Detection and Response · Device Management · MSP · Compliance

## ThreatLocker on APIs.io

Everything profiled for ThreatLocker is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/threatlocker/](https://apis.io/providers/threatlocker/)** — or go straight to one of the APIs or properties below.

### APIs (18)

- [ThreatLocker Application API](https://apis.io/apis/threatlocker/threatlocker-application-api/) — The Application API from ThreatLocker — 6 operation(s) for application.
- [ThreatLocker Computer API](https://apis.io/apis/threatlocker/threatlocker-computer-api/) — The Computer API from ThreatLocker — 21 operation(s) for computer.
- [ThreatLocker Computer Checkin API](https://apis.io/apis/threatlocker/threatlocker-computercheckin-api/) — The ComputerCheckin API from ThreatLocker — 1 operation(s) for computercheckin.
- [ThreatLocker Computer Group API](https://apis.io/apis/threatlocker/threatlocker-computergroup-api/) — The ComputerGroup API from ThreatLocker — 4 operation(s) for computergroup.
- [ThreatLocker Maintenance Mode API](https://apis.io/apis/threatlocker/threatlocker-maintenancemode-api/) — The MaintenanceMode API from ThreatLocker — 4 operation(s) for maintenancemode.
- [ThreatLocker Online Devices API](https://apis.io/apis/threatlocker/threatlocker-onlinedevices-api/) — The OnlineDevices API from ThreatLocker — 1 operation(s) for onlinedevices.
- [ThreatLocker Organization API](https://apis.io/apis/threatlocker/threatlocker-organization-api/) — The Organization API from ThreatLocker — 3 operation(s) for organization.
- [ThreatLocker Policy API](https://apis.io/apis/threatlocker/threatlocker-policy-api/) — The Policy API from ThreatLocker — 1 operation(s) for policy.
- [ThreatLocker Report API](https://apis.io/apis/threatlocker/threatlocker-report-api/) — The Report API from ThreatLocker — 2 operation(s) for report.
- [ThreatLocker Save Search API](https://apis.io/apis/threatlocker/threatlocker-savesearch-api/) — The SaveSearch API from ThreatLocker — 3 operation(s) for savesearch.
- [ThreatLocker Scheduled Agent Action API](https://apis.io/apis/threatlocker/threatlocker-scheduledagentaction-api/) — The ScheduledAgentAction API from ThreatLocker — 6 operation(s) for scheduledagentaction.
- [ThreatLocker System Audit API](https://apis.io/apis/threatlocker/threatlocker-systemaudit-api/) — The SystemAudit API from ThreatLocker — 3 operation(s) for systemaudit.
- [ThreatLocker Tag API](https://apis.io/apis/threatlocker/threatlocker-tag-api/) — The Tag API from ThreatLocker — 3 operation(s) for tag.
- [ThreatLocker Threat Locker Version API](https://apis.io/apis/threatlocker/threatlocker-threatlockerversion-api/) — The ThreatLockerVersion API from ThreatLocker — 1 operation(s) for threatlockerversion.
- [ThreatLocker Upload Request API](https://apis.io/apis/threatlocker/threatlocker-uploadrequest-api/) — The UploadRequest API from ThreatLocker — 2 operation(s) for uploadrequest.
- [ThreatLocker VDI Hyper V API](https://apis.io/apis/threatlocker/threatlocker-vdihyperv-api/) — The VDIHyperV API from ThreatLocker — 1 operation(s) for vdihyperv.
- [ThreatLocker Action Log API](https://apis.io/apis/threatlocker/threatlocker-action-log-api/) — The Action Log API from ThreatLocker — 9 operation(s) for action log.
- [ThreatLocker Approval Request API](https://apis.io/apis/threatlocker/threatlocker-approval-request-api/) — The Approval Request API from ThreatLocker — 12 operation(s) for approval request.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Threatlocker Webhooks](https://apis.io/asyncapis/threatlocker/threatlocker-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [threatlocker-portalapi](https://apis.io/servers/threatlocker/threatlocker-portalapi/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Threatlocker Agentic Access](https://apis.io/agentic-access/threatlocker/threatlocker-agentic-access/)

#### Collections (19)

Postman and Open Collection request collections.

- [Portal Action Log API](https://apis.io/collections/threatlocker/open-threatlocker-actionlog-api/)
- [Portal Application API](https://apis.io/collections/threatlocker/open-threatlocker-application-api/)
- [Portal Approval Request API](https://apis.io/collections/threatlocker/open-threatlocker-approvalrequest-api/)
- [Portal Computer API](https://apis.io/collections/threatlocker/open-threatlocker-computer-api/)
- [Portal Computer Checkin API](https://apis.io/collections/threatlocker/open-threatlocker-computercheckin-api/)
- [Portal Computer Group API](https://apis.io/collections/threatlocker/open-threatlocker-computergroup-api/)
- [Portal Maintenance Mode API](https://apis.io/collections/threatlocker/open-threatlocker-maintenancemode-api/)
- [Portal Online Devices API](https://apis.io/collections/threatlocker/open-threatlocker-onlinedevices-api/)
- [Portal Organization API](https://apis.io/collections/threatlocker/open-threatlocker-organization-api/)
- [Portal Policy API](https://apis.io/collections/threatlocker/open-threatlocker-policy-api/)
- [PortalAPI](https://apis.io/collections/threatlocker/open-threatlocker-portal-openapi-original/)
- [Portal Report API](https://apis.io/collections/threatlocker/open-threatlocker-report-api/)
- [Portal Save Search API](https://apis.io/collections/threatlocker/open-threatlocker-savesearch-api/)
- [Portal Scheduled Agent Action API](https://apis.io/collections/threatlocker/open-threatlocker-scheduledagentaction-api/)
- [Portal System Audit API](https://apis.io/collections/threatlocker/open-threatlocker-systemaudit-api/)
- [Portal Tag API](https://apis.io/collections/threatlocker/open-threatlocker-tag-api/)
- [Portal Threat Locker Version API](https://apis.io/collections/threatlocker/open-threatlocker-threatlockerversion-api/)
- [Portal Upload Request API](https://apis.io/collections/threatlocker/open-threatlocker-uploadrequest-api/)
- [Portal VDI Hyper V API](https://apis.io/collections/threatlocker/open-threatlocker-vdihyperv-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Threatlocker Portal Overlay](https://apis.io/overlays/threatlocker/threatlocker-portal-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Threatlocker Authentication](https://apis.io/security/threatlocker/threatlocker-authentication/)
- [Threatlocker Domain Security](https://apis.io/security/threatlocker/threatlocker-domain-security/)
- [Threatlocker Trust Center](https://apis.io/security/threatlocker/threatlocker-trust-center/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.threatlocker.com/)
- [Documentation](https://threatlocker.kb.help/api-documentation/)
- [Getting started](https://threatlocker.kb.help/getting-started-with-threatlocker-portalapis/)
- [API reference](https://portalapi.threatlocker.com/swagger/index.html)
- [Pricing](https://www.threatlocker.com/pricing)
- [Sign up](https://www.threatlocker.com/try-threatlocker)
- [Support](https://threatlocker.kb.help/)
- [Changelog](https://threatlocker.kb.help/portal-release-notes/)
- [Blog](https://www.threatlocker.com/resources/blogs)
- [Compliance](https://threatlocker.kb.help/compliance/)
- [Terms of service](https://www.threatlocker.com/terms-and-conditions)
- [Privacy policy](https://www.threatlocker.com/legal/privacy-policy)
- [Status](https://threatlockerstatus.com)

## API Evangelist rating

**Kin Score 51.3** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 45.3 |
| Contract governance | 18.2 |
| Operational transparency | 39.5 |
| Developer ergonomics | 58.9 |
| Access clarity | 60.5 |

**Agent readiness 25.9** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | — |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | mostly (partial credit) |

**Regulatory alignment 29.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/threatlocker/](https://apis.io/providers/threatlocker/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for ThreatLocker: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/threatlocker/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
