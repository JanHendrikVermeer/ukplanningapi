# <img src=".github/assets/favicon.svg" height="26" alt=""> UK Planning API — issues & support

Public issue tracker for [ukplanningapi.co.uk](https://ukplanningapi.co.uk) — a REST API and MCP server over UK planning data.

**This repo holds no source code.** It exists so that data problems, bugs and feature requests are reported, discussed and fixed in the open. If a council's numbers look wrong, [say so here](../../issues/new/choose) — the fix helps everyone querying that council.

## What the API covers

| | |
|---|---|
| Planning applications | 1,543,542 |
| Councils with data | 328 |
| Appeal records | 591,282 |
| Enforcement notices | 28,800 |

Plus 212,000+ planning agents with approval rates, case officers, and ward/postcode summaries. Live counts are on the [homepage](https://ukplanningapi.co.uk) — the figures above are from 7 September 2026 and move daily as the scrape lands. (This table refreshes itself weekly via [a scheduled action](.github/workflows/refresh-stats.yml).)

Coverage honesty: data quality varies enormously between councils, and the API tells you rather than hiding it — per-council field coverage is measured daily and published per council. Enforcement notices are published by 153 of 489 UK councils; the API can only serve what councils publish.

## Using it

**REST** — [full docs](https://ukplanningapi.co.uk/api-docs), [get a key](https://ukplanningapi.co.uk/api-signup) (free tier available):

```bash
curl -H "X-Api-Key: YOUR_KEY" \
  "https://ukplanningapi.co.uk/v1/applications?postcode=LS29%206RZ"
```

**MCP** — plug it into Claude, ChatGPT or any MCP client ([setup guide](https://ukplanningapi.co.uk/mcp-setup)):

```json
{
  "mcpServers": {
    "uk-planning": {
      "type": "http",
      "url": "https://ukplanningapi.co.uk/mcp",
      "headers": { "X-Api-Key": "YOUR_KEY" }
    }
  }
}
```

Machine-readable discovery: [`/.well-known/mcp.json`](https://ukplanningapi.co.uk/.well-known/mcp.json) · [`/llms.txt`](https://ukplanningapi.co.uk/llms.txt)

## Reporting an issue

| You found | File |
|---|---|
| Wrong, missing or stale data | [Data issue](../../issues/new?template=data-issue.yml) |
| An endpoint or MCP tool misbehaving | [Bug report](../../issues/new?template=api-bug.yml) |
| Something the API should do but doesn't | [Feature request](../../issues/new?template=feature-request.yml) |

**Never include your API key in an issue.** If you've pasted one anywhere public, treat it as burned and reissue from your [dashboard](https://ukplanningapi.co.uk/api-login).

Account, billing or key questions go to [help@ukplanningapi.co.uk](mailto:help@ukplanningapi.co.uk) — not the public tracker.
