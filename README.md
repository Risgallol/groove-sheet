# Groove Sheet

A drum notation editor in a single HTML file. Write grooves on a step grid, read them as a drum staff, play them back, and export the score as a PDF.

Live copy: https://claude.ai/artifact/MW7MKCXEgunJRQLqKwbCXD (private to the owner's claude.ai account)

## Running it

Open `index.html` in a browser. There is no build step and no server. The one exception is the recorded drum kit: browsers only load its sample files over http, so to hear it run `python3 -m http.server` in this folder and open http://localhost:8000. It needs an internet connection for the web fonts and, the first time you export, for the PDF libraries.

## Features

- **Grid:** 9 voices (crash, hi-hat, ride, three toms, snare, kick, hi-hat foot). Clicking a cell cycles hit → accent → (ghost / cross-stick on snare, open on hi-hat) → off. Drag to paint.
- **Timing:** each bar has its own time signature (2/4–7/4, 3/8–12/8) and each beat its own subdivision (quarters, 8ths, 16ths, 32nds, triplets, sextuplets). Right-click or Alt-click a step to split it in two or merge it with the next.
- **Score:** a two-voice drum staff rendered as SVG, with beams, rests, dots, tuplets, accents, ghost notes and open hi-hats.
- **Song structure:** section labels, repeat signs with a pass count (×2–×16), one-bar "%" repeats, and manual line breaks.
- **Editing:** select bars (click a bar title, Shift-click for a range) to copy, cut, paste, duplicate, clear, delete, or wrap them in repeats. Undo and redo work for every edit.
- **Playback:** synthesized kit, tempo 30–260 with tap tempo, metronome, count-in and loop. Repeats play out in full. Start from any point by clicking the score or a count, or by using the Start menu.
- **Kit:** the Kit button opens per-drum pitch (±12 semitones), length and volume sliders, with a play button for each drum. It has five synthesized presets (Acoustic, Electronic 808, Jazz, Tight funk, Big rock) and one recorded kit, plus master and metronome volume and a demo beat. The recorded kit is the default on a first visit and its samples load when the page opens. It plays the samples in `samples/virtuosity/` (from Virtuosity Drums, CC0; see `SOURCE.md` there) and falls back to the synthesized sounds if they can't be loaded. The kit is saved in the browser and used for every groove.
- **Recording:** the Record button loops the selected bars (all bars if none are selected) with the click on, after a one-bar count-in. Tap K for kick, S for snare and H for hi-hat, or use the on-screen pads; each hit snaps to the nearest step, with output latency taken into account. Space or Esc stops, and one Undo removes the whole take.
- **Saving and sharing:** a library of saved grooves (kept in the browser), share codes (`GS2.`), share links, and PDF export (A4, vector).

## Keyboard

| Keys | Action |
| --- | --- |
| Space | Play / stop |
| ⌘/Ctrl Z, ⇧⌘/Ctrl Z | Undo / redo |
| ⌘/Ctrl C, X, V | Copy / cut / paste selected bars |
| Home | Move the start point to the top |
| Esc | Clear the selection |
| K, S, H | While recording: kick, snare, hi-hat |
| Space, Esc | While recording: stop |

## Where data lives

The current draft, the library, the bar clipboard and view settings are stored in the browser's `localStorage`. Opening `index.html` from disk and opening the claude.ai copy give two separate stores. To move a groove between them, use **Share → Copy code** in one and **Open a groove code** in the other.

## Hosting it as a website

The site is `index.html` plus the `samples/virtuosity/` folder. Any static host works (Vercel, GitHub Pages, Netlify, Cloudflare Pages); there is nothing to build. The `original/` folder is not part of the site.

When the page is served over http(s), the Share dialog also offers **Copy link**. The link is the page's address followed by `#` and the share code, so the groove travels inside the link and nothing is stored on a server. Opening such a link replaces the visitor's current draft; Undo brings it back.

`original/index.html` is the version from before the website changes (no share links, no link-preview tags, no favicon), kept for personal use.

## Code map

Everything is in `index.html`: the styles at the top, then the markup, then one script. Sections in the script, in order:

1. **Model constants:** tick math (quarter = 48 ticks), subdivisions, meters, instruments and their staff positions.
2. **Bar helpers:** beat groups, steps (`cells`), re-metering, split/merge, repeats and play order.
3. **Examples**, then **history** (undo/redo).
4. **Score rendering:** `buildScore()` lays out systems; `renderScore()` draws them on screen.
5. **Grid:** `buildGrid()` and its event handlers, bar selection, copy/paste, and the step context menu.
6. **Audio:** Web Audio drum synthesis and the sampled kit (`SMAP`, `loadSamples`, `sampleHit`), then the transport and recording (`startRec`, `recHit`) (scheduler, playhead, start marker).
7. **Controls**, **library**, **share codes and links** (`encode` / `decode` / `sanitize`, `openFromHash`), and **PDF export** (jsPDF + svg2pdf, loaded when first used).

## Updating the claude.ai copy

Ask Claude to update the artifact at the URL above from this file. The artifact version is the same page without the outer `<!doctype>`, `<html>`, `<head>` and `<body>` wrapper.
