# Arabic Terminology Glossary (Accumulating)

A **living, self-maintained glossary** of standard Arabic renderings for technical and
e-commerce terms commonly used in web development, e-commerce, and marketing.

**Purpose:** the same English term maps to the same Arabic term across all projects, so
output stays consistent. Any agent updates this file when the user settles on a translation
or corrects one. Add a dated line to the update log at the bottom.

**How the agent uses it:** before writing/translating a technical or marketing term, check
here first. If the term is present, use exactly that rendering. If missing, pick the
domain-standard rendering, and add it here.

## Conventions

- Keep true identifiers in Latin script (API, WhatsApp, model/product names, library names).
- For common nouns with a standard Arabic rendering, prefer the standard term.
- Note the domain in brackets when a word has different senses: `run [institutional] → تُدار`.

## Web development

| English | Arabic | Notes |
|---|---|---|
| website | موقع إلكتروني / موقع ويب | |
| application / app | تطبيق | |
| frontend | الواجهة الأمامية | |
| backend | الواجهة الخلفية | |
| database | قاعدة البيانات | |
| server | خادم | |
| API | واجهة برمجة التطبيقات | keep `API` in Latin if preferred |
| framework | إطار العمل | |
| library | مكتبة | |
| repository | المستودع | |
| deployment / deploy | النشر | |
| machine learning | التعلم الآلي | |
| artificial intelligence | الذكاء الاصطناعي | |
| code / codebase | الشيفرة (البرمجية) | `الكود` is the common informal/regional form — see Register notes |
| error / bug | خطأ / خلل | |
| test | اختبار | |
| console [operator UI] | لوحة التحكم | `اللوحة` after the first mention; never `لوحة القيادة` |

## E-commerce & marketing

| English | Arabic | Notes |
|---|---|---|
| e-commerce | التجارة الإلكترونية | |
| product | المنتج | |
| cart | سلة المشتريات | |
| checkout | إتمام الدفع | |
| payment | الدفع | |
| shipping / delivery | الشحن / التوصيل | pick one and stay consistent |
| order | الطلب | |
| customer | العميل | `الزبون` for casual/regional register |
| price | السعر | |
| discount | الخصم | |
| advertising / ads | الإعلانات | |
| marketing | التسويق | |
| sales funnel | مسار المبيعات | |
| lead | عميل محتمل | |
| conversion | التحويل | |
| return on investment (ROI) | العائد على الاستثمار | keep `ROI` in Latin if preferred |
| WhatsApp | واتساب | keep `WhatsApp` in Latin in ads |

## Privacy & telemetry (settled 2026-10-30, open-tilawa)

| English | Arabic | Notes |
|---|---|---|
| analytics / usage statistics | إحصاءات الاستخدام | Google's own Arabic term. `التحليلات` is Apple's; pick one per product |
| telemetry | — | do not transliterate; name the thing (`إحصاءات التشغيل`) |
| anonymous | مجهولة الهوية / بلا اسم | prefer a verb clause: `لا نعرف من أنت` |
| opt in / opt out | تشغيلها / إيقافها | the toggle acts on the *feature*, not on "consent" |
| off by default | معطّلة حتى تشغّلها | avoid `متوقّفة افتراضياً` — a calque of "off by default" |
| IP address | عنوان الإنترنت | never `عنوان الشبكة` — that reads as the local network address |
| we do not store | لا نحتفظ بـ | use only when true; `لا يُرسَل` is false if the request carries it |

## Register notes (Darija / formal)

- For low-literacy Algerian e-commerce marketing, prefer Darija-friendly terms
  (`الزبون`, `التوصيل`) over formal MSA — see `voice-profile.md`.
- When the audience is technical, prefer the MSA standard terms above.

---

## Update log

- 2026-08-19 — glossary created with starter set (web dev + e-commerce). Extend as terms get settled.
- 2026-08-19 — resolved: `code/codebase` canonical = `الشيفرة (البرمجية)`; `الكود` noted as informal/regional.
  (Change here if a preferred form is stated later.)
- 2026-10-29 — `console` (operator UI) settled as `لوحة التحكم`, short form `اللوحة`; project-wide choice
  in open-tilawa/reviews, replacing "dashboard" in English copy.
