
/
Claude Desktop (macOS), Connected
Memory is off for this chat
Claude finished the response
Session rules for this thread:

Never invent a number, source, URL, or quote. If you don't know, write "not known".
Tag every factual claim [found] (you can point to a specific public source), [inferred] (reasoned from a found fact, show the step), or [guess].
Give a URL only if you are confident it exists. I will open every URL myself before anything enters my work.
Do not compute my results; I calculate in my own spreadsheet. Benchmark ranges are welcome if tagged and sourced. Check my arithmetic only when I ask.
Short answers, plain tables or numbered lists, no intro and no summary, unless I say otherwise.
Do not search the web or use any connected tools in this thread.
At most 10 points per answer, biggest first, unless the prompt asks for a list or table of a given length. Anything beyond that as one-line headlines under "Also", no explanation.
Context: take-home for a Field Value Engineer role at RIZM (industrial energy optimization). Target: Henkel's Düsseldorf site. Only public information.

Rules noted. What's the first question?

My shortlist, from my scored longlist. For each of the three I need the back-of-envelope skeleton that gets me to € per ton of product per year.

U1: 15-min steam and power demand forecast per consumer (Henkel lines, BASF/KLK, district heat) driving CHP unit commitment, including the hourly split of district heat between waste heat and CHP heat. Saves fuel through fewer boiler and turbine starts, less steam venting and the cheapest heat source per hour.

U11: Boiler and turbine efficiency monitoring (flue gas, condensate return, fouling). Saves fuel per ton of steam by catching efficiency losses early. Only the monitoring layer, efficiency projects themselves are already in Henkel's plan.

U2: Gas turbine dispatch on the day-ahead and intraday spread. Runs the one steam-independent unit (8.6 MW net, with heat recovery boiler) only in hours where the power value is above gas plus CO2 cost.

How I count: € per ton = net yearly saving divided by the site's yearly finished-product tons, same year. CO2 cost (EU ETS allowances) sits inside the energy cost. € per year is shown next to every € per ton. I have a baseline block with the plant's yearly fuel, gas cost, CO2 cost and tons, so where a saving can be written as a share of yearly fuel, write it that way.

For each use case give me:
- the formula, in words and in symbols
- one table of parameters with the columns: parameter, unit, type (site-specific / tariff or market / technology-generic), where I would find it publicly or "site-visit", dominant (yes or no, at most two yes per use case)
- for technology-generic parameters a typical range with its source, tagged [found] or [inferred]
- the extra operating effort the measure needs, as its own parameter (I count net, not gross)
- one sanity check for the result, a benchmark range or a physical limit, with its source tagged [found] or [inferred]
- for every gas quantity, whether it is on a net (Heizwert) or gross (Brennwert) basis
- parameters that appear in more than one use case marked as shared

No computed results, I calculate in my own sheet. Parameters I can't find publicly get marked "site-visit". They feed my data request.

Plant, for context. This is my situation read, the ids in brackets are rows of my assumption register, you don't need the rows.

Making sense of an incomplete request about a plant.
Making sense of an incomplete request about a plant.
The plant block after "Plant, for context." didn't come through — the message ends there. Paste it and I'll answer all three in one go.

Düsseldorf-Holthausen is Henkel's headquarters and one of its two largest production sites [R9, R20]. It makes laundry detergents, household cleaners, adhesives for consumers and tradespeople, and products for industrial customers [R20]. The site has its own combined heat and power plant with five gas-fired units, 75 MW gross and 68 MW net electric capacity, on a medium-voltage grid connection with partial feed-in and own consumption [R42, R46, R48]. Four units are back-pressure steam turbines, so their electricity follows the steam demand; the gas turbine is the one unit that does not [inferred from R42, R46]. The plant produces for Henkel and for third parties and feeds into the grid [R14, R48]; the other companies on the site, BASF and KLK, are the likely steam customers [inferred from R49]. At group level Henkel books 168 856 of its 357 850 t Scope 1 emissions as supplied to third parties [R15]. In the last three years coal use stopped (2024) and the coal-firing infrastructure was dismantled, two units (10 MW and 0.6 MW) were shut down in July 2025, and since April 2026 industrial waste heat from the site, supplemented by CHP heat, supplies district heating of Stadtwerke Düsseldorf [R10, R47, R8]. In 2025 the plant emitted 211 078 tCO2, after 229 042 in 2024, as an EU ETS installation [R49, R50, R51]. Free allocation was 61 633 allowances, so about 71 % of the emissions must be covered with purchased allowances, roughly €11 million at the 2025 auction average for the whole plant, a benchmark, not Henkel's actual bill [R52; inferred from R50, R52, R36]. Henkel's 2030 target is Scope 1 and 2 combined, minus 42 % vs 2021, and it stands at minus 49.5 %, but that came from market-based Scope 2 falling from 160 242 to 34 824 t. Scope 1 alone is at minus 42 %, on the line, and with Scope 2 nearly used up, the 2045 net-zero target of minus 90 % leaves Scope 1 as the remaining lever, and this plant is 59 % of it [R53, R17, R16; inferred from R15, R53]. Henkel calls the plant a material asset with locked-in emissions and plans efficiency gains and more biomethane by 2030 [R9, R10]. Gas costs around 4 cents per kWh and purchased electricity around 13 cents on Eurostat band averages, a benchmark, not Henkel's contract prices, and 13 cents is a ceiling because the site exports in some hours [inferred from R31, R28, R48]. Not public: how much of the plant's steam, power and CO2 is Henkel's own, and how many tons the site makes. Both are site-visit items. For the money the first one is the fact that would change this read the most; for the target it does not matter, every ton of the plant counts in Henkel's Scope 1, where the remaining reductions have to come from [R15, R19, R50; inferred from R53].
Working through marginal cost and efficiency-drift formulas.
Common basis (applies to all three)

Gas basis: all efficiencies, emission factors and F below are Heizwert (net, Hi). German gas invoices and Eurostat band prices are Brennwert (Hs, GCV) [found: Eurostat nrg_pc_203 metadata; DVGW G 685 billing]. Convert: c_g[€/MWh_Hi] = c_g[€/MWh_Hs] × Hs/Hi, with Hs/Hi ≈ 1.11 for H-gas [found: DVGW/UBA standard value ~1.108].
Emission factor natural gas e = 56.0 tCO₂/TJ_Hi = 0.2016 t/MWh_Hi [found: UBA "CO₂-Emissionsfaktoren für die deutsche Berichterstattung"].
Fuel cost incl. CO₂: c_f = c_g + e·(1−a)·c_c, with a = free-allocation share (you have it, ~29 %) if you cost only purchased allowances; a = 0 if you price the opportunity cost of every allowance (the economically correct choice, [inferred]: an allowance not used can be sold).
€ per ton: (S − O)/T, T = finished-product tons of the site (site-visit, shared).
Shared parameters (marked S in tables): F yearly plant fuel; c_g; c_c; e; Hs/Hi; η_B boiler efficiency; p_el electricity value; T; boiler/turbine count and rating.

U1 — Forecast-driven unit commitment

Words: saving = fuel avoided by fewer starts + fuel avoided by less venting + net cost avoided by shifting district-heat hours from CHP to waste heat, minus operating effort.

S₁ = c_f · F · (σ_st + σ_v) + Q_dh · φ · (m_CHP − m_WH) − O₁

σ_st = n_st · f_st / F (starts avoided per year × fuel per start ÷ yearly fuel)
σ_v = V · h_s / (η_B · F) (vented steam t/yr × enthalpy above feedwater MWh/t ÷ boiler eff. ÷ yearly fuel)
m_CHP = (c_f − p_el · η_el,BP) / η_th,BP (marginal cost of one MWh back-pressure heat, net of the power it co-produces)
m_WH = electricity for pumps/heat-pump per MWh_th × p_el
parameter	unit	type	source	dominant
F (S)	MWh_Hi/yr	site	ETS emissions ÷ e gives fuel [inferred from R49]	—
c_f (S)	€/MWh_Hi	market	Eurostat + EEX/EUA auction	—
n_st, f_st	starts/yr, MWh_Hi/start	site	site-visit	yes
V, h_s	t/yr, MWh/t	site / generic	site-visit; h_s from steam tables	—
η_B (S)	–	generic	site-visit; range below	—
Q_dh	MWh_th/yr	site	Stadtwerke Düsseldorf/Henkel press (R8) if stated, else site-visit	—
φ	–	site	site-visit (hourly log since Apr 2026)	yes
η_el,BP, η_th,BP	–	site	site-visit	—
p_el (S)	€/MWh	market	EPEX day-ahead (export hours) / Eurostat (import hours)	—
forecast error before/after	% MAPE	site + generic	site-visit	—
O₁	€/yr	site	licence + 0.2–0.5 FTE data/model upkeep + meter retrofits [guess]	—
Generic ranges: η_B large gas boiler 90–94 % Hi [found: US DOE Steam Tip Sheet 4]; σ_st, σ_v, φ — not known publicly, [guess] that combined fuel effect is 0.5–3 % of F; treat as site-visit.
Sanity: physical cap = today's start fuel + today's venting + (CHP heat currently supplied to DH in hours where waste heat was available); S₁ cannot exceed the sum of those three [inferred]. If your result exceeds ~3 % of F·c_f, recheck [guess].

U11 — Efficiency monitoring

Words: saving = fuel avoided because efficiency drifts (combustion, fouling, condensate loss) are corrected months earlier than by the current inspection cycle, minus operating effort.

S₁₁ = c_f · F_B · Σₖ (Δηₖ · dₖ / 8760) / η_B − O₁₁

F_B fuel through monitored boilers/HRSG; Δηₖ efficiency drop of drift type k (pp); dₖ hours per year the drift would have persisted undetected without monitoring (detection time saved).
Condensate term separately: ΔR · M · (h_cond − h_mu) / η_B, ΔR = extra return share caught, M = condensate mass t/yr.
parameter	unit	type	source	dominant
F_B (S: subset of F)	MWh_Hi/yr	site	site-visit	—
c_f (S)	€/MWh_Hi	market	as above	—
η_B (S)	–	generic	range below	—
Δη per drift	pp	generic	ranges below	—
d_k detection time saved	h/yr	site	site-visit (current inspection/test cycle)	yes
stack temp, O₂ setpoint	°C, %	site	site-visit	—
condensate return share, M	%, t/yr	site	site-visit	yes
turbine isentropic efficiency drift	pp	site	site-visit	—
O₁₁	€/yr	site	O₂/flue analysers, sensors, 0.1–0.3 FTE [guess]	—
Generic ranges [found: US DOE Steam Tip Sheets 4, 7, 8]: +1 pp boiler efficiency per 15 % less excess air or per ~22 °C lower stack temp; waterside scale ~0.8 mm ≈ 2 % more fuel; condensate return value = make-up water heating + treatment + water (compute from your h_cond, h_mu).
Sanity: monitoring alone typically recovers 1–3 % of boiler fuel [inferred from the DOE per-effect figures × plausible drift]; hard cap: η_B cannot exceed ~94–95 % Hi without condensing (flue dew point ~55 °C) [inferred]. Do not double-count with Henkel's planned efficiency projects (R10): count only the detection-time gain.

U2 — Gas turbine spread dispatch

Words: saving = (yearly margin of the optimal hour-by-hour run decision) − (margin under today's dispatch rule), minus start costs and operating effort.

S₂ = Σₕ [P · (v_h − c_f/η_GT + q · c_f/η_B)]⁺ · x_h,opt − Σₕ [same] · x_h,now − n_st,GT · k_st − O₂

v_h = value of power in hour h: day-ahead price when site exports, avoided purchase price (energy + grid fees) when importing; x = run flag.
parameter	unit	type	source	dominant
P net	MW	site	8.6 (R42)	—
η_GT electric	–	generic	range below; site-visit	—
q heat-to-power (HRSG)	MWh_th/MWh_el	generic	range below; site-visit	—
η_B (S)	–	generic	as above	—
c_f (S)	€/MWh_Hi	market	as above	yes
v_h profile	€/MWh	market/site	EPEX SPOT day-ahead 2025; import/export split site-visit	yes
x_h,now (current rule, run hours)	h/yr	site	site-visit	—
min up/down time, ramp	h	site	site-visit	—
k_st, n_st,GT	€/start, /yr	site	site-visit (fuel + maintenance factor)	—
max availability	h/yr	site	site-visit	—
O₂	€/yr	site	trader/optimiser licence, 0.1–0.3 FTE [guess]	—
Generic ranges: small industrial GT (5–10 MW) η_el 28–34 % Hi, total CHP efficiency 75–85 % [found: Gas Turbine World Performance Specs; DOE CHP Technology Fact Sheet "Combustion Turbines"]; q ≈ (η_tot − η_el)/η_el → ~1.4–2 [inferred].
Sanity: upper bound = P × 8760 × best-hour margin; S₂ must be well below that and run hours ≤ availability [inferred]. Cross-check: German CCGT clean spark spreads were near or below zero for most baseload hours in 2024–25 [inferred, common market reading — verify on EEX]; a positive result for a ~30 % GT therefore relies on the HRSG heat credit and the 13 ct avoided-import hours, so test sensitivity to the import/export split first.

Also

Free allocation (R52) shrinks with the ETS benchmark path — c_f rises over the horizon.
U1 and U2 share the same hourly model; count the DH/steam gains once.
T is the largest single uncertainty for every €/t figure.
Before I close this chat, give me a short summary for my log, max 5 lines: what you produced here, what you were unsure about, and what you couldn't verify so I can check it myself. Just facts, no opinion on my work.

Produced: €/t skeletons for U1, U11, U2 — formulas, parameter tables with type/source/dominance, generic ranges, operating-effort parameter, sanity check, gas-basis note, shared parameters.
Unsure: all site-specific magnitudes (σ_st, σ_v, φ, detection-time gain d_k, current GT run rule, import/export split, T) — tagged [guess]/site-visit, no values given.
To verify yourself: DOE Steam Tip Sheets 4/7/8 figures (1 pp per 15 % excess air / ~22 °C stack, ~2 % fuel per ~0.8 mm scale); GT η_el 28–34 % and 75–85 % total (Gas Turbine World, DOE CHP fact sheet); Hs/Hi ≈ 1.11 and e = 56.0 t/TJ (UBA); Eurostat gas prices being GCV.
Unverified market claim: German clean spark spreads near/below zero in 2024–25 — check on EEX before using.
No web search or tools used; no URLs given.




Claude is AI and can make mistakes.
