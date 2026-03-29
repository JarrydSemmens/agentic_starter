# Commit Log Template

Use this template for commit logs across git, perforce, mercurial, svn, and similar version-control systems.

## Required Structure

Every commit log has:

1. A one-line heading
2. At least one body line

This means commit logs are always at least two lines.

## Heading Formats

### Jira-based work

```text
[XXX-123] - Did the thing with the code for real
```

Rules:

- Keep the Jira ticket key in square brackets.
- Use a concise one-line summary of the change set.
- Base wording on the ticket intent, not a copy of the ticket title.

Optional split-work suffix:

```text
[XXX-123] - Did the thing with the code on backend (1 of 2)
```

### Goal-based work (non-Jira)

```text
[GOAL X.Y] - Implemented the thing with the code for real
```

Rules:

- Use this for projects not using Jira.
- `X.Y` follows the goal hierarchy.
- Keep the summary concise and intent-focused.

## Body Line Format

Use one major change per line:

```text
~ Fixed: A terrible bug in the code
~ Changed: A system to allow for a future dependency more easily
~ Added: A new feature that does a thing
~ Removed: Some big chunk of code that was bad
~ Updated: Some documentation to match the current implementation
```

Optional callout:

```text
NOTE: An important callout, perhaps that this is changeset 1 of 2
```

## Quality Bar

- Be specific about impacted systems, classes, and intent.
- Keep messages concise and readable.
- Avoid uselessly short messages.
- Avoid long report-style commit logs.
