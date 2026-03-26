---
date: 2026-03-26
type: learning
task: oais-l2b
tags: [security, threat-model, stride, appsec]
---

# security-threat-model

## Danh gia (Score 1-10)

| Tieu chi | Score | Ghi chu |
|----------|-------|---------|
| Completeness | 9/10 | 8-step workflow cover full threat modeling lifecycle |
| Usability | 8/10 | Clear steps, risk prioritization guidance |
| Modularity | 8/10 | Repository-grounded — works on any codebase |
| Safety & Reliability | 9/10 | Evidence-based, validate with user, quality check |
| **Tong** | **8.5/10** | **AppSec-grade threat modeling workflow** |

## Uu diem

1. **8-step workflow chi tiet:**
   - Step 1: Scope + extract system model (components, data stores, integrations)
   - Step 2: Derive boundaries, assets, entry points
   - Step 3: Calibrate assets + attacker capabilities
   - Step 4: Enumerate threats as abuse paths
   - Step 5: Prioritize (likelihood x impact)
   - Step 6: Validate with user (1-3 targeted questions)
   - Step 7: Recommend mitigations
   - Step 8: Quality check before finalizing

2. **"Repository-grounded, not generic checklist":**
   - "Anchor every architectural claim to evidence in the repo"
   - "Keep assumptions explicit"
   - "Do not claim components without evidence"

3. **Attacker capability calibration:**
   - Realistic attacker capabilities based on exposure
   - "Explicitly note non-capabilities to avoid inflated severity"
   - Risk: High (pre-auth RCE, auth bypass) / Medium (targeted DoS) / Low (info leaks)

4. **User validation step (Step 6):**
   - Summarize key assumptions
   - Ask 1-3 targeted questions
   - PAUSE and WAIT for feedback
   - If user declines → state unresolved assumptions

5. **Quality check (Step 8):**
   - All entrypoints covered?
   - Each trust boundary in threats?
   - Runtime vs CI/dev separated?
   - User clarifications reflected?
   - Assumptions explicit?

6. **Output**: `<repo-name>-threat-model.md` — named after repo

## Nhuoc diem

1. **Manual process** — Khong co automation scripts
2. **Requires security expertise** — Agent can hieu AppSec de lam tot
3. **STRIDE implicit** — Khong explicitly mention STRIDE framework

## Kha nang tich hop

### Truc tiep ap dung:
- **"Repository-grounded" approach** → Moi analysis skill nen anchor to actual code
- **Validate-with-user step** → Pause + ask targeted questions truoc khi finalize
- **Quality check checklist** → Apply cho bat ky report/analysis output
- **Assumptions tracking** → Explicit assumptions section in every analysis

## Ghi chu ky thuat

1. **2 reference files**: `prompt-template.md` (output contract), `security-controls-and-assets.md` (optional)
2. **Output format**: Markdown threat model file
3. **Mitigation types**: authZ checks, input validation, schema enforcement, sandboxing, rate limits, secrets isolation, audit logging
4. **"Prefer specific implementation hints over generic advice"** — key principle
