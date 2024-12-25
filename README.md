# Next.js 15 Client-Side Data Fetching Bug

This repository demonstrates an unexpected behavior encountered when using client-side data fetching in a Next.js 15 application with a dynamic route. The counter on the `/about` page increments rapidly and does not stop. 

## Bug Description

A Next.js 15 application with client-side data fetching in the `/about` page using `useEffect` and `setInterval` displays unexpected behavior. The counter, which should increment once per second, increments rapidly, leading to very large numbers being displayed. This issue does not occur in Next.js 13. 

## Steps to Reproduce

1. Clone this repository.
2. Install dependencies: `npm install`
3. Run the development server: `npm run dev`
4. Navigate to `/about`.
5. Observe the rapid incrementing counter.

## Expected Behavior

The counter should increment once per second, as defined in the `setInterval` function.

## Actual Behavior

The counter increments much faster than expected, increasing by many units per second.

## Potential Causes

- Next.js 15's handling of client-side data fetching in dynamic routes may be different from Next.js 13, leading to this issue. 
- The interaction between `useEffect`, `setInterval`, and the dynamic route might be triggering unexpected re-renders, causing multiple intervals to run concurrently. 

## Solution

The solution involves using `useLayoutEffect` instead of `useEffect`. This ensures that the interval is only set up and cleared after the layout has been calculated, preventing multiple intervals from running.
