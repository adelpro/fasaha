# Changelog

## 1.3.0 — 2026-10-30

- Six new entries in the accumulating failure log, all caught reviewing real Arabic UI copy:
  passive + abstract nouns in a privacy claim (`تُرسَل … إلى خادمنا وحده`), «off by default» glued
  onto a state (`متوقّفة افتراضياً`), a dangling participle (`ولا عنوان شبكة محفوظ`), the answer
  clause of `إن` left as a bare present, the `X، لا Y` apposition, and an imperative standing in
  for a consequence (`امسح … فيذهب`)
- The register profile gains its first concrete profile (Tilawa app UI) and the rule that
  addresses the root cause rather than the symptom: compose from the Arabic intent, never
  translate a finished English sentence — a corrector can only grade the shape it is given
- Terminology: a privacy/telemetry block (analytics, anonymous, opt in/out, IP address, "we do not
  store") so the same terms stop being decided once per string

## 1.2.0 — 2026-10-08

- Wired the accumulating failure log into the process: step 1 reads `references/llm-failure-log.md`
  before the checklist, step 6 appends any genuinely new pattern (one entry per new pattern, never
  per run, never delete an entry)
- The log existed since 1.1.0 but nothing in the process ever invoked it; this closes that loop so
  a caught pattern is checked first on the next review
- Register instruction no longer stalls: apply the caller's own voice skill when one is loaded, and
  only ask which register when there is no such skill and the user has not stated a preference
- Version bumped in both manifests (`plugin.json` and `.claude-plugin/plugin.json`)

## 1.1.0 — 2026-08-19
- Added register profile (`references/voice-profile.md`) applied after the correctness pass
- Added runnable checklist, accumulating terminology glossary, and accumulating failure log
- Added explicit "write in Arabic" trigger (`اكتب بالعربية` / `اكتبلي بالعربية`)
- Resolved dialect negation mapping (`مش/موش` → `ليس` generally, `لم` only for past negation)
- Trimmed description under the agentskills.io 1024-char limit; added author/license/version frontmatter
- Restructured to a polyglot layout: Agent Plugins 1.0.0 (`plugin.json`) + Claude Code marketplace (`.claude-plugin/`) + skills.sh

## 1.0.0 — 2026-08-19
- Initial release: QALB-grounded Arabic correctness (Sections 1-7) with QALB spelling, worked MT examples, and dialect classification references
