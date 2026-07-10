---
name: harness-readme
description: Guidance for the project harness — one self-contained module per verifier, gate, guardrail seam, sensor, or actuator that lets agents operate, test, and validate this project's real behavior.
metadata:
  version: "3.1"
  agentic_rails_source_version: "3.1"
  owner: "Your Name"
  repo: "your-repo"
---
# Harness

`harness/` is the project's agentic test harness in the classic CI sense: the
rig that lets automation run checks against the real application and collect
logs, evidence, and verdicts. It holds the machinery agents use to operate,
observe, and validate this project — verifiers, gates, guardrail seams,
sensors, and actuators. It is machinery, not narrative: per-story evidence and
outcomes belong in the relevant implementation plan under `context/`, never
here.

## The three-home rule

Every piece of harness machinery has exactly one home:

| Reusable across projects? | Has a lifecycle (hooks, engine updates)? | Home |
| --- | --- | --- |
| Yes | Yes | A marketplace plugin (`agentic_rails_marketplace`) — this folder holds only its per-project seam |
| Yes | No (inert procedure or knowledge) | A tooling-repo skill or agent, deployed by Kung Fu |
| No — project-specific | — | A full local module in this folder |

The promotion path: a check is born here as a local module, proves itself,
and graduates through the tooling repo's proposals inbox into the
marketplace. Its folder here then shrinks to just the seam, keeping the same
module name.

## Module rules

- **One self-contained folder per module**, kebab-case, named for what it
  checks or does. Everything the module needs — README, config, scripts,
  fixtures, truth/golden data — lives inside it, so the module can be
  adopted, disabled, or removed without leaving pieces elsewhere in the
  repository. No shared `scripts/` grab-bag between modules.
- **A seam module for an installed plugin** contains exactly what that
  plugin's README prescribes (typically `config.json`, defaults, drivers,
  goldens) and nothing else; its engine updates through the marketplace.
- **Runtime output is git-ignored inside the module**: `runs/`, `state/`,
  `last-run/`, `captures/`, `reports/`. Tracked files define the module;
  ignored files preserve local durability across turns.
- **No secrets.** Tokens and credentials live at the user level (environment
  variables, dotnet user-secrets, OS keychains), never in a module folder.

## Module contract

Every runnable module meets this contract, stated in its README:

1. **Trigger** — when an agent must run it, in one or two sentences.
2. **Stable exit codes** — `0` pass, `1` fail, and documented codes for
   distinct infrastructure failures (bad arguments, missing tooling, capture
   failure). "Couldn't check" is always a failure, never a silent pass.
3. **Agent-parseable output** — one compact `PASS`/`FAIL` line with the
   reason, plus a JSON report in the module's ignored output folder that says
   *why* it failed, not just that it failed.
4. **Config, not code, as the tuning seam** — thresholds, paths, regions,
   and commands live in a config file so agents tune behavior without editing
   scripts.
5. **A self-test** that proves the module's logic without the real
   app/hardware, so the harness itself is verifiable after setup.

Evaluator-run gates (procedure documents executed by a sub-agent rather than
a script) meet the same spirit: explicit trigger, pass criteria, attempt
loop, and a fixed report format precise enough that any evaluator produces
the same verdict.

## Wiring

Modules only run if agents know they must. `AGENTS.md` §0.2 carries the
standing trigger lines; a module whose trigger is genuinely enforced (not
advisory) must come from a marketplace guardrail plugin's hooks — never from
hand-edited tool settings.

## Installed modules

Keep this table current; it is the harness's index.

| Module | Kind | Engine | Purpose |
| --- | --- | --- | --- |
| _(none yet)_ | | | |
