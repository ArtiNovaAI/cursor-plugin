---
name: list-assets
description: List recent ArtiNova generations for reuse, editing, or export.
---

# List assets

Use `list_assets` to browse recent generations tied to the API key owner.

## Examples

```
list_assets limit=10
get_credits
describe_asset asset_id="YOUR_ASSET_UUID"
```

## Workflow

1. Call `list_assets` to find `asset_id` values
2. Pass ids into `edit_image`, `remove_background`, or `describe_asset`
3. Download assets into the repo when needed

## Error handling

- Retry once on retryable errors
- If the list is empty, generate a new asset first with `generate_image`

Requires `ARTINOVA_API_KEY` in the environment.
