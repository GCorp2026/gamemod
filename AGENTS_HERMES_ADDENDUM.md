# Hermes / OpenClaw Addendum (added by gamemod-2026-10-21 batch)

This wrapper makes **universal-modder** usable inside the Hermes agent harness
without forking it. The original repo lives at
https://github.com/rehan-remade/universal-modder — every original SKILL.md,
AGENTS.md, plugin.json, .mcp.json, pyproject.toml, LICENSE is byte-identical
to upstream at commit (downloaded 2026-10-21T20:35Z; sha256 listed in
`mempalace/wings/gamemod-2026-10-21/wing.json`).

## What this wrapper adds

1. **Nine surface sidecars** at
   `repos/game-loop/{harness,mcp,second_brain,vault,bot_loop,diamond_graph,bench,fable_bench,appfactory}/scripts/`
   each wrapping the universal-modder loop so the 24/7 game desk can dispatch
   it through any surface.
2. **One dispatch orchestrator** at
   `~/.hermes/skills/orchestrator-game-gamemod/scripts/run.py` (env-gate
   `JEV_GAME_MOD=1`, byte-identical-when-off).
3. **10 game-* primitives** in `~/.hermes/skills/game-*` (one per upstream
   skill: game-mod-any-game, game-mod-recon, game-mod-fal-assets, game-mod-asset-pipeline,
   game-mod-reverse-engineering, game-mod-game-automation, game-mod-showcase-video,
   game-mod-mashup-mods, game-mod-publish-mod, game-mod-share-field-notes).
   Each ≤350 L, stdlib-only where the upstream skill allows, env-gated, byte-identical-when-off.
4. **JEV-everywhere wrapper** at
   `~/.hermes/skills/game-mod-jev-tier-wrap/` — wraps every primitive
   with JEV Noul (admission), JEV Choice (route), JEV Score (post-execution).
5. **One mempalace wing** at
   `~/.openclaw/mempalace/wings/gamemod-2026-10-21/` — 7 files minimum
   (wing.json, EPIC.md, STORIES.md, ACS.md, ISSUES.md, FINDINGS.md, ELI5.html).
6. **One published skill bundle** at
   `~/.hermes/skill-store/gamemod-2026-10-21/1.0.0/`
   with per-file sha256 + `tree_sha256` (PIT #259).
7. **Oracle kanban capture** with project=game-loop + batch=gamemod-2026-10-21
   (1 epic + 16 stories + 33 ACs + 8 issues).

## Governance: this is the only allowed shape

Per the operator directive of 2026-10-21, this wrapper IS the integration
contract. Any new game-* skill MUST:
- live in `~/.hermes/skills/game-*`,
- have one sidecar on each of the 9 surfaces,
- be wired into the 16 sales families via `sales-aleia-office-family-bus`,
- be planned by `sales-chief-of-staff-recipe-orchestrator` (12-stage FSM),
- be checked against `sales-charter-spec-extractor`,
- be wrapped by JEV Noul/Choice/Score,
- be no longer than 350 lines (universal-modder vendored scripts are exempt).

## Hard scope (universal-modder CONTRIBUTING.md)

- Single-player games the user owns, OR multiplayer/private servers they run.
- Never ship game files, decompiled code, or game-asset extraction.
- Never write online cheats (aimbots, ESP, speed hacks).
- Never bypass anti-cheat, DRM or ownership checks.
- Ask before driving the mouse / keyboard, installing loaders, or publishing.
