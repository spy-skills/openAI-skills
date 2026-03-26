---
date: 2026-03-26
type: learning
task: oais-l2b
tags: [security, ownership, bus-factor, git-analysis, neo4j]
---

# security-ownership-map

## Danh gia (Score 1-10)

| Tieu chi | Score | Ghi chu |
|----------|-------|---------|
| Completeness | 10/10 | Scripts, queries, visualization, community detection |
| Usability | 7/10 | Nhieu CLI flags — can doc ky |
| Modularity | 9/10 | Python scripts reusable, output CSV/JSON portable |
| Safety & Reliability | 9/10 | Read-only git analysis, configurable filters |
| **Tong** | **9/10** | **Skill doc dao nhat — khong co tuong duong** |

## Uu diem

1. **Unique concept — khong co tuong duong:**
   - Bipartite graph: people <-> files tu git history
   - Bus factor computation per file
   - Sensitive code ownership (auth, crypto, secrets)
   - Co-change graph (Jaccard similarity)
   - Community detection (NetworkX)

2. **2 Python scripts:**
   - `run_ownership_map.py`: Build full ownership map
   - `query_ownership.py`: LLM-friendly JSON queries (bounded output)
   - `community_maintainers.py`: Monthly/quarterly maintainer tracking

3. **Output artifacts phong phu:**
   - `people.csv`, `files.csv`, `edges.csv` — Graph nodes + edges
   - `cochange_edges.csv` — File co-change relationships
   - `summary.json` — Security findings (orphaned code, hidden owners, hotspots)
   - `communities.json` — Auto-detected communities with maintainers
   - `*.graphml` — Optional GraphML for Gephi/Neo4j
   - `commits.jsonl` — Optional commit data

4. **Security queries built-in:**
   - Orphaned sensitive code (stale + low bus factor)
   - Hidden owners (concentrated control)
   - Bus factor hotspots
   - Auth/crypto files with bus factor <= 1
   - Co-change neighbors (ownership drift)

5. **Smart defaults:**
   - Merge commits excluded
   - Dependabot commits excluded
   - Glue files excluded from co-change (lockfiles, .github/*)
   - Override everything via CLI flags

6. **Neo4j export**: `references/neo4j-import.md` cho graph database visualization

## Nhuoc diem

1. **Requires networkx** — Python dependency
2. **CLI flags phuc tap** — Nhieu options (--since, --until, --identity, --date-field, etc.)
3. **Large repos** — `git log` co the cham tren repos lon

## Kha nang tich hop

### Truc tiep ap dung:
- **Bus factor analysis** → Apply cho bat ky repo nao de tim risk
- **Co-change graph** → Tim files thay doi cung nhau — gio architecture
- **Community detection** → Tu dong nhom files/people thanh clusters
- **LLM query helper pattern** → Scripts tra ve JSON bounded — khong load full graph vao context

### Ung dung:
- Onboarding: "Ai biet file nay tot nhat?"
- Risk assessment: "File nao se co van de neu nguoi X nghi viec?"
- Code review: "File nay thay doi thuong di kem file nao?"

## Ghi chu ky thuat

1. **Sensitivity rules**: Default flag auth/crypto/secret paths. Override via CSV config
2. **Timezone detection**: Tu commit offsets — `primary_tz_offset`, `primary_tz_minutes`
3. **Touch mode**: Default = 1 per commit. `--touch-mode file` = per-file touches
4. **Recency weighting**: `--weight recency --half-life-days 180`
5. **Stable maintainers**: `--min-share 0.1` — chi hien maintainers co >= 10% contributions
