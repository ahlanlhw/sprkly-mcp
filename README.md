# Sprkly MCP Server

Post to social media by talking to your AI assistant.

Sprkly is a cross-platform social scheduling tool. This MCP server exposes it as a hosted
connector, so an assistant like Claude can draft captions, queue posts, and pull analytics
directly. No dashboard, no copy-paste.

**Endpoint:** `https://sprkly.app/api/mcp`
**Transport:** Streamable HTTP
**Auth:** OAuth
**Docs:** https://sprkly.app/docs/mcp

This repository contains the connector manifest and documentation. The server itself is hosted
by Sprkly and is closed source.

## Install

### Claude (web, desktop, mobile)

Settings → Connectors → Add custom connector → paste `https://sprkly.app/api/mcp`, then authorize.

### Any Streamable HTTP client

```json
{
  "mcpServers": {
    "sprkly": {
      "type": "http",
      "url": "https://sprkly.app/api/mcp"
    }
  }
}
```

## What it does

| Tool | Purpose |
|---|---|
| `sprkly_list_connected_social_accounts` | Every linked account: platform, handle, follower count |
| `sprkly_list_profiles` | Profile ids needed to target a post |
| `sprkly_draft_post` | Turn a content hint into a caption, saved as a draft |
| `sprkly_schedule_post` | Queue a post for publishing, in one call |
| `sprkly_update_scheduled_post` | Change caption, time, targets, or media before it goes out |
| `sprkly_delete_scheduled_post` | Remove a post from the queue |
| `sprkly_list_scheduled_posts` | The queue, newest first, with status and failure reasons |
| `sprkly_get_post_status` | Full detail for one post, including permalink |
| `sprkly_add_media_from_url` | Pull an image or video from a public link into Sprkly |
| `sprkly_validate_post_policy` | Check a caption against each platform's rules before scheduling |
| `sprkly_get_analytics` | Views and engagement on published posts |
| `sprkly_get_tiktok_posting_options` | Allowed TikTok privacy and interaction settings |
| `sprkly_request_post_approval` | Submit a draft for human review |
| `sprkly_get_post_approval_status` | Whether a post is awaiting review, approved, or rejected |
| `sprkly_get_account_summary` | Plan tier, trial state, connected accounts, queue counts |
| `sprkly_get_billing_summary` | Subscription status, plan, period end, purchased handles |

## Try these

> Show me what's in my Sprkly queue for next week.

> Draft a TikTok caption about our new winter drop and schedule it for Thursday 6pm.

> Which of my posts from the last 30 days got the most engagement?

## Safety

Scheduling and publishing tools change state and are annotated accordingly. Read-only tools
are marked read-only. `sprkly_validate_post_policy` runs a pre-flight check against each target
platform's rules so a post fails in chat rather than at publish time.

## Support

- Docs: https://sprkly.app/docs/mcp
- Issues: use this repository's issue tracker
- Email: hello@sprkly.app

## License

MIT (this manifest and documentation). The Sprkly service is governed by its own terms at
https://sprkly.app.
