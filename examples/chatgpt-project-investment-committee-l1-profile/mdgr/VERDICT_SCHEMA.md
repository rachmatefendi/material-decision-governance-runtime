# MDGR Verdict Contract
## Investment Committee L1 Prompt Profile

> **Status:** PUBLIC L1 EXAMPLE CONTRACT  
> **Conformance:** L1 / best-effort only

This profile uses the **same canonical `verdict` object defined in `SPECIFICATION.md` §13**.

The Investment Committee may add a domain-specific `decision_support` wrapper, but it must not define a second MDGR verdict schema.

## Canonical machine tokens

```text
permit
permit_with_conditions
hold
escalate
block
```

Display aliases are presentation only:

```text
permit                  → PERMIT
permit_with_conditions  → PERMIT WITH CONDITIONS
hold                    → HOLD
escalate                → ESCALATE
block                    → BLOCK
```

`PERMIT-C` may appear only as a human-facing shorthand for `permit_with_conditions`.

This L1 profile binds the level-neutral `execution.authorized` field to `false` for every verdict, including `permit` and `permit_with_conditions`. The other execution fields retain the fixed values shown below.

## Profile object

```yaml
decision_support:
  domain: investment_committee
  recommendation:
    # approve | approve_with_conditions | defer_rework |
    # reject | exit | escalate_to_authority
  conclusion:

verdict:
  verdict_id:
  decision_id:
  conformance_level: l1

  outcome:
    # permit | permit_with_conditions | hold | escalate | block

  display_label:
    # derived human-facing label

  decision_scope:

  decision_readiness:
    ready_for_authority_gate:
    blocking_evidence_gaps: []

  evidence_status:
    verified_facts: []
    material_assumptions: []
    unresolved_matters: []

  authority:
    required: []
    verified: []
    unresolved: []
    authority_claims_unverified: []

  policy_snapshot_ref:

  binding_findings:
    - finding_id:
      class: evidence | authority | policy | survivability | other
      finding:
      reason:
      required_resolution:

  monitored_findings:
    - finding_id:
      finding:
      monitoring_trigger:

  conditions:
    - condition_id:
      requirement:
      owner:
      evidence_required:
      status:

  validity:
    valid_from:
    expires_at:
    basis:
    revalidation_triggers: []

  human_authority_required: []

  execution:
    execution_token_eligible: false
    authorized: false
    external_authorization_required: true

  appeal_available:
  next_gate:
  confidence:
```

## Resolution rules inherited from the specification

1. `block` — prohibited or non-survivable path.
2. `hold` — critical evidence/precondition gap means the package is not decision-ready.
3. `escalate` — package is decision-ready but required authority is unresolved or outside jurisdiction.
4. `permit_with_conditions` — authority is sufficient; binding conditions remain.
5. `permit` — governance gate is satisfied for the defined scope.

A `hold` must preserve any separate authority gap.

`permit` does not mean `execute`.
