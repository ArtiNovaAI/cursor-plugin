---
name: generate-logo
description: Generate startup, app, or SaaS logos with ArtiNova MCP.
---

# Generate logo

Use `generate_logo` for app icons, startup marks, and product branding.

## Examples

```
generate_logo brand_name="ArtiNova" style="minimal" theme="dark"
generate_logo brand_name="LaunchPad" style="modern" theme="light"
```

## Workflow

1. Generate 1–2 logo options
2. Refine with `edit_image` if needed
3. Export to `public/logo.png` or `public/icon.png`
4. Update navbar and metadata references in code

Return values include `suggested_filename` and `svg_available`.

## Error handling

- Retry once on transient MCP failures
- Show structured errors (`error_code`, `message`, `request_id`) instead of generic failure text

Requires `ARTINOVA_API_KEY` in the environment.
