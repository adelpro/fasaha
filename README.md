# fasaha (فصاحة) — Arabic Fluency & Correction

Review and fix AI-generated or AI-translated Arabic so it reads as fluent, native
Modern Standard Arabic (MSA) instead of translated/calqued output.

Fasaha (فصاحة) means *eloquence and correctness of expression* in Arabic — text that
reads as if it was written by a native speaker, not translated.

Grounded in the QALB (Qatar Arabic Language Bank) annotation guidelines
(Zaghouani, Habash & Mohit, CMU-Qatar/Columbia, 2013) plus patterns specific to
LLM translation failures.

## What it fixes

- **Latin-script leakage** — English words left untranslated in technical/marketing copy
- **Sentence-structure calque** — Arabic that mirrors English word order and sentence boundaries
- **Word choice / terminology** — generic-but-wrong renderings instead of domain-standard terms
- **Morphology, agreement & syntax** — gender/number agreement, broken plurals, prepositions, articles
- **Punctuation, hamza & numbers** — Arabic punctuation marks, hamza wasl/qat' and medial seat, number rules
- **Dialectal leakage into MSA** — dialectal words slipping into formal Arabic

## How it works

Running `fasaha` = correctness pass (Sections 1-7 via the runnable checklist) →
register pass (`voice-profile.md`) → a report of what was flagged and corrected.

It ships **living reference files** that any agent updates over time:

- `references/checklist.md` — the runnable quality gate (every check + a defined output shape)
- `references/terminology.md` — accumulating glossary of standard Arabic renderings (web dev, e-commerce)
- `references/llm-failure-log.md` — accumulating log of real caught errors (bad → good → section)
- `references/voice-profile.md` — self-maintained register file (MSA vs Darija, formality, tone)
- `references/qalb-spelling-rules.md` — hamza, punctuation and number rules
- `references/mt-examples.md` — worked machine-translation correction examples
- `references/dialect-classification.md` — QALB's six-category dialect classification
- `references/sources.md` — the QALB source and attribution

## Install

```bash
npx skills add adelpro/fasaha
```

For Claude Code:

```bash
npx skills add adelpro/fasaha -a claude-code
```

## Usage triggers

- Translating INTO Arabic
- Writing original Arabic content
- Reviewing / correcting / proofreading existing Arabic
- Any Arabic quality check (e.g. "راجع لي هذا", "صحح العربية", "ترجم هذا للعربية")
- Proactively before outputting Arabic prose longer than 2-3 sentences

## License

[MIT](LICENSE). The skill condenses and adapts rules from the QALB Guidelines
v0.90 (Zaghouani, Habash & Mohit, CC-BY-licensed corpus); see `references/sources.md`
for full attribution.

## Author

[Adel Ben Yahia](https://github.com/adelpro)
