---
name: sprkly-schedule-post
description: Schedule a social post with sprkly. Needs what to post, where, and when.
---

# Schedule a post

1. Get the four things a post needs: what (caption and any media links), where (platforms or accounts), when (a time in the user's own timezone), and how many.
2. Ask only for what is missing.
3. Write a caption per platform. TikTok and YouTube need a title. Instagram and TikTok need media.
4. Show the user the post. Then call `sprkly_schedule_post` with `media_urls` for any links.
5. If it returns `needsAccountChoice`, ask which accounts, then call again with `profile_ids`.
6. If it returns a validation error, fix what it names and call again.
7. Reply in one line: what goes where, and when.
