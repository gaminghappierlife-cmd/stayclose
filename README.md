# StayClose — Home within reach

StayClose is an Alexa+ MCP prototype for people who cannot always get up. It provides a calm bedside layer for home status, trusted assistance, deliberate assistance-dog signals and dog-aware delivery instructions.

The project is designed for the Amazon Developer Hackathon Alexa+ track. It includes a self-hosted Streamable HTTP MCP endpoint and a web-based simulated Alexa+ experience. No Echo or Ring hardware is required for this demo.

## What the demo proves

The demo calls a real MCP endpoint at `POST /api/mcp` using JSON-RPC and protocol version `2025-11-25`. It exposes five tools: `read_home_status`, `prepare_assistance_request`, `confirm_assistance_request`, `simulate_assistance_dog_signal` and `create_delivery_note`.

The accessible UI lets a resident review simulated home activity, request a trusted-person check-in with confirmation, trigger a deliberate dog signal, prepare an arrival note for a working assistance dog and switch to bedside mode. The page shows the difference between a working prototype, a planned adapter and a user-controlled handoff.

## Important product boundaries

StayClose is not an emergency service. It does not dispatch emergency responders, unlock doors, place orders, send SMS, identify a dog through computer vision or claim to be connected to a live Ring camera, Apple Watch or delivery account. Those are future integrations or user-controlled handoffs. The demo intentionally shows this boundary so a vulnerable resident is not misled about what happened.

## Run locally

Requirements: Node.js and pnpm 10.18.0.

```bash
pnpm install
pnpm dev
```

Open the local preview at `http://localhost:3000`. To validate the production bundle:

```bash
pnpm check
pnpm build
pnpm start
```

The MCP endpoint is `POST /api/mcp`. It supports initialization, session headers, tool discovery and JSON responses. The demo uses JSON responses rather than SSE streaming for individual tool calls; `GET /api/mcp` intentionally returns `405`.

## Repository map

- `client/src/pages/Home.tsx` — accessible product experience and simulator controls.
- `client/src/index.css` — visual system, responsive layout and reduced-motion support.
- `client/src/lib/mcp.ts` — browser MCP client.
- `server/stayclose/mcp.ts` — Streamable HTTP JSON-RPC MCP endpoint.
- `shared/stayclose.ts` — shared state and event types.
- `client/public/logos/` — ecosystem logo assets used in the integration map.
- `docs/DEVPOST.md` — submission description, demo script, feedback and safety notes.
- `research.md` — verified competition and integration research.
- `plan.md` — product and design decisions.

## Competition materials

Start with [`docs/DEVPOST.md`](docs/DEVPOST.md), then use [`submission/FINAL_CHECKLIST.md`](submission/FINAL_CHECKLIST.md) before entering. The project is MIT licensed. The entrant must still create/share the required repository, record the public English demo video under three minutes, confirm eligibility and submit through Devpost.

## Licence

MIT. See [`LICENSE`](LICENSE).
