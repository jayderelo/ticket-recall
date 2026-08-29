# Ticket Recall

Ticket Recall is a portable set of agent skills for keeping software tickets useful when important context lives in conversations, source code, commits, pull requests, or tests instead of the ticket itself. The skills are instruction-only and do not depend on a specific agent harness.

## Skills

| Skill | Purpose |
| --- | --- |
| `ticket-update` | Update a ticket at any point using context supplied and confirmed by the user. |
| `ticket-reconstruct` | Recover missing documentation from implementation and test evidence without confusing observed behavior with original intent. |
| `ticket-review` | Identify missing, stale, contradictory, or unsupported ticket information without changing the ticket. |

Each skill lives in `.agents/skills/<skill-name>/SKILL.md`. A harness that supports the Agent Skills format can load these folders directly or copy them into its configured skills directory.

## Get started

Copy this single prompt into your agent while it is working in the software project whose tickets you want to maintain:

```text
Install Ticket Recall in the current software project from https://github.com/jayderelo/ticket-recall. Retrieve that repository into a temporary location and read its README.md and INSTALL.md completely. Copy only the ticket-update, ticket-reconstruct, and ticket-review skill folders from its .agents/skills directory into this project's .agents/skills directory; do not copy the repository-level README.md or INSTALL.md into this project. Then follow the retrieved INSTALL.md to detect this project's ticket tracker and operating system, request my permission before installing any required CLI, complete authentication with my participation, and verify read-only access to the correct GitHub repository or Jira project. Stop after setup without changing any ticket, and report what was installed, configured, and verified.
```
