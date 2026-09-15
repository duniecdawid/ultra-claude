# Security Policy

## Reporting a vulnerability

Report security issues privately through GitHub's
[private vulnerability reporting](https://github.com/duniecdawid/ultra-claude/security/advisories/new).
Please do not open a public issue for a vulnerability.

Expect an acknowledgement within a week. Ultra Claude is maintained by one
person, so a fix may take longer than that — you will be told either way.

## Scope

Ultra Claude is a Claude Code plugin: skills, agents, and shell scripts that run
locally on your machine with your permissions. It has no server component and
no telemetry. Things worth reporting:

- A skill or script that executes untrusted input, escalates privileges, or
  writes outside the project and the documented `~/.claude/ultra/` paths.
- A path where credentials, tokens, or machine-local values leak into files
  that get committed to a user's repository.
- Anything in `scripts/` that can be induced to run attacker-controlled
  commands.

Out of scope: the behaviour of Claude Code itself and of the Claude models —
report those to Anthropic.
