# Runbook — QBO Reconciliation Procedure

The repeatable per-account flow, the division of labor, and the traps that have already cost time. Read this before touching the bank feed.

## Division of labor

- **Claude (in Chrome)** handles: bank rules, journal entries, register investigation, driving the Reconcile screen, categorizing individual transactions.
- **The user (real mouse)** handles: bulk **select-all → Accept** in the bank-feed queue. The queue's checkboxes do not respond to automation — do not burn time retrying; hand it to the user.

## Guiding approach (user's explicit choice)

**"Post to a sensible account + flag."** Accountant-domain judgment calls (mortgage principal/interest splits, payroll clusters) go to a sensible account or a suspense account and get flagged for the accountant. They must not block reconciliation.

## Per-account reconcile flow

1. **Confirm the anchor** — Dec-2025 statement ending balance and date (see `REFERENCE.md`). Credit cards reconcile to their **close date**, not 12/31.
2. **Clear the bank-feed queue**:
   a. Apply/repair rules so everything categorizable is categorized.
   b. User bulk-accepts.
   c. **Immediately check the Excluded tab** (see gotcha #1). Restore anything there, re-categorize, re-post. Repeat until the Excluded tab stays empty after an accept.
   d. Categorize true stragglers by hand: known-vendor → real account; unknown money-out → suspense; customer payments (Zelle/deposit) → Sales; anything matching another owned account → **Transfer**, not income/expense.
3. **Open Reconcile** (Accounting → Reconcile → account, statement date + ending balance). Check off cleared transactions; read the difference.
4. **Chase the difference to $0**:
   - Book too low → look for excluded/unposted deposits first (that's what caused the $14k gap on 0658).
   - Opening-balance gaps from pre-2025 books → JE to **Opening Balance Equity**, dated 1/1/2025 (or 12/31/2024), flagged for the accountant.
   - Suspicious clusters at period boundaries (e.g. the 12/31/2024 import cluster on 0658) → check the register for duplicated/erroneous imported rows before booking anything.
5. **Finish** the reconcile only at $0 difference. "Save for later" if interrupted — QBO keeps checked-off state.
6. Update `STATE.md` and commit.

## Gotchas (each of these has already happened)

1. **Bulk accept excludes uncategorized items.** Every "select all → Accept" silently moves whatever was uncategorized to the **Excluded** tab. On 0658 this swallowed 713 transactions (all of January 2025, including income deposits) and created a $14,405.76 reconcile difference. **Always check the Excluded tab after every bulk accept.**
2. **QBO session times out** periodically. Re-login is needed and browser tab IDs change afterward — re-acquire the tab, don't assume handles are stable.
3. **Three Wells Fargo feeds are broken** (Error 378): WF Checking 7102, WF Savings 7014, WF CC 6335. Their data has to come from statements/manual import, not the feed.
4. **Credit cards close mid-month** — CapOne 9808 & USB CC 1862 on the 15th, Chase 6745 on the 2nd, WF CC 6335 on the 12th. Reconcile CCs to the close date on the statement.
5. **"Tekmetric" is two different things**: money **out** = software expense (→ Software & Apps); money **in** = customer deposits (→ Sales). Two separate rules exist — don't merge or confuse them.
6. **Zelle from "North Star Auto Repair"** is an internal transfer between the company's own accounts (typically WF 7102 → USB 0658), not revenue.

## Known journal entries (booked or planned)

| JE | Status | Detail |
|---|---|---|
| Loan 9312 setup | ✅ Booked | Shop Equipment (154) / US Bank Loan (265) = $67,208.25; payments split $956.98 principal + $373.25 interest |
| 0658 2024 opening adjustment | ⏳ Planned | ≈ +$1,339.71 to Opening Balance Equity; bank 1/1/2025 = $3,419.48 vs pre-2025 book $2,079.77. Flag for accountant. |
