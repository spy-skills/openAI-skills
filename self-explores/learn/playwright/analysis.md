---
date: 2026-03-26
type: learning
task: oais-l2b
tags: [playwright, browser-automation, wrapper-script, testing]
---

# playwright

## Danh gia (Score 1-10)

| Tieu chi | Score | Ghi chu |
|----------|-------|---------|
| Completeness | 8/10 | Core workflow + patterns + troubleshooting |
| Usability | 9/10 | Wrapper script pattern cuc ky tien dung |
| Modularity | 9/10 | Wrapper script reusable, CLI-first approach |
| Safety & Reliability | 8/10 | Guardrails section, snapshot-before-action pattern |
| **Tong** | **8.5/10** | **Wrapper script pattern + CLI-first automation** |

## Uu diem

1. **Wrapper script pattern:**
   - `scripts/playwright_cli.sh` — Wrap `npx --package @playwright/cli playwright-cli`
   - Chay duoc ma KHONG can global install
   - Pattern: `$PWCLI open`, `$PWCLI snapshot`, `$PWCLI click e15`
   - Portable: set CODEX_HOME 1 lan, dung everywhere

2. **"Snapshot -> Interact -> Snapshot" loop:**
   - Snapshot: lay stable element refs (e1, e2, e3...)
   - Interact: click/fill/type using refs
   - Re-snapshot: after navigation, DOM changes, modals
   - Simple, reliable, deterministic

3. **CLI-first approach:**
   - "Do not pivot to @playwright/test unless explicitly asked"
   - CLI commands > test framework
   - Automation > testing

4. **Guardrails:**
   - Always snapshot before referencing element ids
   - Re-snapshot when refs stale
   - Prefer explicit commands over eval/run-code
   - Use --headed for visual checks

5. **Session management:**
   - `--session marketing`, `--session checkout`
   - Isolate work across projects
   - `PLAYWRIGHT_CLI_SESSION` env var

6. **workflows.md reference:**
   - Standard interaction loop
   - Form submission
   - Data extraction
   - Debugging with traces
   - Multi-tab work
   - Configuration file

## Nhuoc diem

1. **Requires Node.js/npm** — Dependency khong nhe
2. **Element refs can go stale** — Can snapshot lai thuong xuyen
3. **Khong co visual comparison** — Chi screenshot, khong co pixel diff

## Kha nang tich hop

### Truc tiep ap dung:
- **Wrapper script pattern** → Wrap bat ky CLI nao de khong can global install
- **Snapshot-Interact-Snapshot loop** → Standard browser automation pattern
- **Session isolation** → Dung cho multi-project work
- **CLI-first over test framework** → Automation mindset

### Dang dung:
- Claude Code da co webapp-testing skill dung Playwright
- Ket hop voi develop-web-game skill

## Ghi chu ky thuat

1. **CODEX_HOME**: `${CODEX_HOME:-$HOME/.codex}` — default ~/.codex
2. **Skill path**: `$CODEX_HOME/skills/playwright/scripts/playwright_cli.sh`
3. **npx wrapper**: `npx --package @playwright/cli playwright-cli` — no global install needed
4. **Config**: `playwright-cli.json` in current directory
5. **Artifacts**: `output/playwright/` — keep contained
