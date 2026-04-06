<!-- repo-description: Local-first meeting memory with 24 MCP tools for Claude — knowledge workers and developers who use AI daily — zero cloud upload, your AI actually knows what happened in meetings -->

# VaiBcall — Your AI assistant was in every meeting. It just couldn't hear them. Until now.

VaiBcall records, transcribes, and speaker-diarizes your meetings locally — then makes every conversation queryable by Claude via 24 MCP tools. When you open Claude after a meeting, it already knows what was decided, who committed to what, and what changed since last week. No manual copy-paste. No re-briefing. No audio sent anywhere.

Built on [minutes](https://useminutes.app) — open source, MIT licensed.

## The Problem

The average knowledge worker attends 62 meetings per month. Senior operators attend 90–130. At 8 hours of meeting time per week, that's 400+ hours per year of context that exists only in the attendees' memories and scattered notes. Every time you open Claude, you start from scratch — pasting notes, reconstructing context, hoping you captured what mattered. The existing solutions are all wrong: Otter.ai and Fireflies process your audio on their servers (your board calls, investor conversations, and competitive strategy sessions, routed through a third-party cloud). Zoom's built-in recording has no MCP interface. Manual notes are inconsistent and not AI-queryable.

## What This Does

- **Local recording** — audio never leaves your device. whisper.cpp transcription, pyannote-rs speaker diarization in Rust. No Python required.
- **24 MCP tools** — the most complete MCP implementation in the meeting memory category. `search_meetings`, `get_commitments`, `get_person_profile`, `consistency_report`, and 20 more.
- **Commitment tracking** — `get_commitments` extracts who committed to what across a time window. "What did Alex promise in the last two weeks?" is now a one-line Claude query.
- **Consistency reports** — `consistency_report` compares what someone said in different meetings. Flags drift between what they committed to on March 15th and what they said on April 1st.
- **Auto-call detection** — macOS triggers automatically on Zoom, Teams, and Webex. Zero setup per meeting.
- **4 input modes** — live recording, real-time transcript delta, notetaking mode, folder watcher for audio files dropped into a watched directory.
- **Speaker diarization with persistent profiles** — train it once; it knows who's speaking in every future recording.
- **Claude Code plugin** — 12 skills + 1 agent + 2 hooks. Native integration for developers using Claude Code as their primary coding assistant.
- **Obsidian and Logseq sync** — vault-native note export for personal knowledge management.

## Who It's For

**The Back-to-Back Meeting Professional** — founders, VPs, senior operators running 8–10 meetings daily, using Claude as their primary AI tool. They've been re-briefing Claude after every meeting for 18 months. VaiBcall closes that loop permanently.

**The Claude Code Power Builder** — developers who treat VaiBcall's 24-tool MCP server as infrastructure. When they're debugging a system architected in a meeting last week, they want Claude to recall that architecture discussion.

**The Commitment Tracker** — operations leads and project managers who need to know who said what and when. The consistency report is a real operational tool, not a demo feature.

## Why Not Otter.ai or Fireflies?

Those tools process your audio on their servers. Every board call, every investor conversation, every sensitive operations meeting — uploaded to a third-party cloud. VaiBcall's architecture makes that structurally impossible: the transcription runs locally via whisper.cpp, the diarization runs locally via pyannote-rs in Rust, the MCP server runs locally. There is no upload step because there is no server to upload to. On M1/M2, whisper.cpp processes a 1-hour meeting in 3–5 minutes — fast enough for post-meeting use. Live transcript mode is available for real-time delta reads during active meetings. The privacy advantage is architectural, not a policy promise.

## Quick Start

**Option 1: MCP server only (fastest)**

```bash
npx minutes-mcp
```

Add to Claude Desktop's MCP config and you're done.

**Option 2: Brew tap (macOS, full install)**

```bash
brew tap chaosagent/tap
brew install vaibcall
```

**Option 3: Claude Code plugin**
Install the VaiBcall plugin from the Claude Code marketplace. Get 12 skills, 1 agent, and 2 hooks.

The three core MCP tools cover 80% of use cases: `search_meetings`, `get_commitments`, `get_person_profile`. The other 21 tools are there when you need them.

## Pricing / Access

Open source (MIT). Core product is free.

| Tier                | What You Get                                                                | Price         |
| ------------------- | --------------------------------------------------------------------------- | ------------- |
| Core (local)        | All recording, transcription, diarization, 24 MCP tools, Claude Code plugin | Free (MIT)    |
| Managed (planned)   | Cloud-assisted processing, higher throughput, cross-device sync             | ~$15–25/month |
| Enterprise (future) | Team-level meeting memory, shared commitment tracking, compliance export    | TBD           |

Current version: 0.9.3. Distribution: `npx minutes-mcp`, Brew tap, crates.io.
