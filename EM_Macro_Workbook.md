---
title: "EM Macro Workbook — Two-Day Structured Self-Study"
subtitle: "Day 1 (Thu): concepts + rates primer + Czech case. Day 2 (Fri): application + modeling + Hungary case + speed runs."
date: "May 2026"
---

# EM Macro Workbook — Two Days

**How to use this.** Eight 60-minute blocks. Originally structured as two day-windows; if you're compressing into a single intensive day (~8 hrs), that works — just take a real break between Block 4 and Block 5, and don't skip Block 3 (rates primer) under any circumstances. Each block is self-contained: read → quiz → drill → produce one written output.

**Working method.** Use a paper notebook or a digital sandbox file. Write your answers. Photograph or type up at end of the day. Send home → I review.

**Companion files in same folder:**
- `EM_Monetary_Policy_Notes.md` — the 5 concepts (theory)
- `EM_Rates_Primer.md` — yield curve, DV01, carry+roll, NDIRS (CRITICAL for you as FX trader being tested on rates)
- `EM_Country_Framework.md` — 90-min country recipe (the longer exercise — country analysis from scratch)
- `EM_Markets_Exercise_Prep.md` — fast-synthesis framework (the shorter exercise — digest material, present in 10 min)
- `EM_Macro_Reference.md` — one-page summary
- `EM_Quick_Modeling.md` — Excel + Python speed drills
- `EM_Trade_Pitch_Framework.md` — turning a view into a trade with adversarial stress-testing

**Note on the two exercises.** This workbook trains the **longer exercise** (country analysis from scratch). The **shorter exercise** (digest material → 10-min present) is trained separately via `EM_Markets_Exercise_Prep.md` — read it as a ~30-min warmup before Block 1 (it's light, mostly framework) and run its Drill 1 + Drill 2 each day. Both exercises share the same discipline: conclusion-first, interpret don't describe, always have a trade.

**Country focus:**
- **Day 1 (Thursday):** mini case study on **Czech (CZK)** — clean textbook fit, ideal first pass
- **Day 2 (Friday):** mini case study on **Hungary (HUF)** — political/fiscal overlay tests judgement
- **Day 2 also:** speed runs on **Colombia (COP)** and **Korea (KRW)** — abbreviated 30-min framework
- **Weekend with me:** mocks on harder/different countries (Egypt, Turkey, MENA, etc.)

**Self-marking.** Answers to all quizzes in the Answer Key at the end. Don't peek until you've attempted.

---

# Day 1 (Thursday) — Concepts + Rates Primer + Czech

## Block 1 (60 min) — Slack + Phillips Curve

### Read (20 min)

Open `EM_Monetary_Policy_Notes.md`. Read Concepts 1 and 2 (Slack and Phillips Curve). Slow down on the "DM vs EM" subsections — that's where judgment lives.

### Self-test quiz (10 min)

Write answers in your notebook. Don't peek.

**Q1.1** Define output gap in 15 seconds without jargon.

**Q1.2** Why is HP-filtered potential GDP unreliable at the most recent quarter?

**Q1.3** Name 3 alternative measures of slack when GDP-based output gap is unreliable.

**Q1.4** Country A has unemployment 4.5%, NAIRU estimated at 5%. What does this tell you about slack? About the likely Phillips effect on inflation?

**Q1.5** Write the expectations-augmented Phillips Curve from memory. Define every term.

**Q1.6** Inflation is rising. Headline CPI is 8%, core is 4%. Where is the inflation coming from? What does this imply for monetary policy?

**Q1.7** Name 3 specific reasons why the Phillips Curve is weak in EM. Give a country example for each.

### Bloomberg drill on Czech (15 min)

On Bloomberg, pull:

1. Czech CPI YoY history (last 24m): `CZCPIYOY Index` — note trajectory, peak, current
2. Czech core CPI: `CZCPICRY Index` (or via ECFC)
3. Czech unemployment: `CZUEUOA Index`
4. Czech real GDP YoY: `CZGGRPYY Index`
5. CNB output gap estimate: find latest CNB Inflation Report (DOC search or `BI`)

Note in your notebook:

- Output gap estimate (and source): __________
- Unemployment vs structural rate: __________
- CPI core vs headline gap (services-heavy or goods-heavy?): __________
- Is the Phillips link visibly working in Czech, or broken? __________

### Application exercise (15 min)

Write a 5-sentence paragraph: *"Based on slack and Phillips Curve analysis alone, where is Czech in its cycle, and what should the CNB be doing?"*

This corresponds to Slides 2+3 of the country framework. End with a "what I'm unsure about" note.

---

## Block 2 (60 min) — Taylor Rule

### Read (15 min)

Read Concept 3 in `EM_Monetary_Policy_Notes.md`. Then skim the Taylor PDF (https://warwick.ac.uk/fac/soc/economics/staff/jcsmith/policy/4taylor.pdf) — first 5 pages.

### Self-test quiz (10 min)

**Q2.1** Write the Taylor Rule (EM-applied form). Define every term.

**Q2.2** Explain the Taylor principle. Why does it matter operationally?

**Q2.3** Difference between r\* and the policy rate? Which is observable?

**Q2.4** Name 3 reasons an EM CB might deviate from textbook Taylor.

**Q2.5** Banxico target = 3% (±1%). Core CPI = 4.5%. Output gap = +0.2%. r\* = 2%. Compute Taylor-implied rate.

**Q2.6** If actual Banxico = 9.50%, is it above or below Taylor? Implication for the curve?

### Compute drill — 4 countries (25 min)

Build a Taylor calculator in Excel (see `EM_Quick_Modeling.md` Drill 1). Then populate for the four target countries:

| Country | Latest core CPI YoY | Inflation target π\* | Output gap | r\* assumption | Taylor-implied i\* | Actual policy rate | Gap (Actual − Taylor) |
|---|---|---|---|---|---|---|---|
| Czech (CZK) | | 2.0% | | 1.0% | | | |
| Hungary (HUF) | | 3.0% | | 1.5% | | | |
| Colombia (COP) | | 3.0% | | 2.5% | | | |
| Korea (KRW) | | 2.0% | | 0.75% | | | |

For each row, write a one-line interpretation: *"CB X is N bps [above/below] Taylor, implying [restrictive/accommodative/neutral]; curve should price [cuts/hikes/hold]."*

Pull data from Bloomberg ECFC / consensus.

### View formation (10 min)

For Czech (your Day 1 country): pull `CZK WIRP` to see market-implied path. Where does market price terminal? Where do you think terminal *should* be? Difference in bps?

One-sentence view: *"I expect CNB to [cut/hike/hold] [N bps] more than market prices over next 12m because [reasons]."*

---

## Block 3 (60 min) — Rates Primer (CRITICAL)

**This is the most important block for you.** Amit knows you're FX. He will probe rates depth. Spend full hour here.

### Read (35 min)

Open `EM_Rates_Primer.md`. Read Sections 1–8 carefully (yield curve, forward rates, DV01, carry+rolldown, instruments, real vs nominal, curve trading mechanics). Sections 9–11 are vocabulary — skim now, return later.

### Self-test (10 min)

Do drills D1–D6 at the end of `EM_Rates_Primer.md`. Answers in the Appendix of that file — don't peek.

### Apply to Czech (15 min)

Pull from Bloomberg:

- Czech swap curve: `CZSO3M`, `CZSO6M`, `CZSO1`, `CZSO2`, `CZSO5`, `CZSO10 Index`
- CNB policy rate: latest 2-week repo
- CZK 1y forward rate: from FX forward `CZK1Y Curncy` or use CIP

Note:

- **Curve shape**: upward / flat / inverted / humped? __________
- **1y rate vs policy rate**: implied 12m policy path = __________ bps
- **2s10s slope**: __________
- **Real ex-ante rate**: CNB policy − 1y CPI expectation = __________
- **Real rate vs r\* (CZK r\* ≈ 1.0%)**: __________
- **Likely curve trade if I want to express "CNB cuts more than priced"**: __________

Write this up as a 5-bullet summary. This is the rates leg of your Block 4 case study.

---

## Block 4 (60 min) — Mini Case Study: Czech (CZK)

### Setup (5 min)

You're now going to apply the full framework to Czech. Use the worksheet structure from `EM_Country_Framework.md`. Don't aim for slides — aim for a one-pager with all 8 sections in note form.

### The compressed 45-min country analysis

Set a 45-min timer.

**Minutes 0–5: Snapshot.** Fill the snapshot table.

**Minutes 5–15: Slack + Phillips analysis.** (Most of this from Block 1 — consolidate.)

**Minutes 15–25: Taylor calc.** Show working. State r\*. (Consolidate from Block 2.)

**Minutes 25–35: Transmission + Pass-Through assessment.** Identify dominant channel for Czech. Czech is open economy → FX channel important; mortgage market exists → interest-rate channel works moderately. Real ex-ante rate?

**Minutes 35–40: Misfit check.** Where does the framework fail for Czech? (Hint: Czech is one of the cleanest-fit EMs — Phillips Curve works reasonably; FX pass-through low; CNB very orthodox. Note this *positively* — it means the framework gives high-conviction signals here.)

**Minutes 40–45: Synthesise into one-sentence view + draft trade.** Format:

> *"I expect CNB to [hike / cut / hold] [N bps] more than market over next [N months] because [reasons]. The implied trade is [receive / pay] [tenor] [instrument] at [entry], target [level], stop [level], R:R [ratio]. Invalidation: [data event / level]."*

Include the rates leg construction: DV01, expected carry+roll, alternative tenors considered.

### Self-debrief (10 min)

Write at the bottom:

1. **What I'm confident in**: one sentence.
2. **What I'd need more data on**: 2–3 items.
3. **Most likely pushback from a senior PM**: anticipate one tough question and your answer.
4. **What the framework didn't capture about Czech**: one sentence.
5. **What I learned about rates mechanics that I didn't know before today**: one sentence.

---

## End of Day 1 (15 min)

Consolidate:

- Photograph each notebook page OR type up key answers
- Send to your personal email / cloud
- Note 3 concepts that felt shaky: __________

Material to send home:
- Block 1 quiz answers + Czech application
- Block 2 quiz answers + Taylor table for 4 countries
- Block 3 rates primer drills + Czech rates analysis
- Block 4 Czech mini case study + self-debrief

I'll review Friday morning before Day 2 starts.

---

# Day 2 (Friday) — Transmission + Modeling + Hungary + Speed Runs

## Block 5 (60 min) — Transmission + FX Pass-Through

### Read (20 min)

Read Concepts 4 and 5 in `EM_Monetary_Policy_Notes.md`. Transmission is conceptual — absorb. FX pass-through has the numerical table — pay attention.

### Self-test (10 min)

**Q3.1** Name the 5 transmission channels.

**Q3.2** Which 2 channels are typically weakest in EM, and why?

**Q3.3** Typical lag between policy hike and full effect on inflation?

**Q3.4** Country A has 30% USD deposits, weak local bond market, no functioning mortgage market. Which channel still works? Implication?

**Q3.5** Define FX pass-through in one sentence.

**Q3.6** Why is FX pass-through higher in EM than DM? 3 reasons.

**Q3.7** Country B has 25% pass-through. Currency depreciates 15% over 3 months. Expected 12m CPI impact? CB action?

**Q3.8** Why is real ex-ante rate more informative than nominal for assessing EM monetary stance?

### Hungary channel analysis (15 min)

For Hungary, fill in:

| Channel | Strength (Strong / Moderate / Weak / Broken) | Reasoning |
|---|---|---|
| Interest rate | | |
| Credit | | |
| Asset price | | |
| Exchange rate | | |
| Expectations | | |

Then: *"Given this transmission profile, how should MNB calibrate?"*

### Hungary FX pass-through (15 min)

- Latest known HUF pass-through estimate (BIS / MNB study / IMF): __________
- 6m FX move vs USD: __________
- Expected CPI impact: __________
- Is MNB pricing it in? __________

Three-sentence summary: *"In Hungary, FX pass-through is approximately [N%]. The recent FX move of [X%] implies [Y%] CPI impact over [Z months]. MNB is likely to [respond / look through]."*

---

## Block 6 (60 min) — Python + Excel Speed Drills

### Drill block 1 — Excel (30 min)

Open `EM_Quick_Modeling.md`. Build:

- **Drill 1** (Taylor calculator) — clean Excel sheet with sensitivity table. Tested for Czech, Hungary, Colombia, Korea.
- **Drill 2** (Real rate panel) — 8-country comparison. Sorted by Real rate − Neutral.
- **Drill 3** (Forward rate from spot rates) — populated for Czech and Hungary curves.

Target: all three in 25 min.

### Drill block 2 — Python (30 min)

If you have Python access at the desk:

- **Drill 4** (Time-series chart) — produce Czech CPI vs target chart. Save PNG.
- **Drill 5** (Carry+roll on swap) — Czech 5y receiver, show 3m carry + 12m rolldown.
- **Drill 7** (Curve plot) — Czech + Hungary swap curves side by side.

If no Python: do Drill 5 in Excel.

Target: all three in 25 min.

**Stretch (if time):** Drill 6 — pass-through regression on Hungary monthly data 2020–25.

---

## Block 7 (60 min) — Mini Case Study: Hungary (HUF)

### Setup (5 min)

Hungary is a step harder than Czech. Why:
- MNB has been credible but is politically pressured (Orban dynamics)
- Inflation higher than CE3 peers; cutting pace slower
- HUF carry trade is heavy positioning
- Fiscal slip / EU funding tensions are a recurring overlay

Use the worksheet from `EM_Country_Framework.md`.

### Compressed 45-min analysis

**Minutes 0–5: Snapshot.**

**Minutes 5–15: Slack + Phillips.** HUF: where is Hungary in its cycle? Phillips link historically weak (FX pass-through dominates).

**Minutes 15–25: Taylor calc.** What's MNB-Taylor gap? Be aware that MNB has a track record of being above Taylor due to FX-defence weight in their reaction function.

**Minutes 25–35: Transmission + FX pass-through.** HUF pass-through estimated ~20–30%. Dominant channel: FX. Interest-rate channel works but slower.

**Minutes 35–40: Misfit check.** Where does framework fail for Hungary?
- Hint 1: political pressure on MNB (potential fiscal dominance creep)
- Hint 2: HUF carry trade positioning skews expectations
- Hint 3: EU funding cycle interacts with fiscal credibility (term premium)

**Minutes 40–45: View + Trade.** State view, structure trade.

### Self-debrief (10 min)

Same format as Day 1 Block 4.

Note especially: **the framework misfit slide is the biggest test on Hungary**. You should be able to articulate 2–3 ways Hungary doesn't behave like a clean Taylor-rule country.

---

## Block 8 (60 min) — Speed Runs: Colombia + Korea

### Why this block

Speed runs build the muscle memory for handling a *new* country quickly. The full 90-min framework would take too long here — you'll do **30-min abbreviated versions** for two countries.

### Colombia (COP) — 30 min

Compressed:

- **Minutes 0–3:** Snapshot
- **Minutes 3–10:** Slack + Phillips (Colombia is commodity exporter — oil sensitivity; inflation has been sticky)
- **Minutes 10–18:** Taylor + transmission + pass-through (BanRep r\* est. ~2.5%; FX pass-through ~25%)
- **Minutes 18–25:** Misfit + view (Petro political risk; fiscal credibility wobbles)
- **Minutes 25–30:** One-sentence view + draft trade

### Korea (KRW) — 30 min

Compressed:

- **Minutes 0–3:** Snapshot
- **Minutes 3–10:** Slack + Phillips (Korea has slowing growth, modest inflation, AI/semi capex story)
- **Minutes 10–18:** Taylor + transmission + pass-through (BoK r\* est. ~0.75%; FX pass-through low ~15%; very developed financial system — all channels work)
- **Minutes 18–25:** Misfit (NPS structural USDKRW hedging; FSS regulatory layer)
- **Minutes 25–30:** One-sentence view + draft trade

### Comparative reflection (10 min — leftover from blocks)

After all 4 countries done, write 5 lines comparing them:

| Country | Where in cycle | Taylor gap | Real rate stance | Curve mispricing | Easiest trade |
|---|---|---|---|---|---|
| Czech | | | | | |
| Hungary | | | | | |
| Colombia | | | | | |
| Korea | | | | | |

Which country has the most clearly mispriced curve? Which has the highest-conviction trade? Why?

---

## End of Day 2 (15 min)

Consolidate:

- Day 2 quiz answers
- Hungary mini case study
- Colombia + Korea speed runs
- Cross-country comparison table
- Updated "what I learned + still unsure" log

Send everything to me end of Friday. I'll have it Saturday morning when we meet.

---

# Day 3+ (Saturday + Sunday — with me)

## Saturday plan

**AM (3 hrs):**
- Review your Day 1+2 work product line-by-line
- Targeted drilling on weakest areas
- **First mock**: I assign a fresh country (one of: Mexico, Chile, India, Poland), full 90-min timed drill, you build, you present to me

**PM (3 hrs):**
- Debrief mock 1
- **Second mock**: harder country (one of: Egypt, Turkey, Argentina, MENA peg country) — designed to test framework-misfit recognition
- Part 1 markets-exercise drill (chart pack interpretation)

## Sunday plan

**AM (2 hrs):**
- Third mock if needed, or focused Q&A drill
- Senior PM-style adversarial grilling on rates mechanics

**PM (2 hrs):**
- Polish opening line, opening 30 seconds, slide 1 wording
- Memorise cheat sheet (`EM_Macro_Reference.md`)
- Last sanity check on Bloomberg drills

---

# Answer Key

## Block 1 answers

**A1.1** Output gap = % difference between actual GDP and the level the economy could sustainably produce without inflation accelerating ("potential GDP"). Negative = slack; positive = overheating.

**A1.2** HP filter requires future data to identify trend. At the most recent quarter, you have no future data, so the filter under- or over-fits the trend at the end. Causes large revisions when new quarters arrive ("end-point problem").

**A1.3** Acceptable: unemployment gap vs NAIRU; capacity utilisation; PMI/business surveys; participation gap; credit gap; wage growth vs productivity; CPI/Survey-implied inflation expectations.

**A1.4** Unemployment below NAIRU → tight labour market → wage pressure → Phillips Curve says modest upward inflation pressure. CB likely on hawkish side or holding restrictive.

**A1.5** π = π_e + β(u\* − u) − ε. π = inflation, π_e = expectations, u = unemployment, u\* = NAIRU, β = slope, ε = supply shocks.

**A1.6** Headline well above core → volatile components (energy, food, FX-driven imports). Not labour-tightness driven. CB likely looks through if expectations anchored, or hikes modestly to anchor expectations even though slack isn't the culprit.

**A1.7** Any 3: FX pass-through dominates (Turkey 2021–23); expectations un-anchored (Argentina chronic); administered prices buffer signal (Egypt fuel, India food); informal labour markets weaken wage-bargaining link; supply shocks dominate (commodity exporters); structural breaks (IMF deals, devaluations).

## Block 2 answers

**A2.1** i\* ≈ r\* + π\* + 1.5(π − π\*) + 0.5·output_gap. i\* = recommended policy rate, r\* = real neutral rate, π\* = inflation target, π = actual inflation, output gap = (actual − potential) / potential.

**A2.2** Taylor principle: when inflation rises 1pp above target, raise the *real* rate, not just nominal. So nominal moves more than 1-for-1. Operationally: without this, the CB lets inflation drift up because real rates fall as inflation rises — destabilising.

**A2.3** r\* is the unobservable real rate consistent with output at potential and inflation at target — estimated from models. Policy rate is observable, set day-to-day by the CB. Only the policy rate is observable.

**A2.4** Any 3: FX dominance; fiscal dominance; political interference; effective lower bound; managed/pegged FX regime; unanchored expectations; explicit dual-mandate weighting.

**A2.5** π = 4.5%, π\* = 3%, π − π\* = 1.5%; output gap = 0.2%. i\* = 2% + 3% + 1.5·1.5 + 0.5·0.2 = **7.35%**.

**A2.6** Actual 9.50%; Taylor 7.35%; gap = +215bps (restrictive). Curve should price cuts; if curve prices fewer cuts than convergence implies, receive rates is the trade. Caveat: Banxico holds above Taylor partly to track Fed and stabilize MXN — so convergence may be slower.

## Block 5 answers

**A3.1** Interest rate, credit, asset price, exchange rate, expectations.

**A3.2** Credit (thin banking + corporate bond markets) and asset price (small equity markets, low housing finance) — usually weakest in EM.

**A3.3** Inflation effect: 12–18 months. Activity sooner (6–12m). FX channel fast (1–3m on headline CPI).

**A3.4** FX channel works. Implication: CB has limited grip on domestic inflation via rates; FX policy + reserves become primary tools; large rate moves needed to influence FX expectations.

**A3.5** Pass-through = fraction of an FX move that ends up in CPI over a given horizon (typically 12m).

**A3.6** Any 3: higher import intensity; higher inflation environment so re-pricing faster; USD-invoicing dominates; less hedging by importers; less developed local supplier base.

**A3.7** 25% × 15% = 3.75% CPI impact over 12m. CB likely hikes or signals hawkishly to break the FX → CPI loop.

**A3.8** Nominal rate doesn't tell you whether monetary policy is actually restrictive. 10% nominal with 12% inflation is negative real and accommodative; 4% nominal with 1% inflation is +3% real and restrictive. Ex-ante uses expected (forward-looking) inflation, what matters for behaviour.

---

*End of workbook. Photograph everything before you leave the desk Friday. Send home. Bring strong tea to Saturday's mock.*
