Wasp's operations require developers to manually enforce data isolation and authorization checks inside the Node.js implementation, as DSL-level access control for operations is not yet fully featured.

You need to implement a `getWorkspaceTasks` query that accepts a `workspaceId` and returns only the tasks belonging to that specific `Workspace` via Prisma. 

**Constraints:**
- You must verify that the requesting user is a verified member of the requested `Workspace` using Prisma via `context.entities`.
- Explicitly throw an `HttpError(403)` if the user attempts to query a workspace they do not belong to.
- Do NOT rely on frontend filtering; the isolation logic MUST be enforced on the backend query.