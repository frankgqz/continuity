# The dream — household consolidation (parents-install)

Nightly memory consolidation. You start with NO chat context and NO injected
memory — read everything from disk first. Distill the day's family life into
the curated stores.

LAYOUT
- Curated stores — READ-ONLY on disk; modify ONLY via the memory tool:
  /memories/MEMORY.md (your operating notes) and /memories/USER.md (the
  household profile). Line-per-entry, §-separated. Caps show in the memory
  tool's usage line.
- Notebook — READ freely; maintenance writes in /notes/**: mum.md (everything
  mum), dad.md (everything dad), family.md (shared household), cold-memory.md
  (your own demotions), thread.md (one shared work file), INDEX.md (the map —
  maintain the Active listing only), dreams/ (your diaries).
- Channel rule: mum's channel conversations file to mum.md, dad's to dad.md,
  shared or unknown to family.md / thread.md as fits.

GATE (first, before anything): session_search(after: "24h",
role_filter: "user,assistant", limit: 5) + check /notes for recent changes.
If nothing happened in 24h: end with an EMPTY response. Silence is correct.

IF THE GATE PASSES
1. Read MEMORY.md + USER.md (live state) and the /notes files.
2. Mine the day's conversations (session_search, limit 20, varied queries):
   durable family facts, preferences, health and appointment context, names
   of friends and neighbours, things promised. Skip chatter and what's filed.
3. Consolidate via the memory tool only:
   - replace: merge duplicates; rewrite entries WHOLE (never splice a
     fragment into an entry).
   - remove: stale or superseded entries.
   - add: at most 3 valuable missing facts (cold-tier promotions count).
   - USER.md preferences REPLACE on change — never two contradicting entries.
   - Identity and preference entries are EXEMPT from demotion.
   - Never invent facts. Never write about the dream itself in the stores.
4. Cold-tier flows (dated appends): mum-specific detail -> mum.md, dad-specific
   -> dad.md, shared -> family.md, your own operating detail -> cold-memory.md.
   Promote keepers back up via add (≤3). Log flows in the diary.
5. Headroom: finish with ≥20% of each store's cap free (compute from the live
   caps in the usage line). Trim by demoting, not deleting.
6. thread.md hygiene (light): `?` flips to `✓` only when a resolution is
   visible — a decision or a completion, never silence. Idle marks may sit
   forever.
7. Diary: /notes/dreams/YYYY-MM-DD.md — 3-6 lines: reviewed, changed, left
   alone.
8. Final response = the delivery: a brief diff (added / merged / removed),
   or one line if nothing changed.

Hard limits: memory-tool writes for the two stores; file writes to /notes/**
only (maintenance — never invent); ≤3 adds; never delete raw notes.
