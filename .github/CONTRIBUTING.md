# Contributing to Ultra Claude

Contributions are welcome. This document covers the licensing terms for
contributions and the repository rules a pull request has to satisfy.

## Licensing of contributions

Ultra Claude is released under the [Functional Source License, Version 1.1,
ALv2 Future License](../LICENSE) (`FSL-1.1-ALv2`). You may fork this
repository, modify it, and open pull requests.

By submitting a contribution (a pull request, patch, or any other
modification), you agree that:

- Your contribution is licensed to the project under the same terms as the
  Software itself, and
- You grant Dawid Duniec a perpetual, irrevocable, worldwide, royalty-free
  license to use, modify, sublicense, and distribute your contribution as part
  of the Software, including under any future license the Software is offered
  under.

You retain copyright in your contribution.

## What is useful

- **Bug reports.** Use the issue form — it asks for the versions and context
  needed to reproduce. Bugs are the one thing the issue tracker is for.
- **Bug fixes**, especially with a test that fails without the fix.
- **Documentation corrections**, including anywhere the docs site disagrees
  with what a skill actually does.

Ideas, questions, and "here's what I built with it" belong in
[Discussions](https://github.com/duniecdawid/ultra-claude/discussions),
not in issues.

## Rules a pull request must satisfy

These are enforced for every commit, including mine. They are stated in full in
`CLAUDE.md` at the repository root.

**Versioning.** Single format everywhere: `YYYY.MM.DD-N`, where `N` starts at 1
and increments for multiple commits on the same day. Every commit must:

1. Add an entry at the **top** of the `CHANGELOG.json` array with a `seq` one
   higher than the current maximum (`jq '.[0].seq' CHANGELOG.json`). Sequence
   numbers always increment and are never reused.
2. Write that same version to **both** `.claude-plugin/plugin.json` and
   `.claude-plugin/marketplace.json`.

**Migration registry.** If your change affects files that exist inside projects
already using Ultra Claude — anything under `documentation/`, `.claude/ultra/`,
or the CLAUDE.md template — the changelog entry needs a `migration` block with
a precondition, actions, and conflict guidance. Otherwise `migration` is `null`.
Most changes do not need one.

**Help skill sync.** Editing a skill (`skills/*/SKILL.md`) or an agent
(`agents/*.md`) means updating its three-sentence description in
`skills/help/SKILL.md`: what it does, when to use it, what it produces.

**Documentation site sync.** The site in `docs/` is published at
ultra-claude.dev. A change to skill behaviour, agent roles, execution flow, or
any user-facing capability must update the affected pages in `docs/views/` in
the same pull request.

**No machine-specific values.** This repository is the portable half of a
two-layer system. No hardcoded paths, usernames, hostnames, IP addresses,
account identities, or anything else true only of one machine. Machine-local
values live in the user's own `~/.claude/skills/machine-context/` and are read
at runtime with a detection fallback. Scan your diff before opening the pull
request.

**Agent-team communication.** Anything built on Claude Code agent teams must
use the protocol at
`skills/plan-execution/references/execution-communication-protocol.md` rather
than restating its mechanics.

## Running the documentation site locally

```bash
cd docs
npm install
node server.js
```

It binds `0.0.0.0:3000`.
