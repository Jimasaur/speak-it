# Speak It

> "Speak it and it shall be."

A voice-first personal assistant experience prototype focused on clear action review and calm interaction design.

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

The dashboard includes:

- persistent demo state via `localStorage`
- personalized client name from landing-page query/local storage
- action filters for Needs your OK, Handled, Prepared, and Everything
- review and approval interactions that update the demo state
- a text-request form for adding simulated assistant tasks
- activity updates and a reset-demo control

The current interaction is text-driven; live microphone capture and provider-backed voice execution are not implemented here.

## Explore locally

From the repository root:

```bash
python3 -m http.server 4173 --bind 127.0.0.1
```

Open `http://127.0.0.1:4173/`. Demo actions update browser state only; they do not send messages, place orders, move money, or change a real calendar. Use fictional names and requests while exploring, since demo state is saved in this browser's `localStorage`.

## Architecture boundary

This repository contains the static experience prototype. A real deployment would require an authenticated backend, a voice provider, scoped integrations, and server-side approval and audit controls. Those services are outside this repository; the UI is not evidence that they are connected.

## Next build steps

1. Pick a final name. "Speak It" is a placeholder.
2. Replace hardcoded demo data with a static JSON profile/action model.
3. Add a client-page generator for `[name].jimmys.tools` style demos.
4. Wire a real Mercury API read-only endpoint for action drafts/log events.
5. Add a real voice capture/demo path or simulated transcript playback.

## Direction

Premium, calm, capable, dark UI, purple/gold palette. Designed to make the next action and its approval state easy to understand.
