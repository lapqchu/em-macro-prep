---
title: "EM Macro Quick Reference"
subtitle: "One-page memory aid for daily use"
date: "May 2026"
---

# EM Macro Quick Reference

**A condensed version of the framework. Read on the tube. Out loud if you can.**

---

## The 5 Concepts in Plain English

1. **Slack** — Is the economy running below or above its sustainable speed? Output gap < 0 = slack, > 0 = overheating.
2. **Phillips Curve** — Tight labour market → wages → prices. `π = π_e + β(u\* − u) − ε`. Weak in EM; FX dominates.
3. **Taylor Rule** — Policy rate *should* be: `i\* = r\* + π + 0.5(π − π\*) + 0.5·output_gap` (simplified: 1.5 weight on inflation gap).
4. **Transmission** — Channels: interest-rate / credit / asset price / FX / expectations. In EM, FX dominates; bank/credit weaker; dollarisation/fiscal dominance break it.
5. **FX Pass-Through** — % of FX move into CPI. EM 20–50%; DM 5–15%. Higher in high-inflation regimes, lower when anchored.

---

## The 8-Slide Note Structure

1. **The View** — conclusion + trade + R:R in 30 seconds
2. **Cycle / Slack**
3. **Inflation (cyclical or non-cyclical?)**
4. **Taylor: actual vs implied**
5. **Transmission + Pass-Through**
6. **Where framework misfits**
7. **Curve & Trade**
8. **Risks & data to watch**

---

## The 90-Min Time Budget

- 10 min orient
- 35 min analyse (5 concepts)
- 15 min trade idea / curve
- 25 min build note
- 5 min rehearse

---

## Taylor Rule — Country r\* and Target Reference

| Country | r\* (approx) | π\* target | Comments |
|---|---|---|---|
| Brazil | 4–5% | 3% (±1.5%) | High r\* historically; BCB credible |
| Mexico | 2–3% | 3% (±1%) | Banxico tracks Fed closely |
| Chile | 0.5–1.5% | 3% | BCCh orthodox |
| Colombia | 2–3% | 3% (±1%) | |
| Peru | 1–2% | 2% (±1%) | BCRP very orthodox |
| Poland | 1–2% | 2.5% (±1%) | NBP somewhat political |
| Hungary | 1–2% | 3% (±1%) | MNB credible but political pressure |
| Czech | 0.5–1.5% | 2% | CNB front-foot |
| South Africa | 2–3% | 4.5% (3–6%) | SARB orthodox |
| India | 1–2% | 4% (±2%) | RBI flexible IT |
| Indonesia | 2–3% | 2.5% (±1%) | BI dual mandate (inflation + FX) |
| Turkey | 3%+ (unstable) | 5% | Politically distorted |
| Israel | 0.5–1.5% | 1–3% | BoI orthodox |
| Egypt | high, unstable | 7% (±2%) | FX-managed; fiscal pressure |
| Korea | 0.5–1.5% | 2% | BoK measured |
| Thailand | ~0.5% | 1–3% band | BoT cutting cycle |

**Note**: r\* in EM has wide error bars. Always state the assumption out loud.

---

## FX Pass-Through Bands (12m to headline)

- ~5–10%: US, deep DM
- ~10–20%: Euro Area, UK, AUD, CAD, NZD
- ~10–25%: EM Asia (KRW, TWD, THB, MYR, IDR, INR)
- ~20–30%: LatAm major (MXN, BRL, CLP, COP), South Africa, Poland, Hungary, Czech
- ~30–50%: Turkey, Argentina (less anchored), Egypt during shocks
- 50%+: hyperinflation regimes

---

## Opening Line Template

> *"My view on [Country] is [direction] on rates, expressed via [trade]. Three reasons: [A], [B], [C]. The single biggest risk is [D]."*

---

## Common Trade Expressions

| View | Trade |
|---|---|
| CB cuts more than priced (next 12m) | Receive 6m1y, 1y1y, or 1y2y |
| CB cuts persistently (longer cycle) | Receive 2y3y belly |
| CB stays restrictive (over-priced cuts) | Pay front-end |
| Short-end overshooting hike pricing | Receive front-end, tight stop |
| FX strong + lower inflation | Receive belly / receive long-end |
| Fiscal stress widening term premium | Bear-steepener |
| CB credibility wobble | Bear-steepener + watch FX |
| Real rate too high (over-restrictive) | Receive belly outright |

State: instrument, tenor, entry, target, stop, R:R, sizing, invalidation.

---

## "Framework Misfit" Flags

When you see these, say so out loud:

- **Administered prices** (Egypt fuel, India food, Indonesia rice) — buffers FX pass-through; weakens Phillips
- **Pegs and bands** (HKD, AED, SAR, KWD, OMR, BHD) — Taylor doesn't apply; CB is a Fed-importer; trade FX/basis, not domestic policy
- **Heavy dollarisation** (Argentina, parts of LatAm) — domestic rate weak transmission
- **Fiscal dominance** (Argentina chronic, Turkey 2021–23, possible MENA) — CB independence constrained
- **FX dominance / IMF regime** (Egypt post-Mar-24, Pakistan, Sri Lanka) — multilateral targets dictate, not Taylor
- **Capital controls** (China, India to a degree) — onshore curve disconnected from offshore
- **NEER-targeting** (Singapore — MAS targets NEER not rate) — Taylor doesn't apply
- **Resource-curse cycle** (Saudi, Nigeria, Russia) — terms-of-trade swamps domestic cycle

---

## 60-Sec Self-Check

1. Name the 5 concepts. (15 sec)
2. Recite the Taylor formula. (10 sec)
3. State one EM misfit. (10 sec)
4. State the 8-slide structure. (15 sec)
5. State the opening-line template. (10 sec)

---

## Bloomberg Functions

- **WIRP** `<ccy> WIRP` — market-implied policy rate path
- **ECFC** `<country> ECFC` — economic forecast aggregator
- **G** — graphs (CPI, FX, output gap, unemployment)
- **YCGT** — yield curves
- **CFTC** / **FXFA** — positioning + FX forwards
- **NDF** screens for restricted EM
- **NSN** / **TOP** — newswire

---

## Rates Quick Reference (see `EM_Rates_Primer.md` for full)

### Direction

- **Receive** = long bond synthetic = profit when yields fall
- **Pay** = short bond synthetic = profit when yields rise

### Sizing

- Always in DV01, not notional
- DV01 ≈ notional × tenor × 0.0001 (approximation)
- $1m × 5y swap ≈ $500 DV01

### Curve trades

- **Steepener**: pay short, receive long, DV01-neutral
- **Flattener**: receive short, pay long, DV01-neutral
- **Bull steepener**: rates falling, short falls more — CB starts cutting
- **Bear steepener**: rates rising, long rises more — fiscal stress / term premium
- **Bull flattener**: rates falling, long falls more — end of hiking, growth fears
- **Bear flattener**: rates rising, short rises more — CB hiking

### Carry + Roll

- Carry = fixed leg − floating leg, annualised
- Rolldown = expected MTM gain from curve aging (if curve static)
- Both should be quoted with any rates trade pitch

### Forward rates

- 1y2y forward ≈ (r₃ × 3 − r₁ × 1) / 2 [linear approximation]
- Forward curve = market-implied future rate path
- Compare forwards to your fundamental view → mispricing

### Real vs nominal

- Real rate = nominal − expected inflation
- Restrictive: real rate > r\*
- Accommodative: real rate < r\*

### EM-specific

- **NDIRS**: settled in USD, used for restricted currencies (BRL, COP, INR, TWD)
- **Onshore-offshore basis**: widens in stress, narrows in calm
- **Cross-currency basis**: spread in CCS — proxy for USD funding stress
- **Liquidity**: $10–25m clip standard EM; $50m+ shifts curve. Always discuss exit conditions when pitching.

---

## Things to Never Say

- "I'm not sure but I think..." → state view, state confidence, state alternative.
- "The market is wrong." → "I have a different view based on X."
- "I don't have a view." → you must have one.
- Forcing the framework. Flag the misfit.
- A number you can't defend. Estimate openly.

---

## Things to Always Do

- Lead with conclusion.
- State r\* assumption out loud.
- Flag framework misfits.
- Quantify wherever possible.
- State invalidation.
- Acknowledge risk before being asked.

---

*End. Re-read regularly — this is the muscle memory.*
