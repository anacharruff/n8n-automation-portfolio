# n8n Automation Portfolio

AI-powered workflows I designed and built in [n8n](https://n8n.io), a low-code automation platform.

I spent ~10 years at Meta (WhatsApp, Facebook) in customer-operations program management. I was the single-threaded owner of WhatsApp's GenAI support chatbot program, from kickoff to 100% coverage across 20+ languages, and designed a multi-turn LLM-judge evaluation scorecard. These workflows apply the same habits on a smaller scale:

- **Turn signals into action.** Raw data becomes a score, the score decides a route, and each route triggers a playbook.
- **Put an LLM inside a real process.** The AI does one well-defined job; code and rules handle the rest.
- **Constrain the model.** Hard rules in the prompt (time budgets, "only use what's really in the pantry"), plus a guardrail that checks the output and falls back when it fails.

> PMP · IAPP AI Governance (EU AI Act) · Six Sigma Green Belt

---

## Workflows

| Workflow | What it does | Pattern shown | Status |
|---|---|---|---|
| [Customer Success Retention Program](workflows/customer-success-retention-program/) | Scores every account weekly on a weighted health model and routes it to the right playbook: at-risk escalation, voice-of-customer invite, or monitor | Weighted scoring + risk-band routing | Prototype on mock data |
| [Der C1-Booster](workflows/german-c1-booster/) | Emails a daily C1-level business-German lesson: word, realistic scenario, practice challenge | Structured generation from a tightly specified system prompt (Claude) | Ran daily on a schedule* |
| [L'Orchestrateur Culinaire](workflows/l-orchestrateur-culinaire/) | Suggests tonight's dinner using only what's actually in the pantry, emailed to the family at 18:00 | LLM agent with a hard "no invented ingredients" constraint (OpenAI) | Ran daily on a schedule* |
| [An Córas Glic](workflows/daily-chore-allocator/) | Picks the day's chores within a 20-minute budget, at most one high-effort task, and emails the plan every morning | Rule-constrained LLM planning, plus an error-notifier workflow and a v2 guardrail | Ran daily on a schedule* |

\* The personal workflows ran on daily schedules in my n8n Cloud account. They're paused since the trial ended and can be reactivated with the same files.

Each folder has the workflow file(s) to import into n8n and a README covering the problem, how it works and the design decisions.

---

## How to import a workflow

1. In n8n, go to **Workflows → Add workflow**.
2. Click **⋯ (top right) → Import from File** and pick the `.json` file.
3. Connect your own credentials. All credentials, email addresses and account IDs were removed before publishing:
   - an AI model (OpenAI or Anthropic)
   - Microsoft Outlook, for the email steps
4. Replace `you@example.com` with your own email address and activate the workflow.

---

## About me

Customer operations, GenAI deployment and program management. Based in Berlin. Native Spanish, professional English, German B1–B2 (working toward C1; see the C1-Booster).

<!-- Add your LinkedIn URL here, e.g. [LinkedIn](https://www.linkedin.com/in/your-profile) -->
