# Definition of done, RIZM FVE take-home (Henkel Düsseldorf)
All rules below were written and committed before the first research prompt; D1, D2 and D5 were revised once after the reviewer critique in thread 00, still before any research (see commit history).  
**Deliverable:** write-up (max 8 paragraphs), one spreadsheet, README, decision log, AI/tool log, assumption register, transcripts.  
**Brief (in my words):** Henkel opens its Düsseldorf site as a pilot for RIZM's Agentic Energy OS; RIZM knows nothing about the site yet. Show how I would start, from public information and reasoning. (1) Data-driven energy business use cases in €/ton, from forecasting to trading to investment decisions, grounded in the site's current situation. (2) For the first visit, the single most load-bearing data request and stakeholder (30 minutes). Graded on method, not numbers: why this assumption, why this use case and not that one, why €X/ton when the source says €Y, why this tool. Any tool allowed if declared with where it was used; scored against the public scorecard. Deliverable: write-up, code, spreadsheets, README with the entry point; six clean paragraphs and one spreadsheet beat volume. The brief itself is not reproduced in this repo (to avoid RIZM's material showing up in a public repo).

**€/ton (D1):** 
The money a use case saves in a year, divided by the tons of finished product the site makes in that same year. The saving is counted after any extra work the measure needs (net, not gross), and CO2 costs count as part of energy cost. For an investment, I show the yearly saving with the investment spread over its lifetime, plus the payback time. Every case is shown in €/year as well as €/ton. I divide by the whole site's tonnage so cases can be compared; if a case only affects one production line, I also show the number for that line. €/tCO2e only where a case is really about emissions. If the site's tonnage is not public, I estimate it from Henkel's group figure (tier C) and show the result as a range.    
**Reference year (D5):** 2025 for prices and volumes, because it is the latest year with both a Henkel report and full-year price data. Fixed now, before the model exists. For the top use case I also show 2024, to see how much the result depends on the price level. If a site figure only exists for an earlier year, it goes into the register with that year and a note, and I use it unchanged unless a source shows the site has changed. The reference year itself only moves if the site changed materially after the data year, and that gets logged.    
**Ranking rule (D2)**: I use four criteria, each scored 1-3 (with anchors):
- (a) grounded: 
    - 3 = rests on a tier A row with boundary "site"
    - 2 = rests on a tier A row with boundary "group", or on a tier B row
    - 1 = rests on tier C rows only
- (b) magnitude (judged as an order of magnitude before the model exists, re-checked after calc, mismatches logged; the site's annual energy cost is a register row, tier C if needed):
    - 3 = about 5% or more of the site's annual energy cost
    - 2 = 1-5%
    - 1 = under 1%
- (c) quantifiable from one first-visit request: 
    - 3 = one existing data export
    - 2 = one request + processing
    - 1 = data that would have to be created 
- (d) fit to an agentic energy OS (anchored on what rizm.de says the product does):
    - 3 = a recurring decision the OS could take itself
    - 2 = a recurring analysis a person acts on, or a one-off investment decision the OS's data would clearly inform
    - 1 = neither

Anchor for (d), from rizm.de (S2, R1 to R3): the software runs assets and production in 15-minute steps across the power markets, described as fully automated, and it finds and sizes measures from flexibility to investments and hedging, which a human then decides on. So a 3 is a 15-minute kind of decision the software could take itself, a 2 is a decision it prepares for a human.  
Ties are broken by (a). Shortlist = top 3.  
(a) is scored on the weakest row a case rests on, not the strongest, and a range is scored at its low end. The site's energy-cost row is fixed before any case is scored. (b) is scored once before the model as a rough order of magnitude; after the calculation, the computed ranking counts, and any change to the shortlist is logged as a decision. A measure Henkel has visibly already done, or started, is cut or reduced to what is left of it, and logged.

**Evidence rule (D3):**
- A value enters the register only with a URL I opened myself, an exact quote, the year it refers to, and its boundary (site / group / external). 
- Sources:
    - Tier A = published or measured, by the party it is about (Henkel and RIZM) or an official register (the boundary column says whether it covers the site or the group)
    - Tier B = industry benchmark or published price
    - Tier C = my own estimate

**Divergence rule (D4):** 
- When I use a value different from the source, the register carries both along with the reason.

**First-visit rule (D7):** 
- The data request is the one request that turns the most important guessed numbers (tier C rows) of my shortlist into real site numbers, and that Henkel can realistically hand over within a week. 
- The stakeholder is the role that owns the decision my top use case depends on. 
- The 30 minutes are for confirming that case's two most important assumptions and whether the requested data exists in that form.

**Units:** 
- Energy in MWh, mass in t, prices in €/MWh, emissions in tCO2e (emission factors are CO2-only unless the source gives CO2e, the difference of 1-2% is not material to any conclusion here)
- Numbers: thousands separated by a space, decimals by a point (211 078 t, 0.0249). Quotes from sources keep the source's own format.

**Results:**
- Rounded to two significant figures. 
- If a result depends on any tier C row, it is given as a range, never a single point.

**Decision changes:**
- D1–D5 and D7 change only on evidence from the brief, the scorecard, or an opened source, never on a model's opinion. 
- A model's contrary view goes into the log as rejected.

**Verification before submit:**
- Unit and boundary check on every row.
- One hand recompute of the top use case.
- Sensitivity on the two dominant parameters per use case.
- Two red-team passes, the second in a different model (where available).
- Traceability audit (every number → a register row, every "because" → a decision)
- Brief check (each requirement in the brief paraphrase is present in the deliverable)

**AI rules**:
- Session preamble in every thread.
- Nothing from a model enters the register unverified.
- Every session logged with what I kept and rejected.
- AI transcripts are exported.
- Documents are attached, never pasted.
- No third-party document text committed. 
- An AI quality count kept (rows checked, rows rejected, citation accuracy).
- Every mid-way change to a prompt or the preamble logged with its reason.

**Out of scope:**
- detailed engineering design
- vendor comparison
- anything requiring non-public data beyond a stated tier C assumption