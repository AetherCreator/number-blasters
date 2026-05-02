# Clue 4: Hub Wiring + Smoke Test

## Objective
Route the GalaxyHub Word Quest planet to WordQuest.jsx, register the route in App.tsx, unlock the planet styling, and verify a clean production build.

## Files to Read
- `src/hub/GalaxyHub.jsx` (contains word-quest planet entry)
- `src/hub/GalaxyNavigator.jsx` (contains word-quest planet entry)
- `src/App.tsx` (root routing)
- `src/games/word-quest/WordQuest.jsx` (destination)

## Analysis Method
1. Find how Story Quest and Number Blasters are routed in App.tsx — follow that exact pattern.
2. Import `WordQuest` and add a route (path: `/word-quest` if React Router, or matching state-based screen if state-based nav).
3. In GalaxyHub.jsx and GalaxyNavigator.jsx, find the word-quest planet entry. Where Story Quest navigates, Word Quest must navigate.
4. Remove `locked` styling from the Word Quest planet entry (id "word-quest").
5. Run `npm run build` — fix any import/type errors.
6. Update README.md or .claude/CLAUDE.md to flip word-quest from "NEXT" to "shipped v1".

## Output Format
Updated files: `src/App.tsx`, `src/hub/GalaxyHub.jsx`, `src/hub/GalaxyNavigator.jsx`, plus README.md or .claude/CLAUDE.md status update. No new files needed.

## Pass Conditions
- `npm run build` exits 0
- `grep -r "WordQuest" src/App.tsx` returns ≥ 1 line
- `grep -B1 -A3 'id: "word-quest"' src/hub/GalaxyHub.jsx` shows planet not locked
- No import errors in the build output
- GitHub push verified (commit SHA on origin/main)
