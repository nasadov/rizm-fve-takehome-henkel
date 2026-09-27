# RIZM FVE take-home, Henkel Düsseldorf-Holthausen

My answer to the Field Value Engineer take-home: energy use cases for Henkel's Düsseldorf site in €/ton, and the one data request and the one stakeholder for the first visit. Everything rests on public information and on reasoning that is written down. The method was fixed before the research started, and every number can be followed back to its source or to the estimate it is.

Entry point: this file, then `WRITEUP.md`. Tag `v1.0` is the submitted state.

## How to read this in 10 minutes

1. `WRITEUP.md`, six paragraphs.
2. `model.xlsx`, sheets `assumptions` → `calc` → `hand_check`. Every value cell in `calc` reads its number from `assumptions` by register id, so any figure in the write-up leads to its row and its source in one click.
3. `DECISIONS.md`, one row per decision, D1 to D16, each with the alternatives, the reason and what would reverse it.
4. `AI_LOG.md`, one row per AI session with what I kept and rejected, with the full transcripts in `transcripts/`.

## What is where

| File | What it is |
|---|---|
| `ACCEPTANCE.md` | My definition of done, written and committed before the first research prompt: the €/ton metric, the ranking rule with anchors, the evidence rule, the reference year. Unchanged since 2026-09-25. |
| `WRITEUP.md` | The write-up. |
| `DECISIONS.md` | The decision log. |
| `AI_LOG.md` | The AI and tool log. |
| `model.xlsx` | `sources` (22 rows), `assumptions` (the register, 66 rows with gaps in the ids), `usecases` (13 rows, scores and reasons), `calc` (baseline and three use cases), `hand_check` (the top two cases recomputed with typed numbers). |
| `transcripts/` | The planning summary and one file per AI thread: 00 definition of done, 01 sources, 02 situation-read challenge, 03 longlist, 04 model skeleton, 05 red team. |
| `data/` | Raw exports as they came out of the source's own export button, unedited; the register cites them by S-id. |

## Toolchain

| Tool | Version and settings | Used for | Where |
|---|---|---|---|
| Claude, desktop app on macOS | Claude Fable 5.1 in every thread; deepest thinking for threads 00, 02 and 05, default otherwise; web search on for thread 01 only; connectors off; memory off per chat from thread 01 on (00 ran before I decided that); a fixed preamble as the first message of every thread | critique of the definition of done, source hunting, situation-read challenge, longlist, model skeleton, red team | `AI_LOG.md`, `transcripts/` |
| Grammarly | browser extension, free tier; suggestions accepted one by one, no rewrite mode | spelling and grammar | `WRITEUP.md`, `README.md` and the decision rows |
| Google | | finding and opening sources | `model.xlsx`, sheet `sources` |
| Excel for Mac | | the model, a spreadsheet on purpose: a plant manager can check it without code | `model.xlsx` |
| VS Code, Terminal with git and gh, Chrome | | writing, version control, exports, opening every source myself | commit history |

## AI quality count

Six AI threads, 00 to 05, each logged with what came back, what I kept and what I rejected. Thread 00: about 40 critique points, eight of them ranked; six taken into ACCEPTANCE.md, four not adopted, four rejected. Thread 01: a list of leads, of which I opened every one that looked usable; 24 were opened and set aside (S14), the rest became the sources S6 to S18 or are listed in the log as dead or off-topic; all 22 sources in the register were opened by me. Thread 02: the situation read challenged sentence by sentence; sentences that went beyond their evidence were cut or marked as guesses, none entered the register without a source. Thread 03: 13 longlist rows, two edits to the model's text, all 13 scores mine, three kept, one merged, nine cut, six of them on an assumption no register row backs. Thread 04: one model skeleton with three formulas; its emission factor and net-to-gross ratio replaced by the report's own values after I opened it, two DOE efficiency ranges not found in the sheets it named, one accounting proposal rejected (D12), 24 parameter rows R55 to R79 entered with my own estimates or derived values. Thread 05: ten objections and eight headlines, seven objections accepted in whole or in part, three turned down with the reason in the log, three register rows added, fourteen edited, two decisions written (D13, D14). One preamble change (D6, after thread 00).

## What the tools got wrong and lessons out of it

- A quote that does not exist: A web fetch of the UBA report returned an emission factor "on p. 47". The sentence is not in the PDF (row 01b, S19). Lesson: a fetch is a lead, never a quote. Every quote in the register comes from a page I had open.
- Lost units (twice): The project chat priced net-basis fuel (Heizwert) at a gross-basis price (Brennwert), 11 % off in the baseline (R54). Thread 04 gave gross-basis efficiency figures for rows defined on a net basis (R69, R76, S22). Lesson: models drop units. The basis is now written in the unit column of every fuel row, and the net-to-gross factor is its own register row (R56).

## Against the definition of done

`ACCEPTANCE.md` is unchanged since 2026-09-25. Checked against it:

- Done: unit and boundary check on every register row; hand recompute of the top use case and of the second one; one red-team pass (thread 05, its findings in D13 and D14); final read of every file against `ACCEPTANCE.md` on 2026-09-27; brief check; every AI rule (preamble in every thread, nothing from a model in the register unverified, every session logged, transcripts exported, documents attached, no third-party text committed, quality count above, every prompt change logged).
- Not done: the second red-team pass in another model. Sensitivity on the two dominant parameters was run for the top use case only; U11 and U2 carry a range through the tonnage row.

## What I did not use AI for

Scoring the longlist (every score is mine), `model.xlsx` assembly, every choice in `DECISIONS.md`, the hand check, the write-up and this README.

## Time log

| Block | Planned h | Actual h |
|---|---|---|
| Setup and definition of done | 1.5 | 1 |
| Sources and register | 4 | 5 |
| Ranking and model | 5 | 5 |
| Red team, first visit, write-up | 4 | 5 |
| Audits, README, submission | 2 | 2 |