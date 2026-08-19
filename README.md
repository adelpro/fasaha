# fasaha (فصاحة) — Arabic Fluency & Correction

Review and fix AI-generated or AI-translated Arabic so it reads as fluent, native
Modern Standard Arabic (MSA) instead of translated/calqued output.

Fasaha (فصاحة) means *eloquence and correctness of expression* in Arabic — text that
reads as if it was written by a native speaker, not translated.

Grounded in the QALB (Qatar Arabic Language Bank) annotation guidelines
(Zaghouani, Habash & Mohit, CMU-Qatar/Columbia, 2013) plus patterns specific to
LLM translation failures.

## Direct reference

- **Repository:** https://github.com/adelpro/fasaha
- **Raw SKILL.md:** https://raw.githubusercontent.com/adelpro/fasaha/main/skills/fasaha/SKILL.md
- **Install (copy-paste):** `npx skills add adelpro/fasaha`

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

Any agent via skills.sh:

```bash
npx skills add adelpro/fasaha
```

Claude Code (skills.sh route):

```bash
npx skills add adelpro/fasaha -a claude-code
```

Claude Code (marketplace route):

```bash
claude plugin marketplace add github.com/adelpro/fasaha
claude plugin install fasaha@adelpro-fasaha
```

Agent Plugins 1.0.0 bundle (`plugin.json` at repo root) — loadable by compatible clients
from Amazon, Cursor, Microsoft, OpenAI (Codex), and Vercel ecosystems.

## Usage triggers

- Translating INTO Arabic
- Writing original Arabic content
- Reviewing / correcting / proofreading existing Arabic
- Any Arabic quality check (e.g. "راجع لي هذا", "صحح العربية", "ترجم هذا للعربية")
- Proactively before outputting Arabic prose longer than 2-3 sentences

## Sources & QALB attribution

Fasaha is grounded in the Qatar Arabic Language Bank (QALB) annotation guidelines —
the closest published standard for correcting AI/MT-generated Arabic. The rule sets,
worked correction examples, and dialect classification in `references/` are condensed
and adapted from this source:

- **QALB Guidelines v0.90 (PDF):** http://nlp.qatar.cmu.edu/qalb/QALB-guidelines_0.90.pdf
- **QALB project page:** http://nlp.qatar.cmu.edu/qalb/
- **Authors:** Wajdi Zaghouani, Nizar Habash, Behrang Mohit — Carnegie Mellon University
  Qatar & Columbia University (2013)
- **Corpus:** 2 million words of Arabic (native, non-native, and machine-translation output)
  manually corrected by human annotators

Sections 5, 6 and the dialect/spelling references map directly to QALB; Section 7 documents
where the 2013 guidelines do not predict modern LLM failure modes.

## License

[MIT](LICENSE). The skill condenses and adapts rules from the QALB Guidelines
v0.90 (Zaghouani, Habash & Mohit). See [Sources & QALB attribution](#sources--qalb-attribution)
and `references/sources.md` for full attribution.

## Author

[Adel Ben Yahia](https://github.com/adelpro)
