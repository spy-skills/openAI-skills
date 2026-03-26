---
date: 2026-03-26
type: learning
task: oais-l2b
tags: [deployment, render, blueprint, codebase-analysis]
---

# render-deploy

## Danh gia (Score 1-10)

| Tieu chi | Score | Ghi chu |
|----------|-------|---------|
| Completeness | 9/10 | 479L SKILL.md + 10 reference files cover moi scenario |
| Usability | 9/10 | Happy path + decision tree + troubleshooting |
| Modularity | 8/10 | Render-specific nhung pattern portable |
| Safety & Reliability | 8/10 | Blueprint validation, post-deploy checks |
| **Tong** | **8.5/10** | **Skill sau nhat, pattern "analyze -> generate -> deploy"** |

## Uu diem

1. **"Analyze codebase -> Generate config -> Deploy" pattern:**
   - Step 1: Analyze codebase (detect language, framework, dependencies)
   - Step 2: Generate render.yaml Blueprint
   - Step 3: Validate configuration
   - Step 4: Commit and push
   - Step 5: Generate deeplink (Dashboard URL)
   - Step 6: Guide user through Dashboard
   - Step 7: Verify deployment

2. **10 reference files cuc ky to chuc:**
   - `codebase-analysis.md` — How to detect project type
   - `blueprint-spec.md` — render.yaml specification
   - `service-types.md` — Web Service, Static Site, Worker, Cron Job, etc
   - `runtimes.md` — Docker, Node, Python, Go, Rust, etc
   - `configuration-guide.md` — Environment variables, disk, scaling
   - `deployment-details.md` — Git-backed vs Docker image
   - `direct-creation.md` — Alternative to Blueprint
   - `post-deploy-checks.md` — Health checks, endpoint testing
   - `troubleshooting-basics.md` — Common errors
   - `error-patterns.md` — Error -> cause -> fix mapping

3. **Decision tree:**
   - Blueprint (complex: multi-service, databases, cron) vs Direct Creation (simple: single service)
   - Git-backed vs Docker image

4. **Deeplink generation** — Tao Dashboard URL de user click deploy truc tiep

## Nhuoc diem

1. **Render-specific** — Chi dung cho Render platform
2. **479L SKILL.md** — Gan limit 500L, nen split them
3. **Khong co script** — Tat ca la instructions, khong co CLI tool

## Kha nang tich hop

### Pattern portable:
- **"Analyze -> Generate -> Deploy"** → Apply cho bat ky deployment skill
- **Reference organization** → 10 files tach theo concern (analysis, spec, types, runtime, config, troubleshoot)
- **Error patterns mapping** → Error -> Cause -> Fix table format
- **Deeplink pattern** → Generate actionable URL for user

## Ghi chu ky thuat

1. **Blueprint = render.yaml** — Declarative infrastructure-as-code
2. **2 deployment methods**: Blueprint (recommended, multi-service) vs Direct Creation (quick, single)
3. **Post-deploy verification**: Health endpoint check + error log review
4. **MCP support**: Render co MCP server cho Cursor/Claude Code/Codex
