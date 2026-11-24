# Email Toolkits and Agents — Study

## The question

> What are the lighthouse projects addressing email chaos with agents?
> Multi-account visibility, APIs, archive, backup, enhanced queries,
> insights, performant triage, knowledge graphs, second brains.
>
> How do we free professionals from inbox dopamine hits and put complex
> triage-to-action workflows on autopilot, without sacrificing privacy,
> security, or organizational and personal preferences, style, and
> processes?

The interesting bits are **not** "which app has the nicest inbox." They are:

- **Multi-account visibility.** Can one tool see every account a person
  has (personal Gmail, several Workspaces, Microsoft 365, plain IMAP) as
  one archive?
- **Access paths.** IMAP, the Gmail API, Microsoft Graph, mbox/Takeout
  imports. Read-only by construction, or able to change the mailbox?
- **Archive and backup.** What's the store of record? Raw `.eml`, a
  database, both? Can it be rebuilt from originals? Does mail deleted
  upstream survive?
- **Attachments.** Stored once by hash? Text extracted? Searchable?
- **Queries and insights.** Full-text, analytics, search by meaning,
  rank fusion. How fast at hundreds of thousands of messages?
- **Triage to action.** Does it only read, or can it draft, send,
  schedule, file, and follow up? Where does a human approve?
- **Knowledge graph and second brain.** People, threads, documents, and
  commitments as linked records an agent can reason over.
- **Agent surface.** MCP servers, CLIs, APIs, skills. What does an agent
  actually get to call?
- **Privacy and security.** Local-first or hosted? Where do credentials
  live? How is email treated as untrusted input (prompt injection)?
- **Preferences and process.** Can it learn a person's or a firm's style,
  rules, and workflows, or does it impose its own?

## Why this study exists

[kay-os](https://github.com/lossless-group/kay-os) already pulls whole
mailboxes to local disk (`mail/kaymail.py`), mirrors them to Cloudflare R2,
and serves them to agents over MCP. Its next step was attachments, search by
meaning, and a correspondent graph, written up as an exploration and a spec.
While researching that, msgvault turned up doing much of the same thing,
further along. This study is the prep for the question *"adopt, extend, or
build?"*, starting with msgvault and widening to the rest of the field.

## What we are looking at, repo by repo

| Repo | Maintainer | Why it's here |
|---|---|---|
| [`msgvault/`](https://github.com/kenn-io/msgvault) | Wes McKinney and contributors (MIT) | Offline archive of a lifetime of email and chat. Go, SQLite as the store of record, DuckDB over Parquet for analytics, attachments deduplicated by SHA-256 with text extraction, an API, agent skills, and an open proposal for Graph RAG over the archive ([#154](https://github.com/kenn-io/msgvault/issues/154)). The closest match to kay-os's design, and the first candidate to adopt instead of build. |

More references get added as the survey widens: other local archivers,
triage agents, inbox-to-task tools, and email knowledge-graph projects.

## How to use this study

Read the pinned code before answering from memory, and cite
`<repo>/<path>:<line>`. Clone with submodules:

```bash
git clone --recurse-submodules https://github.com/lossless-group/study-email-toolkits-agents.git
```

Notes, profiles, and comparisons go in `context-v/`. Changes to the study go
in `changelog/`.
