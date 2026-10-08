# Patch Notes

## Summary

I identified and fixed four high-value issues affecting task search, filtering, pagination, loading state, and API response time.

1. **Task search/status filtering** — Fixed SQL operator precedence in `TaskRepository.java` by grouping the title/description search conditions before applying the optional status filter. This prevents status filtering from being bypassed for title matches.

2. **Pagination after filters** — Updated `App.jsx` so changing the search query or status resets pagination to page 1. This prevents valid filtered results from appearing empty when the previous page no longer exists.

3. **Loading/error state** — Updated `useTasks.js` to clear stale errors when a new request starts and to stop the loading state when a request fails.

4. **Artificial API delay** — Removed the query-length-based `Thread.sleep()` from `TaskController.java`, which unnecessarily delayed every search request.

## What I did not change

I did not modify the database schema, seed data, API structure, or unrelated frontend/backend code because these were not required to address the identified issues.

## Remaining risk

There are no automated backend tests in the starter project, so verification was performed using the running application and API behavior. Additional automated tests would further protect the filtering and pagination behavior.

## AI/tools used

I used AI assistance to review code, reason about possible bugs, and plan focused fixes. I manually reproduced the filtering and pagination issues, reviewed the resulting changes, and verified that I understood each modification before applying it.