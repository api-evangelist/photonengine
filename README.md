# Photon Engine (photonengine)

Photon Engine (Exit Games) builds cross-platform multiplayer game networking backends - Photon Fusion, Photon Quantum, Photon Unity Networking (PUN), Photon Voice, Photon Chat, and the legacy Photon Bolt - all layered on the proprietary Photon Realtime transport protocol. Photon's core product is **protocol-first and SDK-first, not REST-first**: game clients exchange a custom binary message format (operation requests, operation responses, and events) with Name Server, Master Server, and Game Server roles, over UDP or TCP by default and, importantly, over **WebSocket** (`ws://` unsecured, `wss://` secured on port 443) as a first-class documented transport for WebGL and browser-hosted clients.

Photon's own hosted surface exposes no general-purpose callable REST API for gameplay. The only genuinely HTTP surfaces run in reverse: **Room Lifecycle WebHooks** (Photon's Game Server POSTs room/join/leave/event/property/close notifications to a developer-hosted URL) and the **Custom Authentication webservice contract** (Photon calls out to a developer-hosted HTTP(S) endpoint to validate client tokens before allowing a connection). Account management and CCU/billing are handled through the Photon Cloud Dashboard web UI, not a documented public REST API.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/photonengine/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/photonengine/refs/heads/main/apis.yml)

## Protocol reality check

- **Realtime Transport Protocol** - the actual wire protocol. Binary operation requests/responses/events over UDP (default), TCP, or WebSocket. Documented in [Realtime Intro](https://doc.photonengine.com/realtime/current/getting-started/realtime-intro) and the [Binary Protocol reference](https://doc.photonengine.com/realtime/current/reference/binary-protocol).
- **WebSocket is real and documented**, not a workaround: clients set `ConnectionProtocol` to `WebSocket` (`ws://`, port 80) or `WebSocketSecure` (`wss://`, port 443); self-hosted Photon Server's WebSocket listener defaults to port 9090 (Master) / 9091 (GameServer secure); Photon Cloud's equivalent listener is port 19090. See [Secure Networks](https://doc.photonengine.com/realtime/current/connection-and-authentication/secure-networks) and [WebSocket SSL Setup](https://doc.photonengine.com/server/v4/operations/websockets-ssl-setup). WebSocket is the transport used by WebGL and other browser-hosted clients that cannot open raw sockets.
- **The payload over that WebSocket connection is still Photon's proprietary binary protocol**, not JSON. `asyncapi/photonengine-asyncapi.yml` models the connection life cycle and the operation/event envelope structure honestly, with an explicit `isJson: false` note - it is not a claim that Photon runs a JSON WebSocket chat API.
- **PUN, Fusion, Quantum, Voice, and Chat** are all SDK/product layers on top of the same Realtime transport (Voice explicitly documents that it "is built on top of Photon Realtime and inherits all of its features"). None of them introduce a separate REST surface.
- **Bolt** is Photon's legacy, no-longer-actively-developed netcode product, listed here for completeness alongside PUN/Fusion/Quantum/Voice/Chat, but is deprecated in favor of Fusion.
- **Room Lifecycle WebHooks** and **Custom Authentication** are the one genuinely HTTP-shaped surface in the stack - but Photon is the HTTP *client* and the game developer hosts the HTTP *server*. See [WebHooks](https://doc.photonengine.com/realtime/current/gameplay/web-extensions/webhooks) and [Custom Authentication](https://doc.photonengine.com/realtime/current/connection-and-authentication/authentication/custom-authentication).
- No `collections/` artifact was produced: a Postman/Open Collection models "calls I make to a provider's API," and there is no provider-hosted, developer-callable REST API here to call - the WebHooks/Custom Auth contract is the reverse of that shape.

## Tags

- Gaming
- Multiplayer
- Realtime
- Netcode
- Game Networking
- WebSocket
- Binary Protocol

## Timestamps

- **Created:** 2026-07-03
- **Modified:** 2026-07-03

## APIs

### Photon Realtime Transport Protocol

The core Photon protocol - not a REST or JSON API. Clients connect through a Name Server to a Master Server (matchmaking/lobby) and then a Game Server (room gameplay), exchanging a proprietary binary message format over UDP, TCP, or WebSocket.

- **Human URL:** [https://doc.photonengine.com/realtime/current/getting-started/realtime-intro](https://doc.photonengine.com/realtime/current/getting-started/realtime-intro)
- **Base URL:** `wss://ns.exitgames.com:443`

#### Properties

- [Documentation](https://doc.photonengine.com/realtime/current/getting-started/realtime-intro)
- [API Reference](https://doc.photonengine.com/realtime/current/reference/binary-protocol)
- [AsyncAPI](asyncapi/photonengine-asyncapi.yml) — [AsyncAPI Specification](https://www.asyncapi.com/docs/reference/specification/latest)

### Photon PUN (Photon Unity Networking) API

Legacy Unity multiplayer SDK layered over the Realtime transport protocol. Still supported for existing projects; Photon recommends Fusion or Quantum for new projects.

- **Human URL:** [https://doc.photonengine.com/pun/current/getting-started/pun-intro](https://doc.photonengine.com/pun/current/getting-started/pun-intro)

### Photon Fusion Networking API

Current-generation, high-level networking framework for Unity supporting Shared Mode, Client-Host, and dedicated Server Mode topologies with state-authoritative simulation.

- **Human URL:** [https://doc.photonengine.com/fusion/current/getting-started/fusion-intro](https://doc.photonengine.com/fusion/current/getting-started/fusion-intro)

### Photon Quantum Deterministic Simulation API

Deterministic, ECS-based simulation framework that ships player inputs (not state) across all clients in lockstep.

- **Human URL:** [https://doc.photonengine.com/quantum/current/manual/introduction](https://doc.photonengine.com/quantum/current/manual/introduction)

### Photon Voice API

Cross-platform low-latency voice chat built directly on Photon Realtime, streaming Opus-encoded audio as Realtime events.

- **Human URL:** [https://doc.photonengine.com/voice/current/getting-started/voice-intro](https://doc.photonengine.com/voice/current/getting-started/voice-intro)

### Photon Chat API

Separately billed Photon Cloud service for text messaging, presence, and friend lists over dedicated Chat Servers speaking the same Realtime-style binary protocol.

- **Human URL:** [https://doc.photonengine.com/chat/current/getting-started/chat-intro](https://doc.photonengine.com/chat/current/getting-started/chat-intro)

### Photon Bolt (Legacy, Deprecated)

Legacy UDP-based Unity netcode product, no longer actively developed, superseded by Photon Fusion.

- **Human URL:** [https://doc.photonengine.com/bolt/current/getting-started/bolt-intro](https://doc.photonengine.com/bolt/current/getting-started/bolt-intro)

### Photon Room Lifecycle WebHooks

Outbound HTTP POST callbacks (PathCreate, PathBeforeJoin, PathJoin, PathLeave, PathEvent, PathGameProperties, PathClose) that Photon's Game Server sends to a developer-hosted BaseUrl.

- **Human URL:** [https://doc.photonengine.com/realtime/current/gameplay/web-extensions/webhooks](https://doc.photonengine.com/realtime/current/gameplay/web-extensions/webhooks)

#### Properties

- [Documentation](https://doc.photonengine.com/realtime/current/gameplay/web-extensions/webhooks)
- [OpenAPI](openapi/photonengine-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Photon Custom Authentication Webservice Contract

Outbound HTTP call Photon's server makes to a developer-hosted AuthUrl to validate a connecting client's credentials.

- **Human URL:** [https://doc.photonengine.com/realtime/current/connection-and-authentication/authentication/custom-authentication](https://doc.photonengine.com/realtime/current/connection-and-authentication/authentication/custom-authentication)

#### Properties

- [Documentation](https://doc.photonengine.com/realtime/current/connection-and-authentication/authentication/custom-authentication)
- [OpenAPI](openapi/photonengine-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [GitHub Organization](https://github.com/exitgames)
- [LinkedIn](https://www.linkedin.com/company/photon-engine)
- [Website](https://www.photonengine.com)
- [Documentation](https://doc.photonengine.com)
- [Plans](plans/photonengine-plans-pricing.yml)
- [Rate Limits](rate-limits/photonengine-rate-limits.yml)
- [Fin Ops](finops/photonengine-finops.yml)

## Review

Does Photon Engine expose a documented public WebSocket API? **Yes** - see [review.yml](review.yml) for the full findings. Photon documents `ws://`/`wss://` as an official transport for its Realtime protocol (used heavily by WebGL clients), distinct from the binary payload it carries (not JSON).

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
