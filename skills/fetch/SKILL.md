---
name: fetch
description: Use when fetching content from Wikipedia. WebFetch returns 403 on all Wikipedia URLs. Use curl via Bash instead.
---

# Fetching from Wikipedia

Do not use WebFetch for Wikipedia — it returns 403. Use curl via Bash instead.

Three URL patterns, each returning different formats:

Raw wikitext (wiki markup, good for tables):
```bash
curl -s "https://en.wikipedia.org/w/index.php?title=ARTICLE_NAME&action=raw"
```

Plain text via MediaWiki API (structured JSON, good for article content):
```bash
curl -s "https://en.wikipedia.org/w/api.php?action=query&titles=ARTICLE_NAME&prop=extracts&explaintext=true&format=json"
```

Summary via REST API (short JSON summary):
```bash
curl -s "https://en.wikipedia.org/api/rest_v1/page/summary/ARTICLE_NAME"
```

Replace spaces in `ARTICLE_NAME` with underscores (e.g., `Display_resolution`).

## Common Claude Mistakes

- Silently falling back to non-Wikipedia sources instead of reporting the failure
- Adding `-A "Mozilla/5.0"` to curl (unnecessary — curl's default user-agent is not blocked)
