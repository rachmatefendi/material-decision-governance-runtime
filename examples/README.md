# MDGR Examples

These examples are **synthetic illustrations**, not empirical test results. They are subordinate to [SPECIFICATION §12](../SPECIFICATION.md#12-governance-outcomes-and-resolution-order); [§13](../SPECIFICATION.md#13-canonical-verdict-contract) defines the canonical verdict object.

They show how the same AI reasoning can lead to different governance outcomes depending on evidence, authority, downside, and conditions.

| Example | Main issue | Illustrative outcome |
|---|---|---|
| [Urgent contract](01-urgent-contract.md) | Indeterminate fee basis makes the package not decision-ready; signing authority remains a separate unresolved gap | `hold`; then `escalate` if authority remains unresolved once the package is ready |
| [Capital allocation](02-capital-allocation.md) | Non-survivable downside + missing veto approval | `BLOCK` |
| [Long-term concession](03-long-term-concession.md) | Potential restructuring under binding conditions; authority sufficiency is not established by the request | `permit_with_conditions` is a target only after the §12 requirements are satisfied |

The examples do not prove that an implementation will produce these results reliably.


## L1 prompt-profile example

For a copy-ready L1 prompt profile showing MDGR inside a ChatGPT/LLM project, see:

[`chatgpt-project-investment-committee/`](chatgpt-project-investment-committee-l1-profile/README.md)

This example separates:

- project routing and source discipline;
- domain-specific Investment Committee analysis;
- generic MDGR decision governance;
- human approval authority.

It is intentionally classified as a **prompt-level / L1 profile**.
