# Hunt: Word Quest
Manifest: hunts/word-quest/ADVENTURE-MANIFEST.md
Goal: Ship Word Quest v1 MVP — falling-word arcade with adaptive difficulty in SuperConci
Repo: SuperConci | Branch: main
Treasure: WordQuest.jsx playable on dev server + clean prod build, GalaxyHub routes to it, Conci plays unprompted

## Quartermaster Inventory (VERIFIED 2026-05-02)
### SuperConci
- CLAUDE.md: exists — lists word-quest as "Reading/Phonics — NEXT"
- CONSTITUTION.md: exists
- .claude/: scaffolded (commit 3144668)
- src/NumberBlasters.jsx: 853 lines — arcade template to mirror
- src/hub/GalaxyHub.jsx + GalaxyNavigator.jsx: contain word-quest planet entry already (id, coords, color)
- src/games/story-quest/: full module — confirms `src/games/<name>/` pattern
- Stack: React 19 + Vite + Tailwind + Web Audio API (no native deps)
- No `src/games/word-quest/` directory yet — hunt creates it

## Pre-Hunt Checklist
- [x] Adventure Manifest written and pushed
- [x] Quartermaster inventory done (above)
- [x] No existing word-quest game code (only planet entry in hub) — hunt MERGES into hub
- [x] Number Blasters confirmed as arcade template
- [x] PROMPT.md slim format applied (treasure-mapmaker v3.1)
- [x] Push step in every clue's pass condition
- [x] Model: Nemotron-120B for all (autonomous NIM-direct path)

## Clue Tree
1. [CHAT] [Nemotron-120B] **Word Pack v1** — generate 200-word JSON pack with definitions + difficulty 1–10 + optional thematic tags
   pass: File at src/games/word-quest/data/word-pack-v1.json valid JSON, 200+ entries, all 10 difficulty bands present + GitHub push verified (commit SHA)

2. [CODE] [Nemotron-120B] **Game Core** — Create src/games/word-quest/WordQuest.jsx modeled on NumberBlasters.jsx; falling word-asteroids, prompt-at-top, 60s/3-lives/score loop, no adaptive difficulty yet
   pass: WordQuest.jsx renders, full round playable title→game over, `npm run build` exits 0 + GitHub push verified (commit SHA)

3. [CODE] [Nemotron-120B] **Adaptive Difficulty + Audio** — Add rolling-accuracy difficulty engine (+1 if >80% over last 10, -1 if <50%, clamp 1-10), filter word pool by current_difficulty±1; hook NumberBlasters AudioEngine for correct/wrong/round-end
   pass: Console logs difficulty changes on threshold crosses; audio plays on events; `npm run build` exits 0 + GitHub push verified (commit SHA)

4. [CODE] [Nemotron-120B] **Hub Wiring + Smoke Test** — Wire GalaxyHub/GalaxyNavigator word-quest planet to route into WordQuest; register route in App.tsx; clean build
   pass: `npm run build` exits 0; grep confirms WordQuest imported in App.tsx; planet unlocked in hub + GitHub push verified (commit SHA)

## Parallelism Graph

```
Clue 1 ── Clue 2 ── Clue 3 ── Clue 4
```

### Dependency Table
| Clue | Depends On | Can Parallelize With |
|------|-----------|----------------------|
| 1    | —         | —                    |
| 2    | 1         | —                    |
| 3    | 2         | —                    |
| 4    | 3         | —                    |

### Execution Waves
```
Wave 1: Clue 1
Wave 2: Clue 2
Wave 3: Clue 3
Wave 4: Clue 4
```

### Machine-Readable DAG
```json
{
  "hunt": "word-quest",
  "clues": {
    "1": { "deps": [], "model": "nemotron-120b" },
    "2": { "deps": ["1"], "model": "nemotron-120b" },
    "3": { "deps": ["2"], "model": "nemotron-120b" },
    "4": { "deps": ["3"], "model": "nemotron-120b" }
  }
}
```

### Conductor-Resolver DAG (flat format)
```json
{
  "deps": {
    "1": [],
    "2": ["1"],
    "3": ["2"],
    "4": ["3"]
  }
}
```

## Surface Notes
All clues run autonomously via NIM-direct hunter-loop. Cwd: `/home/yasaisama/SuperConci`. Each PROMPT.md follows treasure-mapmaker v3.1 slim format.

## Dead End Protocol
3 failures on same clue → STUCK.md surfaces to Tyler via /intel/log. Conductor babysitter logs lifecycle events.
