---
name: generate-image
description: Generate landing page heroes, product visuals, and marketing images with ArtiNova MCP.
---

# Generate image

Use `generate_image` for heroes, banners, and product visuals.

## Examples

```
generate_image prompt="Dark SaaS landing page hero for developer tools, 16:9" aspect_ratio="16:9" theme="dark"
generate_image prompt="Minimal fintech dashboard illustration" aspect_ratio="16:9" theme="light"
```

## Workflow

1. Preflight credits with `get_credits` when balance is unknown
2. Call `generate_image` with a specific prompt and aspect ratio
3. Save the returned asset into the repo (for example `public/hero.webp`)
4. Use `edit_image` if the first result needs refinement

## Error handling

If the tool returns a structured error:

- Read `error_code`, `message`, and `request_id`
- Retry once when `retryable` is true (for example `RATE_LIMITED`, `TOOL_TIMEOUT`)
- Do not retry on `INSUFFICIENT_CREDITS` or `TOOL_NOT_ALLOWED`

Requires `ARTINOVA_API_KEY` in the environment.
