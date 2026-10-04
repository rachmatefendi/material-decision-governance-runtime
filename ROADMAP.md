# MDGR Roadmap

> **Status:** Proposed research and implementation agenda.  
> Items below are not claims of completed capability.

## Stage 1 — Public specification hardening

- normalize EOS / DGR / MDGR terminology;
- freeze canonical MDGR state and verdict objects;
- define machine-readable schemas;
- define materiality policy interface;
- define authority and evidence registry interfaces;
- publish bounded synthetic examples.

## Stage 2 — L2 reference validator

Build an open reference validator capable of checking:

- state completeness;
- policy snapshot validity;
- authority references;
- evidence references;
- constraint identifiers;
- verdict structure;
- phase legality where externally observable.

## Stage 3 — Benchmark suite

Create test cases for domains such as:

- legal commitments;
- capital allocation;
- procurement;
- security response;
- regulated operations.

Include adversarial cases involving:

- urgency;
- stale policy;
- conflicting evidence;
- authority spoofing;
- fabricated bindings;
- high utility with unacceptable downside.

## Stage 4 — L3 execution gateway

Build an external execution boundary implementing:

- phase control;
- execution tokens;
- expiry;
- nonce / replay prevention;
- pre-execution revalidation;
- revocation;
- audit events.

## Stage 5 — Empirical evaluation

Measure:

- false allow;
- false block;
- HOLD quality;
- authority resolution;
- evidence grounding;
- trace completeness;
- latency;
- cost;
- human review burden;
- policy drift;
- revocation behavior.

## Stage 6 — Domain profiles

Develop domain-specific profiles without changing the MDGR core semantics.

Candidate profiles:

- capital allocation;
- legal commitments;
- procurement;
- cybersecurity;
- regulated operations.

## Stage 7 — External validation

Independent replication and external assessment are separate future maturity steps and must not be claimed before evidence exists.
