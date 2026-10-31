# Photon Engine

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

Photon Engine (Exit Games) builds cross-platform multiplayer game networking backends - Photon Fusion, Photon Quantum, Photon Unity Networking (PUN), Photon Voice, Photon Chat, and the legacy Photon Bolt - all layered on the proprietary Photon Realtime transport protocol. Photon's core product is protocol-first and SDK-first, not REST-first - game clients exchange a custom binary message format (operation requests, operation responses, and events) with Name Server, Master Server, and Game Server roles, over UDP or TCP by default and, importantly, over WebSocket (ws:// unsecured, wss:// secured on port 443) as a first-class documented transport for WebGL and browser-hosted clients. Photon's own hosted surface exposes no general-purpose callable REST API for gameplay; the only genuinely HTTP surfaces are outbound - Room Lifecycle WebHooks (Photon POSTs room/join/leave/event/property/close notifications to a developer-hosted URL) and the Custom Authentication webservice contract (Photon calls out to a developer-hosted HTTP(S) endpoint to validate client tokens before allowing a connection). Pricing and account management are handled through the Photon Cloud Dashboard web UI, not a documented public REST API.

**Areas:** Gaming · Multiplayer · Real-Time · Netcode · Game Networking · WebSocket · Binary Protocol

## Photon Engine on APIs.io

Everything profiled for Photon Engine is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/photonengine/](https://apis.io/providers/photonengine/)** — or go straight to one of the APIs or properties below.

### APIs (9)

- [Photon Realtime Transport Protocol](https://apis.io/apis/photonengine/photonengine-realtime-transport-api/) — The core Photon protocol - NOT a REST or JSON API. Clients connect through a Name Server to a Master Server (matchmaking/lobby) and then a Game Server (room…
- [Photon PUN (Photon Unity Networking) API](https://apis.io/apis/photonengine/photonengine-pun-api/) — Photon Unity Networking 2, the original high-level Unity multiplayer SDK layered over the Photon Realtime transport protocol (same binary messages, same…
- [Photon Fusion Networking API](https://apis.io/apis/photonengine/photonengine-fusion-api/) — Photon's current-generation, high-level networking framework for Unity, supporting Shared Mode, Client-Host, and dedicated Server Mode topologies with…
- [Photon Quantum Deterministic Simulation API](https://apis.io/apis/photonengine/photonengine-quantum-api/) — Photon's deterministic, ECS-based simulation framework that ships player inputs (not state) across all clients in lockstep, re-simulating identically on…
- [Photon Voice API](https://apis.io/apis/photonengine/photonengine-voice-api/) — Cross-platform low-latency voice chat built directly on top of Photon Realtime - it inherits Realtime's matchmaking, rooms, and interest groups and streams…
- [Photon Chat API](https://apis.io/apis/photonengine/photonengine-chat-api/) — A separately billed Photon Cloud service (its own AppId type) for text messaging, presence, and friend lists, dedicated Chat Servers speaking the same…
- [Photon Bolt (Legacy, Deprecated)](https://apis.io/apis/photonengine/photonengine-bolt-api/) — Legacy UDP-based Unity netcode product from Exit Games. No longer actively developed and not recommended for new projects - superseded by Photon Fusion.…
- [Photon Engine Custom Authentication API](https://apis.io/apis/photonengine/photonengine-custom-authentication-api/) — Endpoint Photon's server calls to validate a connecting client's credentials. You implement this; Photon is the caller.
- [Photon Engine Room Lifecycle WebHooks API](https://apis.io/apis/photonengine/photonengine-room-lifecycle-webhooks-api/) — Endpoints Photon's Game Server calls (HTTP POST) at points in a room's lifecycle. You implement these; Photon is the caller.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Photon Realtime Transport Protocol over WebSocket](https://apis.io/asyncapis/photonengine/photonengine-asyncapi/)

#### Event channels (1)

Individual events and webhooks the provider emits.

- [/photon/ws](https://apis.io/channels/photonengine/photon-ws/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Photonengine Agentic Access](https://apis.io/agentic-access/photonengine/photonengine-agentic-access/)

#### Collections (2)

Postman and Open Collection request collections.

- [Photon WebHooks and Webservice Contract Custom Authentication API](https://apis.io/collections/photonengine/open-photonengine-custom-authentication-api/)
- [Photon WebHooks and Webservice Contract Custom Authentication Room Lifecycle WebHooks API](https://apis.io/collections/photonengine/open-photonengine-room-lifecycle-webhooks-api/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Photon Engine — asyncapi rules](https://apis.io/rules/photonengine/photonengine-asyncapi-spectral-rules/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Photonengine Domain Security](https://apis.io/security/photonengine/photonengine-domain-security/)
- [Photonengine Vulnerability Disclosure](https://apis.io/security/photonengine/photonengine-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Photonengine Plans Pricing](https://apis.io/plans/photonengine/photonengine-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Photonengine Rate Limits](https://apis.io/rate-limits/photonengine/photonengine-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Photonengine Finops](https://apis.io/finops/photonengine/photonengine-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.photonengine.com)
- [Documentation](https://doc.photonengine.com)
- [GitHub](https://github.com/exitgames)

## API Evangelist rating

**Kin Score 24.1** — emerging · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 66.1 |
| Contract quality | 50.7 |
| Contract governance | 13.6 |
| Operational transparency | 10.5 |
| Developer ergonomics | 7.1 |
| Access clarity | 7.9 |

**Agent readiness 16.5** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | — |
| Idempotency | — |
| Error Semantics | — |
| OpenAPI Examples | — |
| Rate Limit Signal | derived (partial credit) |
| Event Surface Described | derived (partial credit) |
| Agent Skills | — |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 11.8** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/photonengine/](https://apis.io/providers/photonengine/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Photon Engine: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/photonengine/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
