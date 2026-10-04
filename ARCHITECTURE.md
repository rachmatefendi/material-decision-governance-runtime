# MDGR Architecture

> Plain-language architecture first; implementation detail second.

## 1. The problem MDGR controls

A normal AI pipeline often looks like:

```text
User asks
   ↓
AI reasons
   ↓
AI recommends
   ↓
Someone acts
```

That path can accidentally convert **persuasive reasoning into practical authority**.

MDGR inserts governance boundaries:

```text
User / System Request
        ↓
Governance State + Authority + Evidence + Policy
        ↓
Reasoning / Failure Discovery
        ↓
Governance Adjudication
        ↓
PERMIT / PERMIT WITH CONDITIONS / HOLD / ESCALATE / BLOCK
        ↓
[separate authorization]
        ↓
[separate execution gate]
        ↓
Real-world action
```

## 2. Logical components

```text
┌───────────────────────────────────────────┐
│               DECISION INTAKE             │
└───────────────────┬───────────────────────┘
                    │
                    ▼
┌───────────────────────────────────────────┐
│ STATE MANAGER / TRIAGE                    │
│ - phase                                   │
│ - materiality / risk                      │
│ - required authority                      │
│ - policy snapshot                         │
│ - evidence / assumptions                  │
└───────────────────┬───────────────────────┘
                    │
                    ▼
┌───────────────────────────────────────────┐
│ REASONING / FAILURE DISCOVERY             │
│ - specialist analysis                     │
│ - breakpoints                             │
│ - downside / missing evidence             │
└───────────────────┬───────────────────────┘
                    │
                    ▼
┌───────────────────────────────────────────┐
│ RISK / CONSTRAINT ADJUDICATOR             │
│ - BINDING                                 │
│ - MONITORED                               │
│ - DISMISSED                               │
└───────────────────┬───────────────────────┘
                    │
                    ▼
┌───────────────────────────────────────────┐
│ VERDICT VALIDATOR                         │
└───────────────────┬───────────────────────┘
                    │
                    ▼
┌───────────────────────────────────────────┐
│ EXECUTION GATEWAY                         │
│ - authority current?                      │
│ - policy current?                         │
│ - conditions satisfied?                   │
│ - token valid / unused?                   │
└───────────────────────────────────────────┘
```

Supporting services may include:

```text
Policy & Constraint Registry
Identity & Authority Registry
Evidence & Provenance Store
Append-only Audit Log
Monitoring & Revocation Service
```

## 3. What the language model owns

The model may help with:

- analysis;
- structured failure discovery;
- synthesis;
- explanation;
- drafting a candidate verdict object.

The model does **not** inherently own:

- organizational authority;
- policy truth;
- identity verification;
- registry truth;
- final execution permission;
- enforcement.

## 4. Why external components matter

At prompt-only level, a model can be instructed to follow governance rules but can still:

- misunderstand them;
- fabricate identifiers;
- accept stale state;
- follow an injected instruction;
- output an invalid transition.

External registries, validators, state machines, and gateways are what allow stronger claims.

## 5. Reference enforcement boundary

```text
                      LANGUAGE MODEL
                           │
          ┌────────────────┴────────────────┐
          │                                 │
          ▼                                 ▼
   reasoning output                  finding output
          │                                 │
          └──────────────┬──────────────────┘
                         ▼
               EXTERNAL VALIDATOR
                         │
                ┌────────┴────────┐
                │ valid           │ invalid
                ▼                 ▼
          governance state       reject
                │
                ▼
          EXECUTION GATEWAY
                │
          token / state check
                │
        ┌───────┴────────┐
        ▼                ▼
     execute            deny
```

## 6. Technology neutrality

MDGR is model-agnostic.

A conforming architecture may use:

- one model;
- several models;
- deterministic policy logic;
- human reviewers;
- rule engines;
- signed registries;
- hybrid systems.

The specification concerns **decision governance semantics**, not a required vendor or agent framework.
