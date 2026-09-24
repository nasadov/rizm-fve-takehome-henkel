# Definition of done, RIZM FVE take-home (Henkel Düsseldorf)
All rules below were written and committed before the first research prompt (see commit history).  
**Deliverable:** write-up (max 8 paragraphs), one spreadsheet, README, decision log, AI/tool log, assumption register, transcripts.  
**Brief (in my words):** (1)data-driven energy use cases for the Düsseldorf site, each measured in €/ton and grounded in the site's current state, (2) one data request and one stakeholder for the first on-site visit, method counts over outcome, and the toolchain must be clearly declared. The brief itself is not reproduced in this repo (to avoid RIZM's material showing up in a public repo).

**€/ton (D1)**: euro per metric ton of finished product leaving the Düsseldorf site, per year. €/tCO2e is reported alongside only where the use case in question is an emissions play. If site tonnage is not public, €/ton is computed from a tier C (see tier definitions under "Evidence rule") allocation of group tonnage, shown as a range and with €/year reported along with it.  
**Reference year (D5)**: [year] for prices and volumes (fixed before the model is built). For the top use case, sensitivity to [other year] is shown.  
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
    - 3 = a recurring decision the OS could own
    - 2 = a recurring analysis a human acts on
    - 1 = a one-off project

Ties are broken by (a). Shortlist = top 3.

**Evidence rule (D3):**
- A value enters the register only with a URL I opened myslef, an exact quote, the year it refers to, and its boundary (site / group / external). 
- Sources:
    - Tier A = published or measured, by the party it is about (Henkel and RIZM) or an official register (the boundary column says whether it covers the site or the group)
    - Tier B = industry benchmark or published price
    - Tier C = my own estimate

**Divergence rule (D4):** 
- When I use a value different from the source, the register carries both along with the reason.

**Units:** 
- Energy in MWh, mass in t, prices in €/MWh, emissions in tCO2e (emission factors are CO2-only unless the source gives CO2e, the difference of 1-2%is not material to any conclusion here)

**Results:**
- Rounded to two significant figures. 
- If a result depends on any tier C row, it is given as a range, never a single point.

**Decision changes:**
- D1–D5 change only on evidence from the brief, the scorecard, or an opened source, never on a model's opinion. 
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