# Deck Workspaces

Each deck lives in its own folder under `decks/`.

Expected files:

- `brief.md`: audience, objective, freeform render hint, and locked source ids.
- `outline.md`: human-editable outline that drives slide generation.
- `deck.md`: generated slide draft and canonical review artifact.
- `deck.public.md`: clean renderer handoff Markdown derived from `deck.md`.
- `render.handoff.json`: machine-readable renderer contract that points external renderers to `deck.public.md`.
- `sources.lock.json`: locked source snapshot used to compose the deck.

Notes:

- Deck workspaces are user output and are gitignored by default. The repository keeps only `decks/README.md` and `decks/.gitkeep`.
- Deck assembly assumes the relevant source material has already been archived and normalized by preprocessing skills.
- Review and edit `deck.md` as needed before handing it to a rendering skill.
- Hand rendering skills `render.handoff.json` or `deck.public.md` by default, not `deck.md`.
- `theme` in `brief.md` is only a style hint string for external skills. It is not backed by an internal theme preset file.
- Inside `deck.md`, use `##` only for slide boundaries. Use `###` or deeper headings inside a slide body.
- HTML output is not produced by the core repository build. Use an explicit rendering skill such as `frontend-design`.
- Playwright verification is required before considering rendered HTML complete.
- At minimum, validate one representative desktop viewport and one representative mobile viewport, and fix any clipping, fixed-UI overlap, or broken layout before handoff.
- If the rendered deck keeps a sticky or floating side directory, also validate an ultra-wide viewport such as `3840x2160`.
