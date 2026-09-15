# Ultra Claude

[![Docs](https://img.shields.io/badge/docs-ultra--claude.dev-111?style=flat-square)](https://ultra-claude.dev)
[![Version](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fduniecdawid%2Fultra-claude%2Fmain%2F.claude-plugin%2Fplugin.json&query=%24.version&label=version&style=flat-square)](CHANGELOG.json)
[![License](https://img.shields.io/badge/license-FSL--1.1--ALv2-blue?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/duniecdawid/ultra-claude?style=flat-square)](https://github.com/duniecdawid/ultra-claude/stargazers)

**Give Claude Code an engineering process.**

Claude Code is astonishing in week one and exhausting by week six: decisions nobody wrote
down, inconsistent patterns, architecture that exists only in old chat sessions. Ultra
Claude is a plugin that fixes that with a process rather than a better prompt — researched
plans, enforced standards, agent-reviewed and tested code, and documentation that stays
true to the codebase.

Full documentation: https://ultra-claude.dev

---

## Install

Two commands in any Claude Code session:

```
/plugin marketplace add duniecdawid/ultra-claude
/plugin install uc@ultra-claude
```

Every skill becomes a `/uc:*` slash command. Optionally keep it current automatically:

```
/plugin marketplace auto-update duniecdawid/ultra-claude
```

## Set up your machine

Once per machine. Installs prerequisites, configures your shell for agent teams, and sets
up tmux if you want the visual pane layout. Safe to re-run.

```
/uc:setup
```

## Initialize a project

Once per project, run from the project root. It reads your codebase, scaffolds
`documentation/`, and derives architecture docs and coding standards from the patterns
already there. Works on existing codebases, not just greenfield.

```
/uc:migrate
```

Review what it generated — `documentation/technology/architecture/` and
`.../standards/`. Every planning skill reads these, so the more accurate they are, the
better the plans.

## Build something

```
/uc:feature-mode add user authentication
```

Feature mode behaves like a senior tech lead: it challenges your scope, researches the
codebase in parallel, and produces a structured plan with testable tasks — before any code
is written. You approve the plan, then:

```
/uc:plan-execution {plan-name}
```

Each task gets a dedicated team: an **Executor** that writes the code, a **Reviewer** that
enforces your standards, and a **Tester** that validates against the product docs. With
tmux, they appear as live panes you can watch. Sessions can die and resume — checkpoints
save progress.

Run `/uc:help` any time to find the right command for what you are doing.

---

## What it is, and is not

Not a framework, library, or runtime. It is 23 skills and 11 agents packaged as a Claude
Code plugin, running entirely inside Claude Code on your machine. Nothing phones home,
there is no account, and you pay only your normal Claude usage.

The documentation it writes is plain markdown that stays useful on its own. Uninstall the
plugin and your repository still works.

**The idea it is built on:** code is a derived artifact. The specification is the source of
truth, architecture docs exist before code is written, and when code diverges from the
spec you fix the spec first. Documentation acts like zoning law — you build freely within
the constraints, but the constraints control direction. Additive changes flow freely,
compatible changes get lightweight review, breaking changes require updating the
architecture doc first.

## Documentation

| Page | |
|------|---|
| https://ultra-claude.dev/getting-started | Install, setup, and first feature in 10 minutes |
| https://ultra-claude.dev/docs/discovery | Product research and market analysis |
| https://ultra-claude.dev/docs/feature-planning | Scope challenge, research, structured plans |
| https://ultra-claude.dev/docs/plan-execution | Agent teams, task pipeline, checkpoints |
| https://ultra-claude.dev/docs/debugging | Hypothesis-driven bug investigation |
| https://ultra-claude.dev/docs/verification | Doc-code drift detection and fixes |
| https://ultra-claude.dev/docs/standards | Define, enforce, and verify coding standards |
| https://ultra-claude.dev/docs/reference | Every skill and agent |

## Contributing

Bug reports and fixes are welcome — see [CONTRIBUTING.md](.github/CONTRIBUTING.md) for the
repository rules a pull request has to satisfy, and
[Discussions](https://github.com/duniecdawid/ultra-claude/discussions) for questions,
ideas, and showing what you built.

## Licence

[FSL-1.1-ALv2](LICENSE) — the Functional Source License. Use it, modify it, fork it and
contribute back freely. The one thing you may not do is sell a competing product built on
it. Every version converts to Apache 2.0 two years after release.
