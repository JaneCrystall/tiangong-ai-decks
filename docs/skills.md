# Skills Setup

This project uses the `skills` CLI in project scope rather than global scope.

## Current Convention

- Project-scoped skills are installed under `.agents/skills/`.
- `.claude/skills` is a tracked symlink to `../.agents/skills` so Claude Code and Codex-compatible tooling can share the same project-local skills directory.
- `skills-lock.json` is committed and records the source plus content hash for each installed skill.
- The repository currently tracks the full `anthropics/skills` set for Codex-compatible project usage.
- `.agents/skills/.gitkeep` keeps the directory present in a clean clone even when no skills have been installed yet.
- Installed third-party skill contents under `.agents/skills/` are local artifacts and are ignored by Git.

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
- Claude Code reads the same project-local skills through the `.claude/skills -> ../.agents/skills` symlink.
- No second install is required just to make the same project skills visible to Claude Code.

```bash
ls -l .claude/skills
```

- Because `.claude/skills` is symlinked, do not separately install another copied skill tree into `.claude/skills` unless you intentionally want it to diverge from `.agents/skills`.
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
