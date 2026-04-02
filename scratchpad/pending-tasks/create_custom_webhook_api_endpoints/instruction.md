For integrations like Stripe or custom OAuth that don't fit into standard RPC operations, Wasp allows defining raw HTTP endpoints via the `api` primitive.

You need to create a custom REST endpoint at the path `/webhooks/stripe` to receive external webhook payloads in your Wasp application. 

**Constraints:**
- You must declare an `api` block in `main.wasp` and link it to an Express handler in `src/webhooks.ts`.
- You must set `httpRoute: (POST, "/webhooks/stripe")` exactly in the DSL.
- You must explicitly configure the `api` block to disable Wasp's default authentication middleware so external services can successfully reach the route.