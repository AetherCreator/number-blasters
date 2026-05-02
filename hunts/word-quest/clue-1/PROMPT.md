# Clue 1: Word Pack v1

## Objective
Generate a JSON word pack with 200+ entries for Word Quest, covering vocabulary from sight-word level (difficulty 1) through middle-school level (difficulty 10).

## Files to Read
- `src/NumberBlasters.jsx` (difficulty curve precedent)
- `src/games/story-quest/packs/PACK-FORMAT.md` (JSON pack pattern in this repo)

## Analysis Method
1. Build a list of 200 distinct words across 10 difficulty bands (~20 per band).
2. Difficulty 1–3: sight words a 5yo reader knows (cat, run, blue, jump, fast).
3. Difficulty 4–6: 2nd–3rd grade vocab (locomotive, brave, gigantic, whisper, journey).
4. Difficulty 7–10: 4th–8th grade vocab (perilous, mythical, contraption, expedition, articulate).
5. For each word: write a 1-sentence definition a child at that reading level can understand.
6. Include thematic tags where natural: trains, fantasy, space, animals, emotions.

## Output Format
Write to `src/games/word-quest/data/word-pack-v1.json`:
```json
{
  "version": 1,
  "generated": "2026-05-02",
  "words": [
    {"word": "quick", "definition": "moving fast or happening soon", "difficulty": 2, "tags": ["common"]},
    {"word": "locomotive", "definition": "a powerful engine that pulls a train", "difficulty": 5, "tags": ["trains"]}
  ]
}
```

## Pass Conditions
- File exists at `src/games/word-quest/data/word-pack-v1.json`
- Valid JSON (parses)
- `words` array length ≥ 200
- Every entry has `word`, `definition`, `difficulty` (integer 1–10)
- All 10 difficulty bands present (≥10 words at each level)
- GitHub push verified (commit SHA on origin/main)
