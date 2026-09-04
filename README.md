# Eduplex Exam Timer

A single-file, self-contained HTML exam timer for classroom or invigilation use. Displays a countdown ring with an optional silent "reading time" phase before the exam clock starts, and includes a focus/projection mode for displaying on a screen during the exam.

No build step, no dependencies, no server required — just open `exam_timer.html` in a browser.

## Features

- **Countdown ring** with a live `MM:SS` readout and status label (READY, READING TIME, EXAM TIME, 5 MINUTES LEFT, FINAL MINUTE, TIME'S UP).
- **Optional reading time phase** — a silent reading period (default 10 min) that counts down in green before automatically handing off to the exam clock (blue). Can be toggled on/off, duration is adjustable, and can be skipped mid-countdown.
- **Exam duration presets** (15 / 30 / 45 / 60 / 90 / 120 min) plus a custom minutes field (1–480).
- **Custom exam title** — type a label (e.g. "Grade 10 Mathematics Final") shown above the timer.
- **Start / Pause / Reset controls**, plus spacebar as a shortcut to start/pause.
- **Audible cues** — a tone when reading time hands off to exam time, and a triple beep when time is up. Can be muted via the Sound toggle.
- **Visual warnings** — the readout turns amber at 5 minutes remaining, red and pulsing in the final minute and after time expires.
- **Focus mode** — hides all setup controls and enlarges the timer for projecting during the exam; requests fullscreen where supported. The logo stays pinned to the corner of the screen even while everything else is hidden.
- **Responsive layout** — optimized for both mobile screens and desktop PCs (the layout centers itself in a card on wider viewports).

## Getting started

1. Download `exam_timer.html`.
2. Open it in any modern browser (Chrome, Edge, Firefox, Safari).
3. (Optional) Set an exam title, toggle reading time on/off and set its length, and choose an exam duration.
4. Click **Start** to begin. Click **Focus mode** to switch to the projector-friendly view.

No installation, internet connection, or account is required. All state lives in memory in the browser tab — refreshing the page resets the timer.

## Usage notes

| Control | Behavior |
|---|---|
| **Start / Pause** | Starts the timer from idle, or pauses/resumes an active countdown. Also triggered by the spacebar (when not focused on a text field). |
| **Reset** | Stops the timer and returns to the idle state using the current settings. |
| **Reading time toggle** | Enables/disables the reading phase. Changing this while idle resets the timer to reflect the new setting. |
| **Reading time minutes** | Editable while idle; disabled once the timer is running. |
| **Exam duration** | Choose a preset or enter custom minutes; changes reset the timer while idle. |
| **Skip reading time** | Only visible during the reading phase; jumps straight to the exam countdown. |
| **Focus mode** | Hides the title input, settings, and footer; enlarges the ring; pins the logo to the screen corner; attempts to enter fullscreen. |
| **Sound: on/off** | Toggles the start-of-exam and time's-up tones. |

## Customization

The file is plain HTML/CSS/JavaScript, so it's easy to adjust directly:

- **Branding** — update the logo (`<img>` in the `<header>`), the name/motto text, and the color palette defined in the `:root` CSS variables (`--navy`, `--green`, `--amber`, `--red`, etc.).
- **Default durations** — change the `examMinutes` and `readingMinutes` variables near the top of the `<script>` block.
- **Duration presets** — edit the `data-min` buttons inside the `.presets` container.
- **Warning thresholds** — the 5-minute and 1-minute warning cutoffs are set in the `render()` function (`remaining <= 300` and `remaining <= 60`).

## Browser support

Uses standard Web Audio (`AudioContext`) for tones and the Fullscreen API for focus mode; both degrade gracefully (wrapped in `try/catch`) if unsupported, so the timer itself will still work. Google Fonts (`Fraunces`, `Inter`) are loaded via `@import` and require an internet connection for custom typography — the layout falls back to system fonts otherwise.

## File structure

This is a single file with everything inline:

```
exam_timer.html   # HTML structure, CSS styling, and JavaScript logic
```

There are no external assets to manage beyond the Google Fonts request.
