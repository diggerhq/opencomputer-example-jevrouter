# OpenComputer with OpenRouter's Jev Router

The smallest useful OpenComputer example for
[`typesafe/jev-router`](https://openrouter.ai/typesafe/jev-router).

[Deploy this template in OpenComputer](https://app.opencomputer.dev/new?repository-url=https%3A%2F%2Fgithub.com%2Fdiggerhq%2Fopencomputer-example-jevrouter)

Jev Router is already the model router. Your agent uses it like any other model:

```ts
import { useModel } from "@opencomputer/agent";

export default function Agent() {
  useModel("typesafe/jev-router");
  return "You are a helpful general-purpose assistant.";
}
```

That is the integration. OpenRouter receives each normal chat request, uses
Jev to choose the downstream model and reasoning effort, and returns that
model's response. The router can adapt as the conversation evolves.

There is no local classification tool, Decisions API request, confidence
threshold, hand-written candidate list, or specialist-agent dispatch in this
example. Those would duplicate functionality already provided by
`typesafe/jev-router`.

## Run it in Development

Requirements: Node.js 22+ and an OpenComputer account.

```bash
npm install
npm run opencomputer -- login
npm run opencomputer -- link --create-project jev-router-example
npm run deploy:watch
```

Open the printed debug-playground URL and try different workloads:

```text
Summarize why idempotency matters in distributed systems in three bullets.
```

```text
Review this TypeScript function for race conditions and propose a tested fix: ...
```

```text
Design a migration plan from a monolith to event-driven services. Include risks,
rollback gates, and a sequence diagram.
```

Continue in the same session with a follow-up question to see routing operate
across a conversation.

## Verify

```bash
npm run typecheck
```

Inspect the session events and your OpenRouter activity to see which downstream
model served a request. The agent should not assert the routed model based on
its own generated text.

OpenComputer's managed model gateway owns provider authentication. This example
does not put an OpenRouter key in source, prompts, or agent runtime variables.
