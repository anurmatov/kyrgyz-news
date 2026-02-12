---
name: kyrgyz-news
description: Search, browse, and explore Kyrgyzstan news from multiple agencies via AI-generated summaries
homepage: https://fuddy-duddy.org
mcp_server: https://mcp.fuddy-duddy.org/
---

# FuddyDuddy News MCP Tools

Access Kyrgyzstan news from multiple news agencies through AI-generated summaries, semantic search, and story clustering.

**MCP Server:** `https://mcp.fuddy-duddy.org/`

## Tools

### search_news
Semantic search across news summaries using natural language queries.

- Supports date extraction from queries (e.g., "news from last week", "events yesterday")
- Returns ranked results with relevance scores
- Use `language: "RU"` for Kyrgyz-language results (default), `language: "EN"` for English translations
- Limit results with `limit` (1-20, default 10)
- Optionally specify `fromDate` and `toDate` in ISO 8601 format

### get_latest_news
Browse recent news summaries with pagination.

- Use `page` (0-based) and `pageSize` (1-20) for pagination
- Filter by `language: "RU"` or `"EN"`
- Returns summary titles, sources, dates, categories, and IDs

### get_news_article
Get the full text of a specific news summary by its ID.

- Returns title, full article text, source info, original article URL, category
- Includes a list of similar articles from other sources covering the same story
- Use the ID from `search_news` or `get_latest_news` results

### get_top_clusters
Get trending news clusters — groups of similar articles from multiple sources covering the same story.

- Returns cluster titles and reference counts
- Filter by `language: "RU"` or `"EN"`
- Clusters with a lead article ID can be explored further with `get_news_article`

## Workflow Patterns

**Find news on a topic:**
1. `search_news` with a natural language query
2. `get_news_article` on interesting results to read the full summary and find related stories

**Browse latest news:**
1. `get_latest_news` to see recent summaries
2. `get_news_article` for full details on any item

**See what's trending:**
1. `get_top_clusters` to find the most-covered stories
2. `get_news_article` on the lead article ID for the full story and related coverage

## Tips

- Most Kyrgyz news is published in Russian — use `language: "RU"` for the broadest coverage
- English translations (`language: "EN"`) are available for most summaries
- Date extraction works with natural language: "last week", "yesterday", "in January"
- Each summary includes a direct link to the article on fuddy-duddy.org
- Each summary links to the original source article for verification
- Cluster reference counts indicate how many sources covered a story