# Adventure Manifest: Word Quest
Created: 2026-05-02
Session: First hunt scaffolded with treasure-mapmaker v3.1 — slim PROMPT.md format from Surgeon autopsy. Stack-validation hunt for the sovereign NIM-direct autonomous loop (OPS-027).
Status: ACTIVE

## The Vision
Word Quest is the SuperConci galaxy's reading game — the planet already on the GalaxyHub map, waiting for a game. It mirrors Number Blasters' arcade rhythm (60s rounds, falling asteroids, score/streak/lives) but tests vocabulary instead of math. The kid sees a prompt at the top ("means: very fast") and four word-asteroids fall — tap the right one before they crash.

The game targets Conci first — he reads at 3rd-grade level at age 5 — but adapts to whoever's playing. Static difficulty tiers don't fit a kid who progresses fast; instead difficulty floats with rolling accuracy. Strong players get harder words, struggling players get easier ones. Same game, different challenge.

This is the v1 MVP: one prompt type (definition match), adaptive difficulty 1-10, audio reused from NumberBlasters. Future hunts add synonym/antonym/fill-in-blank prompt types and themed packs (trains, Hobbit, space).

## Success Looks Like
- Conci taps Word Quest planet on GalaxyHub
- Game starts in <2s with prompt + 4 falling word-asteroids
- He can tell which word matches at his level (~difficulty 5–7 starting)
- Difficulty rises naturally as he gets answers right; drops if he misses
- 60s round ends with a score he wants to beat
- Audio feels coherent with NumberBlasters palette
- Tyler hands phone to Conci, Conci plays unprompted

## What Not to Lose
- The arcade FEEL — fast, snappy, satisfying. Not a quiz.
- Adaptive difficulty as core, not stretch. It is what lets Conci grow with the game.
- Visual coherence with NumberBlasters / GalaxyHub palette (purple #7c6f9c per planet styling)
- Word pack vocab he could meet in The Hobbit / train books / space stories

## Specs Extracted
[IDEA]: Word Quest v1 MVP
[TIER]: Sonnet (mechanical build off NumberBlasters template) + Nemotron for word pack curation
[SURFACE]: NIM-direct hunter-loop (autonomous)
[SPEC]: React component at src/games/word-quest/WordQuest.jsx + word pack at src/games/word-quest/data/word-pack-v1.json + GalaxyHub routing wired. Falling word-asteroids tap-to-match. Adaptive difficulty 1-10 floats with rolling accuracy. NumberBlasters AudioEngine reused.
[HUNT]: word-quest

## Hunts Spawned
| Hunt | MAP.md | Status | Description |
|------|--------|--------|-------------|
| word-quest | hunts/word-quest/MAP.md | PENDING | MVP falling-word arcade w/ adaptive difficulty |

## Cross-Reference
- Inspired by MoreWords (`github.com/AetherCreator/more`) — kid-mode mechanics adapted to SuperConci's arcade pattern
- Sister game: `src/NumberBlasters.jsx` — the template Word Quest extends
- Existing planet entry: `src/hub/GalaxyNavigator.jsx` (id "word-quest", coords (1200, 3800), color #7c6f9c, 📖)
- First hunt scaffolded with treasure-mapmaker v3.1.0 slim PROMPT.md format
