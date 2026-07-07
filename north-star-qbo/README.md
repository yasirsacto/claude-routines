# North Star Auto Repair — QBO 2025 Reconciliation

Client: **North Star Auto Repair LLC** (aka Yuba City Autoworks; formerly Yuba City Tire Pros)
Platform: **QuickBooks Online**, driven via Claude-in-Chrome (browser session required — this repo only stores the routine and state)
Owner on payroll: **Nasir Khan** (personal checking = US Bank 3258)
Entity: likely S-corp (wages + distributions)

## Goal

Finish reconciling **US Bank Checking 0658** (the hub account) for 2025, then reconcile the remaining 9 accounts, hub-first.

## Files

| File | Purpose |
|---|---|
| [`STATE.md`](STATE.md) | Live status: what's done, what's in progress, immediate next steps. **Update at the end of every working session.** |
| [`RUNBOOK.md`](RUNBOOK.md) | The repeatable procedure: per-account reconcile flow, gotchas, division of labor between Claude and the user. |
| [`REFERENCE.md`](REFERENCE.md) | Stable facts: statement anchors, opening balances, bank-rule library, suspense accounts, credit-card close dates. |

## How to resume work

1. Open a Claude session **with the Chrome extension** connected to the browser that's logged into QBO.
2. Paste or reference `STATE.md` as the handoff context.
3. Follow the "Immediate next steps" section in `STATE.md`, using `RUNBOOK.md` for procedure and `REFERENCE.md` for numbers.
4. Before ending the session, update `STATE.md` (and `REFERENCE.md` if anchors/rules changed) and commit.
