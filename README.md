# AI Model Benchmark: Soccer Stars Game

Compare how different AI models handle the same coding prompt: build a single-file HTML5 game inspired by Miniclip's **Soccer Stars** (turn-based 2D carrom-style physics).

Each model gets the identical prompt from [`prompt.txt`](prompt.txt). Each output is saved as one self-contained HTML file. Open the file in a browser to play and judge it.

## Results

| Model | File |
|-------|------|
| Sonnet 5.0 | [`sonet 5.0.html`](<sonet 5.0.html>) |
| Sonnet 5.5 | [`sonnet 5.5.html`](<sonnet 5.5.html>) |
| Opus 5.5 | [`opus 5.5.html`](<opus 5.5.html>) |
| Argon 4 | [`argon 4.html`](<argon 4.html>) |

## The Prompt

Full text in [`prompt.txt`](prompt.txt). Summary of requirements:

- **Deliverable:** one `index.html` file with all CSS, HTML and vanilla JS. No external game or physics libraries.
- **Rendering:** HTML5 Canvas 2D, `requestAnimationFrame` loop, 800x500 pitch.
- **Entities:** 3 red player caps, 3 blue AI caps, 1 ball. Caps larger and heavier than ball.
- **Physics:** exponential friction, wall bounce (~0.85), elastic circle-circle collisions with overlap resolution, `isMoving` state.
- **Gameplay:** drag-and-shoot slingshot input (mouse and touch), goal detection, 1.5s goal pause, first to 2 goals wins.
- **UI:** score, turn indicator, "Reset Game" button, victory / game over modal.
- **AI:** waits 1000ms, picks best cap to hit the ball toward the player's goal, scales power by distance.
- **Code quality:** modular functions, no truncation, edge cases handled.

## How to Test

1. Clone the repo.
2. Open any `.html` file in a modern browser (Chrome, Firefox, Edge, Safari).
3. Play a full match against the AI.

```bash
git clone <repo-url>
cd benchmark
```

## Evaluation Checklist

Score each model on the same criteria:

- [ ] Runs as a single file, no console errors
- [ ] Pitch markings and recessed goal nets drawn correctly
- [ ] Caps and ball sizes, masses and colors match spec
- [ ] Friction and snap-to-zero work
- [ ] Wall and goalpost bounces look right
- [ ] Collisions conserve momentum, no overlap sticking
- [ ] Slingshot aim line and power bar shown while dragging
- [ ] Max drag distance caps launch force
- [ ] Input blocked while anything moves
- [ ] Turn order correct (Player -> AI -> Player)
- [ ] Goal detected only when ball fully crosses line
- [ ] "GOAL!" overlay, 1.5s pause, kick-off reset
- [ ] Win at 2 goals, modal shown, shots disabled until reset
- [ ] AI makes sensible shots after ~1s delay
- [ ] Touch events work on mobile
- [ ] Caps never leave the canvas

## Adding a New Model

1. Give the model the exact prompt from `prompt.txt`. No follow-up fixes.
2. Save the output as `<model name>.html`.
3. Add a row to the Results table.
4. Run the evaluation checklist.

## Notes

- Same prompt, one shot, no edits keeps the comparison fair.
- Results vary per run. Consider generating several samples per model.
