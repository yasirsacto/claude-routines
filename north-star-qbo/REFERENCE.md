# Reference — Anchors, Openings, Rules, Suspense Accounts

Stable facts collected during the engagement. Update only when an anchor, rule, or account changes.

## Statement anchors (Dec 2025) and derived 1/1/2025 openings

| Account | Anchor date | Ending balance | 1/1/2025 opening | Notes |
|---|---|---|---|---|
| USB Checking 0658 (hub) | 12/31 | $1,647.23 | $3,419.48 | Reconcile in progress |
| USB Payroll 4184 | 12/31 | $5,715.32 | $6,166.19 | ~614 txns, accountant-heavy |
| USB Mortgage/Ins 9708 | 12/31 | $2,929.36 | $2,151.22 | 72 txns, ready |
| USB Loan 9312 | 12/23 | $66,251.27 (liability) | $0 | ✅ Fully reconciled |
| CapOne CC 9808 | 12/15 | $4,770.02 (liability) | — | Closes on the 15th |
| USB CC 1862 | 12/15 | $2,824.88 (liability) | — | Closes on the 15th |
| Chase CC 6745 | 12/02 | $12,954.77 (liability) | — | Closes on the 2nd |
| WF CC 6335 | 12/12 | $5,015.86 (liability) | — | Closes on the 12th; feed broken (Error 378) |
| WF Checking 7102 | 12/31 | $116.57 | — | Winding down to close; feed broken (Error 378) |
| WF Savings 7014 | 12/31 | $0.01 | — | Book off ~$399.98; needs Jan–May 2024 statements; feed broken (Error 378) |

## Bank rules created for 0658

| Rule name | Match | Posts to |
|---|---|---|
| Uncategorized Checks 0658 | Contains "Check #" | *Uncategorized Checks* (Other Current Asset, suspense) |
| Uncategorized 0658 Payments | Any of: Electronic Withdrawal / Debit Purchase / Bill Pay / Zelle / Atm Withdrawal | *Uncategorized 0658 Payments* (suspense) |
| Tekmetric Deposits 0658 | Money-in, any of: Tekmetric / Deposit | **Sales** (income) |
| City Tire Pros | (converted earlier) | Transfer: WF 7102 → USB 0658 |

Plus the pre-existing, repaired **111-rule library**, and a separate money-out Tekmetric rule → Software & Apps (do not confuse with the deposits rule).

## Suspense accounts (flagged for accountant reclassification)

- **Uncategorized Checks** — Other Current Asset
- **Uncategorized 0658 Payments**

Both are 0658-scoped holding accounts; the accountant reclassifies later. They exist so reconciliation isn't blocked by judgment calls.

## Known one-off transactions on 0658 (no rule)

| Description | Amounts | Treatment |
|---|---|---|
| Web Authorized Pmt Asbury Environme | $7 / $102 / $137 | → Uncategorized 0658 Payments (suspense) |
| Zelle Standard Pmt From Fnu Ur Rehman | $96 × 2 | → Sales (customer payment) |
| Zelle Instant Pmt From North Star Auto Repair | $1,900 | → Transfer from WF 7102 (internal, NOT income) |

## People / entities

- **Nasir Khan** — owner, on payroll; personal checking = US Bank 3258 (owner-personal, not a business account).
- Business names seen in data: North Star Auto Repair LLC, Yuba City Autoworks, Yuba City Tire Pros (former name — appears in old rules/txns).
- 2026 manual payroll checks to book as wages when 2026 is worked: **#5034, #5158**.
