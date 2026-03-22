---
name: google-stitch
description: Google Stitch — AI UI design tool (stitch.withgoogle.com). Generates UI designs plus HTML/CSS from text prompts. Use for UI screen generation, design iteration, code export, and project/screen management via the Stitch MCP API.
---

# Google Stitch Skill

Stitch is Google's AI-native UI design canvas.

Prompt → high-fidelity UI → HTML/CSS export.

## What it is good for

Use Google Stitch when you want to:
- generate UI screens from a text prompt
- iterate on existing UI concepts
- manage design projects/screens
- export designs as HTML/CSS
- create quick UI prototypes before implementation

## API / MCP Endpoint

Google Stitch exposes an MCP-compatible JSON-RPC endpoint:

`https://stitch.googleapis.com/mcp`

## Authentication

Use OAuth2 with a Google account that has access to Stitch.

A typical flow is:
1. obtain an OAuth2 access token
2. send JSON-RPC requests to the Stitch MCP endpoint
3. use the returned project/screen metadata and download URLs

> Do not hardcode credentials or share private tokens in the skill.

## Available tools

Typical Stitch MCP tools include:

| Tool | Description |
|------|-------------|
| `list_projects` | List projects |
| `get_project` | Get project details |
| `create_project` | Create a new project |
| `list_screens` | List screens in a project |
| `get_screen` | Get screen details and asset/download URLs |
| `generate_screen_from_text` | Generate a UI screen from a prompt |
| `edit_screens` | Edit existing screens |
| `generate_variants` | Generate design variants |

## Example request

```bash
curl -s https://stitch.googleapis.com/mcp \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc":"2.0",
    "id":1,
    "method":"tools/call",
    "params":{
      "name":"generate_screen_from_text",
      "arguments":{
        "projectId":"<PROJECT_ID>",
        "prompt":"A dashboard with KPI cards and a line chart",
        "deviceType":"DESKTOP"
      }
    }
  }'
```

## Device types

Supported `deviceType` values typically include:
- `MOBILE`
- `DESKTOP`
- `TABLET`
- `AGNOSTIC`

## Prompting tips

Be specific about:
- device type
- visual style
- user goal
- information hierarchy
- important components

### Good prompt

`Mobile onboarding for a fitness app, clean minimal layout, iOS-style, progress indicator, one CTA per screen`

### Bad prompt

`nice screen`

## Recommended workflow

1. create or choose a project
2. generate a screen from a detailed prompt
3. inspect the result
4. refine via edit operations
5. generate variants if needed
6. export HTML/CSS for implementation

## Example implementation workflow

1. Generate screen via Stitch API
2. Retrieve HTML/CSS export URL
3. Download export
4. Hand off to implementation agent / frontend workflow

## Notes

- Stitch is strong for rapid UI ideation and structured iteration.
- The best results come from specific prompts, not vague aesthetic wishes.
- Keep credentials, local paths, project IDs, and private project names out of shared/public skill files.
