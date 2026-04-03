# Design Document

## Overview

The Women's Day Safety Reminder is a self-contained static web application delivered as a single `index.html` file. It presents a daily household safety checklist themed around Women's Day, allowing a user to tick off five safety tasks before leaving home and receive immediate feedback via a browser alert.

Because there are no build tools, frameworks, or external dependencies, the entire implementation lives in one file: HTML structure, embedded `<style>` block, and embedded `<script>` block. Deployment is as simple as opening the file in a browser or hosting it on any static file server.

---

## Architecture

The application is a pure client-side, single-page static app with no backend, no network requests, and no persistent state beyond the current browser session.

```
index.html
├── <head>
│   ├── <meta> (charset, viewport)
│   └── <style> (all CSS)
└── <body>
    ├── .page-wrapper      (full-viewport flex centering)
    │   └── .card          (max-width 480px, rounded, shadow)
    │       ├── header     (title + subtitle)
    │       ├── .checklist (5 checkbox items)
    │       ├── #done-btn  (submit button)
    │       └── footer     (Women's Day message)
    └── <script>           (all JS)
```

Data flow:

1. Page loads → all checkboxes unchecked (default HTML state).
2. User ticks/unticks checkboxes → browser manages checked state natively.
3. User clicks "Done for Today" → JS counts unchecked boxes → `window.alert()` fires with the appropriate message.

No state is persisted between page reloads; the checklist resets automatically on refresh.

---

## Components and Interfaces

### 1. Page Wrapper (`.page-wrapper`)

- Full-viewport `<div>` using `display: flex; align-items: center; justify-content: center; min-height: 100vh`.
- Background: soft pink gradient (`#fce4ec` → `#f3e5f5`).

### 2. Card (`.card`)

- `max-width: 480px; width: 100%; padding: 2rem; border-radius: 16px; box-shadow: 0 4px 24px rgba(0,0,0,0.12); background: #fff`.
- On viewports ≤ 480 px the card fills the full width with `padding: 1rem`.

### 3. Header

- `<h1>` — "Women's Safety Reminder" — `font-size: 1.6rem; color: #7b1fa2` (purple).
- `<p class="subtitle">` — "Don't forget these before leaving home ❤️" — `font-size: 1rem; color: #ad1457` (deep pink).

### 4. Checklist (`.checklist`)

Five `<label>` elements each wrapping an `<input type="checkbox">` and a text node. Labels are block-level with `margin-bottom: 0.75rem` for spacing. Custom checkbox accent color: `#e91e8c`.

Tasks (in order):
1. Turn off LPG gas
2. Switch off motor
3. Lock the door
4. Turn off lights
5. Turn off fan

### 5. Done for Today Button (`#done-btn`)

- `background: #e91e8c; color: #fff; border: none; border-radius: 8px; padding: 0.75rem 2rem; font-size: 1rem; cursor: pointer`.
- `:hover` — `background: #c2185b; transform: scale(1.03); transition: all 0.2s ease`.

### 6. Alert Feedback

Triggered by the `click` event on `#done-btn`. Pure `window.alert()` — no custom modal needed.

- All checked → `"Great job! All tasks completed 🎉"`
- Some unchecked → `"You missed X tasks! Please check again ⚠️"` (X = count of unchecked boxes)

### 7. Footer

- `<footer>` — "Happy Women's Day 💐" — `font-size: 0.9rem; color: #9c27b0; margin-top: 1.5rem; text-align: center`.

---

## Data Models

The application has no persistent data model. All state is ephemeral DOM state managed by the browser's native checkbox `checked` property.

### Runtime State (in-memory only)

| Concept | Representation | Notes |
|---|---|---|
| Task list | 5 `<input type="checkbox">` elements | Order fixed; labels are their accessible names |
| Checked count | `document.querySelectorAll('.checklist input:checked').length` | Computed on button click |
| Unchecked count | `5 - checkedCount` | Used to build alert message |

### JavaScript Interface

```js
// Single event listener — the entire JS surface area
document.getElementById('done-btn').addEventListener('click', function () {
  const total = 5;
  const checked = document.querySelectorAll('.checklist input[type="checkbox"]:checked').length;
  const missed = total - checked;

  if (missed === 0) {
    alert('Great job! All tasks completed 🎉');
  } else {
    alert(`You missed ${missed} tasks! Please check again ⚠️`);
  }
});
```

No classes, no modules, no state objects — just one event listener and two DOM queries.

---
