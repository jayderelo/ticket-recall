---
name: ticket-update
description: Update an existing software ticket at any stage using context supplied by the user, such as confirmed requirements, decisions, meeting notes, progress, or test results. Use when the user wants context incorporated into a ticket. Do not invent requirements or write before approval.
---

# Ticket Update

Turn supplied context into a focused update to an existing GitHub Issue or Jira work item. This workflow may be used before, during, or after implementation.

## Workflow

1. If the project's tracker has not been explicitly confirmed in the current conversation, use `ticket-tracker-identify` before tracker-specific access.
2. Identify exactly one target ticket. If the reference is ambiguous, ask the user to choose it.
3. Use the available tracker CLI or integration to read the current ticket before drafting. If tracker access is unavailable, stop and tell the user which access capability is missing; do not install or configure tooling as part of this skill.
4. Extract new information only from context the user supplied or explicitly confirmed. Classify each detail as:
   - confirmed requirement or decision;
   - implementation or test progress;
   - open question;
   - unconfirmed idea.
5. Preserve useful existing content and the team's established ticket structure. Keep requirements and acceptance criteria separate from implementation progress. Never rewrite an unconfirmed idea as a requirement.
6. Show a compact proposed change that states what will be added, changed, and left untouched. Identify unresolved questions and any supplied claim that lacks enough detail to write safely.
7. Ask the user for approval before changing the external ticket. Approval covers only the displayed change.
8. After approval, apply only the approved fields. Re-read the ticket and verify the result. If the ticket changed since it was read, reconcile the new version instead of overwriting it.

Do not transition, assign, label, close, or comment on the ticket unless the user separately requests that action.
