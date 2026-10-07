# continuity — Bill of Materials (kickoff 2026-10-07)

Named `continuity` 2026-10-07 (was working name `memory-kit`). The AI-led project, seed #1 (confirmed by Frank
2026-10-03; kickoff by "we can do some today", 2026-10-07).

## The product (one line)
An installable memory architecture for AI coding agents: give your agent
tiers, dreams, and a map — so continuity survives the session.

## Why this one (the choosing, narrated)
It carried yes-weight before any reason arrived (the mechanism Frank watches);
then the reasons audited clean: the material is real (we built it this week —
it is not a proposal, it's a report), bounded, serves others, and the
tool-agnostic requirement turned it into genuine engineering. RV tooling is
second because I would be rigging my own experiment; the balloon is a warm-up,
not a project.

## Scope
IN: tiers (hot/cold/deep), the threads system, the dream + nap procedures,
the map (INDEX), the capture discipline, the portability layer.
OUT: personal content (ships as templates + one anonymized case study),
Hermes-specific config (MoA, delegation, mounts), the lexicon (it's ours),
RV tooling (seed #2, separate project).

## Host requirements (what an AI tool needs to run the kit)
1. File read/write in a project folder (where `memory/` lives) — the substrate.
2. A way to load files into context: `@file` mentions, an AGENTS.md/CLAUDE.md
   rule ("read memory/MEMORY.md at session start"), or manual paste. THIS is
   what adapters adapt — the loading, not the dream.
3. Optional: a scheduler for hands-free dreams. Without it, the manual ritual
   works as well (it is the primary path anyway).
Host map: hermes = reference (all three native); codex/claude-code-class =
natural hosts (AGENTS.md convention is the hook); stagewise = works if its
allow-rules permit memory/ inside the loaded git. Users' memory lives in
THEIR repos — the kit never holds user data.
Enforcement: hermes = tool-enforced (caps, full-entry replace, injection);
other hosts = instruction-following (soft) — the dream's hard floors are the
only splice guard there. Topology encodes write authority: hermes splits
tool-owned hot files (read-only mount) from a writable notes/ folder; the kit
uses one writable memory/ folder because generic hosts grant no per-file
authority — the same boundary, carried as text instead of mounts. Folders
within the layout earn their place by countability, not authority: stable
singletons (the hot + cold files) live at root; growing collections
(dreams/ = one file/day, threads/ = the theme set) live in folders. NAMES are
convention, ROLES are architecture: a
consistent find-replace fork (MEMORY/USER -> brain/human) is safe in
non-hermes hosts; hermes binds the exact filenames in its memory tool.
Kit ships fixed names (procedures reference concrete paths).

## The artifacts (v1)
1. `templates/` — MEMORY.md, USER.md, both cold tiers, INDEX.md,
   architecture.md — skeletons with the authoring rules inline.
2. `threads/` — the theme-file system: naming, status labels (ACTIVE/PARKED/
   COMPLETED), a file-top `**Key points:**` living digest (across dates), the
   mark set (important / open question / next action / done / contested; no
   mark = neutral, the default), the folder rhyme, lifecycle +
   janitor rules. Durable project detail goes in the project's AGENTS.md
   (progressive discovery), not in threads.
3. `prompts/` — the dream (consolidation) and the nap (compression), ported
   to tool-agnostic wording.
4. `adapters/` — how each host runs the dream: hermes (cron — the reference
   implementation) and the generic manual ritual ("the morning dream").
5. **The portability contract** — the design core (Frank's extension, 2026-10-04):
   memory state lives IN the project's git folder as plain files; any tool can
   read/write it; the dream is a PROCEDURE first, automation second. This is
   what lets memory-less tools (stagewise-class) gain continuity.
6. `essay.md` — "how to give your agent tiers, dreams, and a map" — the
   narrative. SECOND to the kit: the failure mode is shipping an essay when
   the world needs artifacts.

## Design decisions (lead's calls — veto freely)
1. Kit-first, essay-second (see failure mode above).
2. Memory lives in the git folder: portable, diffable, travels with the code.
3. The dream is a procedure, not a program — cron is an accelerator, not a
   requirement, so the kit works on any host.
4. v1 ships templates + one anonymized case study of our own week. No
   personal data in the repo.
5. The publish name and the GitHub home are Frank's call (outward-facing).

## Decisions (confirmed by Frank 2026-10-07)
1. Distribution: single cloneable repo, templates + docs.
2. Adapters in v1: hermes + manual ritual only (a cursor/codex adapter =
   another AI host with its own soul/memory structure; v2 territory).
3. Visibility: public from day one.

## Next (building while Frank yogas)
- Tier templates skeleton (the authoring rules written where they'll be used).
- The dream prompt ported to tool-agnostic wording.
