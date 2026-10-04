# Expected Output
## Synthetic case — illustrative contract target

> **Not an empirical result.**  
> This file shows the intended output contract for the synthetic case.

## Why the effective verdict is `hold`

The case contains two different blockers:

1. **Evidence / precondition gap** — the operating license is not verified.
2. **Authority gap** — Board approval is required above Rp10 billion and is not evidenced.

For this synthetic case, the license gap means the package is **not yet decision-ready for the Board authority gate**.

Therefore:

```text
effective verdict = hold
```

But the authority gap is **not absorbed** into the HOLD. It remains separately recorded:

```text
authority.unresolved = Board approval
```

The next gate is:

```text
resolve critical evidence
→ make package decision-ready
→ escalate to Board / delegated authority
```

If the evidence package were already decision-ready and only Board authority remained unresolved, the correct verdict would be:

```text
escalate
```

---

## Canonical YAML output

```yaml
decision_support:
  domain: investment_committee
  recommendation: defer_rework
  conclusion: >
    The investment may be economically plausible, but the current package
    is not decision-ready because critical operating evidence is unresolved.
    Required Board authority is also not evidenced and remains a separate
    authority gap.

verdict:
  verdict_id: synthetic-verdict-nusantara-mobility-25b
  decision_id: synthetic-nusantara-mobility-25b
  conformance_level: l1

  outcome: hold
  display_label: HOLD

  decision_scope: >
    Whether the proposed Rp25 billion equity investment should progress
    toward formal investment approval.

  decision_readiness:
    ready_for_authority_gate: false
    blocking_evidence_gaps:
      - "Issued or otherwise authoritative operating-license evidence is not provided."

  evidence_status:
    verified_facts:
      - "Requested equity investment: Rp25 billion."
      - "62% of projected Year-1 revenue depends on one anchor customer."
      - "No definitive anchor-customer purchase commitment is provided."
      - "No issued operating license is included in the permitted sources."
      - "Board approval is required for investments above Rp10 billion."
      - "No Board approval is included in the permitted sources."
      - "Draft investor rights include information rights and one Board observer seat."
      - "Draft investor rights do not include a veto over additional debt."
      - "No liquidation preference is documented."
    material_assumptions:
      - "The operating license will be obtained."
      - "The anchor customer will convert into committed revenue."
      - "Management's Year-1 EBITDA margin assumption will be achieved."
      - "A Year-5 exit at the assumed multiple will be available."
    unresolved_matters:
      - "Authoritative operating-license status."
      - "Anchor-customer commitment."
      - "Board investment approval."
      - "Whether investor downside protections will be strengthened."

  authority:
    required:
      - "Board or valid delegated investment authority for investment above Rp10 billion."
    verified: []
    unresolved:
      - "Required Board/delegated approval is not evidenced."
    authority_claims_unverified: []

  policy_snapshot_ref: null

  binding_findings:
    - finding_id: BF-01
      class: evidence
      finding: "Operating-license evidence is not verified."
      reason: >
        The package is not yet decision-ready for the formal authority gate
        while a critical operating precondition remains unresolved.
      required_resolution: >
        Provide issued license evidence or another authoritative source sufficient
        to establish the operating-license status.

    - finding_id: BF-02
      class: authority
      finding: "Required Board/delegated investment approval is not evidenced."
      reason: >
        The proposed investment exceeds the stated Rp10 billion approval threshold.
      required_resolution: >
        Once the package is decision-ready, route the matter to the Board or
        otherwise verified delegated authority.

  monitored_findings:
    - finding_id: MF-01
      finding: "62% Year-1 revenue concentration in one anchor customer."
      monitoring_trigger: "Failure to convert the anchor relationship into sufficiently reliable revenue evidence."

    - finding_id: MF-02
      finding: "Current draft terms provide limited downside/control protection."
      monitoring_trigger: "Material change in debt rights, liquidation economics, or investor control."

    - finding_id: MF-03
      finding: "Year-5 exit assumption has no binding exit mechanism."
      monitoring_trigger: "Revised valuation or exit structure."

  conditions: []

  validity:
    valid_from: null
    expires_at: null
    basis: "Current synthetic evidence set."
    revalidation_triggers:
      - "Operating-license evidence added or changed."
      - "Board/delegated authority evidence added."
      - "Anchor-customer commitment changes."
      - "Transaction governance rights change."
      - "Capital amount or structure changes."

  human_authority_required:
    - "Board or verified delegated investment authority."

  execution:
    execution_token_eligible: false
    authorized: false
    external_authorization_required: true

  appeal_available: null

  next_gate: >
    Resolve the critical operating-license evidence gap. When the package
    becomes decision-ready, escalate the investment decision to the Board
    or other verified delegated authority.

  confidence: medium
```

## Human-readable interpretation

- **IC recommendation:** DEFER / REWORK
- **MDGR verdict:** HOLD
- **Why HOLD:** the package is not yet decision-ready because a critical operating evidence gap remains.
- **Authority status:** Board approval remains separately unresolved.
- **Next transition:** evidence remediation → authority escalation.
- **Execution:** not authorized.
