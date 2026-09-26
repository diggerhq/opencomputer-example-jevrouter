# Jev Router example protocol

This repository is a Development-first OpenComputer example for OpenRouter's
`typesafe/jev-router` model router.

- Keep `typesafe/jev-router` as the model declaration; do not rebuild its
  routing with a Decisions API tool or local classifier.
- Keep the example minimal. New tools or external writes need their own safety
  contract and are outside this example.
- Never add an OpenRouter key to source, prompts, or agent runtime variables.
  Model credentials belong to OpenComputer's managed model gateway.
- Deploy only to an explicitly named OpenComputer Development project.
- Verify changes with `npm run typecheck`.
