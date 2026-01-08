# Sphinixx (working title)

An in-progress ECS-based 2D game engine and live interactive streaming platform.

This project is designed to power **chat-driven, audience-participation games and live shows**, where viewers can directly influence gameplay through chat, polls, donations, and semantics — in real time.

This is **not** a finished engine or SDK.
It is an actively developed platform exploring how games, streamers, and audiences can co-create live experiences.

---

## What Is This?

At its core, Sphinixx is a **live interactive show runner** disguised as a game engine.

It combines:
- A custom ECS-based 2D engine
- High-performance batched rendering
- AI-driven agents and avatars
- Live chat ingestion (Twitch / YouTube)
- Polls, donations, and semantic triggers
- Multiple game modes and state machines
- Built-in tooling for debugging, profiling, and iteration

The goal is to make **the audience a first-class participant**, not just a passive viewer.

---

## What Can It Do?

The platform supports (at various levels of maturity):

- Chat-controlled gameplay (commands, voting, semantics)
- Donation- and reward-triggered events
- AI agents (boids, GOAP-based behaviours)
- Multiple concurrent game modes:
  - Lemmings-inspired viewer-controlled simulations
  - Game shows (Trivia, Genie-style formats)
  - Roleplay-driven experiences
  - Instance-based chaos/survival modes
- Streamer-facing progression and loyalty systems
- Modular HUD and UI components
- In-game debug, metrics, and profiling tools

Most systems are built to be **composable**, not bespoke.

---

## Project Status

This repository documents work completed over roughly **one year of solo development**.

Not everything listed is:
- finished
- stable
- intended for public use

Some systems exist as prototypes, stress tests, or architectural experiments.
Others are production-ready but lack polish.

Expect:
- rough edges
- deprecated systems
- TODOs and unanswered questions

That is intentional and honest.

---

## Inspirations

This project draws inspiration from:

- **Twitch Plays Pokémon** — large-scale audience-controlled gameplay
- **Lemmings** — simple agents, emergent outcomes
- Live game shows and audience participation formats
- Crowd-controlled chaos mods and social experiments
- ECS-driven simulation engines prioritizing scale and composability

---

## Who Is This For?

- Streamers who want deeply interactive formats
- Viewers who enjoy collective chaos and participation
- Developers interested in ECS, simulation, and live systems
- Experimental game designers and event creators

This is **not** trying to be a general-purpose game engine.
It is purpose-built for live, social, chaotic experiences.

---

## Team

Currently developed by a single engineer.

Additional collaborators (art, audio, moderation, tooling) may be involved
on a per-mode or per-project basis as the platform evolves.

---

## Repo Contents

- `what_is_this.md` — detailed architecture and system overview
- Engine-level core systems (ECS, rendering, input, profiling)
- Game-level compositions, modes, and experiments
- Tooling for debugging, metrics, and live iteration

Code and documentation will be reorganized and expanded as the project matures.

---

## Disclaimer

This is an evolving project.
APIs will change.
Systems will be rewritten.
Some ideas will be abandoned.

The purpose of this repo is to document intent, architecture, and progress —
not to present a finished product.

---

## License

TBD.
