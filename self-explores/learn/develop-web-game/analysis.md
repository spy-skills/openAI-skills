---
date: 2026-03-26
type: learning
task: oais-l2b
tags: [game-dev, playwright, testing-loop, web-game]
---

# develop-web-game

## Danh gia (Score 1-10)

| Tieu chi | Score | Ghi chu |
|----------|-------|---------|
| Completeness | 8/10 | Full dev loop: implement -> test -> screenshot -> review -> iterate |
| Usability | 8/10 | Clear workflow, checklist, artifact review |
| Modularity | 7/10 | Web game specific, nhung testing loop pattern portable |
| Safety & Reliability | 8/10 | Deterministic time stepping, progress tracking |
| **Tong** | **8/10** | **Testing loop pattern sang tao nhat** |

## Uu diem

1. **"Implement -> Act -> Pause -> Observe -> Adjust" loop:**
   - Pick goal → implement small → run Playwright test → inspect screenshots → fix → repeat
   - Tight feedback loop, small deltas
   - "Change one variable at a time"

2. **Deterministic time stepping:**
   - `window.advanceTime(ms)` hook — game loop controllable
   - Playwright client advances frames deterministically
   - No flaky timing-dependent tests

3. **`render_game_to_text()` pattern:**
   - Expose game state as JSON: mode, player pos, entities, score
   - "Text state should include enough info to play without visuals"
   - Dual validation: visual (screenshots) + semantic (JSON state)

4. **Progress tracking:**
   - `progress.md` file — persistent across agent sessions
   - "Original prompt:" at top — preserved across continuations
   - TODOs and suggestions for next agent
   - Pattern giong /viec worklog!

5. **Test Checklist:**
   - Movement/interaction inputs
   - Win/lose transitions
   - Score/health changes
   - Boundary conditions (collisions, walls, edges)
   - Menu/pause/start flow
   - Special actions (powerups, combos)

6. **Core Game Guidelines:**
   - Single canvas, centered
   - Minimal on-screen text
   - Background on canvas (not CSS)
   - Fullscreen toggle (f key)

7. **Action payloads (JSON):**
   - buttons, frames, mouse_x, mouse_y per step
   - Deterministic input sequence
   - Reference file: `action_payloads.json`

## Nhuoc diem

1. **Web games only** — HTML/JS canvas games
2. **Requires Playwright** — Node.js dependency
3. **Custom client script** — `web_game_playwright_client.js` specific

## Kha nang tich hop

### Pattern portable:
- **"Implement -> Test -> Screenshot -> Review" loop** → Apply cho bat ky UI development
- **`render_to_text()` pattern** → Expose app state as JSON cho automated validation
- **Deterministic time stepping** → Controllable execution cho testing
- **progress.md pattern** → Multi-agent handoff — giong /viec worklog
- **Dual validation** → Visual (screenshot) + Semantic (JSON state)
- **"Be exhaustive in testing controls"** → Comprehensive test mindset

## Ghi chu ky thuat

1. **Playwright client**: `web_game_playwright_client.js` — action loop + screenshot + console errors
2. **Action format**: JSON with steps array, each step has buttons + frames + mouse pos
3. **advanceTime**: `window.advanceTime(ms)` — step N frames at 60fps
4. **Screenshots**: Capture after each action burst — source of truth
5. **Console errors**: Fix first new error before continuing
6. **Reset between scenarios**: Avoid cross-test state contamination
