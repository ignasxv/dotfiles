# Notion Configuration

## daily-knowledge database
- Database URL: https://www.notion.so/YOUR_DATABASE_ID
- Data source ID: `YOUR_DATA_SOURCE_ID`
- Parent: `{ "type": "data_source_id", "data_source_id": "YOUR_DATA_SOURCE_ID" }`

### Schema
| Property | Type | Options |
|---|---|---|
| Name | title | lesson title |
| Date | date | YYYY-MM-DD (today's date) |
| Category | select | Linux / CLI, Programming, Tools & Setup, Networking, Security, Concepts, Other |
| Tags | multi_select | terminal, notion, claude, linux, gotcha |
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
