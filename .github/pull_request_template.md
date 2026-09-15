## What this changes

<!-- One or two sentences. Link an issue if there is one. -->

## Checklist

These are enforced on every commit, including the maintainer's. Full rules are
in `CLAUDE.md` and `.github/CONTRIBUTING.md`.

- [ ] **Changelog** — new entry at the *top* of `CHANGELOG.json`, with `seq`
      one higher than `jq '.[0].seq' CHANGELOG.json`
- [ ] **Version** — `YYYY.MM.DD-N`, written to **both**
      `.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json`
- [ ] **Migration** — `migration` is `null`, *or* the change touches files that
      exist inside projects using Ultra Claude and carries a migration block
      with precondition, actions, and conflict guidance
- [ ] **Help sync** — if a skill or agent changed, its three-sentence
      description in `skills/help/SKILL.md` is updated
- [ ] **Docs site** — if user-facing behaviour changed, the affected pages in
      `docs/views/` are updated in this same PR
- [ ] **No machine-specific values** — no hardcoded paths, usernames,
      hostnames, IPs, or account identities; `claude plugin validate .` passes
