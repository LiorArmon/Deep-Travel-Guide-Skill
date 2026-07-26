# Deep Travel Guide

A Claude skill for generating deeply researched, beautifully curated travel guides — closer to a professionally written travel book than an AI-generated itinerary.

Built for [Claude](https://claude.com) (claude.ai, Claude Code, Claude Cowork). Drop `SKILL.md` into a skills directory and Claude will use it automatically whenever a trip-planning request comes up.

## What makes this different from a typical itinerary generator

Most AI travel itineraries maximize attraction count: a list of everything worth seeing, with little sense of trade-offs. This skill is built around the opposite principle — **every recommendation has an opportunity cost.** A traveler's time, attention, and energy are limited, and the job of a good guide is curation, not coverage.

Concretely, the skill:

- **Adapts its structure to the trip** rather than forcing every destination into the same template (weekend city break vs. a 24-night multi-region itinerary produce genuinely different guides)
- **Verifies facts with live search** rather than relying on training data for prices, hours, visa rules, and seasonal risk
- **Uses a consistent editorial priority system** (★★★ Essential / ★★☆ Strongly Recommended / ★☆☆ If Convenient) applied to attractions, restaurants, neighborhoods, and accommodation alike
- **Actively protects against FOMO** — telling a traveler plainly when it's fine to skip something famous, without narrating that it's doing so
- **Thinks about emotional pacing**, not just logistical pacing — anticipation, surprise, and rest after intensity, not just avoiding an exhausting schedule
- **Adapts to themed trips** (a football-focused trip, a food trip, a family trip with kids) by reshaping its standing sections — accommodation, food, practicalities — rather than deleting them
- **Delivers a finished Word document** (.docx), not a wall of chat text, using Claude's document-creation tools

## Structure

```
deep-travel-guide/
├── SKILL.md      # the skill itself
└── README.md     # this file
```

`SKILL.md` is self-contained — there are no supporting scripts or assets. It relies on the host environment providing:

- Web search (for research and verification)
- Document creation (for the final .docx output)
- A places/maps tool (optional, for confirming locations)

## Installation

Copy `SKILL.md` into your skills directory, keeping the folder name `deep-travel-guide`:

```
your-skills-directory/
└── deep-travel-guide/
    └── SKILL.md
```

For Claude.ai / Claude Cowork, this typically means uploading the folder as a custom skill. For Claude Code, place it under your project or user-level skills path per the [Claude Code skills documentation](https://docs.claude.com).

## Usage

Just describe the trip:

> Generate a deep travel guide for a 10-day trip to Japan in April — my first visit, mid-range budget, traveling as a couple, interested in food and photography.

The skill will ask clarifying questions only where missing information would materially change the guide, then research, draft, and deliver a finished Word document.

## Design philosophy

See the top of `SKILL.md` for the full editorial philosophy. The short version: **the best trips are not those where the traveler sees the most, but those where they understand the most.** Every section of the skill exists to serve that idea — including knowing what to leave out.

## Version

Current version: 2.0 (see version header inside `SKILL.md`).

## License

MIT — see `LICENSE`.
