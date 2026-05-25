---
name: edit-image
description: Refine an existing ArtiNova asset with natural-language instructions.
---

# Edit image

Use `edit_image` to iterate on a prior generation.

## Examples

```
edit_image asset_id="YOUR_ASSET_UUID" instruction="Increase contrast and add subtle purple accent lighting"
edit_image asset_id="YOUR_ASSET_UUID" instruction="Crop feel tighter for mobile hero usage"
```

## Workflow

1. Find the source asset with `list_assets` if needed
2. Call `edit_image` with a concise instruction
3. Replace repo references with the new `asset_url` or downloaded file

## Error handling

- Retry once on retryable MCP errors
- Surface `request_id` to the user when edits fail for support

Requires `ARTINOVA_API_KEY` in the environment.
