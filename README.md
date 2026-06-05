# Anima Stewardship

A research-grounded redesign of how a Bolter anima manages a standing responsibility —
presented as a single, self-contained, ADHD-friendly web page.

**Live (secret) URL:** https://felttippen123.github.io/stewardship-36fd628d/
**Source:** https://github.com/feltTipPen123/stewardship-36fd628d (public, unguessable slug — share the link, don't circulate)

## TL;DR
Today an anima owns a responsibility by self-scheduling a timer and re-running a loop.
That fights two documented forces at once — AI quality **decays as context grows**, and
**a loop never tells you whether you're making progress**. The proposal ("Stewardship")
reframes a responsibility as a **durable, verifiable, event-driven object an anima tends**:
a charter, a compact memory, signal-driven wakeups, and a fresh-eyes progress check — so
it just works, and knows when to ask.

See [`PLAN.md`](./PLAN.md) for the full plan and the six-pillar summary.

## Files
- `index.html` — the proposal. Self-contained (CDN fonts only); open it directly or serve statically.
- `atlas.html` — **Codebase Atlas**: an 11-stop guided tour of the load-bearing areas, domain model, and key routines underpinning the change surface, with verbatim code inline. Live: `…/stewardship-36fd628d/atlas.html`. Cross-linked from the proposal.
- `PLAN.md` — the plan, the proposal in one screen, and the Bolter code mapping.
- `README.md` — this file.

## What's inside the page
1. How an anima holds a responsibility today (straight from the codebase).
2. The two forces the loop fights — the decay function + "looping ≠ progress" — with real stats.
3. What the field figured out (six patterns, with deep-dive collapsibles + 40+ citations).
4. The proposal: **Stewardship**, six pillars.
5. What it means in the codebase (schema, scheduler, run-beat, tools, system prompt).
6. A beat, end to end.
7. Tradeoffs and explicit non-goals.
8. References.

## ADHD-friendly design choices
30-second TL;DR up top · per-section "in one line" callouts · progressive disclosure
(deep dives collapsed by default) · scannable stat cards · sticky progress bar + dot-nav ·
estimated read times · `prefers-reduced-motion` respected · calm warm palette, high contrast.

## Run locally
```bash
cd anima-stewardship
python3 -m http.server 8080   # then open http://localhost:8080
```

## Deploy
Source is pushed to GitHub and served via GitHub Pages at an unguessable repo slug
(an effectively secret URL the team can open). Verified live via agent-browser before
being declared done.
