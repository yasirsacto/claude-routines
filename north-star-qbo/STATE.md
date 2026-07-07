# Current State — updated 2026-07-07

## ✅ Done

- Chart of Accounts cleaned to the Shop Fix Academy template; 8 bank feeds connected; the 111-rule library repaired.
- **US Bank Loan 9312: fully reconciled.**
  - JE: Shop Equipment (154) / Loan (265) = $67,208.25.
  - Payment split: $956.98 principal + $373.25 interest.
  - Reconciled to $66,251.27 @ 12/23/2025.
- All 10 accounts' Dec-2025 statement anchors collected and 1/1/2025 opening balances derived (see `REFERENCE.md`).

## 🔧 In progress — US Bank Checking 0658 (the hub account)

- All 2025–2026 data loaded; categorized via rules + suspense accounts.
- Reconcile was started; difference was **$14,405.76** (book too low). The reconcile is **"Saved for later"** — not finished.
- **Root cause found:** every "select all → Accept" in the bank feed **excluded** whatever was uncategorized at that moment. **713 transactions were excluded** — mostly all of January 2025, including Tekmetric income deposits.
- **Recovery underway:** excluded transactions restored (Excluded tab was emptied); rules re-categorized ~216; user has been posting them (net +$8,834).
- **~14 true stragglers** remain uncategorized (no rule matches):
  - `Web Authorized Pmt Asbury Environme` ($7 / $102 / $137) → suspense (Uncategorized 0658 Payments)
  - `Zelle Standard Pmt From Fnu Ur Rehman` ($96 × 2) → Sales income
  - `Zelle Instant Pmt From North Star Auto Repair` ($1,900) → **internal WF→USB transfer** (not income)

## ▶️ Immediate next steps on 0658

1. **Check the Excluded tab** — items keep landing there after each bulk accept. Restore + re-post until it stays empty.
2. Categorize the ~14 stragglers (Asbury → suspense; Zelle-from-customer → Sales; the $1,900 North Star Zelle = transfer from WF 7102).
3. **Re-open the saved reconcile** (Accounting → Reconcile → 0658, ending balance $1,647.23 @ 12/31/2025), check off newly-posted transactions, read the new difference.
4. **Book the +$1,339.71 (≈$1,490) 2024 opening adjustment** — JE to Opening Balance Equity to correct the 2024 gap (bank 1/1/2025 = $3,419.48; pre-2025 book balance was $2,079.77).
5. Investigate the suspicious **12/31/2024 import cluster** in the register (possible duplicate/erroneous data inflating the difference). Resolve the residual to $0, then **Finish**.

## 📅 After 0658 — remaining accounts (hub-first order)

Do 0658 and 4184 before the dependents, because of inter-account transfers.

1. **USB Payroll 4184** — ~614 txns, accountant-heavy (payroll clusters → sensible account + flag).
2. **USB Mortgage/Ins 9708** — 72 txns, ready to go.
3. **The 4 credit cards** (CapOne 9808, USB CC 1862, Chase 6745, WF CC 6335) — reconcile to their mid-month close dates, not 12/31.
4. **WF Checking 7102** — winding down to close.
5. **WF Savings 7014** — blocked: needs Jan–May 2024 statements to explain the $399.98 book gap.

Also queued for 2026 work: two 2026 manual payroll checks (**#5034, #5158**) to book as wages.
