# Copilot instructions

## Build, test, and lint

- The app is a standalone `index.html`; open it directly in a browser to run it. No server or dependency installation is needed.
- There is no build, lint, or automated test command configured. Verify behavior in a browser; there is no test runner or single-test selector.

## Architecture

- The app is intentionally self-contained in `index.html`: markup, CSS, quiz data, and browser JavaScript all live in that file, with no external dependencies.
- The `questions` array is the source of truth for question copy, choices, zero-based correct-answer indexes, categories, and explanations. `renderQuestion`, `selectAnswer`, and `showResults` drive the quiz flow and score-based result screen.
- CSS custom properties in `:root` define the light palette; `prefers-color-scheme: dark` overrides them. Reuse these tokens when styling new quiz elements so both themes stay aligned.

## Codebase conventions

- Keep quiz content data-driven in `questions`; the number of questions and progress display derive from its length.
- Use native DOM elements and event listeners. Answer choices are real buttons, number keys 1–4 select choices, and Enter advances after an answer.
- Preserve the existing accessibility behavior: labeled progress bar and score announcements, answer labels, visible `:focus-visible` outlines, focus moved to the next button after answering, and reduced-motion support.
- Keep correct/wrong feedback tied to the `correct`/`wrong` classes and the `--correct`/`--wrong` theme tokens.
