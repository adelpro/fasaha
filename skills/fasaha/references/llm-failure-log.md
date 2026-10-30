# LLM Arabic Failure Log (Accumulating)

A **living log** of real Arabic errors caught by fasaha. Each entry records a case where
AI output was wrong, what correct Arabic looks like, and which fasaha section caught it.

**Purpose:** builds a growing corpus of actual failure patterns so the skill improves over
time and so similar errors are caught faster. Any agent appends an entry when it catches a new
pattern. Do not delete entries — add to the log.

## Entry schema

```
## YYYY-MM-DD — <short title>

- source (EN): <original English where applicable>
- bad (AI output): <the wrong Arabic>
- good (corrected): <the corrected Arabic>
- section: <1 Latin leakage | 2 calque | 3 word choice | 4 morphology/agreement |
           5 punctuation/hamza/numbers | 6 dialect > MSA | 7 LLM-specific gap | R register>
- note: <brief why it failed / the fix>
```

## Entries

## 2026-08-19 — RESOLVED: dialect negation mapping (was مش/موش → لم)

- source (EN): n/a (MSA target)
- bad (AI output): `مش`/`موش` → `لم` (from original reference)
- good (corrected): `مش`/`موش` → `ليس` generally; `لم` only when negating a past action
  (e.g. `هو مش طويل` → `ليس طويلاً`; `هو مش راح` → `لم يذهب`).
- section: 6
- note: Fixed in `dialect-classification.md` 5.6.5 and SKILL.md Section 6. Don't blanket-replace
  with `لم`; match the mapping to the predicate.

## 2026-10-29 — abstract English nouns calqued into Arabic plan/UI prose

- source (EN): "push the missing releases to the fleet", "shared primitives", "commit it on its own"
- bad (AI output): `انشر الناقص على الأسطول`، `الأصليّات المشتركة`، `يُلتزم وحده`
- good (corrected): `أضف الناقص إلى كل الخوادم`، `المكوّنات المشتركة`، `يُحفظ في commit مستقل`
- section: 3 word choice, 2 calque
- note: Group nouns borrowed from English product-speak (`fleet`, `primitives`) have no Arabic
  life of their own; name the actual objects (`كل الخوادم`, `المكوّنات`). And `يُلتزم` as a verb
  for git commit is a double calque (meaning + Arabicised jargon): keep `commit` as an
  identifier or say `يُحفظ في commit`.

## 2026-10-29 — Latin brand name split across an Arabic line break

- source (EN): "Self-hostable infrastructure for the Open Tilawa WebTorrent stack"
- bad (AI output): «… لمنظومة Open» / «Tilawa على WebTorrent» — the product name wrapped between its
  two words, so the headline reads as two unrelated fragments.
- good (corrected): «… لمنظومة <bdi style="white-space:nowrap">Open Tilawa</bdi> على WebTorrent»
- section: 5 punctuation/hamza/numbers (bidi and line breaking)
- note: An embedded Latin run is a bidi island. Without isolation and `nowrap`, the browser may
  break inside the name and reorder what is left across the line. Wrap every Latin product name in
  `<bdi>` with `white-space: nowrap`; keep the surrounding Arabic as the only breaking context.

## 2026-10-29 — infrastructure jargon carried into a public banner

- source (EN): "A peer-to-peer Quran recitation player that streams audio from WebTorrent peers, with
  the operator's own node as the HTTP safety net."
- bad (AI output): «مشغّل تلاوات القرآن الكريم يبثّ الصوت من أقران WebTorrent ندًّا بندًّا، وتكون
  عقدتك أنت شبكةَ الأمان عبر HTTP.»
- good (corrected): «مشغّل تلاوات القرآن الكريم يبثّ الصوت مباشرةً بين المستمعين عبر WebTorrent،
  وخادمك بديلٌ جاهزٌ إن تعذّر ذلك.»
- section: 3 word choice, R register
- note: Correct Arabic, wrong audience. `عقدة` (node), `أقران` (peers) and `HTTP` are the operator's
  vocabulary, not a listener's; a banner needs the effect (`مباشرةً بين المستمعين`, `بديلٌ جاهز`).
  Keep the jargon in docs and error messages, translate the benefit in public copy. Faithfulness is
  kept at the level of the claim, not the vocabulary.

## 2026-10-30 — privacy copy: passive + abstract nouns read as translation

- source (EN): "Recitation names and playback outcomes are sent to our server alone, with no identifier."
- bad (AI output): «تُرسَل أسماء التلاوات وحالة التشغيل إلى خادمنا وحده، بلا معرّف يدلّ عليك.»
- good (corrected): «لا يصل إلى خادمنا إلا اسم التلاوة وهل عمل التشغيل، من دون أن نعرف من أنت.»
- section: 2 calque, 3 word choice
- note: Three English habits survived: the passive (`تُرسَل`), the compound abstract noun
  (`حالة التشغيل` = "playback outcomes"), and the "alone/only" adverbial tacked on the end
  (`وحده`). Arabic restricts with a negated verb + `إلا`, and prefers a clause (`هل عمل التشغيل`)
  to a nominal compound. Grammar was perfect; the sentence shape was English.

## 2026-10-30 — "off by default" glued onto a state

- source (EN): "Optional, and off by default."
- bad (AI output): «اختيارية ومتوقّفة افتراضياً»
- good (corrected): «متروكة لك: معطّلة حتى تشغّلها»
- section: 3 word choice, 2 calque
- note: `افتراضياً` is a calque of "by default" that Arabic UI rarely needs, and `متوقّفة` describes
  a machine that stopped, not a feature that is off. Name the state in the reader's terms
  (`معطّلة حتى تشغّلها`) and the choice belongs to them (`متروكة لك`).

## 2026-10-30 — "and no stored IP" rendered as a bare participle

- source (EN): "…with no identifier and no stored IP address."
- bad (AI output): «بلا معرّف يدلّ عليك، ولا عنوان شبكة محفوظ.»
- good (corrected): «من دون أن نعرف من أنت، ولا نحتفظ بعنوان الإنترنت الخاص بك.»
- section: 2 calque, 3 word choice, 4 morphology
- note: `ولا عنوان شبكة محفوظ` is an English absolute construction with the participle trailing
  ("and no stored address") — it has no verb and no predicate in Arabic, so it dangles. Rebuild it
  as a clause with a subject. Also `عنوان الشبكة` means the local network address; an IP is
  `عنوان الإنترنت`.

## 2026-10-30 — the answer clause of «إن» left as a bare present

- source (EN): "If you turn this on, we know which reciter and which surah."
- bad (AI output): «إن شغّلتها، نعرف أيّ قارئ وأيّ سورة.»
- good (corrected): «إن شغّلتها، عرفنا القارئ والسورة.»
- section: 4 morphology/syntax, 2 calque
- note: Two faults in one clause. The answer to `إن` must be jussive or take `فـ`, not a bare
  present indicative; and `أيّ` opens a question that is never closed (`تستمع إليه` is missing),
  so the sentence stops where Arabic expects the rest. A completed past (`عرفنا`) satisfies both
  and matches the app's register.

## 2026-10-30 — «X، لا Y» apposition

- source (EN): "Its purpose is fixing breakage, not following you."
- bad (AI output): «الغرض إصلاح ما يتعطّل، لا متابعتك.»
- good (corrected): «ليس المقصود تتبّعك، بل معرفة ما ينكسر.»
- section: 2 calque
- note: A bare `لا` + noun after a comma is the English "X, not Y". Arabic contrasts with
  `ليس … بل`, with `ما … إلا`, or with a negated verb. This is the sentence a native reader
  trips on even when they cannot name the rule, and it is the strongest "translated" tell in a
  paragraph of otherwise correct Arabic.

## 2026-10-30 — imperative standing in for a consequence

- source (EN): "Clear site data and it is gone with it."
- bad (AI output): «امسح بيانات الموقع فيذهب معها.»
- good (corrected): «يبقى حتى تمسح بيانات الموقع، فإذا مسحتها ذهب.»
- section: 2 calque, R register
- note: The English clause joins an action to its result with «and», which in Arabic reads as an
  instruction to the reader. When the point is *when the data disappears*, not *what the reader
  must do*, state the condition (`حتى تمسح` / `إذا مسحتها`) and let the verb fall where the
  consequence falls.

[Add new entries above this line when a fresh error is caught.]

## 2026-10-28 — fragment as a lede + "row" leaking into UI copy

- source (EN): "Nodes that distribute the torrents. The dashboard keeps their status and proxies torrent operations with the credentials stored on each row."
- bad (AI output): `الخوادم التي توزّع ملفات التورنت. تحفظ اللوحة حالتها وتنفّذ عمليات التورنت عبر بيانات الاعتماد المخزّنة في كل صف.`
- good (corrected): `خوادم التوزيع هي التي تنشر ملفات التورنت. تتابع اللوحة حالة كل خادم وتنفّذ عليه عمليات التورنت ببيانات الاعتماد المخزّنة له.`
- section: 2 calque, 3 word choice
- note: Three faults at once. (1) The first "sentence" is a bare relative phrase with no predicate — a noun fragment copied from English; a lede needs a complete sentence (`هي التي تنشر`). (2) `تحفظ حالة` renders "keeps the status" literally; for ongoing tracking the verb is `تتابع`/`ترصد`, whereas `تحفظ` means to preserve. (3) `في كل صف` describes the database row, not the operator's mental model — say `المخزّنة له` (stored for it). Also `عبر` is a translationese instrumental; use the plain `بـ`.
