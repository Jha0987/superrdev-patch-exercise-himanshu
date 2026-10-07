# Patch Notes

## Summary of Changes

I focused on four high-value issues across the backend and frontend.

1. Removed an artificial Thread.sleep delay from the task search endpoint because it added unnecessary request latency.
2. Fixed the native SQL search query by grouping the title/description OR condition so archived and status filters are applied consistently.
3. Fixed frontend request state handling so loading is cleared after failures, previous errors are cleared when a new request starts, and stale requests cannot overwrite newer results.
4. Reset pagination to page 1 whenever the search term or status filter changes.

## What I Chose Not to Change

I did not rewrite the application or introduce new libraries. I also left the existing pagination architecture unchanged because the exercise is intended to be a focused patch rather than a redesign.

## Biggest Remaining Risk

The backend currently retrieves all matching tasks and performs pagination in application memory. This may become inefficient as the number of tasks increases. Database-level pagination would be the next improvement.

## Tools / AI Used

I used ChatGPT to review the frontend, backend, and SQL logic and to help identify likely bugs and possible fixes. I reviewed the suggestions manually and kept only changes that I could understand and explain.