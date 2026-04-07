# Skills Setup

This project uses the `skills` CLI in project scope rather than global scope.

## Current Convention

- Project-scoped skills are installed under `.agents/skills/`.
- `skills-lock.json` is committed and records the source plus content hash for each installed skill.
- The repository currently tracks the full `anthropics/skills` set for Codex-compatible project usage.
- The checked-in installation is copied into the repository, not symlinked to an external location.

## Install All Anthropic Skills For This Project

```bash
npx skills add https://github.com/anthropics/skills --skill '*' -a codex -y --copy
```

Equivalent npm script:

```bash
npm run skills:install:anthropic
```

## Daily Commands

List installed project skills:

```bash
npm run skills:list
```

Restore from `skills-lock.json`:

```bash
npm run skills:restore
```

Check for updates:

```bash
npm run skills:check
```

Update installed skills:

```bash
npm run skills:update
```

## Agent Path Notes

- For this repository, Codex-compatible project skills live in `.agents/skills/`.
- If you want Claude Code to load the same skill set, install separately to `.claude/skills/`:

```bash
npx skills add https://github.com/anthropics/skills --skill '*' -a claude-code -y --copy
```

- `.claude/settings.local.json` is not a skill directory and does not install or restore skills by itself.

## Installed Skill Set

The current project lock includes these skills from `anthropics/skills`:

- `algorithmic-art`
- `brand-guidelines`
- `canvas-design`
- `claude-api`
- `doc-coauthoring`
- `docx`
- `frontend-design`
- `internal-comms`
- `mcp-builder`
- `pdf`
- `pptx`
- `skill-creator`
- `slack-gif-creator`
- `template-skill`
- `theme-factory`
- `web-artifacts-builder`
- `webapp-testing`
- `xlsx`
