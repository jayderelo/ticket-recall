---
name: ticket-reconstruct
description: Recover missing ticket documentation from implementation evidence such as source code, diffs, commits, pull requests, tests, and observed behavior. Use when the implementation exists but the ticket is empty or incomplete. Distinguish evidence from inferred intent and require approval before writing.
---

# Ticket Reconstruct

Rebuild useful ticket documentation from implementation evidence without pretending that observed behavior proves the original business intent.

## Workflow

1. Identify exactly one ticket and the implementation evidence that belongs to it. Establish the relationship through explicit user context, branch or commit references, pull-request links, or other reliable project evidence.
2. Read the current ticket before analyzing the implementation. Preserve any supported existing information.
3. Inspect the smallest sufficient evidence set: relevant diffs, commits, source paths, tests, configuration, and execution results. Do not treat filenames, comments, or commit messages as authoritative when stronger evidence contradicts them.
4. Separate findings into:
   - observed implemented behavior;
   - behavior verified by tests or execution;
   - technical constraints visible in the implementation;
   - inferred intent that still needs confirmation;
   - gaps that cannot be recovered from implementation evidence.
5. Draft reconstructed documentation that clearly labels observed behavior and unresolved intent. Acceptance criteria may be reconstructed only when each criterion is supported by implementation or test evidence; do not present them as proof of the original agreement.
6. Cite concrete evidence in the proposal using repository-relative paths, commit or pull-request references, and test names where available.
7. Show the proposed ticket change and ask the user to confirm both its accuracy and whether it should be written.
8. After approval, update only the approved fields, re-read the ticket, and verify the result. Stop if concurrent changes require reconciliation.

Do not modify source code as part of reconstruction unless the user separately asks for implementation work.
