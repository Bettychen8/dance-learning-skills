---
name: hot-dance-tutorial-search
description: Find recent popular Xiaohongshu and Douyin jazz, KPOP, and girl-group dance tutorial videos using the user's logged-in Chrome profile. Use when Codex needs to search both platforms, include Douyin's #抖音潮流舞蹈大赛 tag feed, rank visible likes, deduplicate songs with Douyin priority, and return up to ten clickable learning links with concise Chinese tags. Do not use this skill to save, download, post, or otherwise control either platform's client.
---

# Hot Dance Tutorial Search

Find a concise, current learning list of high-like dance tutorials. Default to the most recent 30 days, up to ten distinct songs, visible likes only, and Douyin as the preferred duplicate source.

## Workflow

1. Search both platforms conservatively.
   - Use the user's logged-in Chrome profile.
   - Use the Xiaohongshu Quick Search extension only as a navigation shortcut; it does not change platform permissions or collection behavior.
   - Read [references/platform-search-workflow.md](references/platform-search-workflow.md) before searching.
   - Do not batch-open videos, paginate aggressively, call hidden APIs, save, download, or post content.

2. Build and rank candidates.
   - Keep only in-window jazz, KPOP, girl-group dance, mirror, breakdown, slow-practice, or beginner-friendly tutorial cards.
   - Use only the visible like count. Do not open every detail page to find favorites.
   - Normalize song titles and group duplicate songs. Keep Douyin over Xiaohongshu for the same song; otherwise keep the higher-like version.
   - Prefer explicit tutorials over pure performance clips when their like counts are similar.

3. Return the learning list.
   - Give no more than ten songs.
   - Make every song title a clickable official detail link.
   - Preserve a complete Xiaohongshu URL with its current token parameters; do not replace it with a bare note ID.
   - Do not claim that a mobile app handoff was tested unless it was actually tested.

## Output Contract

Write concise Chinese and return exactly this table:

| 歌曲名 - 演唱者 | 点赞量 | 标签 |
|---|---:|---|
| [Song - Artist](https://example.com) | 1.2万赞 | 编舞人编舞／女团舞／镜面教学 |

- Write `约1.2万赞` when the platform abbreviates the count; otherwise write `1234赞`.
- Write `音源作者未标注` when an artist is not visible and cannot be reliably verified. Never guess.
- Put an explicitly named choreographer first in the tag field. When none is shown, omit it and retain useful visible tags such as `爵士舞`, `KPOP`, `女团舞`, `韩舞教程`, `镜面教学`, `动作分解`, `慢速分解`, or `零基础`.
- Add a single short note only when fewer than ten eligible videos exist or a Xiaohongshu link may expire.
