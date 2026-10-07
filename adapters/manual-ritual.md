# Adapter: manual ritual (works on any host with file access)

The primary path. No scheduler, no plugins — a folder, a rule, and a paste.

## 1. Create the memory folder
In your project repo: `memory/` with the seven templates from `templates/`
(MEMORY.md, USER.md, cold-user.md, cold-memory.md, deep-user.md, INDEX.md,
plus `threads/` and `dreams/` as empty folders). Commit it. From now on your
memory versions with your code.

## 2. Wire the loading (the actual adapter step)
Add this to your project's AGENTS.md (or CLAUDE.md — whichever your tool
auto-reads):

    At session start, read memory/MEMORY.md and memory/USER.md.
    When you learn something durable, edit them with FULL-ENTRY edits (never
    splice a fragment into an existing entry). Work state goes in
    memory/threads/ following the notation in memory/INDEX.md. Project
    knowledge stays in this file.

Tools with `@file` mentions (cursor-class) can instead just `@memory/MEMORY.md`
in the first message of each session.
Use the HARDEST hook your host offers: `@memory/MEMORY.md` imports (claude-code
CLAUDE.md, cursor rules) force the content in; the "read at session start"
instruction merely asks. And mind the re-injection difference: a load-once
file rides the conversation and can be compacted out of very long sessions —
hosts like hermes re-inject every message (memory survives compression); on
load-once hosts, keep sessions bounded or re-load mid-session.

## 3. Conversation access (the host-variable step)
The dream mines "the day's conversations" — where those live differs by host:
- **Session logs on disk** (codex/claude-code-class): point the dream at the
  log paths — add them to the AGENTS.md rule; it reads them like any file.
- **No transcripts on disk** (editor/web chats): the dream works only from
  what sessions left IN memory/ (threads, notes). The in-session net is the
  whole net here — capture as it happens is the portable layer.
- The dream's honesty rule: if there is nothing to read, it says so in its
  report — it never invents conversations.

## 4. The dream (daily, or whenever)
Open a fresh session, paste `prompts/dream.md`, say "run the dream." The gate
keeps it cheap on quiet days (it answers with silence). Commit memory/
afterwards — the diff IS the review.

## 4. The nap (rarely)
When a store nears its cap: paste `prompts/nap.md`, run.

That is the whole installation. If your tool can read and write one folder,
it can have continuity.
