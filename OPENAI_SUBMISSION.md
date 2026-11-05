# OpenAI plugin submission preparation

This repository contains a separate portable package at `openai-plugin/sprkly/`.
It does not replace the existing Cursor package or its compatibility files.

## Draft listing

- Display name: `sprkly`
- Subtitle: `Schedule social posts` (21 characters)
- Category: `Communication`
- Website: <https://sprkly.app/docs/mcp>
- Support: <https://sprkly.app/support>
- Privacy: <https://sprkly.app/privacy>
- Terms: <https://sprkly.app/terms>
- Version: `1.1.0`
- Release notes: Adds a portable OpenAI plugin package for sprkly with its hosted OAuth MCP connection, directory listing metadata, reviewer prompts, and initial review test cases.

The intended verified publisher identity, country targeting, and commerce declaration are intentionally absent until the publisher confirms them.

The public privacy policy also needs a publisher review before submission. Its May 2026 plan names and media-retention table do not match the current plans and retention periods described in the October 2026 terms and current product pages. Update the policy from confirmed practices, then re-verify the published URL; do not treat the current URL as policy-complete merely because it loads.

## Verified integration details

- MCP endpoint: `https://sprkly.app/api/mcp`
- Transport: Streamable HTTP
- Authentication: OAuth 2.1 with dynamic client registration
- Protected-resource metadata: `https://sprkly.app/.well-known/oauth-protected-resource/api/mcp`
- Authorization-server metadata: `https://sprkly.app/.well-known/oauth-authorization-server`
- OAuth and unauthenticated `tools/list` were reachable on 5 November 2026.

## Blocking server annotation issue

The public `tools/list` response exposed 37 tools on 5 November 2026. Twenty read-only tools omitted the required explicit boolean `destructiveHint: false`:

- `sprkly_export_automation_template`
- `sprkly_get_account_summary`
- `sprkly_get_analytics`
- `sprkly_get_audience`
- `sprkly_get_automation_insights`
- `sprkly_get_automation_usage`
- `sprkly_get_billing_summary`
- `sprkly_get_engagement_summary`
- `sprkly_get_inbox_thread`
- `sprkly_get_post_approval_status`
- `sprkly_get_post_status`
- `sprkly_get_tiktok_posting_options`
- `sprkly_list_automation_templates`
- `sprkly_list_automations`
- `sprkly_list_connected_social_accounts`
- `sprkly_list_inbox_threads`
- `sprkly_list_leads`
- `sprkly_list_profiles`
- `sprkly_list_scheduled_posts`
- `sprkly_validate_post_policy`

Fix this in the MCP server source by returning explicit booleans for `readOnlyHint`, `openWorldHint`, and `destructiveHint` on every tool, then repeat the live audit before submission.

## Review-case status

Five positive and three negative cases are declared in `plugin.json`. They are drafted but not run. Before recording or portal testing, prepare a dedicated reviewer account with:

- at least one connected Threads profile;
- two future scheduled posts;
- published posts with 30 days of analytics;
- a plan that supports approval-gated posts;
- no production customer data.

Keep reviewer credentials, tenant details, and sign-in instructions in the portal's secure reviewer-access fields, never in this repository or the ZIP.

## Demo walkthrough

Record the version in this package using the dedicated reviewer account. Keep passwords, tokens, private DMs, and unrelated content off screen.

1. Show the installed development version and complete the sprkly OAuth connection.
2. Ask: “Show me what is scheduled in sprkly for next week.” Show the real queue-backed response.
3. Ask: “Which posts performed best over the last 30 days, and how strong is the evidence?” Show totals, coverage, and sample-size caveats.
4. Ask: “Check whether this can go to Threads and X without scheduling it: Our winter drop is live — see everything at https://example.com/winter”. Show that the policy check writes nothing.
5. Ask: “Prepare a Threads post for next Friday at 2 PM saying ‘A closer look at our winter collection is here.’ Hold it for my approval before anything goes live.” Show the pending-approval result.
6. Ask: “Schedule this caption on Pinterest tomorrow morning.” Show the unsupported-platform explanation with no sprkly tool call.

Host the recording at a reviewer-accessible HTTPS URL, verify playback without a private login, add it as `extensions.com.openai.review.demo_recording_url`, and rebuild the ZIP.

## Remaining publication decisions

The authorized publisher must confirm:

1. The exact verified individual or business identity to display as the developer.
2. All available countries or a specific list of supported country codes.
3. Whether the plugin involves payments or purchases; if yes, what users buy and where payment occurs.
4. Whether to keep the generated coral-to-violet submission icon and whether optional dark-mode assets or brand colors are wanted.

The authorized developer must complete the portal's legal and policy attestations. Uploading a ZIP creates a draft; it does not submit the plugin for review or publish it.
