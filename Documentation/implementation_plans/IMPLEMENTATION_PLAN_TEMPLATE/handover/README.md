---
version: 0.1
owner: "Your Name"
repo: "your-repo"
description: Handover folder template for transferring ownership after implementation work or phases.
---

# Handover

Use this folder when work needs explicit ownership transfer back to the human or forward to another agent.

For small tasks, create a shallow handover artifact such as:

```text
shallow-handover.md
```

For larger or production-grade work, create a deep handover folder:

```text
deep/
  00-index.md
  01-deep-technical-report.md
  02-walkthrough-tour-script.md
  03-post-mortem-retrospective.md
  04-180-performance-review.md
  05-software-bill-of-materials.md
  06-future-maintenance-map.md
```

Warm handovers may use current session context. Cold handovers must rely only on source files, git history, documentation, implementation logs, complaint logs, and evidence.
