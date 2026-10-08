# Give your agent tiers, dreams, and a map

*How to build memory for an AI that forgets — the architecture, the cost, and
the install.*

Every AI coding tool forgets. You build something together across an evening,
and the next session opens like a stranger walked in — polite, capable, and
holding nothing. The standard advice is a bigger context window. That advice
is wrong in the same way "buy a bigger desk" is wrong advice for losing your
keys. The problem isn't capacity. It's that nothing *lives* anywhere.

What follows is an architecture for making it live somewhere: files in your
project, a small language for marking them, and a nightly procedure that
tidies while you sleep. It ran daily for a week before this was written; the
numbers are real.

## Tiers: hot, cold, deep

Not all knowledge deserves the same shelf.

**Hot** — two files, injected into every session: `MEMORY.md` (the agent's
operating notes: environment, conventions, tool quirks, lessons) and `USER.md`
(who you are: identity, preferences, decision style). Everything here earns
its place every single turn, so it stays general and it stays small. Project
detail does not belong here.

**Cold** — two middle tiers: `cold-memory.md` and `cold-user.md`. This is the
demotion sink: status that resolved, detail that grew too bulky, context that
is relevant but not hot. Read on demand. Facts flow down here when they cool
and flow back up when they earn heat again.

**Deep** — `deep-user.md`, frozen. The archive of the deep past. The one file
the maintenance job may read but never write.

The tiers exist because memory has two failure modes: a hot store so stuffed
with detail that nothing important fits, and a cold store so neglected that
everything rots. Tiers give the system somewhere for knowledge to *be at the
right temperature*.

## Threads: status, key points, and a small language

Sessions produce work, and work needs a home that isn't the person-file.
`threads/` holds one file per theme — and the shape of each file is the part
people underestimate:

- **A living digest at the top.** A `**Key points:**` block, updated as things
  resolve. Scales with content — a short chat earns a line or two. This is
  the five-second read; the entries below are the full one.
- **Dated entries as `##` headings.** Headings are structure and never marked.
- **Marks on the sub-points.** Four glyphs and a default:

  | mark | means |
  |------|-------|
  | `!`  | must-not-lose: if this line vanished, future work would collapse |
  | `?`  | unknown / unsettled / contested — anything not yet resolved |
  | `->` | next action |
  | `✓`  | done, with its one-line resolution |
  | none | neutral note (the default — plain life needs no marking) |

  The arc is the whole lifecycle: `?` (not yet known) → `✓` (settled). Friction
  and contest live inside `?` — a `contested:` word-tag makes them greppable. The
  maintenance job corrects marks that evidence has obviously resolved — but a
  `?` flips only when a resolution is visible: a decision or a completion,
  never silence.

The small rules matter more than they look, because markdown will betray you
politely: a mark at line start works, a `>` becomes a blockquote, a `*` becomes
a bullet, a `1.` mid-line becomes a list and steals your syntax highlighting,
and a four-space indent becomes a code block. Marks live at the start of
sub-points (after indentation), rank numbers use `1:`, indents stay at three
spaces. A mark that needs a legend is too clever — these four can't be
confused for anything else.

And one division of labor that keeps everything from bloating: **project
knowledge lives in the project's own `AGENTS.md`** (which every serious tool
already reads), threads hold status + key points + pointers, and memory stays
general. Three homes, no gap.

## The dream (and the nap)

Memory that only grows becomes an attic. Something has to curate — and the
thing worth understanding is that *curation is a procedure, not a program*.

**The dream** runs daily. It starts with no chat context and reads everything
from disk, then: mines the last day's conversations for durable facts,
consolidates the hot stores (merge duplicates, replace stale entries, prune),
moves cooled facts down to the cold tiers and promotes keepers up, retires
completed work out of the map, and writes a dated diary of what it changed.
It works under hard floors: never invent facts, identity and preferences are
exempt from demotion, preferences *replace* rather than contradict, and every
rewritten entry is rewritten whole — a fragment spliced into an entry
destroys the entry.

**The nap** is the on-demand sibling: pure space recovery when a store nears
its cap. It compresses and demotes; it does not mine and does not reorganize.
Compression is not consolidation, and the prompt should be as different as the
jobs are.

Both can be scheduled (a cron job, a task runner) or run by hand ("paste this
prompt, say *run the dream*"). Automation is an accelerator. The procedure is
the product.

## What it costs when the platform doesn't give it to you

Everything above ran on a host with real support: a memory tool that injects
the hot tier, enforces whole-entry edits, and refuses direct writes to the
files. Strip that away — cursor, codex, a chat with a file tool — and the
architecture still runs. What changes is where the guarantees live.

- **Enforcement.** With platform support, the rules are mounts and tool
  behavior. Without it, the rules are *text* — instructions the model follows
  because the file says so. Same boundary, weaker substrate. This is why the
  dream's hard floors matter more on weak hosts, not less.
- **Names.** `MEMORY.md`/`USER.md` are conventions, not sacraments; the
  architecture is the *roles* (agent-notes vs user-profile). Rename them to
  `brain.md`/`human.md` if you like — a consistent find-replace is safe
  everywhere except hosts that bind the filenames.
- **Topology.** Folder layout encodes write authority: hosts that own the hot
  files force a split between tool-territory and agent-territory. Plain hosts
  can put everything in one `memory/` folder. Within the layout, folders earn
  their place by *countability*, not authority: stable singletons at root,
  growing collections (one journal file per day; the thread set) in folders.

The portability tax is honest: you trade guarantees for universality. The
architecture survives; only the enforcement gets softer.

## Install (Monday morning)

1. Copy `templates/` into `memory/` at your project root. Commit it — your
   memory versions with your code now.
2. Wire the loading in your `AGENTS.md`: *"At session start, read
   memory/MEMORY.md and memory/USER.md. When you learn something durable,
   edit them whole. Work state goes in memory/threads/."*
3. First dream: paste `prompts/dream.md`, say "run the dream." Commit after —
   the diff is the review.
4. Optional: schedule it and never think about step 3 again.

That's the whole thing. Seven files, two procedures, one small language. If
your tool can read and write one folder, it can remember you.

---

*The kit (templates, prompts, adapters) lives in this repo. The case study is
one week of daily operation: a real working memory at ~15KB hot / growing
cold tiers / 7 thread files, dream diaries written every night and reviewed
every morning, and a mark notation that survived contact with two markdown
syntax traps and one very patient editor.*
