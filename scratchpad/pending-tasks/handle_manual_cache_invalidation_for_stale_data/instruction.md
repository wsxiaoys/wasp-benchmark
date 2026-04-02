Wasp's automatic cache invalidation relies on Prisma entity tracking, which fails when state changes occur outside the database (e.g., calling a third-party API) or when updating non-entity configurations.

You need to debug and fix a stale data issue in `src/Dashboard.tsx` where a custom action `syncExternalData` executes successfully, but the associated `getStats` query does not automatically refresh on the UI. 

**Constraints:**
- You must use Wasp's `useQueryClient` wrapper from `@tanstack/react-query` to manually trigger the cache invalidation inside the React component after the action succeeds.
- Do NOT add a dummy `Task` or `User` entity to the `syncExternalData` action declaration in `main.wasp` just to force an automatic refresh.
- You must invalidate ONLY the specific query key associated with the Wasp `getStats` operation.