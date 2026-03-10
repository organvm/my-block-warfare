# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**TurfSynth AR** - A location-based AR game concept blending GTA/Schedule I turf dynamics with Pokémon Go collection mechanics. The core differentiator is **environmental synthesis**: the user's real-world surroundings generate visuals, animations, sounds, and creatures procedurally.

This repository contains:
- **Theoretical specifications** (`TurfSynth-AR-Concept.md`) - Product design, game mechanics, scaling estimates
- **Prototype apps** (from Google AI Studio) - Proof-of-concept spatial/map tools

## Repository Structure

```
my-block-warfare/
├── TurfSynth-AR-Concept.md      # Master product specification
├── specs/                        # Feature specifications (SDD approach)
├── mcp-maps-3d/                  # 3D map tool using Gemini + MCP
└── spatial-understanding/        # Spatial detection tool using Gemini
```

## Development Commands

Both prototype apps use Vite + TypeScript:

```bash
# mcp-maps-3d (LitElement + MCP + Google Maps)
cd mcp-maps-3d
npm install
npm run dev      # Start dev server
npm run build    # Production build

# spatial-understanding (React + Jotai + Tailwind)
cd spatial-understanding
npm install
npm run dev      # Start dev server
npm run build    # Production build
```

**Required**: Set `GEMINI_API_KEY` in each app's `.env.local` file.

## Architecture Patterns

### mcp-maps-3d
- **MCP (Model Context Protocol)** architecture: Server exposes map tools, client relays AI function calls
- LitElement web components (`MapApp`)
- In-memory transport linking MCP client/server
- Gemini 2.5 Flash for natural language → map actions

### spatial-understanding
- React 19 with Jotai for atomic state management
- Atoms defined in `atoms.tsx`, hooks in `hooks.tsx`
- Detection modes: 2D bounding boxes, 3D bounding boxes, segmentation masks, points
- Supports live screenshare and static image analysis

## Specification-Driven Development

This project uses the **speckit** methodology. Specifications live in `specs/` and drive implementation:

```bash
/speckit.specify <feature>    # Create feature specification
/speckit.plan <tech-context>  # Generate implementation plan
/speckit.tasks                # Generate executable task list
```

Key concept: Specifications are truth, code is generated output.

## Key Technical Decisions

- **Privacy-by-design**: Store/transmit only "Place Fingerprints" (low-dimensional vectors), never raw camera/audio
- **Geofencing**: Server-side exclusion of sensitive locations (schools, hospitals, private residences)
- **Anti-cheat**: GPS spoof detection, movement plausibility, influence submission validation
- **Synthlings**: Procedural creatures with attributes derived from environment scans (palette, geometry, motion, sound)

## Deployments

| Prototype | URL | Platform |
|-----------|-----|----------|
| `mcp-maps-3d` | https://turfsynth-mcp-maps.pages.dev | Cloudflare Pages |
| `spatial-understanding` | https://turfsynth-spatial.pages.dev | Cloudflare Pages |

<!-- ORGANVM:AUTO:START -->
## System Context (auto-generated — do not edit)

**Organ:** ORGAN-III (Commerce) | **Tier:** standard | **Status:** PUBLIC_PROCESS
**Org:** `organvm-iii-ergon` | **Repo:** `my-block-warfare`

### Edges
- **Produces** → `unspecified`: product
- **Produces** → `organvm-vi-koinonia/community-hub`: community_signal
- **Produces** → `organvm-vii-kerygma/social-automation`: distribution_signal

### Siblings in Commerce
`classroom-rpg-aetheria`, `gamified-coach-interface`, `trade-perpetual-future`, `fetch-familiar-friends`, `sovereign-ecosystem--real-estate-luxury`, `public-record-data-scrapper`, `search-local--happy-hour`, `multi-camera--livestream--framework`, `universal-mail--automation`, `mirror-mirror`, `the-invisible-ledger`, `enterprise-plugin`, `virgil-training-overlay`, `tab-bookmark-manager`, `a-i-chat--exporter` ... and 12 more

### Governance
- Strictly unidirectional flow: I→II→III. No dependencies on Theory (I).

*Last synced: 2026-03-08T20:11:34Z*

## Session Review Protocol

At the end of each session that produces or modifies files:
1. Run `organvm session review --latest` to get a session summary
2. Check for unimplemented plans: `organvm session plans --project .`
3. Export significant sessions: `organvm session export <id> --slug <slug>`
4. Run `organvm prompts distill --dry-run` to detect uncovered operational patterns

Transcripts are on-demand (never committed):
- `organvm session transcript <id>` — conversation summary
- `organvm session transcript <id> --unabridged` — full audit trail
- `organvm session prompts <id>` — human prompts only


## Active Directives

| Scope | Phase | Name | Description |
|-------|-------|------|-------------|
| system | any | prompting-standards | Prompting Standards |
| system | any | research-standards-bibliography | APPENDIX: Research Standards Bibliography |
| system | any | research-standards | METADOC: Architectural Typology & Research Standards |
| system | any | sop-ecosystem | METADOC: SOP Ecosystem — Taxonomy, Inventory & Coverage |
| system | any | autopoietic-systems-diagnostics | SOP: Autopoietic Systems Diagnostics (The Mirror of Eternity) |
| system | any | cicd-resilience-and-recovery | SOP: CI/CD Pipeline Resilience & Recovery |
| system | any | cross-agent-handoff | SOP: Cross-Agent Session Handoff |
| system | any | document-audit-feature-extraction | SOP: Document Audit & Feature Extraction |
| system | any | essay-publishing-and-distribution | SOP: Essay Publishing & Distribution |
| system | any | market-gap-analysis | SOP: Full-Breath Market-Gap Analysis & Defensive Parrying |
| system | any | pitch-deck-rollout | SOP: Pitch Deck Generation & Rollout |
| system | any | promotion-and-state-transitions | SOP: Promotion & State Transitions |
| system | any | repo-onboarding-and-habitat-creation | SOP: Repo Onboarding & Habitat Creation |
| system | any | research-to-implementation-pipeline | SOP: Research-to-Implementation Pipeline (The Gold Path) |
| system | any | security-and-accessibility-audit | SOP: Security & Accessibility Audit |
| system | any | session-self-critique | session-self-critique |
| system | any | source-evaluation-and-bibliography | SOP: Source Evaluation & Annotated Bibliography (The Refinery) |
| system | any | stranger-test-protocol | SOP: Stranger Test Protocol |
| system | any | strategic-foresight-and-futures | SOP: Strategic Foresight & Futures (The Telescope) |
| system | any | typological-hermeneutic-analysis | SOP: Typological & Hermeneutic Analysis (The Archaeology) |
| unknown | any | gpt-to-os | SOP_GPT_TO_OS.md |
| unknown | any | index | SOP_INDEX.md |
| unknown | any | obsidian-sync | SOP_OBSIDIAN_SYNC.md |

Linked skills: evaluation-to-growth


**Prompting (Anthropic)**: context 200K tokens, format: XML tags, thinking: extended thinking (budget_tokens)

<!-- ORGANVM:AUTO:END -->


## ⚡ Conductor OS Integration
This repository is a managed component of the ORGANVM meta-workspace.
- **Orchestration:** Use `conductor patch` for system status and work queue.
- **Lifecycle:** Follow the `FRAME -> SHAPE -> BUILD -> PROVE` workflow.
- **Governance:** Promotions are managed via `conductor wip promote`.
- **Intelligence:** Conductor MCP tools are available for routing and mission synthesis.
