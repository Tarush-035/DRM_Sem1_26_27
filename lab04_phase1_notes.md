# Lab 04 Assignment 03: Phase 1 notes (TCS.NS)

Branch: `lab04-assignment03`. The notebook is edited in place. Provided cells are unchanged, except `TICKER = "TCS.NS"` in the identification cell.

## Run locally (once, same day, with internet)
1. Fill `NAME`, `CAMPUS_ID`, `EMAIL`, `HONOUR` in the identification cell. Cell 2 stops until you do.
2. `Restart & Run All`. Expect `[LIVE]` for `stock` and `inr_r`. If either prints `[SIM]`, fix the connection first.
3. Rule 1 screen: if any day has |log return| > 8%, the run stops and prints the day. Check NSE announcements and news, then add it to `FLAG_LOG`
   (kind `earnings` or `market` if no corporate action). A split, bonus, demerger or merger stops the analysis: tell me.
4. Do not re-run on another day before pasting outputs: the window is `today - 730 days`, so every number shifts with the date.
5. Paste back: Q1 table and rolling-vol range, Q2(b) table, Q3 tables and fitted slope, Q4(a) table, Q4(b) table, Q4(c) cycle table, Supplements A, B, C tables, Q5(a) trade count, Q5(b) tables, Q5(c) table and the printed decomposition.

## Fetch from NSE (Q4(b))
Fill the seven constants in the Q4(b) cell: `C_OBS`, `P_OBS`, `K_OBS`, `S_OBS`, `EXPIRY_OBS`, `QUOTE_ASOF`, `QUOTE_SOURCE`.
- Option chain for TCS, one monthly expiry roughly 20 to 40 days out.
- The strike nearest to spot, call and put with the same strike and expiry.
- Premium: prefer the bid/ask mid at one timestamp, and state in `QUOTE_SOURCE` whether you used last traded price or mid.
- `S_OBS` is the underlying value shown on the same chain screen at the same moment. Note the time.
- Check whether any ex-dividend date falls between the quote date and the expiry. If one does, add it to `DIV_TABLE`.

## Verify (not yet checked against a primary source)
- Every row of `DIV_TABLE` against the NSE corporate-actions page for TCS. Five rows (four distinct ex-dates, all before 2025) are inferred from record dates (T+1) in my source and are marked `inferred` in the table.
- That there is no demerger, merger or buyback in the window (no hit in the sources I read).
- `q`: the table gives the trailing-365-day cash dividends divided by the last close.

## Sandbox results (all `[SIM]`)
`sandbox_run/Lab04_SIM_sandbox_run_NOT_FOR_SUBMISSION.ipynb`: full run, no errors, all assertions pass. The numbers in it are simulated and must not be quoted.
A second sandbox run with fake Q4(b) constants confirmed that code path runs; it is not saved.
