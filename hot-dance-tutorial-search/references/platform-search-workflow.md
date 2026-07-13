# Platform Search Workflow

## Scope

- Default window: the current date minus 30 days.
- Required categories: jazz, KPOP, and girl-group dance.
- Eligible learning formats: tutorial, mirror practice, movement breakdown, slow practice, or beginner learning.
- Ranking signal: visible likes only.

## Xiaohongshu

1. Search focused combinations such as `爵士舞 教学`, `KPOP 女团舞 教学`, and `镜面舞蹈教学`.
2. Read visible card titles, dates, likes, tags, and detail URLs.
3. Exclude cards outside the window and pure lifestyle or dance-performance posts with no practical learning value.
4. Retain the complete URL exposed by the page, including `xsec_token`; it can expire, but removing it can make the link fail on PC.

## Douyin

1. Search focused combinations such as `爵士舞 教学`, `KPOP 女团舞 教学`, and `女团舞 镜面分解`.
2. Also enter `#抖音潮流舞蹈大赛`. Use its visible feed and any available visible filters or search controls to find jazz, KPOP, girl-group dance, tutorial, mirror, and breakdown videos.
3. Merge tag-feed and keyword-search candidates before deduplication.
4. Use the canonical official video URL shown by the page, normally `https://www.douyin.com/video/<id>`.

## Date and Duplicate Rules

- Convert relative dates such as `3天前` against the current date. Exclude old month/year labels that predate the cutoff.
- Normalize song titles by case, punctuation, whitespace, and bracketed qualifiers.
- Keep the Douyin card when the same song appears on both platforms. Otherwise keep the card with more visible likes.
- Do not infer a song's artist, a choreographer, a favorite count, or a teaching format from an unclear card.
