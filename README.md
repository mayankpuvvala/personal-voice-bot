# Mayank Puvvala — Personal Voice Assistant

A phone/browser bot that speaks on Mayank's behalf, built the same way as
`restaurant_voice_bot` (Vapi + n8n), repointed at his own background instead
of a restaurant's:

1. The bot answers as Mayank's AI assistant — clearly not Mayank himself,
   never pretends otherwise if asked.
2. It answers questions it knows (experience, skills, projects, education,
   links) from a facts block sourced from his resume and public profiles,
   and takes a message (name + contact + question/opportunity) for anything
   it doesn't.
3. Every night, it can call Mayank with a spoken summary of everyone who
   reached out that day — who asked what, and who needs a follow-up.

## Knowledge base

`knowledge_base.md` is the single source of truth for what the assistant
knows about Mayank. It was built from:

- **Resume** (master, per your instruction): `Mayank_Puvvala_GenAI.pdf` in
  Downloads root.
- **GitHub** (github.com/mayankpuvvala) — bio + pinned repos, fetched.
- **Hugging Face** (huggingface.co/mayankpuvvala) — Spaces, models, datasets,
  fetched.
- **Medium** (medium.com/@puvvalamayank) — post titles + summaries, fetched.
- **LinkedIn** (linkedin.com/in/mayankpuvvala) — **not fetched**, LinkedIn
  blocks automated requests. If you want its content (headline, About
  section, recommendations) included, paste it into `knowledge_base.md`
  manually and then update the facts block in `vapi_assistant.json`.
- **LeetCode** (leetcode.com/u/mayankpuvvala) — **not fetched**, same
  reason. Same manual-add path if you want stats included.

There are 40+ other resumes in your Downloads/Resumes folder tailored to
specific companies/roles — none of those were read or used. If you want the
assistant to speak to a specific role focus (e.g. backend, full-stack)
instead of the GenAI-generalist framing in the master resume, tell me which
file and I'll fold it in.

Edit `knowledge_base.md` first when anything changes (new role, new
project, updated links), then copy the relevant bits into the `=== ABOUT
MAYANK ===` block in `vapi_assistant.json`'s system prompt — Vapi reads the
JSON, not the markdown file.

## Architecture

```
Phase 1 (today, $0):
  Recruiter / visitor ──"Talk to Assistant" (browser)──> Vapi bot
                                                              │
                                                 bot calls logInquiry tool
                                                              │
                                             n8n "Log Inquiry" webhook
                                                              │
                                         appends row to Google Sheet ("Log" tab)

  Manually run n8n's "End of Day" branch → builds a sample summary from
  today's rows → (once Phase 2 wired up) calls Mayank via Vapi.

Phase 2 (once you attach a real phone number):
  Caller ──call──> Vapi phone number ──> bot answers ──> same logging
                                                            pipeline as above

  Nightly: n8n Schedule Trigger → reads today's Sheet rows → builds summary
           → POSTs to Vapi's outbound Call API → Vapi calls Mayank and
             reads the summary, can answer follow-ups from it
```

## Files in this folder

- `knowledge_base.md` — source of truth for what the assistant knows about
  Mayank. Edit here first.
- `vapi_assistant.json` — the "Mayank Puvvala - AI Assistant" (answers
  questions / takes messages for opportunities). Test directly in Vapi's
  dashboard.
- `vapi_summary_assistant.json` — the assistant used for the nightly call to
  Mayank with a digest of the day's inquiries. Also testable directly.
- `personal_reception_workflow.json` — import into n8n. Two branches:
  log-inquiry webhook, and the end-of-day summary call.
- `demo_call_widget.html` / `demo_site/index.html` — standalone "Start Call"
  browser widget (same file, `demo_site/index.html` is the one to deploy,
  e.g. to GitHub Pages).

## Setup

Same steps as `restaurant_voice_bot`'s README, with these substitutions:

1. **n8n on Railway**: import `personal_reception_workflow.json` instead of
   the restaurant one.
2. **Google Sheet**: create a tab named `Log` with header row
   `Timestamp | CallDate | CallerName | CallerContact | Topic | Resolved | Details | Company`.
3. **Vapi assistants**: paste `vapi_assistant.json` as a new Assistant
   (Edit as JSON), fill in `server.url` with the Log Inquiry webhook's
   Production URL. Create a second Assistant from
   `vapi_summary_assistant.json` for the nightly digest call.
4. **Config nodes**: same as before — `timeZone`, `googleSheetId` on the Log
   branch; add `mayankPhoneNumber`, `vapiPhoneNumberId`,
   `vapiSummaryAssistantId` on the Summary branch once you have Phase 2's
   phone number.
5. **Demo widget**: fill in `VAPI_PUBLIC_KEY` and `VAPI_ASSISTANT_ID` in
   `demo_call_widget.html` / `demo_site/index.html` — these are placeholders,
   not reused from the restaurant project's demo (those keys belong to that
   assistant only).

## Notes

- The assistant is written to be transparent that it's an AI assistant
  representing Mayank, not Mayank himself — if asked, it says so plainly.
- It won't invent salary expectations, availability/notice period, or any
  detail not present in the facts block — it takes a message for those
  instead of guessing.
- `logInquiry`'s `company` field replaces the restaurant bot's
  `guestsCount` — it's populated only when the inquiry is a job opportunity.
