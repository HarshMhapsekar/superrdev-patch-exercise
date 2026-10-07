@'
# Notes

## Summary of changes

- Fixed the task search query so the title/description search conditions are grouped before the optional status filter is applied. This prevents tasks from bypassing the archived and status conditions because of SQL operator precedence.
- Removed the artificial request-thread delay from the backend controller.
- Reset pagination to page 1 when the search text or status filter changes.
- Improved frontend request handling by clearing old errors, ending the loading state after failures, and cancelling superseded requests with AbortController to prevent stale responses from replacing newer results.

## Not changed

I left the SQL and Oracle reference artifacts unchanged because they are not executed by the local application, and I kept the patch focused on the running backend and frontend. I also did not redesign pagination or add unrelated features.

## Biggest remaining risk

The backend loads all matching records before applying pagination in memory. This can become inefficient as the task table grows.

## Tools / AI used

I used ChatGPT/Codex to help inspect the codebase, reason about likely bugs, review the final diff, and run build checks. I reviewed the suggested changes, applied the focused fixes, and prepared handwritten explanations in my own words.
'@ | Set-Content -Encoding utf8 NOTES.md

New-Item -ItemType Directory -Force handwritten