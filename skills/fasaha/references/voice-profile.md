# Arabic Voice & Register Profile (Fasaha)

A **generic, self-maintained** register profile for Arabic writing. This file is NOT
tied to a specific author or external voice skill. It is a living template the agent
updates whenever the user states a tone/register preference or corrects an output.

Load it with fasaha: `fasaha` makes the Arabic correct and native-sounding (the
structural pass), then apply the matching register profile below for tone, formality,
and register choices on top. If no profile fits, ask which register the user wants.

## Status

- filled: no
- profiles: 0
- source: agent-maintained (self-service)
- updated: 2026-08-19

## How to use this file

1. Before writing Arabic, find the profile whose `scope` matches the task (app UI,
   docs/README, marketing, social post, formal letter, etc.).
2. Apply its `language`, `formality`, `tone`, `preferences`, and `never` list.
3. If no existing profile matches, run the closest one as a base, then ask the user
   once for the missing register choices.
4. When the user states a preference or corrects you:
   - update the matching profile (edit the values), or
   - add a NEW profile (one per distinct register), and
   - append a dated line to `## Update log` below.

## Adding / updating a profile (schema)

Each profile is a numbered block. Copy this template and fill it:

```
## Profile N — <short name>

- scope: <when this register applies — contexts/audiences>
- language: <MSA | Darija | mixed MS/Darija (specify ratio) | other dialect>
- formality: <formal | semi-formal | casual>
- audience: <who it's for — e.g. devs, general public, low-literacy, customers>
- tone: <one line: warm / neutral / direct / authoritative / friendly ...>
- preferences:
  - <e.g. specific terminology, phrases to always use, style choices>
- never:
  - <e.g. formal MSA in marketing, English tech words, French loanwords...>
```

Keep profiles concise. A profile is a delta, not an essay — one or two lines per
field is enough.

---

## Profile 1 — Tilawa app UI (open-tilawa)

- scope: user-facing strings in `apps/web/src/i18n/messages.ts` and docs shown to users
- language: MSA
- formality: semi-formal, literary without being ornate
- audience: general Arabic-speaking listeners
- tone: calm, plain, quiet confidence; never sells
- preferences:
  - short declaratives; one idea per row/hint, the long explanation behind a details link
  - compose from the Arabic intent, never from a finished English sentence: translating a
    finished sentence preserves its shape, and the shape is what reads as machine-written
  - domain vocabulary fixed by the app: الأقران (peers), خادمنا (our server), التلاوة, القارئ,
    حلقة (ring), المزامنة, مؤقّت النوم
  - em dash / `—` used inside hints exactly as the existing copy does
  - concrete claims only: "لا نحفظ" over "لا يُرسَل" when the request does carry it
- never:
  - Latin-script tech jargon (تليمتري، أناليتكس، ديب لينك) — name the thing in Arabic
  - absolute privacy claims the transport cannot honour
  - exclamation marks, marketing intensifiers, emoji

---

## Update log

- 2026-08-19 — file created as a generic self-maintained template. No profiles yet.
  First profile appears when the owner states a register preference or corrects output.
- 2026-10-30 — Profile 1 added from open-tilawa's existing `messages.ts` register
  (MSA, terse, no Latin jargon) while writing the telemetry toggle copy.
