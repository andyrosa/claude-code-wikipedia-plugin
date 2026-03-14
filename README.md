# wikipedia

A Claude Code plugin for fetching content from Wikipedia.

## Why this exists

Claude Code's built-in `WebFetch` tool returns HTTP 403 on all Wikipedia URLs. Wikipedia's server blocks requests from Python HTTP libraries (`python-requests`, `urllib`) based on their default user-agent strings. This is separate from robots.txt — it is an active server-side filter. WebFetch uses one of these libraries internally and has no parameter to override the user-agent.

This plugin teaches Claude to use `curl` via the Bash tool instead. Curl's default user-agent (`curl/X.X`) is not blocked.

## Related open issues

Issues on `anthropics/claude-code`:

- [#7568](https://github.com/anthropics/claude-code/issues/7568) — WebFetch uses a generic user-agent (root cause)
- [#22846](https://github.com/anthropics/claude-code/issues/22846) — WebFetch returns 403 on Wikipedia and other sites
- [#29009](https://github.com/anthropics/claude-code/issues/29009) — Claude Desktop share URLs return 403
- [#33985](https://github.com/anthropics/claude-code/issues/33985) — WebFetch: allow access to public claude.ai/share links

## Skills

### `/wikipedia:fetch`

Fetches Wikipedia articles using curl. Supports three URL patterns:

- Raw wikitext — wiki markup, good for extracting tables
- MediaWiki API — structured JSON with plain-text article content
- REST API — short JSON summary

## Installation

```
/plugin install wikipedia
```

Or add from this repository:

```
/plugin marketplace add andyrosa/claude-code-wikipedia-plugin
/plugin install wikipedia@andyrosa/claude-code-wikipedia-plugin
```
