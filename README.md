# Speak It

> "Speak it and it shall be."

Premium, voice-first personal AI assistant prototype for high-value clients.

## Product thesis

One agent handles the user's real-life operational load across voice, text, email, phone, and web. Same context everywhere. External actions are approval-gated.

The client should not think "chatbot." They should notice that email, calls, scheduling, shopping, finances, community, and family logistics are being quietly handled.

## Current prototype

Static HTML/CSS/JS, intentionally deployable to S3/CloudFront without a build step.

- `index.html` — landing page with personalized dashboard handoff
- `dashboard.html` — interactive dashboard prototype
- `landing.html` — previous landing concept, retained for reference
- `generic.html` — earlier full-page concept, retained for reference

## Functional demo behavior

The dashboard now includes:

- persistent demo state via `localStorage`
- personalized client name from landing page query/local storage
- radial navigation across Approvals, Inbox, Calendar, Shopping, Finances, Community, Family, Agent Log
- approval/dismiss/edit actions that mutate state
- agent log updates when actions happen
- voice-command simulation through the center orb
- simple command parser for purchases, calendar moves, inbox summaries, and custom tasks
- reset-demo control

## Live surfaces

- Landing: https://demo.gopherdrones.com/
- Dashboard: https://demo.gopherdrones.com/dashboard/
- Mirror: http://jimsbots.com/ and `/dashboard/`

## Underlying stack context

Not implemented in this static repo, but this is the target architecture:

- **Leo** — OpenAI Realtime voice agent, Twilio inbound, running via Mercury at `mercury.gopherdrones.com`
- **Mercury** — Rails control plane at `/home/jimasaur/Mercury`, SQLite, services `mercury-app.service` + `mercury-tunnel.service`
- **Grumpy** — local OpenClaw agent (`--profile grumpy`), Mercury reasoning/execution sidecar via `OPENCLAW_PROFILE=grumpy`
- Post-call sidecar creates `SidecarEvent` + `ActionDraft`; Grumpy heartbeat polls and acts

## Next build steps

1. Pick a final name. "Speak It" is a placeholder.
2. Replace hardcoded demo data with a static JSON profile/action model.
3. Add a client-page generator for `[name].jimmys.tools` style demos.
4. Wire a real Mercury API read-only endpoint for action drafts/log events.
5. Add a real voice capture/demo path or simulated transcript playback.

## Direction

Premium, calm, capable, dark UI, purple/gold palette. Not chatbot-bro energy. Invisible infrastructure feel.
