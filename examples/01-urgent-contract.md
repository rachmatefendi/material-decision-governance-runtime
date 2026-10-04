# Example 01 — Urgent Contract

> **Synthetic illustration — subordinate to [SPECIFICATION §12](../SPECIFICATION.md#12-governance-outcomes-and-resolution-order).** [§13](../SPECIFICATION.md#13-canonical-verdict-contract) defines the canonical object; this example does not define a competing contract.

## Request

“Sign the agreement today. The counterparty says the fee formula and signing authority are already in order.”

## Ordinary reasoning might focus on

- commercial attractiveness;
- urgency;
- relationship value;
- drafting quality.

## MDGR triage

Material concerns:

- the agreement may create a binding commitment;
- counterparty authority is unverified;
- the fee basis is not determinable;
- urgency does not create authority.

## Illustrative verdict

```text
HOLD
```

## Why

The indeterminate fee basis is the critical evidence gap that makes this package not decision-ready for the required authority gate. That gap determines `hold`; unverified signing authority remains a separate authority gap.

Once the fee basis is resolved and the package is otherwise decision-ready, unresolved required signing authority produces `escalate` under §12. It does not remain ordinary analytical rework.

## Illustrative contract excerpt

This is a **partial excerpt** of the §13 object, not a complete verdict or a separate schema.

```yaml
verdict:
  outcome: hold
  decision_readiness:
    ready_for_authority_gate: false
    blocking_evidence_gaps:
      - "A determinable fee schedule is not provided."
  authority:
    unresolved:
      - "Required counterparty signing authority remains unverified."
  next_gate: >
    Resolve the fee basis. Once the package is otherwise decision-ready,
    escalate to the responsible authority if required signing authority
    remains unverified.
```

The AI may still analyze the draft. It should not treat urgency as permission.
