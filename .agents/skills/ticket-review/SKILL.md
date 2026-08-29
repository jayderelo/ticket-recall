---
name: ticket-review
description: Review an existing software ticket for missing, stale, contradictory, or unsupported information using supplied context and available implementation evidence. Use for ticket quality assessment and gap analysis. Keep the review read-only unless the user separately asks to update the ticket.
---

# Ticket Review

Assess whether a ticket is accurate and sufficient for the people who must implement, test, review, manage, or maintain the work.

## Workflow

1. Identify and read exactly one target ticket. Read-only access is sufficient.
2. Determine the review evidence available: user-supplied context, linked source material, implementation changes, tests, pull requests, and current project conventions.
3. Evaluate the ticket for:
   - missing context, scope, constraints, or acceptance criteria;
   - stale statements contradicted by newer confirmed information or implementation;
   - unsupported claims with no reliable source or evidence;
   - contradictions within the ticket or between the ticket and evidence;
   - requirements mixed with implementation progress;
   - open questions hidden as assumptions.
4. Report each finding with its category, impact, supporting evidence, and a concrete recommendation. Clearly distinguish facts from inferences.
5. State when the available evidence is insufficient to judge a section. Do not manufacture completeness.

This skill is read-only. Do not edit, comment on, transition, assign, label, or close the ticket. If the user wants to apply confirmed corrections, recommend `ticket-update`; if documentation must be recovered from implementation, recommend `ticket-reconstruct`.
