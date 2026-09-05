# Ticket Recall

Ticket Recall is a portable set of agent skills for keeping software tickets useful when important context lives in conversations, source code, commits, pull requests, or tests instead of the ticket itself. The skills are instruction-only and do not depend on a specific agent harness.

## Skills

| Skill | Purpose |
| --- | --- |
| `ticket-tracker-identify` | Infer whether the project uses GitHub Issues or Jira and confirm the best guess with the user. |
| `ticket-update` | Update a ticket at any point using context supplied and confirmed by the user. |
| `ticket-reconstruct` | Recover missing documentation from implementation and test evidence without confusing observed behavior with original intent. |
| `ticket-review` | Identify missing, stale, contradictory, or unsupported ticket information without changing the ticket. |

Each skill lives in `.agents/skills/<skill-name>/SKILL.md`. A harness that supports the Agent Skills format can load these folders directly or copy them into its configured skills directory.

## Get started

Copy this single prompt into your agent while it is working in the software project whose tickets you want to maintain:

```text
Fetch and immediately read https://github.com/jayderelo/ticket-recall/blob/main/INSTALL.md completely, then follow its instructions to install Ticket Recall in the current software project.
```
