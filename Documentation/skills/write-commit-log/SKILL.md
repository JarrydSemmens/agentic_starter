---
name: write-commit
description: Writes a standardised commit log following a template. Used after a task is completed to put a commit log into the chat for the user to copy into their repository software of choice.
---

# Write Commit

Write a commit log, that follows the template log template defined in references\commit_log_template.md and output that commit log to the user in the conversation.

## When to Use

- Use this skill when you have completed a task and are summarizing what you did in the conversation with the user.
- This skill is helpful for providing detailed and succinct commit logs that are standardised and agnostic to the repository software.
- This skill improves agentic safety by encouraging the user to perform the final commit step.

## Instructions

- Review what you have done.
- Open references\commit_log_template.md and read it all.
- Follow the template instructions when writing a commit log.
- Output the log to the user in the chat so they may read and copy it to their clipboard easily.