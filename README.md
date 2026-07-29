# Deep Travel Guide

A Claude skill for generating deeply researched, beautifully curated travel guides — closer to a professionally written travel book than an AI-generated itinerary.

Built for [Claude](https://claude.com) (claude.ai, Claude Code, Claude Cowork). Drop this folder into a skills directory and Claude will use it automatically for trip planning, itinerary, or "where should I stay / what should I see" requests.

## What makes this different from a typical itinerary generator

Most AI travel itineraries maximize attraction count: a list of everything worth seeing, with little sense of trade-offs. This skill is built around the opposite principle — **every recommendation has an opportunity cost.** A traveler's time, attention, and energy are limited, and the job of a good guide is curation, not coverage.

Concretely, the skill:

- **Adapts its structure to the trip** rather than forcing every destination into the same template (weekend city break vs. a multi-week regional trip produce genuinely different guides)
- **Verifies facts with live search** rather than relying on training data for prices, hours, visa rules, and seasonal risk
- **Uses a consistent editorial priority system** (★★★ Essential / ★★☆ Strongly Recommended / ★☆☆ If Convenient) applied to attractions, restaurants, neighborhoods, and accommodation alike, with every rating carrying its own justification
- **Actively protects against FOMO** — a family of named editorial devices (Skip Without Regret, Same Magic Fewer Crowds, What You're Actually Paying For) that tell a traveler plainly when it's fine to skip something famous, redirect to a genuinely comparable alternative, or know what they're actually paying for — without ever narrating that it's doing so
- **Thinks about emotional pacing**, not just logistical pacing — anticipation, surprise, and rest after intensity, not just avoiding an exhausting schedule
- **Adapts to themed trips** (a football-focused trip, a food trip, a family trip with kids, reduced mobility) by reshaping its standing sections — accommodation, food, practicalities — rather than deleting or over-explaining them
- **Delivers a finished document** — a Word (.docx) file by default, Markdown if a docx tool isn't available — not a wall of chat text

## Structure

```
deep-travel-guide/
├── SKILL.md                 # core workflow, philosophy, priorities, writing style, output format
├── references/
│   ├── audiences.md         # Traveling with Kids / Traveling with Reduced Mobility — loaded only when relevant
│   └── devices.md           # full definitions of the 8 editorial decision-support tools
├── LICENSE
└── README.md                # this file
```

SKILL.md tells the model exactly when to read each reference file — they aren't optional background reading, they're loaded on an explicit trigger (e.g. "if the trip explicitly involves children... read `references/audiences.md`"). This keeps the resident cost lower for the common case while keeping conditional content reliable rather than something the model has to remember unprompted.

It relies on the host environment providing:

- Web search (for research and verification)
- Document creation (for the final .docx output; falls back to Markdown if unavailable)
- A places/maps tool (optional, for confirming locations)

## Installation

Copy this whole folder into your skills directory, keeping the folder name `deep-travel-guide` and the `references/` subfolder intact:

```
your-skills-directory/
└── deep-travel-guide/
    ├── SKILL.md
    ├── references/
    │   ├── audiences.md
    │   └── devices.md
    ├── LICENSE
    └── README.md
```

For Claude.ai / Claude Cowork, this typically means uploading the folder as a custom skill. For Claude Code, place it under your project or user-level skills path per the [Claude Code skills documentation](https://docs.claude.com).

## Usage

Just describe the trip:

> Plan a 10-day trip to Japan in April — my first visit, mid-range budget, traveling as a couple, interested in food and photography.

The skill will ask clarifying questions only where missing information would materially change the guide, then research, draft, and deliver a finished document.

## Design philosophy

See the top of `SKILL.md` for the full editorial philosophy. The short version: **the best trips are not those where the traveler sees the most, but those where they understand the most.** Every section of the skill exists to serve that idea — including knowing what to leave out.

## Version

Current version: 5.1 (see version header inside `SKILL.md` — kept in sync with this README on every release).

## License

MIT — see `LICENSE`.
