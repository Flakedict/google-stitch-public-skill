# Google Stitch — SDK and Tooling Notes

## MCP Endpoint

`https://stitch.googleapis.com/mcp`

## Useful MCP tools

- `list_projects`
- `get_project`
- `create_project`
- `list_screens`
- `get_screen`
- `generate_screen_from_text`
- `edit_screens`
- `generate_variants`

## SDK Patterns

### Basic generation
```ts
import { stitch } from '@google/stitch-sdk';
const project = stitch.project('<project-id>');
const screen = await project.generate('A login page with email and password fields');
const htmlUrl = await screen.getHtml();
const imageUrl = await screen.getImage();
```

### Edit a screen
```ts
const edited = await screen.edit('Make the background dark and add a sidebar');
```

### Variants
```ts
const variants = await screen.variants('Try different color schemes', {
  variantCount: 3,
  creativeRange: 'EXPLORE',
  aspects: ['COLOR_SCHEME', 'LAYOUT'],
});
```
