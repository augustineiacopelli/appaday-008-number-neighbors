# App 008 — Number Neighbors

**Category:** G · Games and Interactive
**Live:** [augustineiacopelli.github.io/appaday-008-number-neighbors](https://augustineiacopelli.github.io/appaday-008-number-neighbors)
**Built:** 2026-05-14

## What It Does

Number Neighbors is a sliding tile puzzle (the classic 15-puzzle) playable across three grid sizes: 3×3, 4×4, and 5×5. Slide numbered tiles into ascending order with the empty space in the bottom-right corner. Every shuffle is guaranteed solvable via parity checking. Tracks move count, elapsed time, and personal best per grid size using localStorage.

## How to Use

Tap or click any tile adjacent to the empty space to slide it. On desktop, arrow keys also work — they push the neighboring tile into the gap. Switch grid sizes with the 3×3 / 4×4 / 5×5 buttons at any time. Hit **Hint** when stuck — the solver highlights the optimal next tile to move in green. The hint clears after each move and can be requested again from the new position.

## Technical Notes

- Vanilla HTML/CSS/JS, no frameworks or dependencies
- Tiles are absolutely positioned DOM elements; movement is CSS `left`/`top` transitions for true physical sliding animation
- Solvability guaranteed via inversion-count parity check before any shuffle is accepted
- Hint system uses A* search with Manhattan distance heuristic, run in 14ms time-sliced chunks via `setTimeout` to keep the UI non-blocking
- Click handling is delegated to the board element and always derives tile position from live state via `tiles.indexOf(val)` — prevents index corruption across async solver callbacks
- Personal bests stored in `localStorage` keyed by grid size

## Definition of Complete

- [x] Functional on 3×3, 4×4, and 5×5 grids without errors
- [x] Every puzzle is guaranteed solvable
- [x] Smooth sliding tile animation
- [x] Move counter, timer, and personal best tracking
- [x] Working A* hint system that identifies the optimal next move
- [x] Mobile-friendly tap targets and layout
- [x] Published to GitHub Pages
