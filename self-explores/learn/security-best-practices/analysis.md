---
date: 2026-03-26
type: learning
task: oais-l2b
tags: [security, best-practices, progressive-disclosure, code-review]
---

# security-best-practices

## Danh gia (Score 1-10)

| Tieu chi | Score | Ghi chu |
|----------|-------|---------|
| Completeness | 9/10 | 10 reference files cover Python/JS/TS/Go voi 9 frameworks |
| Usability | 9/10 | 3 operating modes ro rang, workflow decision tree |
| Modularity | 10/10 | **Mau muc Progressive Disclosure** — SKILL.md nhe, refs nang |
| Safety & Reliability | 10/10 | MUST/SHOULD/MAY format, evidence-based findings |
| **Tong** | **9.5/10** | **Skill chat luong cao nhat trong repo** |

## Uu diem

1. **Progressive Disclosure mau muc:**
   - SKILL.md (86L): Chi workflow + decision tree
   - references/ (10 files): Chi tiet theo language-framework-stack
   - File naming: `{language}-{framework}-{stack}-security.md`
   - Agent chi load reference phu hop voi project hien tai

2. **3 Operating Modes:**
   - **Generation mode** (default): Viet code secure-by-default
   - **Passive review** (always on): Tu dong phat hien vulnerabilities khi edit code
   - **Active audit** (explicit): Full security scan + report

3. **Reference file quality cuc cao (FastAPI example):**
   - Normative requirements: MUST/SHOULD/MAY format
   - Audit rules: bad patterns + detection + fix
   - 10-point audit order (entrypoints → config → auth → input → injection → SSRF)
   - Required finding format: Rule ID, Severity, Location, Evidence, Impact, Fix, Mitigation
   - Cover: CORS, CSRF, TLS, HSTS, cookies, XSS, SSTI, file handling, WebSocket

4. **Override mechanism:**
   - Project-specific overrides duoc ton trong
   - "Don't fight with the user" — report but don't block
   - Suggest documentation for overrides

5. **Report format:**
   - Executive summary
   - Severity sections (Critical/High/Medium/Low)
   - Numeric IDs cho findings
   - Impact statements cho critical findings
   - Line numbers required

6. **Practical wisdom:**
   - TLS caution: "Be careful about not reporting lack of TLS as a security issue"
   - HSTS warning: "dangerous to use without full understanding"
   - Secure cookies: Only set if TLS enabled, else breaks app
   - "Avoid breaking the user's project" — security fixes must not cause regressions

## Nhuoc diem

1. **Chi 3 languages** — Python, JS/TS, Go. Thieu Rust, Java, C/C++
2. **Thieu automated scanning** — Chi co guidance, khong co scripts
3. **Reference files co the outdated** — Framework versions fixed (FastAPI 0.128.x)

## Kha nang tich hop vao he thong hien tai

### Truc tiep ap dung:
- **Reference organization pattern** → `{language}-{framework}-{stack}-security.md` naming convention
- **3 Operating Modes** → Moi skill nen co: default mode + passive mode + explicit mode
- **MUST/SHOULD/MAY format** → Dung cho bat ky reference nao can normative requirements
- **Finding format** → Standard cho moi security-related skill output
- **Override mechanism** → Moi skill nen respect project-specific overrides

### Can dieu chinh:
- Them references cho Rust, Java (lang pho bien)
- Them scripts de auto-detect language/framework
- Update framework versions khi co breaking changes

## Ghi chu ky thuat

1. **Decision tree**: Inspect repo → identify languages/frameworks → load matching refs → operate in mode
2. **Filename convention**: `python-fastapi-web-server-security.md`, `javascript-general-web-frontend-security.md`
3. **General file**: `{language}-general-{stack}-security.md` — agnostic to framework
4. **Web apps**: MUST check BOTH frontend AND backend references
5. **Report output**: `security_best_practices_report.md` hoac user-specified location
6. **Fix workflow**: Single finding at a time, clear comments, consider regressions, follow commit flow
