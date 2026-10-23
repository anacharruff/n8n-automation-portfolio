# n8n Automation Portfolio

AI-powered workflows I designed and built in [n8n](https://n8n.io), a low-code automation platform.

I spent ~10 years at Meta (WhatsApp, Facebook) in customer-operations program management. I was the single-threaded owner of WhatsApp's GenAI support chatbot program, from kickoff to 100% coverage across 20+ languages, and designed a multi-turn LLM-judge evaluation scorecard. These workflows apply the same habits on a smaller scale:

- **Turn signals into action.** Raw data becomes a score, the score decides a route, and each route triggers a playbook.
- **Put an LLM inside a real process.** The AI does one well-defined job; code and rules handle the rest.
- **Constrain the model.** Hard rules in the prompt (time budgets, "only use what's really in the pantry"), plus a guardrail that checks the output and falls back when it fails.

> PMP · IAPP AI Governance (EU AI Act) · Six Sigma Green Belt

## Workflows

| Workflow | What it does | Pattern shown | Status |
|---|---|---|---|
| [**Customer Health Scoring**](customer-health-scoring/) | Scores every account weekly on a weighted health model and routes it to the right playbook: at-risk escalation, Voice of Customer invite, or monitor | Weighted scoring + risk-band routing | Prototype on sample data |
| [**Smart Chore Allocator**](smart-chore-allocator/) (An Córas Glic) | Picks the day's chores within a 20-minute budget, at most one high-effort task, and emails the plan every morning | Rule-constrained LLM planning, code guardrail with fallback, error-notifier workflow, v1 → v2 iteration | Ran daily on a schedule* |
| [**C1 German Booster**](c1-german-booster/) (Der C1-Booster) | Emails a daily C1-level business German lesson: word, realistic scenario, practice challenge | Structured generation from a tightly specified system prompt (Claude) | Ran daily on a schedule* |
| [**Culinary Orchestrator**](culinary-orchestrator/) (L'Orchestrateur Culinaire) | Suggests tonight's dinner using only what's actually in the pantry, emailed at 18:00 | LLM agent with a hard "no invented ingredients" constraint (OpenAI) | Ran daily on a schedule* |

\* The personal workflows ran on daily schedules in my n8n Cloud account. They're paused since the trial ended.

## Highlight: adding a guardrail (v1 → v2)

The first version of the chore allocator trusted the model's JSON output. v2 checks it in code: it rejects chores that aren't on the list, recalculates time and effort from the source data instead of trusting the model's numbers, and switches to a rule-based plan if any rule is broken. A separate error workflow emails me if anything still fails. [Read the details →](smart-chore-allocator/#from-v1-to-v2-adding-a-guardrail)

## Skills demonstrated

- **AI agent design:** system prompts with strict output contracts (JSON schemas, fixed section headings, "use only these ingredients" constraints)
- **Reliability for LLMs:** validating model output, re-deriving numbers from the source of truth, rule-based fallbacks, error workflows
- **Business logic in code:** weighted scoring models, routing rules, rotation algorithms (JavaScript Code nodes)
- **Integration:** Anthropic Claude and OpenAI models, Microsoft Outlook (OAuth2), scheduled triggers, n8n Error Trigger

## Using these workflows

1. In n8n, go to **Workflows → Import from File** and choose the workflow's `.json` file.
2. Add your own credentials (Anthropic / OpenAI API key, Microsoft Outlook OAuth2). No credentials are included in this repo.
3. Replace `you@example.com` with your email address in the Send Email node.
4. Run it once manually to test, then activate it.

Each folder's README lists the specific setup steps.

## Tech stack

n8n · JavaScript · Anthropic Claude · OpenAI GPT · Microsoft Outlook · LangChain agent nodes
