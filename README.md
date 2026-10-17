<p align="center"><img src="logo.png" width="96" height="96" alt="LivePublicator"></p>

# LivePublicator MCP server

Publish press releases from ChatGPT, Claude and other AI assistants. Tell your assistant your news. It drafts the release with you, you check a private preview, and after you say publish, it goes live on its own page on LivePublicator. You never leave the chat.

Every release gets a permanent page with key facts, a quote, questions and answers and a press contact, in a clear, structured format that people, search engines and AI tools can read.

- **Connector address:** `https://livepublicator.com/api/mcp` (remote MCP server, streamable HTTP)
- **Sign-in:** OAuth. You sign in with a one-time link sent to your email. No API keys.
- **Setup guide:** https://livepublicator.com/publish-from-ai
- **Pricing:** https://livepublicator.com/publish-from-ai#pricing
- **Support:** support@livepublicator.com

This repository is the public listing for the hosted server. It has no server code.

## Add it to your assistant

### ChatGPT

Works today on ChatGPT team and company plans (Business, Enterprise, Edu). Plus, Pro and Free: coming soon through the ChatGPT app store.

1. A workspace admin turns on developer mode. Then open Settings, Apps and click **Create**.
2. Paste `https://livepublicator.com/api/mcp`, choose **OAuth**, click **Scan tools**, then **Create**.
3. Sign in with the link we email you, then ask ChatGPT to publish your news.

### Claude

Works today on all Claude plans (Free allows one custom connector).

1. Open **Customize**, then **Connectors**. Click **+ Add**, then **Add custom connector**. On Team and Enterprise, an owner adds it once under Organization settings.
2. Paste `https://livepublicator.com/api/mcp`. Choose **Sign in now** and **Use Claude's published identity**, then **Add**.
3. Sign in with the link we email you, then ask Claude to publish your news.

### Gemini

Works today with personal Google accounts. US only for now, with Google AI Pro or Ultra.

1. On gemini.google.com open Settings, then **Connected Apps**.
2. Click **Add a custom app** and paste `https://livepublicator.com/api/mcp`.
3. Sign in with the link we email you, then ask Gemini to publish your news.

### Grok

1. Open grok.com/connectors and click **New connector**, then **Custom**.
2. Paste `https://livepublicator.com/api/mcp`.
3. Sign in with the link we email you, then ask Grok to publish your news.

### OpenClaw

```
openclaw mcp add livepublicator --url https://livepublicator.com/api/mcp --transport streamable-http --auth oauth
openclaw mcp login livepublicator
```

### Hermes

Add this to `~/.hermes/config.yaml`, run `hermes mcp login livepublicator` and sign in, then `/reload-mcp`:

```yaml
mcp_servers:
  livepublicator:
    url: "https://livepublicator.com/api/mcp"
    auth: oauth
```

### Claude Code

```
claude mcp add --transport http livepublicator https://livepublicator.com/api/mcp
```

Then type `/mcp` and sign in.

### Cursor, Windsurf and other MCP clients

Add a server named `livepublicator` with the address `https://livepublicator.com/api/mcp` in their MCP settings, then sign in when asked. For a `mcp.json` file:

```json
{
  "mcpServers": {
    "livepublicator": { "url": "https://livepublicator.com/api/mcp" }
  }
}
```

## Example prompts

1. Publish a press release about our new feature.
2. Turn this blog post into a press release and publish it.
3. We just hired a new CTO. Announce it.

## Tools

| Tool | What it does |
| --- | --- |
| `preview_press_release` | Shows a private preview of a release without signing in. Publishes nothing. |
| `get_account` | Shows your account: the company, the saved press contact and spokesperson, and the credits left. |
| `create_release` | Saves a release as a draft, checks it, and returns a private preview link or every problem to fix. |
| `update_release` | Changes fields of a draft and checks it again. |
| `add_image` | Adds a cover image to a draft. |
| `publish_release` | Publishes a draft after you have seen the preview and said to publish. Uses 1 credit. |
| `get_release_status` | Says where a release is: draft, waiting for review, scheduled or live. |
| `list_releases` | Lists your earlier releases. |
| `fix_live_release` | Fixes the text of a live release within 24 hours of it going live. |

## Pricing

Previews are free. Publishing uses 1 credit per release. Credits are bought on the LivePublicator website, never in the chat, and they never expire. If a release is not published, its credit comes back. See https://livepublicator.com/publish-from-ai#pricing.

Some releases wait for a person to check them before they go live (up to 24 hours). LivePublicator emails you when it is live.

## Privacy and terms

LivePublicator receives only what your assistant sends to its tools (the release, its image and your account email), never your other chats.

- Privacy: https://livepublicator.com/privacy#ai-assistants
- Terms: https://livepublicator.com/terms
- Help: https://livepublicator.com/help/connect-ai-assistant

## Support

support@livepublicator.com

## Licence

The files in this repository are under the MIT licence (see LICENSE). The LivePublicator service has its own terms: https://livepublicator.com/terms
