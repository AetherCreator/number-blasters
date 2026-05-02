# TREASURE: Word Quest — Hunt Complete

## Final Integration Check (run after Clue 4)

### Build
- [ ] `npm run build` exits 0 with no warnings
- [ ] No TypeScript errors

### Navigation
- [ ] Open dev server, land on Galaxy Hub
- [ ] Word Quest planet visible, no longer locked
- [ ] Tap Word Quest → arrives at WordQuest title screen

### Game Loop
- [ ] Tap Start → game begins, prompt visible at top, 4 word-asteroids falling
- [ ] Tap correct → score increases, combo, correct sound
- [ ] Tap wrong → life lost, wrong sound
- [ ] 3 lives lost → game over screen with final score
- [ ] 60s timer → ends round even with lives remaining

### Adaptive Difficulty
- [ ] Play 10 answers correct → console logs difficulty bump
- [ ] Play 10 answers wrong → console logs difficulty drop
- [ ] Difficulty stays clamped to 1–10

### Word Quality
- [ ] Easier words at lower difficulty are kid-readable
- [ ] Harder words at higher difficulty are middle-school appropriate
- [ ] Definitions are clear and grade-appropriate

### The Conci Test
- [ ] Hand iPhone to Conci → he plays unprompted
- [ ] He gets at least one round above his starting difficulty
- [ ] He wants to play a second round
