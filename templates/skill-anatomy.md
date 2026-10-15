# Skill anatomy — the five-room home for HOW + scars

Use when a procedure, pitfall, or taste rule has outgrown threads/ and wants
its own home. Portable across hosts via the agentskills.io standard: a folder
with a `SKILL.md` (name + description frontmatter) that agents load on demand.
The DESCRIPTION is the entire load trigger — write it first, write it well.

The home of a piece of knowledge is the MOMENT IT IS CONSULTED. Step-level
whys sit beside their steps; things looked up mid-failure collect; things
checked at the end verify. The rooms below are lookup moments, not categories.

```
## <skill> — if task ~ description, load
- context optimization, moderate detail, what the agent lacks, explain why
Discovery       name / description / use when (+ not for) / metadata / related
Road Rules      topology / world limits / always-on rules / sources of truth
Workflow        pre-requisites / procedure / commands / situational hows / defaults
Lessons         gotchas / skill limits / what looks broken but isn't / refinement
Taste           user's preferences / collaboration style / project conventions
Verification    completion criteria / what success looks like / tests
References      extended disclosure / assets / templates / tools and scripts
```

Carried rules:
- Explain the WHY inline beside each step/rule ("do X because Y tends to
  cause Z" beats "ALWAYS X" — reasoning outlasts directives). Lessons
  collects only CROSS-CUTTING whys and refinements.
- When multiple approaches are valid, Workflow names the DEFAULT.
- Skill limits live in Lessons; scope-level can't-do lives in Discovery's
  "not for."
- Quoted user verdicts live in Taste so the same correction never repeats.
- The gap test for every line: "Would the agent get this wrong without this
  instruction?" — if no, cut it. Write what the agent LACKS; never explain
  what it already knows.
- De-dupe rule: stable navigation pointers may double; evolving rules and
  state never. A skill and an AGENTS.md may point at each other; they may
  not both carry the rule.

Home split: per-repo knowledge goes in the project's AGENTS.md; skills hold
what travels ACROSS projects (or when no repo exists). A skill earns itself
when the knowledge repeats or is scar-shaped — scars are filed the same day.
