# AGENTS.md

## Project

Pac-Man-like game (vanilla JS + HTML5 Canvas + CSS). Learning project using spec-driven development.

## Commands

- No build step, no dependencies, no lint/test/typecheck.
- Run: open `src/index.html` in browser, or `npx serve .` → http://localhost:3000.

## Architecture

- Plain scripts, no modules. `src/index.html` loads in order: `js/maze.js` → `js/game.js` → `js/render.js` → `js/main.js`.
- Cross-file state via `window.*` globals: `createGame`, `update`, `DIRS`, `MAZE`, `TUNNEL_ROW`, `PACMAN_START`, `GHOST_STARTS` (game.js); `draw` (render.js).
- State machine: `'start' | 'playing' | 'won' | 'lost'`. Win overlay: "GANASTE"; loss: "PERDISTE"; start/restart button: "Start" / "Reiniciar".
- Maze: 28×31 cells, 31 strings × 28 chars; `#`=wall, `.`=dot, `-`=door, space=empty; tunnel row `TUNNEL_ROW = 14`; pac start (13,23).
- Ghosts: `hunter` chases (best Manhattan direction), `random` picks random; dead-end fallback allows reversing.
- Render: `TILE = 20`; walls drawn as connected segments; pacman mouth animates via `frame`; ghost colors; HUD.

## Workflow

- Spec-driven via `/spec` skill: `open-pacman/.agents/skills/spec/` (from `klerith/fernando-skills`; lockfile `open-pacman/skills-lock.json`). Specs go to `specs/NN-slug.md` (not created yet).

## Gotchas

- Keyboard: Arrow keys via `e.key`, only applied while state is `'playing'`.
- User-facing strings and comments in Spanish.

## Verification

- No automated tests. Verify manually by playing the game in a browser.
