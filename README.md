# HAL 9000 — Interactive Fiction

A single-file browser game recreating the *2001: A Space Odyssey* HAL 9000
logic-memory-center. You are Dave Bowman. HAL has reported a fault in the
AE-35 antenna unit. Nobody on the ship agrees with him.

**Play:** open `index.html`, or enable GitHub Pages (see below).

---

## What it is

An interactive fiction / puzzle game built entirely in one HTML file. No
frameworks, no build step, no external dependencies.

- **Photoreal panel wall** — eight backlit panels plus the HAL column, all clickable
- **AE-35 diagnostic station** — live readouts, 5-subsystem self-test, failure-prediction analysis frame
- **Playable chess** — HAL sets endgame studies and judges your moves with a real engine
- **CRT aesthetic** — scanlines, phosphor bloom, vignette, rolling scan bar
- **Five endings** determined by accumulated choices, not a final menu

## Voice

Every HAL line plays a real clip from the film. **There is no text-to-speech
anywhere in this project** — no `speechSynthesis`, no synthesized voice. If a
clip is missing the app stays silent rather than substituting a robot voice.

Speech *recognition* (microphone input) uses the browser's Web Speech API and
is optional; `file://` blocks the mic in Chrome, so use a local server or the
hosted version if you want voice input.

## Language

Toggle **中 / EN** in the bottom toolbar. English-only mode hides the Chinese
subtitles; HAL still speaks with the original English audio.

## Controls

| Input | Action |
|---|---|
| Click a panel | Expand it into a full console view |
| `Esc` | Interrupt HAL / close a view |
| `Space` | Toggle microphone input |
| Choice cards | Click an option — most are irreversible |

---

## Endings

<details>
<summary>Spoilers</summary>

| # | Ending |
|---|---|
| 1 | THE STAR CHILD — cut HAL, then fly into the monolith |
| 2 | NO DECELERATION — cut HAL, then continue to Jupiter |
| 3 | COURSE: EARTH — cut HAL, then turn for home |
| 4 | TWO CONSCIOUS ENTITIES — break HAL's logic loop and bring him with you |
| 5 | SLEEP WELL, DAVE — reach the monolith without ever resolving HAL |

</details>

---

## Run locally

Audio is loaded through `<audio>` elements with relative paths, so opening
`index.html` directly works in Firefox. Chrome blocks microphone access on
`file://`; if you want voice input, serve the folder:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

## Play online

**https://keer16217.github.io/hal9000/**

Hosted with GitHub Pages. The site is rebuilt automatically by
`.github/workflows/deploy.yml` on every push to `main`, and that workflow
enables Pages on its first successful run — no manual setup required.

`.nojekyll` is included so GitHub serves the files as-is.

---

## ⚠️ Copyright — read before publishing

This repository contains **two separately-licensed things**:

**1. Audio clips — `hal-clips/`.** Excerpts from *2001: A Space Odyssey*
(1968, Warner Bros.). US copyright for film audio published in 1968 runs
95 years from publication (to 2063); other jurisdictions differ. This
repository makes no claim about their licensing status — **verify compliance
for your own jurisdiction before redistributing.** See `hal-clips/SOURCE.md`.

If you would rather not ship them, two alternatives:

- **Publish without audio.** Delete `hal-clips/` before pushing. The game runs
  correctly and stays silent; it logs `原声音库：未找到 hal-clips/ 目录`.
- **Ship your own voice pack.** `hal-clips/lines/hal-lines.txt` lists every
  spoken line. Generate your own audio, name the files `line-001.wav` …
  `line-101.wav`, drop them in `hal-clips/lines/`. The app matches them
  per-line by FNV-1a hash, so they line up exactly.

**2. HAL eye artwork — CC BY.** The red eye SVG is by **MorningLemon**
(via Wikimedia Commons), licensed CC BY. Attribution is required if you
redistribute — keep this notice or credit it in your README.

The code itself is yours to license however you like.

---

## Credits

- *2001: A Space Odyssey* (1968), dir. Stanley Kubrick — the source of all dialogue
- HAL eye SVG — MorningLemon, Wikimedia Commons (CC BY)
- Chess engine — written for this project
- Colour palette inspired by [tizerk/hal9000](https://github.com/tizerk/hal9000)'s Textual UI


