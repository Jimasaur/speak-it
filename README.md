# Speak It

> "Speak it and it shall be."

Premium, voice-first personal AI assistant prototype for high-value clients.

## Product thesis

The agent speaks and listens as the primary interface. The screen is not a control panel; it is a calm approval surface for the few moments that need judgment.

The client should not think "chatbot." They should notice that email, calls, scheduling, shopping, finances, community, and family logistics are being quietly prepared or handled.

## Current prototype

Static HTML/CSS/JS, intentionally deployable behind Caddy/S3/CloudFront without a build step.

- `index.html` — Sarah-specific landing page
- `dashboard/index.html` — final approval-surface dashboard, based on the top-three card stack
- `dashboard-card.html` — alternate single-card experiment, retained for comparison
- `dashboard-stack.html` — source variant used for the final dashboard
- `dashboard-radial.html` — earlier radial-nav concept, retained for comparison
- `dashboard.html` — earlier tabs/list dashboard, retained for comparison
- `variants.html` — local variant picker; not required for public deployment

## Final demo behavior

The public demo focuses on the new modality:

- Sarah-personalized landing page
- top-three approval stack instead of broad navigation
- active context halo showing where proposals came from
- `Yes`, `Change`, and `Not now` actions
- `Not now` behaves as snooze semantics, not deletion
- quiet activity log
- simulated voice-command orb that drafts new proposals
- persistent demo state via `localStorage`

## Deployment target

Requested public host:

- `https://sarah.gatherwell.tools/`

DNS currently points at GatherWell EC2 (`3.132.63.35`). Deploy by serving this static directory from the GatherWell Caddy container under a dedicated `sarah.gatherwell.tools` site block.

## Underlying stack context

Not implemented in this static repo, but this is the target architecture:

- **Leo** — OpenAI Realtime voice agent, Twilio inbound, running via Mercury
- **Mercury** — Rails control plane and ActionDraft store
- **Grumpy** — local OpenClaw agent / execution sidecar
- **Skippy** — coordination, product direction, and demo polish
- External actions remain approval-gated.

## Next build steps

1. Decide whether `Speak It` is the final name or a demo codename.
2. Replace hardcoded demo data with a static JSON profile/action model.
3. Wire a read-only Mercury endpoint for action drafts/log events.
4. Add real voice capture or transcript playback.
5. Generate per-client demo pages from profile data.

## Direction

Premium, calm, capable, dark UI, purple/gold palette. Not chatbot-bro energy. Invisible infrastructure feel.
