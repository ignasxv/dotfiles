# Notion Configuration

## daily-knowledge database
- Database URL: https://www.notion.so/fc9ac6768e41437daecb9fc29fa6b541
- Data source ID: `38b3818c-d4e0-4fa4-a368-8babb9b6c640`
- Parent: `{ "type": "data_source_id", "data_source_id": "38b3818c-d4e0-4fa4-a368-8babb9b6c640" }`

### Schema
| Property | Type | Options |
|---|---|---|
| Name | title | lesson title |
| Date | date | YYYY-MM-DD (today's date) |
| Category | select | Linux / CLI, Programming, Tools & Setup, Networking, Security, Concepts, Other |
| Tags | multi_select | terminal, notion, claude, linux, gotcha (ONLY these values are valid — do not use other tags) |
| Source | rich_text | e.g. "Claude Code session", "YouTube", "article" |

### Entry content format
```
## What I Learned
...

## Steps / Commands
...

## Gotchas
...

## Key Concepts
...
```

Use `mcp__notion__notion-create-pages`. Load Notion tools first with `ToolSearch` if not available.
