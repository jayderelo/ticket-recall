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
Read the Ticket Recall INSTALL.md and follow its project setup instructions. Detect this project's ticket tracker and the current operating system without assuming that an installed CLI proves which tracker the team uses. If the tracker is ambiguous, ask me whether we use GitHub Issues or Jira. Check whether the appropriate CLI is installed and authenticated. If installation is needed, show me the exact OS-appropriate commands and ask for my permission before running them. Complete authentication with my participation, verify read access to the correct repository or Jira project, and stop after setup without updating any ticket. Then tell me when to use ticket-update, ticket-reconstruct, or ticket-review.
```
