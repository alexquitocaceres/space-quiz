# Copilot instructions

## Project shape

This is a dependency-free, single-page Spanish space quiz. The complete application lives in `index.html`: semantic HTML, inline CSS, quiz data, and vanilla JavaScript share one file. It runs directly in a browser from `file://`; there is no server-side code, bundler, or module system.

The question array is the source of truth for quiz content and scoring. `renderQuestion()` builds each question's answer buttons, `selectAnswer()` handles one-time scoring and feedback, and the next/restart handlers move between questions and the results view. Keep changes to question count, progress, score, and results consistent with that flow.

## Commands and checks

There are no project-defined build, test, or lint commands or dependencies. Open `index.html` directly in a browser to run the app. For a change to quiz behavior, verify the correct and incorrect answer paths, score and progress updates, advancing through the last question, results, and restart in the browser. Check keyboard focus as the view changes.

## Project conventions

- Keep the app self-contained in `index.html`; do not add a framework or runtime dependency without an explicit project requirement.
- User-facing interface text and quiz content are in Spanish. Questions use objects with `question`, `answers`, zero-based `correct`, and explanatory `fact` fields.
- CSS is organized in the page's `<style>` block and uses custom properties in `:root`; extend those tokens for shared colors rather than scattering new theme values. Preserve the narrow, centered card layout and its responsive treatment.
- The page supports light and dark system color schemes and reduced-motion preferences. Preserve both when changing colors or animations.
- Quiz choices and navigation are native buttons. Preserve visible keyboard focus, focus transfer to the first answer after advancing or restarting, and the existing ARIA live/progress semantics.
- Insert dynamic question, feedback, and result copy as text rather than interpreting it as HTML. Answer labels are currently assigned through `textContent`.
