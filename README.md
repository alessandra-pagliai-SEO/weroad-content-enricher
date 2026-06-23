# weroad-context-enricher

A Claude skill that generates a ready-to-paste enrichment prompt for AI content creation tools.

Given a destination or theme, it queries the WeRoad travel catalog via MCP, scrapes itinerary pages when needed, and extracts unique hands-on experiences that go beyond standard travel guides. The output is a minimal prompt snippet listing concrete activities to be woven naturally into any article or SEO content — with no brand references, no operational details, no fluff.

## What it does

1. Takes a destination or theme as input (e.g. "Tokyo", "natural hot springs in Italy", "Japan skiing")
2. Queries the WeRoad travel catalog to find relevant itineraries
3. Scrapes itinerary pages when titles alone don't provide enough detail
4. Extracts concrete, non-obvious experiences — the kind not found in standard travel guides
5. Returns a minimal prompt block ready to paste into any content creation tool

## Output format

```
Arricchisci il contenuto integrando in modo naturale queste esperienze concrete, senza citarle come lista e senza riferimenti a brand o operatori:

- [experience 1]
- [experience 2]
- ...
```

## When to use it

When you want to enrich a travel article with authentic, proprietary experiences before passing it to a content generation tool.

## Requirements

- Claude Code with MCP access to the WeRoad travel catalog (`mcp__23b855af-7c6e-408e-98e9-79f891cff102__search_travels`)

## Installation

Install the `.skill` file via Claude Code:

```bash
claude skill install weroad-context-enricher.skill
```
