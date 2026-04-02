# Rendering Contract

External HTML rendering is intentionally outside the core repository build.

When a renderer or rendering skill is asked to produce HTML for a deck, use this input order:

1. `decks/<deck-id>/render.handoff.json`
2. `decks/<deck-id>/deck.public.md`
3. `decks/<deck-id>/sources.lock.json`
4. `decks/<deck-id>/brief.md`

Rules:

- Default to `deck.public.md` as the display artifact.
- Treat `deck.md` as review-only input.
- Do not render `Speaker Notes`.
- Do not surface HTML comment directives such as `<!-- sources: ... -->`, `<!-- layout: ... -->`, `<!-- id: ... -->`, or `<!-- kicker: ... -->`.
- Do not expose source ids, archive keys, or internal pipeline metadata in the visible presentation unless the user explicitly asks for citation UI.
- Only inspect `deck.md` when the public artifact is missing or a user explicitly asks to debug the review layer.

The purpose of this contract is to keep the public presentation clean while preserving a richer review artifact for editing and provenance.
