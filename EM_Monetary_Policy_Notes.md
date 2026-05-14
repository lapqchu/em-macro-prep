---
title: "EM Monetary Policy — Study Notes"
subtitle: "5 core concepts, first-principles, EM-applied"
date: "May 2026"
---

# EM Monetary Policy — Study Notes

**Purpose.** Self-study notes for a junior EM trader looking to systematise how they think about central bank reaction functions, inflation dynamics, and the relationship between domestic macro and the rates curve. Designed to be applied to any EM country in ~90 minutes of focused analysis.

**Companion files (in the same folder):**
- `EM_Country_Framework.md` — the 90-min operating recipe for applying these concepts to any country
- `EM_Macro_Reference.md` — one-page summary for daily reference
- `EM_Macro_Workbook.md` — structured exercises and self-tests
- `EM_Trade_Pitch_Framework.md` — turning a macro view into a tradeable expression with adversarial stress-testing

**Reading order:** Section 0 first. Then Concepts 1 → 5 in order (each builds on the prior). Sections 6–9 after.

**Integration with `em-macro-trader` skill (your own work):** the country analysis here maps onto the **Tactical layer (Willer/Chandran/Lam)** and the **Strategic layer (Booth)** of your framework. Where the standard monetary-policy framework misfits a particular country, the Booth 4D risk lens flags *why* (sovereign default risk, political risk, unknown unknowns, exit liquidity).

---

## Section 0 — Read This First

### What the framework is for

The five concepts below form a closed loop that lets you go from a country's macro state → an estimate of where the policy rate *should* be → a view on whether the curve is pricing it correctly → a trade.

1. **Slack / Output Gap** — Is the economy running below or above its sustainable speed?
2. **Phillips Curve** — When the economy runs hot (low slack), inflation rises (in theory; often badly broken in EM).
3. **Taylor Rule** — A recipe that tells you what the central bank's policy rate *should* be, given inflation and slack.
4. **Transmission** — When the central bank moves rates, how does that change reach the real economy?
5. **FX Pass-Through** — When the currency moves, how much of that move shows up in domestic inflation?

The loop: slack drives inflation (2), which combined with slack drives the policy rate (3), which propagates through the economy (4), with FX as one channel and a separate inflation source (5).

### The single most important habit

When the framework you've internalised doesn't fit the country you're analysing, **say so out loud**. Forcing the model is the mark of a junior. Naming the misfit — *"the Phillips Curve doesn't transmit cleanly here because of [X]; I weight FX pass-through more heavily"* — is the mark of someone with judgment.

Booth's 4D risk assessment in your `em-macro-trader` skill catches this naturally: countries with high SDm (sovereign default macro), high Pr (political risk), or low E (exit liquidity) often don't fit textbook monetary policy.

---

## Concept 1 — Business Cycle, Output Gap & Slack

### Intuition first (no jargon)

Imagine the economy is a car. The car has a comfortable cruising speed — call it 60mph — that it can sustain without overheating or wearing out the engine. That cruising speed is **potential output**.

Sometimes the car drives slower than 60mph (recession — engine cool, factories idle, people unemployed). Sometimes it drives faster than 60mph (boom — engine hot, factories full, labour scarce). The gap between actual speed and 60mph is the **output gap**.

- Output gap **negative** → economy below potential → "slack" exists → inflation pressure low → central bank can be loose.
- Output gap **positive** → economy above potential → "overheating" → inflation pressure high → central bank must tighten.
- Output gap **zero** → economy at potential → equilibrium.

That's it. That's the whole concept. Everything else is measurement.

### Mechanics

**Output gap** = (Actual GDP − Potential GDP) / Potential GDP, expressed as %.

Example: actual GDP $100bn, potential GDP $102bn → output gap = −2.0% (running 2% below sustainable level).

But here's the trick: **potential GDP is not observable**. You estimate it. Three common approaches:

1. **HP filter** (Hodrick-Prescott statistical filter): smooths actual GDP into a trend line. Pros: simple. Cons: end-point bias — recent data is unreliable.
2. **Production function approach**: estimate potential from capital stock, labour force, TFP. Pros: theoretically grounded. Cons: needs decent data on all three.
3. **Multivariate filters** (IMF's "MV filter"): combine GDP, inflation, unemployment to back out potential consistent with the Phillips Curve. This is what IMF Article IVs use.

**Alternative measures of slack** (when GDP-based output gap is unreliable, especially in EM):

- **Unemployment gap** = actual unemployment − NAIRU. NAIRU = the unemployment rate consistent with stable inflation.
- **Capacity utilisation** — % of factories at full pelt. PMI surveys also useful.
- **Labour force participation gap** — relevant for EM where informality hides true slack.
- **Credit gap** — credit-to-GDP deviation from trend (BIS tracks this).

### DM vs EM — where this gets messy

In a clean DM country, you have decent GDP data, low informality, and can use a multivariate filter with confidence.

In EM, the model breaks for five reasons:

1. **Data quality.** GDP revisions in EM can be huge (Mexico, India, Egypt routinely revise quarters by 50bp+).
2. **Structural breaks.** A country that just devalued, defaulted, signed an IMF deal, or had a regime change can't be HP-filtered cleanly.
3. **Informal economy.** If 30%+ of activity is informal (Egypt, Nigeria, Peru, Mexico to a degree), measured GDP understates the level.
4. **Supply-side shocks dominate demand.** EM inflation is often FX/food/fuel driven — not output-gap driven. The Phillips link gets noisy.
5. **Commodity dependence.** For commodity exporters (Chile, Colombia, South Africa, Russia), the cycle is partly terms-of-trade. Potential output itself shifts when copper/oil prices shift.

### What can break the concept

- **Supply shocks**: oil spike → inflation up + output below potential. Slack didn't cause inflation.
- **Hysteresis**: deep recessions permanently lower potential (skill loss).
- **Productivity surprises**: AI/capex can lift potential; CB might think overheating when really potential stepped up.

### Application — how you use this

When analysing a country, the slack section answers:

- "Where is this economy in its cycle — early recovery, mid-cycle, late-cycle, recession?"
- "How tight is the labour market — unemployment vs NAIRU, wage growth, vacancies?"
- "What's the IMF's output gap estimate vs the central bank's?" (These often disagree. If the CB has a *more positive* gap than the IMF, the CB will be more hawkish than the IMF projects.)

**Look for divergence.** The juicy trades exist where the CB's view of the cycle differs from the market's, or from the IMF's. That's where rates are mispriced.

### Self-test

1. Define output gap in 10 seconds without jargon.
2. Why is HP filter unreliable at end-points?
3. Name 3 alternative measures of slack when GDP-based output gap is unreliable.
4. Why is output gap fragile in EM? Give 3 reasons.
5. IMF says Country X output gap is −1.5%; CB says 0.0%. What does that imply for the policy rate path vs market expectations?

---

## Concept 2 — The Phillips Curve

### Intuition first

Tight labour market → workers can demand higher wages → firms pay them and pass costs to consumers as higher prices. So **low unemployment → wage growth → price inflation**. The Phillips Curve.

Reverse: when the labour market is slack, wage pressure fades and inflation cools.

The Phillips Curve is the engine connecting Concept 1 (slack) to inflation. Without it, you can't get from "economy running hot" to "CB should hike."

### Mechanics

Expectations-augmented Phillips Curve:

**π = π_e + β · (u\* − u) − ε**

Where:
- **π** = actual inflation
- **π_e** = inflation expectations
- **u** = actual unemployment rate
- **u\*** = NAIRU
- **β** = slope coefficient
- **ε** = supply shocks (oil, FX, food)

In plain English: inflation today = expectations + labour market overheating + supply shocks.

### The two breakdowns that matter

1. **Flat Phillips Curve.** Post-2008 in DM, the curve flattened: unemployment dropped sharply but inflation didn't pick up. Why? (a) expectations firmly anchored at target; (b) globalisation imported deflation; (c) measurement issues.
2. **Supply-shock-dominated inflation.** In 2021–23, inflation spiked from supply chains, energy, food — not labour-market tightness. The Phillips link was masked by supply.

### DM vs EM — the bigger differences

In EM the Phillips Curve is often weak or unreliable:

1. **FX pass-through dominates.** EM inflation is often more driven by exchange-rate moves than domestic labour. A 10% FX depreciation can lift CPI 2–4% in one year — far more than any plausible domestic slack effect.
2. **Anchoring is fragile.** Countries with a history of high inflation (Turkey, Argentina, parts of LatAm pre-2000) — expectations move quickly with realised inflation. The curve becomes vertical.
3. **Administered/regulated prices.** Energy, food, utility subsidies in many EMs (Egypt, India, Indonesia, MENA) mean CPI doesn't fully reflect market forces.
4. **Informal labour markets.** NAIRU is hard to measure. Recorded unemployment may be low but mostly informal — no wage-bargaining power.

### What can break it

- Expectations un-anchor (Turkey 2021–23, Argentina chronically).
- Supply shocks dominate the cyclical signal.
- Subsidy reforms, VAT changes, administered-price shifts cause one-off inflation.
- Structural labour-market changes (migration, formalisation, demographics) shift NAIRU.

### Application — how you use this

Phillips Curve gives you:

- "Is inflation cyclical (slack-driven, responds to monetary policy) or non-cyclical (FX/food/energy)?"
- "Are inflation expectations well-anchored?" If yes, CB has room to look through one-off shocks. If no, CB must hike aggressively to re-anchor.
- "Where is wage growth vs productivity?"

For the trade: non-cyclical inflation → CB should look through → lower rates than market prices → **receive rates** in the belly. Cyclical and unanchored → hike-and-keep-hiking → **pay** the front end.

### Self-test

1. Write the expectations-augmented Phillips Curve and define each term.
2. Why did the Phillips Curve appear "dead" in DM after 2008?
3. Name 3 reasons the Phillips Curve is weaker in EM.
4. How do you measure inflation expectations? Name 3 sources.
5. EM country has CPI 8%, headline rising, output gap −2%, unemployment at NAIRU. What's the most likely inflation driver, and what should the CB do?

---

## Concept 3 — The Taylor Rule

### Intuition first

The Taylor Rule is a **recipe** for the central bank. Given (a) inflation vs target and (b) output vs potential, it spits out the policy rate the CB should set.

Not a *law* — CBs don't blindly follow it. But a useful **reaction-function benchmark**. Compare actual rate to Taylor-implied rate → you see whether the CB is dovish or hawkish vs the rule. From that, you form a view on whether the curve is mispriced.

### Mechanics

Classic Taylor (1993):

**i\* = r\* + π + 0.5 · (π − π\*) + 0.5 · (y − y\*)**

Where:
- **i\*** = recommended nominal policy rate
- **r\*** = real neutral rate ("R-star")
- **π** = current inflation (often core)
- **π\*** = inflation target
- **(π − π\*)** = inflation gap
- **(y − y\*)** = output gap as %
- The two 0.5s are **the weights** — Taylor's original suggestion.

Worked example (US-style):
- r\* = 0.5%, π = 3.0%, π\* = 2.0%, output gap = 0.5%
- i\* = 0.5 + 3.0 + 0.5·(3.0 − 2.0) + 0.5·(0.5) = 0.5 + 3.0 + 0.5 + 0.25 = **4.25%**

If actual policy rate is 4.50% → roughly Taylor-neutral.
If 3.50% → dovish vs the rule by ~75bps.

### The version you actually use in EM

**i\* ≈ r\* + π\* + 1.5 · (π − π\*) + 0.5 · output_gap + γ · FX_term**

The 1.5 on the inflation gap reflects the "**Taylor principle**": if inflation rises 1pp above target, raise the **real** rate, not just the nominal. So nominal moves more than 1-for-1.

**The FX term** is critical for EM. Many EM CBs (Banxico, BCB, BSP, RBI, NBP, BoT, SARB) layer in a partial FX-stabilisation objective. Currency weakens → they hike more than textbook Taylor would imply.

### Reaction functions vary — build a mental table

| CB | Mandate | Effective weights |
|---|---|---|
| **Fed** | Dual: inflation + employment | Inflation 0.5–1.5, output gap 0.5; FX ~0 |
| **ECB** | Price stability primary | Inflation 1.5; output gap 0.5; FX small |
| **BoE** | Inflation target 2% | Inflation 1.0–1.5; output gap 0.3–0.5; FX small |
| **BoJ** | Price stability + financial stability | Asymmetric — focus on getting inflation up; FX recently relevant |
| **BCB (Brazil)** | Inflation target | Inflation 1.5+; output gap moderate; FX moderate (officially zero) |
| **Banxico** | Inflation target | Inflation 1.5; FX significant (real-rate parity to Fed) |
| **TCMB (Turkey)** | Inflation officially; politically unorthodox | Historically low to inflation gap; FX dominant in stress |
| **SARB** | Inflation target band 3–6% | Inflation 1.0; FX moderate |
| **CBE (Egypt)** | Inflation target nominally; FX-managed de facto | Heavy FX weighting |
| **PBoC (China)** | Multiple objectives — growth, FX, financial stability | Inflation weight low; FX & growth weight high |
| **MAS (Singapore)** | NEER-targeting — doesn't use a rate | Taylor doesn't apply at all |

### What can break the rule

- **Effective lower bound** (DM 2008–22). CB pinned at zero, uses QE/forward guidance instead.
- **Fiscal dominance**: government deficits so large CB can't hike without bankrupting sovereign (Argentina, Turkey under certain regimes).
- **FX dominance**: currency in free-fall, CB hikes to defend FX regardless of slack/inflation (Turkey 2018, Argentina, Egypt 2024).
- **Political interference**: unorthodox political leader forces CB off the rule (Erdogan 2021–23).
- **r\* uncertainty**: r\* is unobservable and shifts. Post-COVID, many believe DM r\* is higher than pre-COVID.

### Application — how you use this

Taylor is your **anchor**:

1. Take current core inflation, inflation target, output gap.
2. Compute back-of-envelope Taylor rate (r\* ≈ 1–2% for most EMs, coefficient 1.5 on inflation gap, 0.5 on output gap).
3. Compare to actual policy rate.
4. Actual **above** Taylor → CB restrictive → expect cuts → **receive rates** front to belly.
5. Actual **below** Taylor → CB dovish or constrained (FX/fiscal dominance) → either curve under-prices hikes, or you need a different expression.

**State your r\* assumption out loud.** Shows you understand the rule's sensitivity.

### Self-test

1. Write the Taylor Rule from memory. Define each term.
2. What is the "Taylor principle" and why does it matter?
3. Why do EM central banks deviate from textbook Taylor?
4. CB X has policy rate 8%, inflation 6%, target 4%, output gap +1%, r\* = 1.5%. Compute Taylor-implied rate. Is the CB restrictive or accommodative?
5. Country Y: r\* = 2%, inflation 12%, target 5%, output gap −3%. Taylor says? Now the currency is in free fall — what's likely to happen to actual policy regardless of Taylor?

---

## Concept 4 — Transmission Mechanisms

### Intuition first

The CB sets the **policy rate** (overnight). But the economy doesn't care about overnight rates — it cares about mortgages, business loans, consumer credit, bond yields, asset prices, FX. **Transmission** is how the policy rate ripples through to real activity and inflation.

Five main channels. In DM, all five work reasonably. In EM, some are weak or broken, and the FX channel often dominates.

### The 5 channels

**1. Interest rate channel.** Policy rate ↑ → deposit & lending rates ↑ → less borrowing → less consumption & investment → lower demand → lower inflation. Lag: ~12–18 months.

**2. Credit channel.** Policy rate ↑ → banks tighten lending standards → credit availability shrinks → real activity slows. Strong in bank-based finance (Europe, EM Asia) vs market-based (US).

**3. Asset price channel.** Policy rate ↑ → bond yields ↑ → equity prices ↓ (discounted cash flows) → wealth effect → consumers spend less. House prices similar.

**4. Exchange rate channel.** Policy rate ↑ → currency strengthens (carry, IR differential) → imports cheaper → headline inflation falls. Stronger currency → exports less competitive → external demand for output falls. Strong in small open economies.

**5. Expectations channel.** CB credibility → anchored expectations make Phillips Curve flatter and inflation more controllable. Forward guidance works via this channel.

### DM vs EM — what's different

In EM:

- **Interest rate channel weaker.** Many EM households don't have mortgages (or have fixed-rate); businesses borrow from informal channels; corporate bond markets thin.
- **Credit channel weaker.** Many EM banks are loan-deposit funded; less sensitive to wholesale funding cost. State-owned banks lend on policy, not market signals.
- **Asset price channel weaker.** EM stock markets small relative to GDP; few households own equities; housing informal/unfinanced.
- **FX channel dominant.** EM economies more open (high trade-to-GDP), higher pass-through, FX-elastic.
- **Expectations channel fragile.** EM expectations less anchored; CB credibility matters more, but harder to maintain.
- **Dollarisation reduces effectiveness.** Where loans/deposits are partly USD (Argentina, parts of LatAm), the domestic policy rate has weaker grip.
- **Fiscal dominance can short-circuit transmission.** If government forces CB to buy bonds, tightening signal is undermined.

### What can break the mechanism

- **Banking crisis** — banks under stress don't pass rate signals correctly.
- **Zero/effective lower bound** — policy maxed out.
- **Fiscal dominance** — as above.
- **Dollarisation** — as above.
- **Capital controls** — cut the FX channel.
- **Administered/regulated prices** — energy/food don't respond to rates.

### Application — how you use this

Transmission tells you **how fast and strongly** policy moves will work:

- "If the CB hikes 100bps, when does it show up in inflation?" Typical: 12–18 months for full effect on activity; FX channel faster (1–3 months for headline CPI pass-through).
- "Which channels are working?" If weak banks, no mortgage market, but free-floating FX → FX channel does most of the work.
- "What's the right pace of tightening?" Fast transmission → CB doesn't need to hike as much.

For trade: weak transmission → CB stays restrictive longer → curve too steep → **receivers in the belly**. FX-dominant transmission → CB constrained by FX → trade FX directly alongside rates.

### Self-test

1. Name the 5 transmission channels.
2. Which 2 are typically weakest in EM, and why?
3. Typical lag between policy hike and full effect on inflation?
4. A country has 30% USD-denominated deposits, weak local bond market, no functioning mortgage market. Which channel still works? What does that imply?
5. If transmission is impaired, what does the CB do? What does it mean for the yield curve?

---

## Concept 5 — Exchange Rate Pass-Through

### Intuition first

A weaker currency makes imports more expensive in local-currency terms. Those higher import prices feed into domestic CPI directly (imported consumer goods) and indirectly (input costs, then passed through to retail). The fraction of an FX move that ends up in CPI is the **pass-through coefficient**.

Example: currency devalues 50%. Pass-through 0.4 (40%) → expect CPI +20% over 12–24 months, all else equal. That's why EM CBs panic about FX.

### Mechanics

Simple model:

**Δπ_t = α + β · ΔFX_t + γ · ΔFX_{t-1} + δ · (output gap) + ε**

β + γ is the **pass-through elasticity**. Typical estimates:

| Country | Approx 12m FX pass-through to headline CPI |
|---|---|
| US | ~5–10% |
| UK, Euro Area | ~10–15% |
| Australia, Canada | ~10–20% |
| EM Asia (KRW, TWD, THB) | ~10–25% |
| Mexico | ~20–30% |
| Brazil | ~10–20% (declined as anchored) |
| South Africa | ~20–30% |
| Turkey | ~30–50% |
| Argentina | ~50–80% (very high) |
| Egypt | very high during FX shocks (40%+) |

### Three drivers of pass-through

1. **Import intensity.** Open economies (Singapore, HK) have higher pass-through — more of consumption is imported.
2. **Inflation environment.** High/volatile inflation regimes → higher pass-through (firms re-price faster). Anchored low-inflation regimes → lower pass-through.
3. **Pricing currency of trade.** Most global trade invoiced in USD (Gita Gopinath's "dominant currency paradigm"). So pass-through is mostly through USD-cross moves, not trade-weighted moves.

### The asymmetries

- **Asymmetric in size**: 30% depreciation in one shot passes through more than three 10% depreciations spread out (regime change effect).
- **Asymmetric in direction**: depreciations pass through faster and more fully than appreciations. Firms raise prices on cost shocks; reluctant to cut.
- **Asymmetric in cycle**: pass-through higher when output gap positive (firms can pass through) and lower when slack is large (absorbed in margins).

### Interaction with monetary policy

Two key implications:

1. **FX-defence hikes.** In high-pass-through EMs, the CB hikes aggressively when FX depreciates — *not* because of overheating but to break the FX → CPI loop. Looks like a Taylor-rule violation; actually rational.
2. **Real interest rate matters more than nominal.** Use **real ex-ante rates** (policy rate − expected inflation) and compare to neutral. Nominal can look high but be loose in real terms.

### What can break the relationship

- **Administered prices** in CPI basket buffer pass-through (fuel subsidies, regulated utilities).
- **Hedging by importers** — large importers forward-hedge, smoothing pass-through.
- **Strategic pricing** — dominant retailers may absorb FX moves to maintain market share.
- **Substitution to local goods** — high tariffs/quotas mean less imported goods.
- **Capital controls** decouple onshore FX from market pressure.

### Application — how you use this

FX pass-through tells you:

- "How urgent is the FX situation for the CB?" High pass-through + weak FX = CB must respond.
- "Is current rate stance high enough?" Compare ex-ante real rate vs neutral.
- "Where will the curve react?" High pass-through means FX shocks immediately reprice the front end.

For trade: FX strengthening → expect CPI lower than consensus → CB cuts more than priced → **receive rates** in the 6m–2y. FX heading weaker → opposite.

### Self-test

1. Define pass-through in one sentence.
2. Why is pass-through higher in EM than DM?
3. Name 3 factors that drive pass-through *down* in a country.
4. Country has 30% pass-through; currency drops 20%. Expected 12m CPI impact? What does the CB do?
5. Why is "real ex-ante rate" more informative than nominal for assessing EM monetary stance?

---

## Section 6 — Tying It Together: The Country Logic Tree

When analysing a country, work through:

1. **Slack** — where is the economy in its cycle? (Concept 1)
2. **Inflation driver** — cyclical (slack-driven, Phillips) or non-cyclical (FX/food/energy)? (Concept 2)
3. **Taylor benchmark** — given slack + inflation, what should the policy rate be? Is the CB above, at, or below? (Concept 3)
4. **Transmission** — which channels work? How fast/strong will policy effects be? (Concept 4)
5. **FX pass-through** — how exposed is inflation to FX? Is FX a constraint on policy? (Concept 5)
6. **Misfits** — where does the framework break down for *this* country?
7. **View** — one sentence: *"I expect the CB to [hike / cut / hold] over the next [N] months because [the 2–3 key reasons]; the curve currently prices [X], which is [too hawkish / too dovish]."*
8. **Trade** — express the view in the rates curve. See `EM_Country_Framework.md` and `EM_Trade_Pitch_Framework.md`.

---

## Section 7 — Reading Priorities

### Must-read

- **John Taylor, "Discretion versus Policy Rules in Practice" (1993)** — the original Taylor paper. The PDF is at https://warwick.ac.uk/fac/soc/economics/staff/jcsmith/policy/4taylor.pdf. Read in full. Note the original 1993 weights, the r\* discussion, the criticism section.
- **IMF Article IV Staff Reports** for 2–3 EM countries (Brazil, Mexico, South Africa, India good choices). Read the "Monetary Policy" section in each. They explicitly discuss output gap, Phillips Curve, transmission, FX pass-through — same framework you're building.

### Should-read (weekend)

- **Mishkin, "The Economics of Money, Banking, and Financial Markets"** — chapters on monetary policy strategy, transmission mechanisms, inflation. Specifically:
  - "Strategy and Tactics of Monetary Policy" (Taylor Rule, reaction functions)
  - "Transmission Mechanisms of Monetary Policy"
  - "Aggregate Demand and Supply Analysis"

- **Siddhartha Jha, "Interest Rate Markets" (2011)** — your skill references this already. Re-read the chapters on:
  - Yield curve construction and shape
  - Curve trades (steepeners, flatteners, butterflies)
  - Monetary policy and the yield curve
  - Carry and rolldown decomposition
  These are your **trade-expression** vocabulary.

- **Willer, Chandran & Lam, "Trading Fixed Income and FX in EM" (2020)** — in your `em-macro-trader` skill. Re-read:
  - Factor hierarchy (carry / momentum / growth surprises / valuation)
  - Rate cycle timing rules
  - Event playbooks (CB surprises, IMF programs, emergency hikes)

- **Booth, "Emerging Markets in an Upside Down World" (2014)** — in your skill. Re-read:
  - 4D risk assessment (SDm / Pr / U / E)
  - Blow-up indicators
  - Risk perception inversion

- **BIS, "Inflation in Emerging and Developing Economies"** — search "BIS Phillips Curve emerging markets" for the working papers. Gives EM-specific evidence on Phillips Curve flatness and FX pass-through.

### Bloomberg functions

- **WIRP** `<ccy> WIRP` — market-implied policy rate path
- **ECFC** `<country> ECFC` — economic forecast aggregator (GDP, CPI, unemployment consensus)
- **G** for graphs — CPI, core CPI, FX, output gap, unemployment
- **YCGT** — yield curves (`<country> YCGT`)
- **CFTC** / **FXFA** — positioning + FX forwards
- **NDF curves** — for restricted-currency EM
- **NSN** / **TOP** — newswire

---

## Section 8 — Things to Avoid Saying

- "I'm not sure but I think..." → state the view, then state the uncertainty: *"My base case is X, confidence Y; alternative is Z"*.
- "The market is wrong because..." → markets aren't wrong; you have a different view based on different information or weights. Frame that way.
- Forcing the framework on a country where it doesn't fit. Better: *"The textbook Taylor doesn't apply cleanly here because [reason]; what I look at instead is..."*
- "I don't have a view" — you must have one.
- Generic statements ("the curve looks steep") without numbers ("the 1y2y curve at 75bps is wider than the post-2020 median of 40bps").

---

## Section 9 — 60-Second Self-Diagnostic

Run this before sleeping each night:

1. Name the 5 concepts. (15 sec)
2. State one EM "misfit" for each. (30 sec)
3. State the Taylor formula. (15 sec)

If you can't do all three in 60 seconds without notes by Saturday night, slow down and re-read.

---

## Appendix — Glossary

- **NAIRU**: non-accelerating inflation rate of unemployment.
- **r\* (r-star)**: real interest rate consistent with output at potential and inflation at target. Unobservable; estimated.
- **Output gap**: (actual GDP − potential GDP) / potential GDP, %.
- **Core inflation**: CPI ex food & energy. Smoother signal of underlying trend.
- **Pass-through**: fraction of FX move that ends up in CPI.
- **Anchored expectations**: inflation expectations close to and stable around CB's target.
- **NDIRS**: non-deliverable interest rate swap. EM equivalent of vanilla IRS where underlying is non-deliverable.
- **DV01**: dollar value of a 1bp change.
- **Receiver / Payer**: in a swap, the party receiving / paying fixed.
- **Steepener / Flattener**: long-end yield rises faster (steepener) or vice versa.
- **Real rate**: nominal rate − expected inflation. "Ex-ante real rate" is forward-looking.
- **Neutral rate**: policy rate that neither stimulates nor restricts.
- **Fiscal dominance**: fiscal policy constrains monetary policy.
- **FX dominance**: FX considerations override domestic Taylor logic.

---

*End. Next: `EM_Country_Framework.md` for application.*
