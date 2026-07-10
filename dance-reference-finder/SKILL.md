---
name: dance-reference-finder
description: Find high-quality Douyin reference videos for a dance from a user-provided dance video, song name, choreography name, or partial clue. Use when Codex needs to identify likely music or choreography, search Douyin for the same dance, rank high-like reference videos, and return a concise manual-save list of up to three official Douyin links. Do not use this skill to control the Douyin client or download videos.
---

# Dance Reference Finder

Find the strongest references for learning a specific dance. Give the user a short manual-save list; the user saves any selected video through the official Douyin client.

## Workflow

1. Determine the search query.
   - Inspect the supplied dance video, its filename, audio, and representative frames when they help identify the song or choreography.
   - Search a known song or choreography name directly.
   - Prefer choreography-specific queries over a broad song-only search.

2. Search and rank.
   - Read [references/douyin-workflow.md](references/douyin-workflow.md) before ranking candidates.
   - Confirm that the visible moves match the user's dance before recommending a video.
   - Prioritize the same choreography, original creator or teacher, visible likes, clear full-body framing, and complete, mirror, back-view, or slow-learning value.

3. Return the save list.
   - Give no more than three candidates.
   - Do not control the Douyin client, click save, download media, bypass login, or work around platform restrictions.
   - If no exact match is found, say so plainly and provide at most two closely related learning references only when their limitations are clear.

## Output Contract

Write concise Chinese. Start with `**优先保存**`. For every item include:

- A Douyin jump link on the creator name.
- Duration and the visible popularity count.
- `关键词：...`
- `用途：...`

Call a visible count `赞` only when it is visibly a like count. Never invent collection counts.
