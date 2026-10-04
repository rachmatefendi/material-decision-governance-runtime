# MDGR Glossary

## Authority
The legitimate organizational, legal, or delegated power to make or approve a decision.

## Binding finding
A finding that must be resolved or satisfied before the decision may progress.

## Decision
An authorized verdict selecting, conditioning, or prohibiting a course of action.

## Decision validity window
The period during which a decision remains valid before it must be revalidated.

## Escalate
Under [SPECIFICATION §12](SPECIFICATION.md#12-governance-outcomes-and-resolution-order), use `escalate` when the package is otherwise decision-ready but required authority is missing, unverified, or outside the current jurisdiction; apply the resolution order in §12.2.

## Execution
A real-world action taken by an authorized actor.

## Execution gate
An external control that checks whether a consequential action is currently allowed.

## Execution token
A scoped, time-bounded authorization artifact for a specific governed action. In strong implementations it should be externally issued and validated.

## Hold
Under [SPECIFICATION §12](SPECIFICATION.md#12-governance-outcomes-and-resolution-order), use `hold` when a critical evidence or precondition gap makes the package not decision-ready for the required authority gate; any separate authority gap remains explicit and becomes an escalation gate once the package is ready, subject to §12.2.

## MDGR
**Material Decision Governance Runtime** — the canonical name used in this repository.

## Monitored finding
A non-blocking finding that remains visible and may trigger revalidation or future action.

## Permit
The material governance gate is satisfied for the defined scope and state.

## Permit with conditions
Human-facing label for the canonical machine token `permit_with_conditions`.

`PERMIT-C` may be used as a display shorthand only. It is not a second verdict token.

The decision may progress only under explicit binding conditions.

## Policy snapshot
The specific policy version(s) under which a verdict was produced.

## Protected interest
A person, right, duty, public interest, organizational interest, or other value that governance is required to protect.

## Reasoning
Analysis of facts, assumptions, alternatives, and consequences.

## Revocation
A later governance event that invalidates a previously effective permission.

## Survivability
Whether credible downside remains within a recoverable or otherwise acceptable boundary after enforceable controls are considered.

## Verdict
The formal MDGR machine outcome: `permit`, `permit_with_conditions`, `hold`, `escalate`, or `block`.
