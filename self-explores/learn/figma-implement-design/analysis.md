---
date: 2026-03-26
type: learning
task: oais-l2b
tags: [figma, design-to-code, mcp, ui-implementation]
---

# figma-implement-design

## Danh gia (Score 1-10)

| Tieu chi | Score | Ghi chu |
|----------|-------|---------|
| Completeness | 9/10 | 7-step workflow day du tu setup MCP den validate |
| Usability | 8/10 | Clear workflow, co examples (Button, Dashboard) |
| Modularity | 7/10 | Phu thuoc Figma MCP server — khong dung standalone |
| Safety & Reliability | 8/10 | Incremental validation, document deviations |
| **Tong** | **8/10** | **Design-to-code workflow hoan chinh nhat** |

## Uu diem

1. **7-step workflow cuc ky chi tiet:**
   - Step 1: Setup Figma MCP (if needed)
   - Step 2: Get Node ID (tu URL hoac desktop app)
   - Step 3: Fetch Design Context (get_node with plugin_data)
   - Step 4: Capture Visual Reference (screenshot for validation)
   - Step 5: Download Required Assets (images, icons, SVGs)
   - Step 6: Translate to Project Conventions (the core step)
   - Step 7: Validate Against Figma (compare code vs design)

2. **"1:1 visual fidelity" goal** — Khong phai "close enough", ma pixel-perfect

3. **MCP integration pattern** — Dung Figma MCP tools:
   - `get_node`: lay design context, properties, styles
   - `screenshot`: capture visual reference
   - `download_asset`: tai images, icons

4. **Translation rules** — Step 6 co rules cu the:
   - Component organization based on Figma layers
   - Design system integration (tokens, variables)
   - Code quality: semantic HTML, accessible, responsive

5. **Common Issues section** — Troubleshooting:
   - Truncated output → fetch child nodes separately
   - Visual mismatches → re-validate with screenshots
   - Token differences → check Figma Variables

## Nhuoc diem

1. **Requires Figma MCP server** — Khong dung duoc neu khong co Figma account + MCP setup
2. **Khong co reference files** — Tat ca 264L trong SKILL.md body (gan limit 500L)
3. **Thieu automated validation** — Validate bang mat (compare screenshots), khong co tool
4. **Figma-specific** — Khong apply cho Sketch, Adobe XD, hay design tools khac

## Kha nang tich hop vao he thong hien tai

### Truc tiep ap dung:
- **Workflow pattern** → Apply cho bat ky design-to-code skill: fetch -> capture -> translate -> validate
- **MCP integration** → Pattern ket noi external design tools qua MCP
- **"Incremental validation"** → Validate sau moi buoc, khong doi den cuoi

### Can dieu chinh:
- Figma MCP → Can setup Figma MCP server rieng (hoac dung Figma REST API)
- Claude Code khong co screenshot compare built-in → Can them Playwright skill

## Ghi chu ky thuat

1. **Node ID format**: `123:456` (tu Figma URL hoac Inspect panel)
2. **get_node returns**: layout, styles, text content, component properties, auto-layout, constraints
3. **screenshot**: PNG capture tai thoi diem fetch — dung lam "truth" de validate
4. **Asset download**: images, icons rieng tu files — khong embed base64
5. **Design tokens**: Map Figma Variables → CSS custom properties hoac theme tokens
