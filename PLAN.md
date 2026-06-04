# PLAN — Anima Stewardship

A research-grounded redesign of how a Bolter anima manages a standing responsibility,
plus an ADHD-friendly website to present it to the team.

## Why this exists
Today an anima "owns" a responsibility by self-scheduling a cron/`runAt` task and
re-running a loop. Two compounding problems make that unreliable at the horizons
Bolter promises ("just works", days/weeks, no babysitting):

1. **The decay function** — AI quality drops as context grows (effective context ≪
   advertised) and errors compound over long autonomous trajectories. A self-scheduled
   loop maximizes *both* bad variables: long accumulating context AND long trajectories.
2. **Looping ≠ progress** — a timer tells you *when* to act, never *whether you're getting
   anywhere*. There is no charter, no acceptance criteria, no durable per-responsibility
   state, no "done". The anima grades its own homework against a one-line description and
   drifts.

## Deliverable
A single, self-contained, ADHD-friendly web page (`index.html`) that:
- States the problem in plain language with a 30-second TL;DR.
- Quantifies the two forces with real research numbers (stat cards + citations).
- Summarizes the literature (context rot, agentic decay, progress assessment,
  scheduling paradigms, memory/re-grounding, multi-agent) with progressive-disclosure
  deep dives.
- Proposes "Stewardship": a 6-pillar redesign.
- Maps each pillar to concrete Bolter changes (schema, scheduler, tools, system prompt).
- Names risks, tradeoffs, and explicit non-goals.

Published to a GitHub repo with an unguessable slug + GitHub Pages → a "secret" URL the
team can open. Verified live via agent-browser before being declared done.

## The proposal in one screen — "Stewardship"
Reframe a responsibility from *a recurring alarm* into *a durable, verifiable,
event-driven object an anima tends*.

- **P1 Charter, not a cron string** — intent + acceptance criteria + scope, defined once,
  recited every beat.
- **P2 Durable working state, not chat archaeology** — a compact anima-maintained state
  record + append-only beat ledger; re-ground from this, not from decaying chat.
- **P3 Wake on signals, not just the clock** — first-class event triggers; dormant-until-
  signaled; cron only for genuinely periodic beats; heartbeat as a reasoning gate.
- **P4 Progress judged against criteria by a fresh lens** — each beat ends with an explicit
  assessment in clean context (not self-narration); real states: advancing/stable/blocked/done.
- **P5 Adaptive cadence + honest escalation** — next-wake chosen from assessed state within
  guardrails; budgets + circuit breakers; surface a crisp ask when blocked.
- **P6 Short fresh beats; delegate reads, serialize writes** — minimize both decay variables;
  fresh-context sub-beats for parallel investigation; single-threaded decisions.

## Bolter mapping (for the team to build)
- Evolve `scheduled_tasks` → richer responsibility object (charter/acceptance/state/status/
  nextWakeAt/triggers/budget).
- New `responsibility_beats` append-only ledger (retires the vestigial checkpoint fields).
- `scheduler.ts`: keep cron/timer; add event-trigger subscription + adaptive next-wake;
  heartbeat reasoning-gate job.
- `run-scheduled-job.ts` → run-beat: re-ground from charter+state+last-K ledger, work,
  verifier pass, write ledger + compact state + next-wake.
- New tools: set_charter, update_responsibility_state, set_next_beat, watch_event,
  escalate_to_owner.
- `system-prompt.ts`: recite charter+acceptance+state+last beat at the TOP of beat context.

Reuse existing `dispatch_jobs` queue, `dispatch_complete` waiters, memory infra, and the
event sources already captured in-process — do not stand up parallel systems or duplicate
event sources. Aggressive cutover, not a parallel migration.

## Non-goals
- A generic workflow engine. Per-anima concurrency caps. Timing-gate "fixes". Rate limiting
  of multi-anima interaction. These are explicitly out.

## Status
See README.md for the live URL and repo.
