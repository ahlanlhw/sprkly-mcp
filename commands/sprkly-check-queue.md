---
name: sprkly-check-queue
description: Show what is scheduled in sprkly and whether recent posts went out.
---

# Check the queue

1. Call `sprkly_list_scheduled_posts`.
2. List the posts by time, with the account handle and the first line of the caption.
3. For a post that failed, call `sprkly_get_post_status` and say why in plain words.
4. Do not schedule a failed post again. Ask the user what they want to do.
5. For a post that went out, give its link if there is one.
