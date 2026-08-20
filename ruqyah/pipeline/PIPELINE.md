# Ruqyah Intake → Treatment Plan Pipeline

Runbook for the daily scheduled session ("Ruqyah daily intake processing" Routine). Follow it
exactly. Everything happens on branch **`claude/ruqyah-south-africa-scholar-w4wwjv`** — check it
out first (`git fetch origin claude/ruqyah-south-africa-scholar-w4wwjv && git checkout
claude/ruqyah-south-africa-scholar-w4wwjv`), and push state updates back to the same branch.

## What this pipeline does

Google Form "Ruqya Questionare" → responses spreadsheet → this session detects new
submissions → writes a complete treatment plan per the knowledge base → renders a PDF →
emails it to Yasir (yasirsacto@gmail.com) **for his verification** with a push notification →
records the submission as processed. Yasir reviews and forwards to the client himself.
**Never send anything to the client directly.**

## Step 1 — Find the live responses sheet

The live sheet is pinned in `state/processed.json` (`live_sheet_id`:
`1YKhZKe-TeDp3REDairF65Gf_ilutlkHXY_mabu79fTY`, owner imammyklodi@gmail.com, shared with
yasirsacto@gmail.com on 2026-08-20, verified readable). Use it directly. If it is ever
inaccessible, fall back to searching Google Drive for a live spreadsheet
(`application/vnd.google-apps.spreadsheet`) whose title contains `Ruqya Questionare` and
`Responses` — NOT the static CSV snapshots named `...Form Responses 1.csv`.

- If the sheet cannot be read at all: **end silently** this run; if it stays unreadable two
  runs in a row, send one PushNotification flagging lost sheet access.

## Step 2 — Read rows and diff against state

Download the sheet as CSV (`download_file_content` with `exportMimeType: text/csv`). The
columns are the Ruqyah SA self-diagnosis questionnaire (timestamp, name, contact method,
email/phone, then ~26 symptom questions across mental states, health, blockages, dreams,
sleep phenomena).

Load `ruqyah/pipeline/state/processed.json`. A row is NEW if its `Timestamp` value is not in
`processed_timestamps`. If there are no new rows: **end silently** (still commit nothing).

**Privacy rule: no client personal data (names, contacts, symptoms) goes into git — not in
the state file, not in commit messages, and no client plan files are committed.** Plans live
in Yasir's email and in the files delivered to him in this chat; the git-committed state is
timestamps only.

## Step 3 — Build each new client's treatment plan

For each new row, author a complete plan following the knowledge base in this repo:

1. **Diagnose** with `ruqyah/DIAGNOSIS.md` (four categories, 4+ rule) and map the answered
   symptoms through `ruqyah/SYMPTOM-INDEX.md` to indications and prescription add-ons.
2. **Prescribe** per `ruqyah/TREATMENT.md`: the full general verse series with counts, the
   specific cancellation verses for this person's symptoms, the 12-day program, senna/sidr/
   hijama/oil components as indicated, protections, and FAQs.
3. **Write the plan HTML** using `ruqyah/pipeline/sample-plan.html` as the structural
   template (same CSS, same section order). Requirements:
   - Remove the red SAMPLE banner.
   - Header block: client name, contact from the row, intake date, blank "Prepared by" /
     "Reviewed & issued" lines, Source: Ruqyah South Africa — ruqyah.org.za.
   - **Complete verse tables** — every passage of the general series and every prescribed
     specific verse rendered with Arabic + transliteration + translation. No truncation.
     Use canonical Qur'anic Arabic (verify wording against a reliable mushaf text from
     memory; the site extractions in `ruqyah/sources/` carry the counts and transliteration
     style but their Arabic has OCR/spacing artifacts — do not copy Arabic blindly).
   - Personalized "What your answers indicate" section referencing their actual answers.
   - FAQs section (adapt the sample's core set; add case-specific ones).
   - Adaptations: for a child, follow the child-adaptation approach of the Muhammad Nouri
     plan (`ruqyah/pipeline/nouri-plan-reference.txt`): senna withheld, hijama not DIY,
     incense modified, parent-administered.
   - Save as `ruqyah/pipeline/plans/YYYY-MM-DD_<Name_Slugged>.html`.
4. **Safety gates (non-negotiable, from `ruqyah/AGENT-NOTES.md`):**
   - The plan always carries the "MEDICAL CARE DOES NOT STOP" box.
   - Suicidal thoughts / self-harm answers → add a prominent red flag box at the TOP of the
     email to Yasir ("This intake reports suicidal thoughts — crisis support first: SADAG
     0800 567 567 (SA) or 988 (US); please handle personally and promptly") and a gentle
     "speak to someone today" line inside the plan. Never skip this.
   - Seizures/fainting, GI bleeding, pregnancy complications or similar → doctor-first note
     in both the email and the plan.
   - Never name or accuse any person as the sorcerer. Never tell anyone to stop medication.

## Step 4 — Render the PDF

```bash
mkdir -p ~/.fonts && cp ruqyah/pipeline/fonts/*.ttf ~/.fonts/ && fc-cache -f
CHROME=$(ls -d /opt/pw-browsers/chromium_headless_shell-*/chrome-linux/headless_shell 2>/dev/null | head -1)
[ -z "$CHROME" ] && CHROME=$(ls -d /opt/pw-browsers/chromium*/chrome-linux/chrome 2>/dev/null | head -1)
"$CHROME" --headless --disable-gpu --no-sandbox --no-pdf-header-footer \
  --print-to-pdf=/tmp/<Name>_Ruqyah_Treatment_Plan.pdf "file://$PWD/ruqyah/pipeline/plans/<file>.html"
```

Verify the PDF is non-trivial in size, then screenshot-check one page if anything about the
fonts changed (`--screenshot=` + Read the PNG): Arabic must be shaped (connected letters,
right-to-left), never disconnected boxes.

## Step 5 — Deliver for verification

**Do not put file bytes (base64) through tool calls — it is token-prohibitive and risks
corruption. And per the privacy rule, client plan files never go into git.**

1. **SendUserFile**: send the rendered PDF into this session's chat (`display: attach`,
   caption naming the client and intake date). This is Yasir's copy for forwarding.
2. **Gmail** (connector) `send_message`:
   - To: `yasirsacto@gmail.com`
   - Subject: `Ruqyah plan ready for review — <Client Name>`
   - `htmlBody`: a review digest — who submitted, safety flags FIRST, what the answers
     indicate (mapped symptom clusters), the exact prescription (each specific verse by
     name and reference), and the programme components — with a prominent note that the
     complete PDF is in the Claude session chat. The PDF delivered via SendUserFile is the
     authoritative full document (Gmail clips very long bodies, so don't inline the whole
     plan; the digest must be complete enough to review the prescription decisions).
   - `body` (plain-text alternative): the same digest in plain text.
3. **PushNotification**: `Ruqyah plan ready: <Client Name> — plan in your email, PDF in the session chat.`

## Step 6 — Record state and push

Append the processed row's `Timestamp` to `processed_timestamps` in
`ruqyah/pipeline/state/processed.json` (timestamps only — no names or contacts) and note the
disposition in `history` in aggregate, PII-free terms. Commit ONLY the state file, with a
neutral message like `Update pipeline state`, and push to
`claude/ruqyah-south-africa-scholar-w4wwjv` (retry with backoff; on non-fast-forward: fetch,
rebase, push again). Plan HTML/PDF files stay untracked in the session workspace.

## Notes

- Volume is low (a few per week at most); process all new rows in one run.
- If a row is garbage/test data (no name, no symptoms), record it in state with
  `"skipped": true` and do not generate a plan or email.
- If anything fails midway (e.g. Gmail error), do NOT record the row as processed — the next
  daily run retries it.
- Do not create pull requests. Do not email anyone other than yasirsacto@gmail.com.

## How this runs (live config)

- Routine **"Ruqyah daily intake processing"** (`trig_01TYyKkiao6Ls2FGmKHQB9yV`), cron
  `0 14 * * *` UTC (~7:00 AM Pacific), fires into the persistent pipeline session
  `session_01WTUxW2iuFLHKP5jDWygRes` — that session holds the Gmail and Google Drive
  connectors (org policy blocks attaching connectors to fresh-session triggers).
- Prerequisite: the LIVE "Ruqya Questionare (Responses)" Google Sheet must be shared with
  yasirsacto@gmail.com (it lives in another Google account). Until then, every run ends
  silently.
- Yasir can also say "process the form now" in the session at any time for an immediate run.
