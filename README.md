# ArtiNova for Cursor

Generate landing page heroes, logos, and marketing assets inside Cursor via the ArtiNova MCP server.

**Install:** [cursor://plugin/install/artinova](cursor://plugin/install/artinova)  
**Docs:** https://artinova.ai/developers/cursor

## Install

1. Install the plugin: open `cursor://plugin/install/artinova` or search **ArtiNova** in Cursor Settings → Plugins.
2. Create an API key at https://artinova.ai/profile → **Agent API Keys** (`an_live_*` prefix).
3. In Cursor Settings → **Tools & MCP**, set environment variable `ARTINOVA_API_KEY` to your key.
4. Reload Cursor (`Developer: Reload Window`).
5. Confirm **ArtiNova** shows as connected under Tools & MCP.

The plugin calls `https://artinova.ai/api/mcp/v1`. No manual config file edits are required after install.

## Quickstart

Ask in chat:

```
/artinova Generate a dark SaaS landing page hero for a developer tools startup, 16:9
```

Or invoke MCP tools directly:

```
generate_image prompt="Minimal fintech dashboard UI mockup, light theme, 16:9" aspect_ratio="16:9"
```

## Example prompts

```
/artinova Generate a dark SaaS landing page hero for a developer tools startup, 16:9
/artinova Generate a modern fintech dashboard UI mockup, light theme, 16:9
/artinova Create a minimal logo for ArtiNova on a dark theme
```

## What you get

- Durable asset library with signed URLs and creation IDs
- Credit governance, scopes, and optional org keys
- Structured MCP errors designed for coding agents
- Skills for generate, edit, logo, background removal, and asset listing

## MCP headers

Every request sends:

- `Authorization: Bearer ${ARTINOVA_API_KEY}` (from your Cursor env)
- `x-artinova-source: cursor` (optional analytics attribution; not required for tool execution)

No user PII is sent in headers.

## Troubleshooting

| Issue | Fix |
| --- | --- |
| MCP shows disconnected | Set `ARTINOVA_API_KEY` in Cursor env and reload |
| `UNAUTHORIZED` | Key revoked, disabled, or wrong prefix (`an_live_*`) |
| `INSUFFICIENT_CREDITS` | Add credits in Profile; new personal keys get 20 starter credits before first MCP call |
| `TOOL_NOT_ALLOWED` | Check key scopes in Profile → Agent API Keys |
| No image in response | Parse JSON `asset_url` from the tool text payload |

Structured errors include `error_code`, `message`, `retryable`, and `request_id`. Retry once when `retryable` is true. Do not retry on `INSUFFICIENT_CREDITS`, `TOOL_NOT_ALLOWED`, or `API_KEY_DISABLED`.

## Links

- Source: https://github.com/ArtiNovaAI/cursor-plugin
- Cursor landing: https://artinova.ai/developers/cursor
- Developer hub: https://artinova.ai/developers
- API docs: https://artinova.ai/developers/docs
- Agent onboarding: https://artinova.ai/agents

## License

MIT
