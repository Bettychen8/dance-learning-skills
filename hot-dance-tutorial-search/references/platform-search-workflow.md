# Platform Search Workflow

## Scope

- Default window: the current date minus 30 days.
- Required categories: jazz, KPOP, and girl-group dance.
- Eligible learning formats: tutorial, mirror practice, movement breakdown, slow practice, or beginner learning.
- Ranking signal: visible likes only.

## Stage A: Trend Discovery

Use discovery results to identify songs, not to select final videos.

### Xiaohongshu

Search a small set of focused combinations:

- `爵士舞 教学`
- `KPOP 女团舞 教学`
- `镜面舞蹈教学`
- `<current month> 热门舞蹈`
- `最近很火的舞蹈`

Read visible card titles, dates, likes, hashtags, and song or choreographer names. High-like performances and roundup posts may supply song candidates but are not eligible final tutorials.

### Douyin

Search a small set of focused combinations:

- `爵士舞 教学`
- `KPOP 女团舞 教学`
- `女团舞 镜面分解`
- `<current month> 热门舞蹈 教学`
- `最近热门舞蹈`
- `抖音潮流舞蹈大赛 KPOP 教学`

Always inspect `#抖音潮流舞蹈大赛`. Use visible roundup, challenge, and performance cards to discover current song names.

### Candidate Pool

- Normalize song names as they are collected.
- Build at least 15 distinct song candidates when enough visible results exist.
- Record the strongest visible trend signal for each song: likes, date, category, and source platform.
- Do not discard a song merely because the discovery card is a performance; exact tutorial search happens next.

## Stage B: Song-Specific Tutorial Search

For each strong candidate, search both platforms with focused combinations:

- `<song> 教学`
- `<song> 舞蹈教学`
- `<song> 分解`
- `<song> 镜面`
- `<song> <choreographer> 教学` when a choreographer is visible

Keep only results that:

- fall inside the date window;
- visibly teach or slow down learnable movement;
- match jazz, KPOP, or girl-group dance unless the user expands the scope;
- expose a visible like count and a usable official detail link.

Exclude pure performances, trend summaries, unrelated card dances, Hiphop, and otaku dance from the final list unless the user requested those categories.

## Recovery Pass

Do not report fewer than ten songs after only the broad searches.

When fewer than ten eligible songs remain:

1. Revisit current-month roundups and related-search suggestions on both platforms.
2. Add newly visible high-like song names to the candidate pool.
3. Search those songs directly with `教学`, `分解`, and `镜面`.
4. Reapply the date and category gates.

Return fewer than ten only after both platforms, the Douyin contest tag, at least one trend-discovery pass, and song-specific searches have been exhausted conservatively.

## Platform Details

### Xiaohongshu

Retain the complete URL exposed by the page, including `xsec_token`; it can expire, but removing it can make the link fail on PC.

### Douyin

Use the canonical official video URL shown by the page, normally `https://www.douyin.com/video/<id>`. Open only finalists when a result card must be opened to expose its canonical video ID.

## Date and Duplicate Rules

- Convert relative dates such as `3天前` against the current date. Exclude old month/year labels that predate the cutoff.
- Treat the exact cutoff date as eligible unless the user requests a different convention.
- Normalize song titles by case, punctuation, whitespace, and bracketed qualifiers.
- Keep the Douyin card when the same song appears on both platforms. Otherwise keep the card with more visible likes.
- Do not infer a song's artist, a choreographer, a favorite count, or a teaching format from an unclear card.

## Final QA

Before responding, verify:

- both Xiaohongshu and Douyin were searched;
- `#抖音潮流舞蹈大赛` was inspected;
- the discovery pool reached 15 distinct songs when enough results existed;
- strong song candidates received exact tutorial searches;
- all finalists are inside the date window and requested category scope;
- no pure performance remains;
- duplicates prefer Douyin;
- finalists are sorted by visible likes;
- every title links to the official detail page.
