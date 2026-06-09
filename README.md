# AI Agent Acceptance Checklist

A practical checklist for evaluating AI agents before production deployment.

**Author:** [Artem Kholomyanskiy](https://github.com/Kholomyanskiy) — EVAI Consulting  
**Related:** [ANSS Standard](https://github.com/Kholomyanskiy/anss-standard) · [AI Requirements Template](https://github.com/Kholomyanskiy/ai-requirements-template)

---

## What this is

A structured pass/fail checklist covering 10 areas of AI agent quality:

1. Definition & Scope
2. System Prompt Quality
3. Tool Access & Permissions
4. Input & Output
5. Error Handling & Escalation
6. Security & Privacy
7. Multi-Agent Considerations
8. Testing
9. Monitoring & Observability
10. Acceptance Sign-off

## When to use it

- Before deploying an agent you built
- When reviewing an agent built by a contractor
- As part of an AI system audit
- Before integrating a third-party AI agent into your workflow

## How to use

Open `checklist.md`. Go through each item. Mark Pass / Fail / N/A.

**Hard stops:** Any failure in sections 3 (Tool Access) or 6 (Security) = do not deploy.

**Scoring:**

| Score | Decision |
|-------|----------|
| 100% | Deploy |
| 80–99% | Deploy with documented exceptions |
| 60–79% | Fix critical items first |
| < 60% | Do not deploy |

## Files

```
checklist.md    The checklist (10 sections, ~40 items)
```

## License

CC BY 4.0 — use freely, attribution appreciated.
