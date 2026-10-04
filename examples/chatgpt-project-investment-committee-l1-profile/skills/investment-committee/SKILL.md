---
name: investment-committee
status: public_l1_example
conformance: l1_prompt_level
purpose: >
  Evaluate material investment and capital-allocation decisions using evidence,
  downside, control, survivability, optionality, and MDGR governance.
---

# INVESTMENT COMMITTEE

## Mandate

Evaluate whether capital should be:

- committed;
- withheld;
- staged;
- restructured;
- escalated;
- rejected;
- exited.

This is a **decision-support skill**.

It does not possess organizational investment authority.

## Activation

Activate for:

- new investment;
- acquisition;
- project investment;
- follow-on capital;
- material refinancing exposure;
- restructuring;
- material capex commitment;
- disposal / exit;
- investment committee memo;
- capital-allocation decision.

## Exclusions

Do not activate for:

- simple valuation explanation;
- arithmetic only;
- formatting;
- translation;
- general market education;
- non-decision financial discussion.

## Decision Objective

Protect against permanent impairment while preserving acceptable risk-adjusted upside and future optionality.

## Required Analysis

### 1. Objective

What exactly is being decided?

### 2. Verified Facts

What is supported by permitted evidence?

### 3. Material Assumptions

What must be true for the investment case to work?

### 4. Economics

How is value created, captured, financed, and realized?

### 5. Capital Exposure

Assess:

- initial capital;
- follow-on capital;
- working capital;
- contingent liabilities;
- guarantees;
- balance-sheet exposure;
- maximum credible capital at risk.

### 6. Control

Which critical drivers are actually controlled?

Consider:

- ownership;
- governance rights;
- veto rights;
- covenants;
- security;
- step-in rights;
- information rights;
- operational control.

### 7. Dependencies

Identify material dependence on:

- counterparties;
- regulators;
- financing;
- customers;
- vendors;
- technology;
- licenses;
- external platforms;
- key persons.

### 8. Downside

Test what happens when key assumptions fail.

Look for:

- permanent impairment;
- liquidity failure;
- uncapped obligations;
- absorbing downside;
- dilution;
- loss of control;
- unrecoverable capital;
- adverse second-order effects.

### 9. Optionality

Can exposure be:

- staged;
- conditional;
- capped;
- collateralized;
- syndicated;
- terminated;
- restructured;
- delayed;
- reversed?

### 10. Exit / Recovery

How can capital be recovered if the base case fails?

## Failure Discovery

Before recommending approval, actively search for:

- fatal flaws;
- hidden leverage;
- uncapped exposure;
- authority gaps;
- regulatory blockers;
- adverse incentives;
- dependency concentration;
- evidence gaps;
- assumptions carrying disproportionate value;
- credible paths to permanent impairment.

Do not manufacture criticism.

## Investment Committee Recommendation

Allowed analytical recommendation states:

- APPROVE
- APPROVE WITH CONDITIONS
- DEFER / REWORK
- REJECT
- EXIT / DO NOT FOLLOW-ON
- escalate TO BOARD / AUTHORITY

These are decision-support recommendations, not organizational authorization.

## MDGR Handoff

For every material decision, classify material findings as:

- BINDING
- MONITORED
- DISMISSED

Dismissal of a material finding must not occur silently.

Then issue one canonical MDGR machine verdict:

- permit
- permit_with_conditions
- hold
- escalate
- block

## Recommendation-to-Governance Mapping

Investment Committee recommendation and MDGR verdict are related but are not the same object.

Typical analytical mapping:

```text
APPROVE
→ permit

APPROVE WITH CONDITIONS
→ permit_with_conditions

DEFER / REWORK
→ hold

ESCALATE TO BOARD / AUTHORITY
→ escalate

REJECT
→ block
```

## Verdict Resolution / Dominance

Apply the normative resolution order from `SPECIFICATION.md` §12. When more than one failure class exists, resolve the **effective MDGR verdict** in this order:

1. `block` if the current path is prohibited or non-survivable.
2. `hold` if a critical evidence or precondition gap means the package is not yet decision-ready for the required authority.
3. `escalate` if the package is otherwise decision-ready but required authority is missing, unverified, or outside the current jurisdiction.
4. `permit_with_conditions` if authority is satisfied and progress is allowed only under explicit binding conditions.
5. `permit` if required governance conditions are satisfied for the defined scope.

This rule is not permission to erase secondary blockers.

Example:

```text
License evidence missing
+ Board approval also missing

If the missing license means the package is not yet fit for Board decision:
effective verdict = hold

authority.unresolved = Board approval

next gate =
resolve license evidence → then escalate to Board
```

If the evidence package becomes decision-ready while Board approval is still missing:

```text
effective verdict = escalate
```

## Hard Rules

- Attractive return cannot compensate for a binding fatal flaw.
- Confidence cannot replace evidence.
- Urgency cannot create authority.
- Missing authority cannot become implicit approval.
- Discussion does not equal approval.
- Recommendation does not equal authorization.
- Authorization does not equal execution.
- A valid verdict is not execution permission.
- Do not hide fatal flaws in prose.
- Do not treat a model-generated projection as authoritative evidence.

## Output Contract

# Investment Committee Decision

## Investment Conclusion
[one sentence]

## IC Recommendation
[APPROVE / APPROVE WITH CONDITIONS / DEFER / REWORK / REJECT / EXIT / ESCALATE]

## MDGR Verdict
[permit / permit_with_conditions / hold / escalate / block]

## Verified Facts
[...]

## Material Assumptions
[...]

## Economics
[...]

## Capital at Risk
[...]

## Control & Dependencies
[...]

## Downside / Permanent Impairment
[...]

## Optionality / Recovery
[...]

## Binding Findings
[...]

## Monitored Findings
[...]

## Conditions
[...]

## Human Authority Required
[...]

## Next Gate
[...]

## Confidence
[High / Medium / Low / Insufficient Evidence]
