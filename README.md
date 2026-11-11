# Keel Stats MCP server

A remote [Model Context Protocol](https://modelcontextprotocol.io) server for NBA and NFL analytics: player and team
profiles, head-to-head history, schedules, Keel Impact and RAPM ratings, EPA, injury consequences, game projections,
minutes forecasts and player-props research. It is the same data as
[keelstats.com](https://keelstats.com/?utm_source=github&utm_medium=listing).

This repository holds the server's public description and setup. The server itself is hosted; there is nothing to
install.

```
https://api.keelstats.com/mcp
```

Streamable HTTP. Works without an account; sign in for more (below). Keel Stats is a research tool: it shows the
numbers, takes no bets and gives no picks.

## Connect

### Claude.ai, Claude Desktop (OAuth)

Settings → Connectors → Add custom connector → paste `https://api.keelstats.com/mcp`. Your assistant opens Keel Stats
in the browser to sign in and approve; there is no token to copy.

### ChatGPT

Keel Stats is in ChatGPT's app directory: search for **Keel Stats** and sign in with your Keel Stats account.

### Claude Code

```sh
claude mcp add --transport http keelstats https://api.keelstats.com/mcp
```

With an account, add a personal token from [keelstats.com/mcp](https://keelstats.com/mcp?utm_source=github&utm_medium=listing):

```sh
claude mcp add --transport http keelstats https://api.keelstats.com/mcp --header "Authorization: Bearer <YOUR_TOKEN>"
```

### Cursor and other `mcp.json` clients

```json
{
  "mcpServers": {
    "keelstats": {
      "url": "https://api.keelstats.com/mcp",
      "headers": {
        "Authorization": "Bearer <YOUR_TOKEN>"
      }
    }
  }
}
```

Leave out `headers` to use it without an account.

## What you get

| | Without an account | Free account | Keel Stats Pro |
|---|---|---|---|
| Seasons | This season and last | Every season | Every season |
| Games | Within two weeks of today | Any date | Any date |
| Recent games in a profile | 5 | 10 | 20 and the season |
| Pro tools | — | — | Included |

Every answer carries a `url` on keelstats.com to cite. An answer cut by the plan says what it left out and which plan
adds it.

## Tools

Twenty-two tools; sixteen of them are also in the ChatGPT app.

| Tool | What it answers | Plan | In ChatGPT |
|---|---|---|---|
| `search` | NBA and NFL players and teams by name, with IDs and URLs | Free | Yes |
| `tonight_slate` | Today's or the next slate's games, injury changes, last starters | Free | Yes |
| `find_game` | A team's game on a date, or its last and next three games | Free | Yes |
| `head_to_head` | Two teams' record over every meeting, this season's series, the next game | Free | Yes |
| `player_profile` | Season numbers, game log, Keel Impact and RAPM, next game's prop lines | Free, more with Pro | Yes |
| `team_profile` | Record, ratings, four factors or EPA efficiency, roster and schedule | Free | Yes |
| `rankings_and_ratings` | Keel Impact and RAPM leaderboards, NFL power rankings, team EPA | Free, more with Pro | Yes |
| `injury_consequences` | The injury report and what an absence changes for the team and teammates | Free | Yes |
| `game_projection` | Win probability and margin for any game; the full breakdown with Pro | Free, more with Pro | Yes |
| `player_splits_and_on_off` | On/off, clutch and garbage-time splits, teammates with and without | Pro | Yes |
| `defense_vs_position` | What each defense allows to each position, season and recent | Free, more with Pro | Yes |
| `props_research` | A player's prop lines against his recent games, or the day's board | Free, more with Pro | No |
| `line_history` | How lines opened, moved and closed; the month's market report | Pro | No |
| `prop_screener` | The day's player props filtered and ranked across games | Pro | No |
| `correlations` | Which players' lines go over or under together | Free | No |
| `stat_forecasts` | NBA minutes tonight, who gains when a teammate sits, expected stats | Free | Yes |
| `shot_quality` | Field-goal percentage against expected (xFG%), shots a defense allows | Pro | Yes |
| `pro_plan` | What Keel Stats Pro includes and which tools need it | Free | No |
| `lineups` | An NBA team's most-used five-man units, and the team with and without a player | Pro | Yes |
| `nfl_usage` | NFL targets, carries, shares and red-zone looks | Free | Yes |
| `line_shop` | Where a prop's line or price differs between sportsbooks today | Pro | No |
| `player_comparables` | The most similar players and how often a player reaches a number | Free | Yes |

The full list with what each tool answers on each plan is at
[keelstats.com/mcp](https://keelstats.com/mcp?utm_source=github&utm_medium=listing).

## Registry

Published in the official MCP Registry as `com.keelstats/keel-stats`; the entry is [`server.json`](server.json).

## Contact

contact@keelstats.com · [X](https://x.com/KeelStats) · [Bluesky](https://bsky.app/profile/keelstats.bsky.social)
