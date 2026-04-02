Adding custom fields to Wasp's default authentication flow requires a specific multi-step configuration across the DSL and backend code.

You need to add a `phoneNumber` field to the built-in signup process by modifying the DSL configuration and implementing a backend validator. 

**Constraints:**
- You must define `userSignupFields` inside the `auth` block in `main.wasp`.
- You must implement the field validation logic in a newly created `src/auth.ts` file and link it to the DSL configuration.
- Do NOT bypass Wasp's native `SignupForm` React component; you must pass the `additionalFields` configuration directly to it in the frontend.