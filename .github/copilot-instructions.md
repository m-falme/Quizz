# Copilot instructions

## Project shape

`quiz.html` is the entire application: semantic HTML, CSS, the question bank, and browser JavaScript live in one standalone file. The script is at the end of the document and uses the existing DOM directly. There are no external assets or runtime dependencies; keep the page usable by opening the file directly in a browser.

The `questions` array is the source of quiz content. Each entry has a `question` string, four `answers`, a zero-based `correct` answer index, and a `fact` shown after answering. The quiz state (`currentIndex`, `score`, `answered`) drives the `renderQuestion` → `selectAnswer` → next-question/results flow. Keep updates to score, progress, feedback, and focus consistent across these transitions; `restart` resets the state and starts at the first question.

## Project-specific conventions

- Keep styling, markup, and interaction logic in `quiz.html`; use the existing CSS custom properties for palette changes, with light defaults and a `prefers-color-scheme: dark` override.
- Preserve the narrow responsive layout, mission-control answer hover/focus treatment, visible keyboard focus, and feedback states (`correct`, `wrong`, `reveal`).
- Preserve accessible behavior when changing interactions: native buttons for choices/actions, the labeled answer group and progress bar, polite live regions, and programmatic focus when advancing, showing results, or restarting.
- Keep animation changes compatible with `prefers-reduced-motion` and `forced-colors`; the existing responsive breakpoint is 480px.
- Keep question correctness tied to the zero-based `correct` index when editing answer order. Update the progress maximum and initial question count if changing the number of questions.

## Build, test, and lint

There are no package manifests, build scripts, test runner, or linter configured in this repository. No build or automated single-test command is available. For a manual smoke test, open `quiz.html` directly in a browser and verify keyboard answer selection, correct and incorrect feedback, score and progress updates, the final score/reaction, and replay.
