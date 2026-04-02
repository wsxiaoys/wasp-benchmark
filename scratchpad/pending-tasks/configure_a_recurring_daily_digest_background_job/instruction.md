Wasp provides built-in orchestration for background jobs and email sending, configured directly via the declarative DSL.

You need to set up a background job named `dailyDigestJob` that executes a Node.js function to send a summary email to all users using the built-in `emailSender` utility. 

**Constraints:**
- The job schedule MUST be defined using a standard cron expression in `main.wasp` to run daily at 8:00 AM.
- You must configure the `emailSender` to use the `Dummy` provider in the app's configuration for local testing.
- Do NOT use external job schedulers (like `node-cron`); use exclusively Wasp's `job` declaration.