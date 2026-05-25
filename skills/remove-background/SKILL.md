---
name: remove-background
description: Remove backgrounds from ArtiNova assets for transparent PNG/WebP exports.
---

# Remove background

Use `remove_background` for cutouts and compositing workflows.

## Examples

```
remove_background asset_id="YOUR_ASSET_UUID"
```

## Workflow

1. Generate or select a source asset
2. Call `remove_background`
3. Export transparent output to `public/` or design asset folders

## Error handling

- Retry once when `retryable` is true
- Confirm the asset id exists via `list_assets` before retrying `ASSET_NOT_FOUND`

Requires `ARTINOVA_API_KEY` in the environment.
