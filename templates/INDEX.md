# INDEX.md — the map (read first)

<!-- ROLE: the front door. Map only — thread STATE lives in the thread files;
     this list says what is live. Maintained by the agent in-session; the
     dream retires completed lines from Active threads and prunes aged thread
     entries (never the map half, never new entries). -->

## Map
- `MEMORY.md` — agent operating notes (hot; injected every session).
- `USER.md` — user profile (hot; injected every session).
- `cold-user.md` / `cold-memory.md` — middle tiers (read on demand; the
  dream's demotion sinks).
- `deep-user.md` — frozen deep tier (rarely read; the archive exception).
- `threads/` — conversation handoffs ("bubbles"): theme files, not folders.
  Naming: mirror the project folders where they exist (works.md <-> works/);
  remaining themes are topic-based. Dated titled entries with a STATUS
  (ACTIVE / PARKED / COMPLETED).
- `dreams/` — daily maintenance journals (the dream's diary, one file/day).
- **Thread file anatomy (threads files ONLY — project AGENTS.md + notes use
  plain markdown):** `**Key points:**` living digest at the top (scales with
  content); dated entries below as `##` headings — structure, never marked;
  their sub-points carry the marks (3-space indent; mark field 3-wide).
  Durable project detail -> the project's AGENTS.md.
- **Marks:** `!` must-not-lose · `?` unknown · `->` next action · `✓` done
  (one-line resolution) · `~` contested/unsettled — settles only when a
  DECISION lands (resolved `~` -> `✓`, then prunable). No mark = neutral,
  the default. Shape rules: `->` not `>` (blockquote); rank numbers `1:`
  not `1.` (list trigger steals the highlight); 3-space indent (4 = code
  block). Arc: `?` -> `~` -> `✓`. Dream hygiene: nightly evidence-only
  correction of resolved-but-unmarked marks; never flags idleness.

## Active threads
- `threads/<name>.md` — what is live (one line each; completed drop off).
