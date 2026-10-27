# Instructions for agents working in this repository

This is a single static page, `index.html`, published with GitHub Pages from
`main`. There is no build step: what is in the file is what ships.

## Design review issues

Issues labelled `design-review` come from Loupe, a tool a designer or product
manager uses to leave notes directly on the live page. Each note has a
screenshot, the element's CSS selector, and the element's computed styles at
the time the note was written. The selector and styles are the fastest way to
find the right rule in `index.html`.

When an issue asks you to apply review notes:

- **Stay inside the design system.** It is defined as CSS custom properties in
  `:root` at the top of `index.html` — colours, the spacing scale
  (`--space-*`), radii (`--radius-*`), type sizes (`--text-*`). Use those
  variables. Do not introduce new literal colours, sizes, or spacing values.
  If a note seems to need a value that isn't in the system, pick the nearest
  step and say so in the PR.
- **Prefer reusing existing patterns.** If a note says "make it like the main
  button", find the class the main button already uses and apply it rather
  than restyling from scratch.
- **Change only what the note asks for.** No drive-by refactors, no
  reformatting of unrelated CSS.
- **Don't guess at decisions.** If a note can only be answered by new copy,
  new behaviour, or a judgement call the reviewer hasn't made, skip it and
  explain why in the PR description.
- **One pull request per issue**, covering all the notes in it.
- **In the PR description**, list every note by its number with one line on
  what changed, or why it was skipped. The reviewer reads this, not the diff.
- **Reference the issue** with `Ref #<issue number>` in the PR description
  (not `Fixes` — the issue stays open until the reviewer accepts each note).
- **End the PR description with a status block** Loupe reads to update each
  note. One line per note you handled, `done` or `skipped` with a short
  reason in the reviewer's language:

  ```
  <!-- loupe
  1: done
  2: skipped — непонятно, убрать сообщение или перенести
  -->
  ```

## Follow-up comments on design review issues

The reviewer answers from Loupe by commenting on the same issue. Comments
that mention `@claude` are new work:

- `@claude **Заметка N** — вернула после проверки: …` — the fix for note N
  was not right. Read the comment (and the "now" screenshot if attached),
  fix it again.
- `@claude **Заметка N** — ответ: …` — the answer to a note you skipped.
  Now apply it.

For either, open a **new** pull request with `Ref #<issue>` and a status
block that lists only the notes it addresses. Leave notes that weren't
mentioned alone.

`✅ **Заметка N** принята.` means the reviewer accepted note N — nothing to do.
Comments without `@claude` are the team talking; don't act on them.

Issues additionally labelled `needs-decision` are for humans to discuss. Do
not act on them unless someone explicitly asks you to in a comment.

The `loupe-assets` branch only stores screenshots for issues. Never merge it
and never base work on it.
