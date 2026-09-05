---
name: ticket-tracker-identify
description: Identify whether a software project uses GitHub Issues or Jira when the tracker is not already confirmed in the current conversation. Inspect project evidence and installed CLIs, present a best guess with confidence, and ask the user to confirm it before tracker-specific work.
---

# Ticket Tracker Identify

Determine the project's ticket tracker without relying on installation-session context or a previous conversation.

## Workflow

1. Use an explicit tracker choice already confirmed by the user in the current conversation. Otherwise, inspect repository remotes, issue templates, contribution docs, existing ticket links or references, project configuration, and other user-supplied context.
2. Check whether both `gh` and `acli` are installed. Treat CLI availability as supporting evidence, not proof:
   - explicit project configuration and ticket links outweigh CLI availability;
   - installed `acli` makes Jira highly likely unless stronger project evidence points elsewhere;
   - if only `gh` is installed, GitHub Issues is a reasonable but inconclusive guess;
   - a missing CLI does not mean its tracker is unused.
3. State one best guess, the strongest evidence, and a plain-language confidence level. Ask the user to confirm that guess instead of asking an open-ended "GitHub Issues or Jira?" question.
4. If the user rejects the guess or names the other tracker, accept the correction immediately and continue with the corrected tracker. Do not defend the original inference or repeat the selection question.
5. Return the confirmed tracker and its matching access method: `gh` for GitHub Issues or `acli` for Jira Cloud.

This skill identifies the tracker only. Do not install a CLI, authenticate, or modify a ticket. If the confirmed tracker's access method is unavailable, return that fact to the calling workflow so it can stop or direct the user to setup.
