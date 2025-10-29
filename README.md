# Unit 8.8 -- The Date Object

## Crash Course: JavaScript Date & Timers

-   **Create a Date:** `const d = new Date();`
-   **Parts:**
    -   Month (0--11) → `d.getMonth() + 1`\
    -   Day (1--31) → `d.getDate()`\
    -   Year (YYYY) → `d.getFullYear()`\
    -   Day of week (0--6, Sun--Sat) → `d.getDay()`
-   **Epoch ms:** `d.getTime()` (ms since Jan 1, 1970)
-   **Timer loops:**
    -   Start: `const id = setInterval(fn, 10);`\
    -   Stop: `clearInterval(id);`
-   **Writing to page:**
    `document.getElementById('someId').textContent = '…';`
-   **Event listeners (required):**
    `document.getElementById('myBtn').addEventListener('click', handler);`\
    (No inline `onclick` attributes.)

------------------------------------------------------------------------

## Goal

Build a small page that:

1.  Shows the **current date** as:\
    `DayOfWeek, M/D/YYYY` (e.g., `Tuesday, 10/28/2025`) inside `#myDate`
2.  Starts a running **elapsed time (seconds)** since page load,
    updating \~every 10ms, inside `#myTimer`
3.  Toggles the timer **Start/Stop** with a button `#myBtn` (text
    switches between "Stop" and "Start")

### Required IDs (for autograding)

-   `myDate` --- where you print the date string
-   `myTimer` --- where you print elapsed seconds (e.g., `1.23`)
-   `myBtn` --- the toggle button (must be wired with
    `addEventListener`, not inline `onclick`)

### Functional Details

-   On load, display the date in `#myDate`.
-   Also on load, capture a `start = new Date().getTime()` and begin a
    `setInterval` that:
    -   Reads `now = new Date().getTime()`
    -   Computes elapsed seconds: `(now - start) / 1000`
    -   Writes that to `#myTimer` with **two decimals** (e.g.,
        `time.toFixed(2)`).
-   The button toggles:
    -   If running → `clearInterval`, set text to **Start**
    -   If stopped → `setInterval` again, set text to **Stop**

> Tip: Map `getDay()` to names:
> `['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'][d.getDay()]`.

------------------------------------------------------------------------

## HTML

``` html
<div id="myDate"></div>
<div id="myTimer"></div>
<button id="myBtn">Stop</button>
```

------------------------------------------------------------------------

## What the Autograder Checks

1.  **Required elements exist** (`#myDate`, `#myTimer`, `#myBtn`)
2.  **Event wiring** uses `addEventListener` (no inline `onclick`)
3.  **Date format** looks like `DayOfWeek, M/D/YYYY` and the numeric
    date matches today
4.  **Timer runs** (value increases after \~120ms)
5.  **Toggle works** (button text flips Start/Stop and timer
    pauses/resumes)
6.  **Elapsed is monotonic** (keeps increasing while running)

**Score:** 100 points total (10 + 15 + 20 + 20 + 20 + 15)
