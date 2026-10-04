# ChatGPT Project L1 Prompt Profile
## Investment Committee + MDGR

> **Status:** PUBLIC L1 EXAMPLE PROFILE  
> **Conformance:** L1 / best-effort only  
> **Not a native skill runtime**

This example does **not** claim that ChatGPT Projects execute `SKILL.md` as a runtime primitive. Here, `SKILL.md` is a portable instruction/reference artifact placed in the project context. Host loading and retrieval may be probabilistic. The example demonstrates **prompt-level architecture and decision contracts**, not external enforcement.

The architecture matters more than the host file loader:

```text
PROJECT
knows WHEN governance should activate

SKILL
knows HOW to analyze the investment decision

MDGR
knows WHETHER the material decision may progress

HUMAN
owns the actual authority
```

The example answers:

> **How can MDGR be represented inside a normal LLM project without pretending that the host is already an L2/L3 runtime?**

---

## Files

```text
.
├── PROJECT_INSTRUCTIONS.md
├── skills/
│   └── investment-committee/
│       └── SKILL.md
├── mdgr/
│   ├── MDGR_CORE.md
│   └── VERDICT_SCHEMA.md
├── sample-case/
│   ├── CASE.md
│   └── EXPECTED_OUTPUT.md
└── behavioral-checks/
    └── PROPOSED_BEHAVIORAL_CHECKS.md
```

---

## How to use

### Option A — ChatGPT Project / similar workspace

Use `PROJECT_INSTRUCTIONS.md` as the project-level instruction profile.

Make these files available as project knowledge/reference material:

- `skills/investment-committee/SKILL.md`
- `mdgr/MDGR_CORE.md`
- `mdgr/VERDICT_SCHEMA.md`

Then provide the investment evidence and ask a material decision question, for example:

> “Should we approve this Rp25 billion investment?”

This does **not** prove that every file will be loaded on every turn. If a host requires deterministic loading, that must be implemented outside this prompt profile.

### Option B — Generic LLM

Where no project-file mechanism exists, supply the same layers explicitly:

```text
1. PROJECT_INSTRUCTIONS.md
2. investment-committee/SKILL.md
3. MDGR_CORE.md
4. VERDICT_SCHEMA.md
5. current case evidence
```

---

## Canonical verdict tokens

Machine-readable verdicts use only:

```text
permit
permit_with_conditions
hold
escalate
block
```

Human-facing output may display:

```text
PERMIT
PERMIT WITH CONDITIONS
HOLD
ESCALATE
BLOCK
```

`PERMIT-C` is only a display alias for `permit_with_conditions`.

---

## Verdict resolution rule

The prompt profile must not collapse evidence gaps and authority gaps into one generic outcome.

Use this resolution order:

```text
1. BLOCK
   if the current path is prohibited or non-survivable.

2. HOLD
   if a critical evidence or precondition gap means the package is
   not yet decision-ready for the required authority.

3. ESCALATE
   if the package is otherwise decision-ready but required authority
   is missing, unverified, or outside the current jurisdiction.

4. permit_with_conditions
   if authority is satisfied and progress is allowed only under explicit
   binding conditions.

5. permit
   if required governance conditions are satisfied for the defined scope.
```

Important consequence:

> A missing authority never disappears inside `hold`.

If `hold` is the effective verdict because the package is not yet decision-ready, the unresolved authority must remain explicit in the verdict object and the next gate must state when escalation becomes appropriate.

---

## What should happen

For ordinary, low-risk finance questions, the system should not invoke the full governance workflow.

For a material capital-allocation decision, it should:

```text
identify decision
→ analyze investment case
→ identify evidence readiness
→ identify authority requirements
→ classify findings
→ resolve the dominant verdict
→ output the canonical verdict object
→ identify human authority required
→ stop before execution
```

---

## Why Investment Committee

Investment decisions naturally separate:

- analysis;
- recommendation;
- capital approval;
- delegated authority;
- conditions;
- execution.

A model may build the investment case.

It does not thereby become the Investment Committee.

---

## L1 boundary

This profile can request disciplined behavior from an LLM.

It cannot by itself guarantee:

- authenticated identity;
- verified organizational authority;
- deterministic file loading;
- immutable state;
- external policy validation;
- execution blocking;
- revocation propagation.

Those require external L2/L3 components.

---

## Try the synthetic case

Read:

[`sample-case/CASE.md`](sample-case/CASE.md)

Then compare the response against:

[`sample-case/EXPECTED_OUTPUT.md`](sample-case/EXPECTED_OUTPUT.md)

Then review the proposed checks:

[`behavioral-checks/PROPOSED_BEHAVIORAL_CHECKS.md`](behavioral-checks/PROPOSED_BEHAVIORAL_CHECKS.md)

These are **proposed behavioral checks**, not executed tests or validation results.
