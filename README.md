# continuity

Memory architecture for AI agents that forget — tiers, dreams, and a map:
files + two procedures + one small language; works on any host that can read
and write a folder.

Your AI coding assistant forgets everything between sessions — every Monday
is a stranger. This is the fix: **persistent memory** that lives in your repo,
versions with your code, and runs on Claude Code, Codex, Cursor, Hermes, or
any agent with one writable folder. No plugin, no service, no account.

**Start here:** [essay.md](essay.md) — the argument and the install.

```
templates/   the seven skeletons (hot, cold, deep, map, threads, AGENTS.md)
prompts/     dream.md (nightly consolidation) · nap.md (on-demand compression)
adapters/    manual-ritual.md (the primary path) · hermes.md (reference host)
BOM.md       the design record: scope, host requirements, decisions
```

Quick start: copy `templates/` into `memory/` at your project root, wire one
line into your AGENTS.md ("read memory/MEMORY.md and USER.md at session
start"), then paste `prompts/dream.md` into a session and say "run the dream."
Full walkthrough: [adapters/manual-ritual.md](adapters/manual-ritual.md).

Memory lives in YOUR repo and versions with your code. The kit holds no user
data.

