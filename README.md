# sprkly MCP server and plugin

Post to social media by talking to your AI assistant.

- sprkly schedules posts to Instagram, TikTok, YouTube, Threads, Facebook, Bluesky, X, LinkedIn and Telegram.
- This MCP server lets an assistant like Cursor or Claude queue posts, check the queue and read how posts did.
- No dashboard. No copy and paste.

**Endpoint:** `https://sprkly.app/api/mcp`
**Transport:** Streamable HTTP
**Sign-in:** OAuth. You sign in to sprkly in your browser the first time. No API key in any file.
**Docs:** https://sprkly.app/docs/mcp

This repo holds the plugin files and the docs. The server is hosted by sprkly and is closed source.

## Plans

- Works on the 7-day free trial. No card needed.
- Works on every paid plan: US$29, US$39, US$49 or US$99 a month. See https://sprkly.app/checkout.
- Not on the Free plan.

## Install

### Cursor

- Install the sprkly plugin. It adds the MCP server, a skill, a rule and two commands.
- Or add the server by hand in `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "sprkly": {
      "url": "https://sprkly.app/api/mcp"
    }
  }
}
```

- Reload Cursor. When sprkly shows in the MCP list, approve the sign-in.

### Claude (web, desktop, mobile)

- Settings, then Connectors, then Add custom connector.
- Paste `https://sprkly.app/api/mcp`, then sign in.

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

## What is in this repo

| Path | What it is |
|---|---|
| `.cursor-plugin/plugin.json` | The plugin manifest |
| `.mcp.json` | The hosted MCP server |
| `skills/sprkly/SKILL.md` | How to post well with sprkly |
| `rules/sprkly.mdc` | Safety rules for posting |
| `commands/sprkly-schedule-post.md` | Schedule a post |
| `commands/sprkly-check-queue.md` | See what is queued |
| `server.json` | MCP Registry entry |
| `glama.json` | Glama listing |

## What it does

**Posts**

| Tool | What it does |
|---|---|
| `sprkly_schedule_post` | Queue a post in one call. It checks each platform's rules first. |
| `sprkly_update_scheduled_post` | Change the caption, time, accounts or media before it goes out |
| `sprkly_delete_scheduled_post` | Take a post out of the queue |
| `sprkly_draft_post` | Save a caption as a draft |
| `sprkly_list_scheduled_posts` | The queue, with status and why a post failed |
| `sprkly_get_post_status` | One post in full, with its link |
| `sprkly_validate_post_policy` | Check a draft against each platform's rules without posting |
| `sprkly_add_media_from_url` | Pull a photo or video from a public link |
| `sprkly_upload_media` | Send files from your disk |
| `sprkly_get_tiktok_posting_options` | The TikTok privacy settings you are allowed |
| `sprkly_request_post_approval` | Send a draft for review |
| `sprkly_get_post_approval_status` | Is it waiting, approved or turned down |

**Accounts and numbers**

| Tool | What it does |
|---|---|
| `sprkly_list_profiles` | The accounts you can post to |
| `sprkly_list_connected_social_accounts` | Each linked account, with handle and followers |
| `sprkly_get_analytics` | Views and engagement, best times, top posts |
| `sprkly_get_audience` | Who follows you on Instagram |
| `sprkly_get_engagement_summary` | Last week against the week before |
| `sprkly_get_account_summary` | Plan, trial, accounts and queue counts |
| `sprkly_get_billing_summary` | Plan and when it renews |

**Instagram auto replies and inbox**

| Tool | What it does |
|---|---|
| `sprkly_list_automation_templates` | Ready-made auto replies |
| `sprkly_create_automation_from_template` | Set one up and turn it on |
| `sprkly_import_automation_template` | Read or set up a template file |
| `sprkly_export_automation_template` | Save an auto reply as a file |
| `sprkly_list_automations` | What is on |
| `sprkly_pause_automation` | Turn one off |
| `sprkly_resume_automation` | Turn one back on |
| `sprkly_get_automation_usage` | People messaged this month, and the limit |
| `sprkly_get_automation_insights` | What auto replies did over 7, 30 or 90 days |
| `sprkly_list_leads` | Who asked for the link |
| `sprkly_list_inbox_threads` | Who is waiting for an answer |
| `sprkly_get_inbox_thread` | Read one conversation |
| `sprkly_reply_to_dm` | Answer a DM |
| `sprkly_reply_to_comment` | Answer a comment in public |

## Try these

> Show me what is in my sprkly queue for next week.

> Write a TikTok caption about our new winter drop and schedule it for Thursday 6pm.

> Which of my posts from the last 30 days did best?

## Safety

- Tools that change things are marked that way. Read-only tools are marked read-only.
- `sprkly_schedule_post` checks each platform's rules first, so a post fails in chat, not at publish time.
- Inbox tools stay off until you allow inbox access.

## Support

- Docs: https://sprkly.app/docs/mcp
- Issues: this repo's issue tracker
- Email: hello@sprkly.app

## License

MIT for the files in this repo. The sprkly service has its own terms at https://sprkly.app.
