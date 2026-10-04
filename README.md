# Material Decision Governance Runtime (MDGR) v1.0

> **PUBLIC SPECIFICATION BASELINE · SPECIFICATION, NOT A PRODUCTION RUNTIME**

**MDGR is a checkpoint between “AI recommends something” and “an organization is allowed to act on it.”**

An AI can produce a convincing answer. That does **not** mean:

- the evidence is complete;
- the person asking has authority;
- the downside is acceptable;
- the governing policy is current;
- the recommendation is approved;
- the action may be executed.

MDGR makes those checks explicit.

---

## Understand MDGR in 30 seconds

Suppose ChatGPT says:

> “This Rp25 billion investment looks attractive. Approve it.”

MDGR asks:

```text
Are the important facts verified?
Is the decision package actually ready?
Who has authority to approve it?
Is there a binding legal / policy / risk blocker?
Could the downside permanently impair the organization?
If approved, is execution separately authorized?
```

Then MDGR returns one governance outcome:

| Outcome | Meaning |
|---|---|
| **PERMIT** | The governance gate is satisfied for the defined scope. |
| **PERMIT WITH CONDITIONS** | It may progress only if binding conditions are satisfied. |
| **HOLD** | Critical evidence or a precondition is missing, so the package is not decision-ready. |
| **ESCALATE** | The package is decision-ready, but the required authority is missing, unverified, or belongs elsewhere. |
| **BLOCK** | The current path must not proceed. |

**PERMIT still does not mean EXECUTE.**

That distinction is the core of MDGR.

---

## Use it in ChatGPT today

The repository includes a simple **Investment Committee L1 prompt profile**.

Start here:

[`examples/chatgpt-project-investment-committee-l1-profile/`](examples/chatgpt-project-investment-committee-l1-profile/README.md)

Practical flow:

```text
1. Create a ChatGPT Project / LLM workspace
2. Use PROJECT_INSTRUCTIONS.md
3. Add the Investment Committee SKILL.md as project knowledge
4. Add MDGR_CORE.md and VERDICT_SCHEMA.md
5. Upload the investment evidence
6. Ask: "Should we approve this investment?"
```

The conceptual split is:

```text
PROJECT
knows WHEN governance should activate

SKILL
knows HOW to analyze the investment

MDGR
knows WHETHER the material decision may progress

HUMAN / ORGANIZATION
owns the actual authority
```

### Important limitation

This ChatGPT example is **L1 / prompt-level governance**.

It can improve decision discipline, but it does not provide:

- authenticated organizational authority;
- deterministic file loading;
- immutable state;
- external policy enforcement;
- execution blocking;
- revocation enforcement.

Those require external infrastructure.

---

## Reasoning, decision, and execution are different

```text
REASONING
"What appears to be the best option?"
        ↓
DECISION
"Is this option permitted and properly authorized?"
        ↓
EXECUTION
"May this specific action actually happen now?"
```

**Reasoning is not permission.**

A model may help analyze a decision without possessing authority to approve or execute it.

---

## How MDGR works

```text
Decision Request
      │
      ▼
┌──────────────────────┐
│ 1. TRIAGE            │
│ evidence, state,     │
│ policy, authority    │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ 2. FAILURE DISCOVERY │
│ breakpoints, missing │
│ evidence, downside   │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ 3. ADJUDICATION      │
│ binding / monitored  │
│ / dismissed findings │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ 4. VERDICT           │
│ permit / conditions  │
│ hold / escalate /    │
│ block                │
└──────────┬───────────┘
           ▼
┌──────────────────────┐
│ 5. EXECUTION GATE    │
│ authority, policy,   │
│ scope, freshness     │
└──────────────────────┘
```

At stronger implementation levels, validation and execution controls live **outside the language model**.

---

## Where MDGR is useful

MDGR is intended for decisions where downside, authority, or irreversibility are material, for example:

- capital allocation;
- acquisitions and major investments;
- binding legal commitments;
- corporate actions;
- regulated operations;
- consequential procurement;
- high-impact cybersecurity actions;
- decisions affecting third parties or public safety.

It is intentionally not designed for routine drafting, formatting, creative ideation, or other low-risk reversible work.

---

## What MDGR is — and is not

### MDGR is

- a material-decision governance specification;
- a state- and authority-aware control architecture;
- a model-agnostic way to formalize `hold`, `escalate`, `block`, conditional progress, and permit states;
- a specification for binding decisions to evidence, authority, policy, constraints, and validity windows.

### MDGR is not

- a new foundation model;
- a chatbot persona;
- a replacement for directors, lawyers, risk officers, regulators, or other accountable humans;
- proof that AI reasoning is correct;
- a universal safety guarantee;
- an implemented L2/L3 runtime in this repository;
- permission to execute real-world actions merely because a model produced a verdict.

---

## Canonical verdict tokens

Machine-readable outcomes use only:

```text
permit
permit_with_conditions
hold
escalate
block
```

Human-facing labels may render them as:

```text
PERMIT
PERMIT WITH CONDITIONS
HOLD
ESCALATE
BLOCK
```

`PERMIT-C` is only a display alias for `permit_with_conditions`.

The normative resolution rules are in [`SPECIFICATION.md` §12](SPECIFICATION.md#12-governance-outcomes-and-resolution-order).

---

## Conformance levels

MDGR separates written governance rules from actual enforcement.

| Level | Implementation | Defensible claim |
|---|---|---|
| **L0** | Advisory guidance | Governance concepts are documented. |
| **L1** | Prompt / in-context governance | Best-effort behavioral compliance. |
| **L2** | External validator + authoritative registries | Invalid or unbound verdicts can be rejected. |
| **L3** | External state machine + execution gate | Invalid state, phase, authority, or execution paths can be externally prevented. |

This v1.0 repository specifies the model and includes an L1 example. It does **not** claim an implemented L2/L3 system.

---

## Repository map

```text
.
├── README.md
├── LICENSE
├── NOTICE
├── RELEASE_NOTES.md
├── SPECIFICATION.md
├── ARCHITECTURE.md
├── CONFORMANCE.md
├── THREAT_MODEL.md
├── GLOSSARY.md
├── ROADMAP.md
├── docs/
│   ├── NOMENCLATURE.md
│   ├── PUBLIC_RELEASE.md
│   └── PACKAGING_VERIFICATION.md
├── examples/
│   ├── README.md
│   ├── 01-urgent-contract.md
│   ├── 02-capital-allocation.md
│   ├── 03-long-term-concession.md
│   └── chatgpt-project-investment-committee-l1-profile/
│       ├── README.md
│       ├── PROJECT_INSTRUCTIONS.md
│       ├── skills/
│       │   └── investment-committee/
│       │       └── SKILL.md
│       ├── mdgr/
│       │   ├── MDGR_CORE.md
│       │   └── VERDICT_SCHEMA.md
│       ├── sample-case/
│       │   ├── CASE.md
│       │   └── EXPECTED_OUTPUT.md
│       └── behavioral-checks/
│           └── PROPOSED_BEHAVIORAL_CHECKS.md
└── paper/
    └── README.md
```

---

## Start here

If you only want to understand MDGR:

1. read this README;
2. open the [Investment Committee example](examples/chatgpt-project-investment-committee-l1-profile/README.md);
3. read [`ARCHITECTURE.md`](ARCHITECTURE.md).

If you want to implement it:

1. read [`SPECIFICATION.md`](SPECIFICATION.md);
2. read [`CONFORMANCE.md`](CONFORMANCE.md);
3. read [`THREAT_MODEL.md`](THREAT_MODEL.md);
4. use the canonical verdict contract in the specification.

---

## Current maturity

| Item | Status |
|---|---|
| MDGR core | **Public Specification v1.0** |
| State / authority / verdict model | **Specified** |
| Threat model | **Specified** |
| L0–L3 conformance model | **Specified** |
| Investment Committee L1 prompt profile | **Included** |
| Behavioral evaluation of the L1 profile | **Not yet executed / not reported** |
| L2 reference validator | **Not included / not demonstrated** |
| L3 execution gateway | **Not included / not demonstrated** |
| Empirical benchmark results | **Not established** |
| External validation | **Not established** |

This repository should be read as a **normative specification and public reference artifact**, not as a production safety product.

---

## Research paper

The historical preprint **Governing Before Reasoning** is part of the research lineage behind MDGR and uses the earlier names **EOS** and **Decision Governance Runtime (DGR)**.

The PDF is intentionally **not distributed in this repository**.

This keeps the public MDGR repository self-contained and avoids coupling the repository license to the paper's separate publication/distribution treatment.

See [`paper/README.md`](paper/README.md) and [`docs/NOMENCLATURE.md`](docs/NOMENCLATURE.md).

---

## License

Except where explicitly stated otherwise, this repository is licensed under the **Apache License 2.0**.

See [`LICENSE`](LICENSE) and [`NOTICE`](NOTICE).

The historical paper is not part of this licensed repository distribution.

---

## Author

**Rachmat Efendi**  
Independent Researcher — Jakarta, Indonesia

---

## Release

**v1.0 — Public Specification Baseline**

This release freezes the public MDGR specification and its canonical verdict semantics. Future material changes to outcome semantics, authority rules, state ownership, or execution logic should be versioned explicitly.
