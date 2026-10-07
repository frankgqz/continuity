# Adapter: hermes (the reference host)

Hermes does all three host requirements natively, so this adapter is mostly
"where things already are."

## Mapping (kit layout -> hermes)
- `memory/MEMORY.md` + `memory/USER.md` -> hermes's native memory store
  (injected every session; edited via the memory tool, which enforces the
  caps — the kit's full-entry rule is the memory tool's replace rule).
- `cold-user.md` / `cold-memory.md` -> the cold tiers (hermes users often
  name them personally — frank.md / hermes.md — names beat symmetry).
- `memory/threads/`, `memory/dreams/`, `memory/INDEX.md` -> the notes folder
  (whatever the notes mount points at).

## Loading
Nothing to wire: the hot tier is injected; the notes folder is read on demand
via the map (INDEX.md is the front door).

## Conversation access
Native and first-class: the dream uses the session search tool (transcript
FTS over the sessions database) — the reference implementation of the mining
step. The in-session net still matters: threads entries are the floor if a
session dies before noting anything.

## The dream
Create a cron job (daily, ~3am local, deliver=local) whose prompt is
`prompts/dream.md`'s prompt section verbatim. Schedule ideas and gotchas:
paused/one-shot jobs refuse manual runs — use a recurring schedule. The
nightly commit is the review moment.

## The nap
The on-demand job (`prompts/nap.md`) — trigger it with a word ("nap"), with an
optional target in the run prompt.

## What hermes adds beyond the kit
The memory tool (caps + enforced full-entry edits), the scheduled runner, and
session transcripts the dream can mine. The kit does not require any of that —
it is the same architecture with cheaper parts.
