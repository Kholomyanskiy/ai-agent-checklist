# AI Agent Acceptance Checklist

Use before deploying an AI agent to production, or when reviewing an agent built by someone else.

**Pass / Fail / N/A for each item.**

---

## 1. Definition & Scope

- [ ] The agent has a single, clearly stated purpose
- [ ] The agent's scope is explicitly bounded (what it does NOT do is written down)
- [ ] The agent has a name and role that matches its actual function
- [ ] There is a human owner responsible for this agent

---

## 2. System Prompt Quality

- [ ] The system prompt states the agent's role in the first sentence
- [ ] The system prompt lists what the agent must NOT do
- [ ] The system prompt handles the "I don't know" case explicitly
- [ ] The system prompt does not rely on implicit assumptions
- [ ] The system prompt has been tested against adversarial inputs
- [ ] Tone and output format are specified

---

## 3. Tool Access & Permissions

- [ ] Every tool the agent has access to is actually needed
- [ ] The agent cannot access data outside its defined scope
- [ ] Write/delete operations are explicitly authorized (or absent)
- [ ] File system access is scoped to specific directories only
- [ ] External API calls are to known, approved endpoints only

---

## 4. Input & Output

- [ ] All input sources are documented
- [ ] The agent validates input before processing
- [ ] Output format is defined and consistent
- [ ] The agent does not leak internal prompts or system instructions in output
- [ ] Long outputs are chunked or summarized appropriately

---

## 5. Error Handling & Escalation

- [ ] The agent has an explicit "I can't do this" response path
- [ ] Errors are logged with enough context to debug
- [ ] There is a defined escalation path to a human
- [ ] The agent does not retry indefinitely on failure
- [ ] Partial results are labeled as such

---

## 6. Security & Privacy

- [ ] No credentials, API keys, or secrets are in the system prompt
- [ ] No PII is logged or persisted without explicit authorization
- [ ] The agent cannot be instructed to ignore its system prompt via user input (prompt injection resistance)
- [ ] Output is sanitized before display in UI (XSS, injection)
- [ ] GDPR / data residency requirements are met (if applicable)

---

## 7. Multi-Agent Considerations

*(Skip if standalone agent)*

- [ ] The agent's role in the pipeline is documented
- [ ] Input/output contracts with other agents are explicit
- [ ] The agent does not blindly trust input from other agents
- [ ] There is a circuit breaker if upstream agent fails
- [ ] The orchestrator has visibility into this agent's status

---

## 8. Testing

- [ ] At least 5 happy-path test cases exist and pass
- [ ] At least 3 edge cases are tested (empty input, unexpected format, boundary values)
- [ ] At least 2 adversarial inputs are tested (prompt injection, scope violations)
- [ ] Output is deterministic enough for regression testing (or randomness is controlled)
- [ ] A human has reviewed 20+ real outputs before go-live

---

## 9. Monitoring & Observability

- [ ] Each agent invocation is logged with: timestamp, input summary, output summary, latency
- [ ] There is an alert if error rate exceeds threshold
- [ ] Cost per invocation is tracked
- [ ] There is a way to kill or pause the agent without code changes

---

## 10. Acceptance Sign-off

- [ ] Product owner has approved the agent's behavior
- [ ] At least one person other than the builder has reviewed the system prompt
- [ ] Go/no-go decision is documented with date and approver

---

## Scoring

Count passed items. Suggested thresholds:

| Score | Decision |
|-------|----------|
| 100% | Deploy |
| 80–99% | Deploy with documented exceptions |
| 60–79% | Fix critical items first |
| < 60% | Do not deploy |

Items in sections 6 (Security) and 3 (Tool Access) are **mandatory** — any failure = do not deploy.

---

*Part of the [ANSS Standard](https://github.com/Kholomyanskiy/anss-standard) ecosystem.*  
*Author: Artem Kholomyanskiy, EVAI Consulting*
