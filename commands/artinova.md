---
name: artinova
description: Run ArtiNova creative workflows in natural language — generate, edit, logo, and asset library tools.
---

# /artinova

Natural-language entrypoint for ArtiNova MCP tools.

Requires `ARTINOVA_API_KEY` in the environment (`an_live_*`).

## Usage

```
/artinova <request>
```

## Examples

```
/artinova Generate a dark SaaS landing page hero for a developer tools startup, 16:9
/artinova Create a minimal logo for ArtiNova on a dark theme
/artinova Remove the background from my latest hero image
/artinova Show my recent generated assets
/artinova How many credits do I have?
```

## Available tools

- `generate_image` — heroes, banners, product visuals
- `edit_image` — iterate an existing asset
- `remove_background` — transparent PNG/WebP cleanup
- `generate_logo` — startup/app logos
- `list_assets` — recent generations
- `get_credits` — remaining credits
- `describe_asset` — vision metadata for an asset

## Agent workflow

Generate → refine → export → save into repo → update frontend references.

## Error handling

1. Parse structured MCP errors (`error_code`, `message`, `retryable`, `request_id`)
2. Retry **once** when `retryable` is true
3. Report non-retryable errors clearly (credits, scopes, disabled keys)
4. Include `request_id` in user-facing failure messages

Do not produce verbose UX copy in tool responses. Consume the JSON payload directly.

Developer docs: https://artinova.ai/developers/docs
