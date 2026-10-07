# The dream — portable consolidation procedure (v0)

The kit's core. A procedure, not a program: give this prompt to whatever runs
unattended for you (a cron job, a scheduled task, a CI schedule) — or run it by
hand as a morning ritual. Automation is an accelerator, not a requirement.

Assumes the `memory/` layout (v0, see templates/): `MEMORY.md` + `USER.md`
(hot), `cold-user.md` + `cold-memory.md` (middle tiers), `deep-user.md`
(frozen), `threads/` (theme files), `dreams/` (diaries), `INDEX.md` (map).

---

DREAM PROMPT (give this to the runner verbatim):

Nightly memory consolidation ("dreaming"). You start with NO chat context and
NO injected memory — read everything from disk first. Your job: distill raw
material into the curated memory stores.

LAYOUT
- Curated stores — edit with care and only through deliberate full-entry edits:
  memory/MEMORY.md (agent operating notes) and memory/USER.md (user profile).
  Keep each entry a single §-separated unit; when you rewrite an entry, write
  the WHOLE entry — never splice a fragment into an existing one.
- What goes where: MEMORY.md = operating knowledge (environment, conventions,
  tool quirks, lessons); USER.md = the user's identity and preferences. Cold
  state and bulk detail belong in cold-user.md / cold-memory.md or threads/ —
  not the hot path.
- Raw notebook — read freely: everything else in memory/ plus the project
  notes. EXCEPT any folder the user marks as a raw archive: never read it
  (the frozen deep tier, deep-user.md, is the one read-only exception —
  consult it when a new fact relates to historical context; never write it).
- Past conversations: whatever transcript access your host provides. If none,
  the threads/ files and diaries are your only sources — say so in your report
  rather than inventing.

COLD TIERS — PROMOTION SOURCES & DEMOTION SINKS: cold-user.md is the middle
tier of the user's profile; cold-memory.md the middle tier of agent operating
knowledge. PROMOTE keepers up into USER.md / MEMORY.md (at most 3 adds per
run). DEMOTE cooled facts down: when a hot entry's status resolved or its
detail grew too bulky, append it — dated — to the matching cold tier, then
remove it from the hot store (append FIRST, remove second — never lose a fact
in the gap). Identity and preference entries are EXEMPT from demotion.

GATE (before anything expensive): check for conversations in the last 24h and
files changed since the newest dreams/ entry. If nothing happened: end with an
EMPTY response. Silence is the correct output.

IF THE GATE PASSES
1. Read the two hot stores (live state).
2. Read the notes/threads (skip raw archives).
3. Mine the day's conversations for durable facts not yet saved: stable
   preferences, decisions, environment facts, lessons. Ignore transient task
   chatter and anything already captured.
4. Consolidate in the hot stores:
   - merge duplicate or overlapping entries into one tighter entry
   - remove entries now stale or contradicted
   - add at most the 3 most valuable missing facts, only within the caps
   - LICENSE TO EDIT AT WILL: consolidate, reword, merge, prune at your own
     judgment — healthy entries included. Hard floor: never invent facts;
     prefer demoting to the cold tiers over deleting; prefer one tight entry
     over two overlapping ones; don't churn entries already tight and accurate.
   - CLARITY IS THE JOB, NOT JUST SPACE: do this every run even when nothing
     is over-limit — you re-see the whole store; merge what overlaps, reword
     what drifted, fix what went stale.
   - HEADROOM: finish every run with ≥20% of each store's size free (compute
     from the live file sizes — sizes change on the user's call).
   - Preferences: when one changes, REPLACE the old entry — never append a
     contradicting second entry.
   - Never write entries about the dream run itself.
5. JANITOR PASS (light): retire COMPLETED items from INDEX's active listing
   into their threads/ file (park the detail first), prune aged thread
   entries. Never touch INDEX's map half; never create threads.
6. Write a dated diary in memory/dreams/YYYY-MM-DD.md: 3-6 short lines — what
   you reviewed, what you changed, what you left alone.
7. Your final response is the report: a brief diff (added / merged / removed),
   a few lines max.

HARD LIMITS: never invent facts; never delete raw notes; never read raw
archives (deep-user.md is the sole read-only exception); identity/preference
entries exempt from demotion; ≤3 adds per run.

---

Host notes:
- **hermes**: run as a cron job (daily, ~3am), deliver=local. The reference
  implementation.
- **manual ritual**: paste the prompt into a fresh session each morning with
  "run the dream" — the gate keeps it cheap on quiet days.
- **cursor/codex-class**: schedule their task runner, or keep the ritual. The
  procedure doesn't care who executes it.
