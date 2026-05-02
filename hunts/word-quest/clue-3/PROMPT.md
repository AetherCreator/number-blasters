# Clue 3: Adaptive Difficulty + Audio

## Objective
Layer adaptive difficulty into WordQuest.jsx — difficulty floats with rolling accuracy of last 10 answers — and hook NumberBlasters AudioEngine sounds into game events.

## Files to Read
- `src/games/word-quest/WordQuest.jsx` (file from Clue 2)
- `src/NumberBlasters.jsx` (audio engine reference + sound design)

## Analysis Method
1. Add state `currentDifficulty` (init 5) and `recentAnswers` (boolean array, max length 10).
2. After each answer, push correct/incorrect into `recentAnswers`, trim to last 10.
3. When `recentAnswers.length === 10`: compute accuracy. If >0.8 → `currentDifficulty = min(10, currentDifficulty+1)` and clear array. If <0.5 → `currentDifficulty = max(1, currentDifficulty-1)` and clear array.
4. Modify `generatePrompt` to filter words to `currentDifficulty ± 1` band before picking. If <4 words available, expand to ±2.
5. `console.log` every difficulty change with old/new values for verification.
6. Hook AudioEngine: `correctHit()` on correct, `wrongHit()` on wrong, `gameOver()` on round end. Add `gameOver()` to AudioEngine if not present (descending arpeggio).

## Output Format
Updated `src/games/word-quest/WordQuest.jsx`. If AudioEngine is extracted to a shared module, create `src/games/_shared/AudioEngine.js` and import into both NumberBlasters.jsx and WordQuest.jsx — verify NumberBlasters still works.

## Pass Conditions
- WordQuest.jsx contains adaptive-difficulty state + threshold logic
- Console logs show difficulty changes on threshold crosses (eyeball via dev server, play 10 answers, watch console)
- Audio plays on correct/wrong/end events
- `npm run build` exits 0
- NumberBlasters still builds and runs cleanly (if AudioEngine extracted)
- GitHub push verified (commit SHA on origin/main)
