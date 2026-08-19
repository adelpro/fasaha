# Changelog

## 1.1.0 — 2026-08-19
- Added register profile (`references/voice-profile.md`) applied after the correctness pass
- Added runnable checklist, accumulating terminology glossary, and accumulating failure log
- Added explicit "write in Arabic" trigger (`اكتب بالعربية` / `اكتبلي بالعربية`)
- Resolved dialect negation mapping (`مش/موش` → `ليس` generally, `لم` only for past negation)
- Trimmed description under the agentskills.io 1024-char limit; added author/license/version frontmatter
- Restructured to a polyglot layout: Agent Plugins 1.0.0 (`plugin.json`) + Claude Code marketplace (`.claude-plugin/`) + skills.sh

## 1.0.0 — 2026-08-19
- Initial release: QALB-grounded Arabic correctness (Sections 1-7) with QALB spelling, worked MT examples, and dialect classification references
