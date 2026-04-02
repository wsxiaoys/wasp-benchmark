Wasp handles frontend-backend RPCs via declared actions that automatically invalidate React query caches when tied to an entity.

You need to implement a `markAllDone` action in `src/actions.ts` that sets the `isDone` boolean to `true` for all tasks belonging to the current authenticated user, and declare this operation in `main.wasp`. 

**Constraints:**
- You must explicitly throw an `HttpError(401)` if `context.user` is undefined inside the Node.js action implementation.
- You must list `entities:[Task]` in the `main.wasp` action declaration to ensure automatic UI refreshing.
- Do NOT modify the Prisma schema; assume the `Task` entity already has `isDone` and `userId` fields.