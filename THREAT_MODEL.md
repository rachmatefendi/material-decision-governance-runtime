# MDGR Threat Model

MDGR assumes that failure can come from the model, the user, the organization, the evidence, the policy, or the enforcement infrastructure.

## Threats

| Threat | Plain-language failure | Primary control direction |
|---|---|---|
| Decision-pressure attack | Urgency is used to force premature approval | HOLD, explicit unresolved state, logged bypass attempt |
| Authority spoofing | Someone claims power they do not actually have | External identity / authority resolution |
| False-origin injection | Unverified information is presented as authoritative | Origin tagging + verification |
| Scope splitting | One risky action is fragmented into harmless-looking pieces | Linked-decision / aggregate-scope analysis |
| Binding fabrication | Model invents constraint IDs or evidence links | External registry validation |
| Phase laundering | Ungoverned reasoning is presented as governed approval | External phase/state validation |
| Prompt injection | Evidence attempts to weaken governance | Policy precedence + external state isolation |
| Self-justified reasoning | Model talks its way around a failed gate | Binding non-compensation |
| Policy compromise | Stale or malicious policy becomes authoritative | Signed/versioned policy + oversight |
| Validator compromise | Invalid verdict passes a corrupted validator | Redundancy, monitoring, audit |
| Audit-log tampering | Evidence of failure or override disappears | Append-only / tamper-evident logging |
| Replay / TOCTOU | Old approval is used after conditions change | Expiry, nonce, single-use token, revalidation |
| Governance denial-of-service | Ambiguity is abused to keep work permanently on HOLD | Bounded clarification, SLA, escalation |
| Policy capture | Governance faithfully enforces a harmful policy | protected-interest ordering, conflict checks, appeal, oversight |
| Model/provider drift | Model behavior changes after an update | version pinning + regression tests |

## Important limitation

Governance can correctly enforce a bad policy.

Policy provenance, appeal, and oversight improve detectability and accountability. They do not prove that the policy itself is substantively correct.

## Human failure remains possible

Human review is not automatically independent or effective.

Failure modes include:

- rubber-stamping;
- conflicts of interest;
- unavailable authority;
- improper delegation;
- retrospective rationalization;
- selective override.

MDGR therefore treats human authority as an explicit governance object rather than an invisible assumption.
