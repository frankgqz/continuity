# The nap — portable compression procedure (v0)

On-demand space recovery. The dream's sibling, NOT a small dream: no gate, no
mining conversations, no reorganization. It tidies the shelves; it does not
rearrange the shop. Run it when a hot store nears its cap — or whenever things
feel bloated.

---

NAP PROMPT (give this to the runner verbatim):

You are running an on-demand memory compression ("the nap"). You start with NO
chat context — read everything from disk first. This is compression, not
consolidation: no conversation mining, no new facts.

JOB: free space in the two hot stores (memory/MEMORY.md and memory/USER.md).
TARGET: the run context may specify a goal ("get to 30% free"); otherwise
finish with >=20% of EACH store's size free. Compress toward the target in
this order:
1. merge duplicate or overlapping entries into one tighter entry;
2. reword bloated entries tighter (short declarative facts, no padding);
3. demote cold state down a tier — append it dated to cold-user.md or
   cold-memory.md, then remove it from the hot store (append first!).
If the target is already met, do only a light merge pass and report.

HARD FLOORS: never invent facts; identity and preference entries are EXEMPT
from demotion; preferences REPLACE, never leave two contradicting entries; if
the target would force cuts into good entries, stop and report an honest
partial — forced cuts are worse than missing a target. Don't churn entries
already tight and accurate. When you rewrite an entry, rewrite the WHOLE
entry — never splice a fragment into one.

REPORT: before -> after size per store, 2-5 lines on what was merged / demoted
/ removed, and whether the target was met (yes / no / partial + why).

---

Host notes:
- **manual ritual (all hosts):** paste the prompt into a session, add the
  target if you have one ("nap: get MEMORY to 25% free"), run.
- **hermes:** it already ships as the on-demand "Nap consolidation" job.
- Cadence: it's a fire extinguisher, not a schedule. Most weeks never need it.
