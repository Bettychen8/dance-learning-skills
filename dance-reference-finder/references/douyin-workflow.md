# Douyin Dance Reference Workflow

## Search Strategy

Start with the narrowest known signal. When only a video is available, inspect its filename, metadata, a short audio segment, and a few movement frames only as needed. Search in this order:

```text
<song> 舞蹈
<song> <choreographer> 编舞
<song> <choreographer> 完整版 镜面
<song> <choreographer> 分解 教学
```

Many videos use the same song with different choreography. Do not treat a song match as an action match.

## Ranking

Rank candidates in this order:

1. Same choreography or clearly identical movement sequence.
2. Original choreographer, teacher, or clearly credited source.
3. High visible like count.
4. Full-body, stable, unobstructed framing.
5. Full performance, mirror/back view, slow version, or useful tutorial.
6. Recency as a tiebreaker only.

Prefer a mix of one strong finished performance, one original/teacher reference, and one mirror/slow/tutorial reference. Return fewer than three when fewer strong matches exist.

## Manual-Save Output

Use this exact shape:

```markdown
**优先保存**

1. [@作者](https://www.douyin.com/video/...) | 00:27 | 7981 赞
   关键词：`#歌曲 #编舞 #镜面`
   用途：完整全身且动作与原视频一致，适合作为主对照。
```

Do not add a separate explanation of search steps. The user saves selected videos through the official Douyin client; do not attempt saving, downloading, login automation, CAPTCHA handling, or platform workarounds.
