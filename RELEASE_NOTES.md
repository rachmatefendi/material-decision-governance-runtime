# Release Notes

## MDGR v1.0 — Public Specification Baseline

Initial public release of **Material Decision Governance Runtime (MDGR)**.

MDGR is a model-agnostic governance specification for material AI-assisted decisions. It separates reasoning, authorized decision, and execution; formalizes evidence readiness, authority, binding findings, bounded verdicts, validity, and execution gating; and uses an L0–L3 ladder to distinguish prompt-level guidance from externally enforced controls.

### Included

- normative MDGR specification;
- reference architecture;
- threat model;
- conformance model;
- glossary;
- implementation roadmap;
- synthetic examples;
- Investment Committee L1 prompt profile for ChatGPT / LLM workspaces;
- proposed behavioral checks.

### Canonical verdict tokens

```text
permit
permit_with_conditions
hold
escalate
block
```

### Claim boundary

This release is a **Specification**.

It does not claim:

- implemented L2/L3 enforcement;
- empirical validation;
- deterministic governance;
- production readiness;
- external validation.

The proposed behavioral checks have not yet been reported as an executed evaluation.

### License

Repository contents are licensed under **Apache License 2.0**, except where explicitly stated otherwise.

### Historical paper

The EOS/DGR preprint is not distributed in this repository and remains a separate publication artifact.
