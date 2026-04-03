# Implementation Plan: Women's Day Safety Reminder

## Overview

Build a single `index.html` file containing all HTML structure, embedded CSS, and embedded JavaScript for the Women's Day Safety Reminder checklist app.

## Tasks

- [x] 1. Create `index.html` with base HTML structure
  - Create the file with `<!DOCTYPE html>`, `<head>` (charset, viewport meta), and `<body>`
  - Add the `.page-wrapper` div and `.card` div inside body
  - Add `<header>` with `<h1>` ("Women's Safety Reminder") and `<p class="subtitle">` ("Don't forget these before leaving home ❤️")
  - Add `<footer>` with "Happy Women's Day 💐"
  - _Requirements: 1.1, 3.1, 3.2, 7.1_

- [x] 2. Add the checklist and button markup
  - Add a `<div class="checklist">` with five `<label>` + `<input type="checkbox">` pairs for: "Turn off LPG gas", "Switch off motor", "Lock the door", "Turn off lights", "Turn off fan"
  - Add `<button id="done-btn">Done for Today</button>` below the checklist
  - Ensure all checkboxes are unchecked by default (no `checked` attribute)
  - _Requirements: 4.1, 4.2, 4.4, 5.1, 5.3_

- [x] 3. Embed CSS in a `<style>` block
  - Style `.page-wrapper`: `display: flex; align-items: center; justify-content: center; min-height: 100vh` with soft pink gradient background (`#fce4ec` → `#f3e5f5`)
  - Style `.card`: `max-width: 480px; width: 100%; padding: 2rem; border-radius: 16px; box-shadow: 0 4px 24px rgba(0,0,0,0.12); background: #fff`
  - Style `h1` with `color: #7b1fa2`, `.subtitle` with `color: #ad1457`, footer with `color: #9c27b0`
  - Style `.checklist label`: block-level, `margin-bottom: 0.75rem`, `font-size` at least 1rem (≥16px), checkbox `accent-color: #e91e8c`
  - Style `#done-btn`: pink background `#e91e8c`, white text, rounded corners; add `:hover` with `background: #c2185b; transform: scale(1.03); transition: all 0.2s ease`
  - Add responsive rule: `@media (max-width: 480px)` — card fills full width, `padding: 1rem`
  - _Requirements: 1.2, 2.1, 2.2, 2.3, 2.4, 3.3, 4.3, 5.2, 8.1, 8.2, 8.3_

- [x] 4. Embed JavaScript in a `<script>` block
  - Add a single `click` event listener on `#done-btn`
  - Inside the handler: query `.checklist input[type="checkbox"]:checked` to get checked count, compute `missed = 5 - checked`
  - If `missed === 0` call `alert('Great job! All tasks completed 🎉')`, else call `alert(\`You missed ${missed} tasks! Please check again ⚠️\`)`
  - _Requirements: 1.3, 4.5, 6.1, 6.2, 6.3_

- [x] 5. Final checkpoint — verify the file is self-contained and correct
  - Confirm no external `<link>`, `<script src>`, or `fetch` calls exist in the file
  - Confirm all five checklist items are present and unchecked by default
  - Confirm alert messages match the exact strings in requirements 6.1 and 6.2
  - Ensure all tests pass, ask the user if questions arise.
  - _Requirements: 1.4_

## Notes

- Tasks marked with `*` are optional and can be skipped for faster MVP
- The entire app is one file — no modules, no build step, no dependencies
- Checkpoints ensure incremental validation before moving on
