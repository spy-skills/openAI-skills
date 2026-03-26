---
date: 2026-03-26
type: learning
task: oais-l2b
tags: [deployment, cloudflare, workers, decision-tree]
---

# cloudflare-deploy

## Danh gia (Score 1-10)

| Tieu chi | Score | Ghi chu |
|----------|-------|---------|
| Completeness | 10/10 | 307 reference files cover 40+ Cloudflare products |
| Usability | 8/10 | Decision trees cho 6+ scenarios |
| Modularity | 7/10 | Cloudflare-specific, nhung decision tree pattern portable |
| Safety & Reliability | 8/10 | Authentication check, wrangler CLI |
| **Tong** | **8/10** | **Kho bau reference, decision tree pattern** |

## Uu diem

1. **307 reference files** — Lon nhat trong repo. Cover:
   - Workers, Pages, Durable Objects, Workflows, Containers
   - KV, D1, R2, Queues, Vectorize, Secrets
   - Workers AI, AI Gateway, Agents SDK
   - Tunnel, Spectrum, TURN, Smart Placement
   - WAF, DDoS, Bot Management, mTLS
   - Images, Stream, Calls

2. **6+ Decision Trees:**
   - "I need to run code" → Workers/Pages/Durable Objects/Workflows/Containers
   - "I need to store data" → KV/D1/R2/Queues/Vectorize/Secrets
   - "I need AI/ML" → Workers AI/Vectorize/Agents SDK/AI Gateway
   - "I need networking" → Tunnel/Spectrum/TURN/Smart Placement
   - Security → WAF/DDoS/Bot Management/mTLS
   - Media → Images/Stream/Calls

3. **Product Index table** — 40+ products voi reference directory links

4. **Auth flow**: `npx wrangler whoami` check truoc moi thao tac

## Nhuoc diem

1. **Cloudflare-specific** — 100% platform-specific
2. **307 files co the overwhelming** — Can to chuc tot hon (da co Product Index)
3. **SKILL.md 224L** — Chu yeu la decision trees, it workflow chi tiet

## Kha nang tich hop

### Pattern portable:
- **Decision Tree pattern** → "I need X" → product recommendation. Apply cho bat ky multi-product ecosystem
- **Product Index** → Table mapping product → reference file. Giup agent navigate
- **Reference organization at scale** → 307 files van manageable nho naming + index

## Ghi chu ky thuat

1. **wrangler CLI** — Primary tool: `npx wrangler`
2. **Decision trees** la core — SKILL.md giup agent CHON dung product, refs day chi tiet
3. **Pattern**: SKILL.md = navigation layer, references/ = implementation details
