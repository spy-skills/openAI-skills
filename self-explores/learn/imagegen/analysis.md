---
date: 2026-03-26
type: learning
task: oais-l2b
tags: [imagegen, openai-api, cli-pattern, prompt-engineering]
---

# imagegen

## Danh gia (Score 1-10)

| Tieu chi | Score | Ghi chu |
|----------|-------|---------|
| Completeness | 9/10 | Generate, edit, batch. Taxonomy 16 use cases |
| Usability | 9/10 | Decision tree, CLI recipes, prompt templates |
| Modularity | 8/10 | Bundled CLI reusable, OpenAI API dependent |
| Safety & Reliability | 8/10 | Dry-run mode, guardrails, never modify script |
| **Tong** | **8.5/10** | **Bundled CLI pattern mau muc** |

## Uu diem

1. **Bundled CLI pattern:**
   - `scripts/image_gen.py` — Single entry point cho tat ca operations
   - 3 commands: `generate`, `edit`, `generate-batch`
   - `--dry-run`: Test ma khong goi API
   - "Never modify scripts/image_gen.py" — treat as immutable tool

2. **Use-case taxonomy (16 slugs):**
   - Generate: photorealistic-natural, product-mockup, ui-mockup, infographic-diagram, logo-brand, illustration-story, stylized-concept, historical-scene
   - Edit: text-localization, identity-preserve, precise-object-edit, lighting-weather, background-extraction, style-transfer, compositing, sketch-to-render

3. **Prompt augmentation framework:**
   - Structured spec: use case, asset type, scene, subject, style, composition, lighting, constraints, avoid
   - "Augmentation vs invention" — chi add implicit details, KHONG invent new
   - Invariants for edits: "change only X; keep Y unchanged"

4. **Batch workflow:**
   - JSONL input: 1 job per line
   - `--concurrency 5` — parallel API calls
   - Temp files under `tmp/imagegen/` — cleanup after run

5. **5 reference files:**
   - `cli.md`: Full CLI reference
   - `image-api.md`: API parameters
   - `prompting.md`: Prompt engineering principles
   - `sample-prompts.md`: Copy-paste recipes
   - `codex-network.md`: Sandbox/network troubleshooting

## Nhuoc diem

1. **OpenAI API required** — OPENAI_API_KEY + network access
2. **gpt-image-1.5 specific** — Model-specific, may change
3. **Khong co local alternative** — Khong fallback to Stable Diffusion etc.

## Kha nang tich hop

### Pattern portable:
- **Bundled CLI pattern** → Wrap API calls vao 1 script, expose qua CLI flags
- **Taxonomy slugs** → Classify requests de chon dung workflow
- **Prompt augmentation** → Structured spec format cho bat ky AI generation
- **"Never modify the script"** → Immutable tool principle
- **Dry-run mode** → Test workflow ma khong call API

## Ghi chu ky thuat

1. **CODEX_HOME pattern**: `${CODEX_HOME:-$HOME/.codex}/skills/imagegen/scripts/image_gen.py`
2. **Default model**: gpt-image-1.5 (unless user asks for gpt-image-1-mini)
3. **Sizes**: 1024x1024, 1536x1024, 1024x1536, auto
4. **Transparent bg**: Requires output_format = png or webp
5. **Downscale**: `--downscale-max-dim 1024` — web-optimized copy
6. **Dependencies**: `uv pip install openai pillow`
