# Intent

**Open-source communication platform. Private by design, not by promise.**

Discord asks for your government ID. Slack sells your conversations to train AI. Telegram's encryption is opt-in and closed-source. Every major platform treats privacy as a feature toggle, not a foundation.

We're building what they won't.

---

## What Intent Is

A real-time chat platform with voice, text, and community features — built from scratch with privacy and performance as architectural decisions, not marketing copy.

- **End-to-end encryption** for DMs and voice (MLS protocol, SRTP)
- **Self-hostable** — run your own instance, own your data, federate with others
- **Lightweight** — sub-80MB RAM idle, native desktop via Tauri
- **Open protocol** — fully documented spec, anyone can build a client
- **Bot-friendly** — SDKs mirror discord.js and discord.py patterns for easy migration
- **WebRTC SFU voice** — low-latency, high-quality, no P2P mesh scaling problems

This isn't a Discord skin. It's a ground-up rethink of how community platforms should work.

---

## Architecture

```
Rust backend (Axum + PostgreSQL + Redis)
  REST API + WebSocket gateway (MessagePack binary protocol)
  WebRTC SFU voice (str0m, TURN/STUN relay)
  64-bit permission bitfields, role-based access control

React 19 web client (TypeScript, Vite, Zustand, Tailwind)
  Real-time via gateway, not polling
  Dark theme, keyboard-driven

Bot SDKs
  intent.js  — TypeScript, mirrors discord.js
  intent.py  — Python, mirrors discord.py

Open protocol spec
  Gateway opcodes, REST endpoints, rate limiting, voice signaling
  OpenAPI 3.1 schema included
```

Everything except the server backend is MIT licensed. The protocol is fully open — build your own client, your own bot, your own tools.

---

## Current Status

**Phase 1 — core platform in active development.**

| Component | Status |
|-----------|--------|
| REST API (servers, channels, messages, roles, invites) | Working |
| WebSocket gateway (MessagePack, heartbeat, events) | Working |
| Permission system (bitfield, role stacking, overrides) | Working |
| Redis event streaming (real-time fan-out) | Working |
| WebRTC SFU voice (str0m) | In progress |
| Web client (React 19) | In progress |
| Bot SDK — intent.js | In progress |
| Bot SDK — intent.py | In progress |
| Desktop client (Tauri) | Planned |
| E2E encryption | Planned |
| Federation | Planned |

Not ready for daily use yet. Building in the open.

---

## Why This Matters

Communities shouldn't have to choose between features and privacy. Right now, every mainstream platform forces that tradeoff.

Discord has the features. But it also has mandatory biometric verification, closed-source clients, 400MB+ RAM usage, and a business model that depends on locking you in.

Matrix and XMPP have the privacy. But the UX gap is real — most communities won't migrate to something that feels like a downgrade.

Intent closes that gap. Feature parity with Discord. Privacy guarantees you can verify. Performance that doesn't eat your RAM.

**You shouldn't need to read a terms of service update to know your conversations are private.**

---

## Get Involved

Every repo has issues tagged and scoped for contributors. Each one has a CONTRIBUTING.md with the workflow, branching conventions, and code standards. CI runs automatically on PRs.

| You are | You can |
|---------|---------|
| **Frontend dev** | Build the web client (React 19, TypeScript, Tailwind) |
| **Systems dev** | Contribute to the protocol spec, audit the architecture |
| **Bot developer** | Port your Discord bots, shape the SDK APIs |
| **Security researcher** | Review the encryption design, find vulnerabilities |
| **Designer** | Help define the UI/UX for a platform people actually want to use |
| **Community leader** | Test with your community, give feedback on what matters |
| **Anyone** | Star the repos, file issues, spread the word |

---

## Repositories

| Repo | What it is | License |
|------|-----------|---------|
| **[intent](https://github.com/IntentAi/intent)** | Project hub, vision, documentation | MIT |
| **[intent-protocol](https://github.com/IntentAi/intent-protocol)** | Full protocol spec — REST, gateway, voice, auth | MIT |
| **[intent-clients](https://github.com/IntentAi/intent-clients)** | Web client (React 19 + TypeScript + Vite) | MIT |
| **[intent.js](https://github.com/IntentAi/intent.js)** | TypeScript bot SDK (discord.js-compatible) | MIT |
| **[intent.py](https://github.com/IntentAi/intent.py)** | Python bot SDK (discord.py-compatible) | MIT |
| **[intent-migrate](https://github.com/IntentAi/intent-migrate)** | Discord migration toolkit | MIT |

Server backend is proprietary — enables sustainable development through managed hosting. Everything you interact with as a user, developer, or bot author is open source.

---

## The Baseline

- No government ID collection
- No biometric scanning
- No selling conversation data
- No closed-source clients
- No vendor lock-in

Privacy isn't a premium tier. It's the default.

---

**Star the repos. Read the protocol. Pick an issue. Build with us.**
