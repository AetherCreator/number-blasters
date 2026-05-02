# Clue 2: Game Core

## Objective
Build `src/games/word-quest/WordQuest.jsx` — a playable arcade word game modeled on NumberBlasters.jsx, where word-asteroids fall and the kid taps the one matching a prompt at the top.

## Files to Read
- `src/NumberBlasters.jsx` (full file — the template; mirror its structure, audio engine, starfield, HUD, lives, score, timer)
- `src/games/word-quest/data/word-pack-v1.json` (word pool from Clue 1)

## Analysis Method
1. Create new file `src/games/word-quest/WordQuest.jsx` modeled on NumberBlasters.jsx structure.
2. Replace `generateProblem(difficulty)` with `generatePrompt(words)` that picks a target word and 3 distractors, returns `{prompt: "means: <definition>", choices: [4 words], correctIndex}`.
3. Asteroid component renders a word string instead of a math choice.
4. Tapping an asteroid checks against `correctIndex` — correct → score+combo+sound, wrong → lose life+sound.
5. Round = 60s, 3 lives, score with combo bonus (same rhythm as NumberBlasters).
6. No adaptive difficulty yet — random pull from the pack.
7. Default-export the component.

## Output Format
Single React file at `src/games/word-quest/WordQuest.jsx`:
- Imports React hooks
- Reuses AudioEngine class from NumberBlasters (copy or import)
- Renders Title → Game → Game-over screens
- HUD with score, streak, time, lives
- 4 falling word-asteroids on screen at once
- No external network calls

## Pass Conditions
- File `src/games/word-quest/WordQuest.jsx` exists
- Imports `word-pack-v1.json` correctly
- `npm run build` exits 0 with this file in the source tree
- Test render via `import WordQuest from './games/word-quest/WordQuest'` in App.tsx (commented OK) — no compile errors
- GitHub push verified (commit SHA on origin/main)
