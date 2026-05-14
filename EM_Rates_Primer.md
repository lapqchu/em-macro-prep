---
title: "EM Rates Primer for FX Traders"
subtitle: "First-principles: yield curves, DV01, carry+roll, NDIRS, basis"
date: "May 2026"
---

# EM Rates Primer for FX Traders

**Why this file exists.** If your background is FX, you have intuition for forwards, basis, carry-via-FX, and intervention dynamics. But interest rates products use different vocabulary, different risk units, and different P&L decomposition. A senior PM testing you on EM macro will *push you off FX and onto rates* because that's where the depth tests live. This file builds your rates intuition from first principles — no priors assumed.

**Sources integrated:** Siddhartha Jha's *Interest Rate Markets* (rates mechanics, DV01 thinking, carry+rolldown) and the rates section of Willer/Chandran/Lam's *Trading FI in EM* (which you have digested in your `em-macro-trader` skill).

**Reading order.** Sections 1–5 give you the vocabulary. Section 6 onwards is application: how to read a curve, how to construct a trade, how to talk about P&L.

---

## Section 1 — What Is a Rate?

### A rate is a discount, not just a number

When you see "5y Czech govvy yields 3.50%", that means: if you buy a 5-year Czech government bond at today's price, hold to maturity, and reinvest all coupons at 3.50%, your annualised return is 3.50%.

Equivalently, the bond's price today is the present value of all future cashflows, discounted at 3.50%.

**Inversion intuition (drill this until it's automatic):**

- Yields **up** → bond prices **down**.
- Yields **down** → bond prices **up**.

A receiver of fixed in a swap is **economically equivalent to owning a bond** (you receive the coupon-like fixed leg, you take duration risk). A payer of fixed is **economically equivalent to being short a bond**.

So:
- **Receive rates** = long bond = makes money when yields fall
- **Pay rates** = short bond = makes money when yields rise

### Three types of rates you'll encounter

1. **Spot rate** (zero-coupon rate, "zero"): the rate that discounts a single cashflow at time T. Example: the 5y zero rate is what you'd earn on a 5-year zero-coupon bond.
2. **Forward rate**: the rate, agreed today, for a future period. Example: the "1y2y forward rate" is the rate, agreed today, for the 2-year period starting 1 year from now.
3. **Par rate** (also "swap rate"): the rate on a coupon bond / vanilla swap that makes its price equal to par (face value). This is what you actually trade in IRS/NDIRS. The yield curve in most markets is quoted in par swap rates.

For practical EM trading, the **par swap rate** is your main number. Forwards you compute from par rates.

---

## Section 2 — The Yield Curve

### What you see

A yield curve is a chart: x-axis = tenor (1m, 3m, 6m, 1y, 2y, 5y, 10y...); y-axis = the rate at each tenor.

The curve's **shape** has economic content:

- **Upward-sloping (steep)**: short rates low, long rates high. Markets expect future short rates to rise (CB will hike, or term premium is high).
- **Flat**: short ≈ long. Markets expect short rates to be stable.
- **Inverted (downward-sloping)**: short rates higher than long. Markets expect CB to cut significantly. Often a recession signal in DM. Common in restrictive EM where CB is in a hiking pause but cuts are priced.
- **Humped**: short rates rise, peak somewhere in the belly (e.g. 2–3y), then decline. Often when CB has more hikes priced but cuts after that.

### Why this matters for monetary policy analysis

When you compare your Taylor-implied policy rate path to the market, you read it off the curve:

- 1y rate vs current policy rate → market's expectation of average policy rate over the next year.
- Forward 1y rate at 12m horizon → what market thinks policy will be in 12 months.

Example: Banxico at 9.50%. 1y MXN NDIRS at 8.50%. Means market prices ~100bps of cuts on average over the next year. If your Taylor says Banxico should be at 7.00%, you think the market is under-pricing cuts by 150bps. **Receive 1y NDIRS** at 8.50% is your expression.

### Steepening vs flattening (vocabulary)

- **Steepening**: long-end yield rises more than short-end (or short falls more than long).
- **Flattening**: long-end yield falls more than short-end (or short rises more than long).
- **Bull steepener**: rates falling generally, short falls more than long ("bull" because long-bond owners win).
- **Bear steepener**: rates rising generally, long rises more than short.
- **Bull flattener**: rates falling generally, long falls more than short.
- **Bear flattener**: rates rising generally, short rises more than long.

In monetary policy cycles:
- **CB starts cutting** → bull steepener at first (short rallies hardest), then bear steepens if growth recovers.
- **CB starts hiking** → bear flattener (short sells off hardest), then bull flattens if expectations of recession build.

---

## Section 3 — Forward Rates: The Hidden Curve

### Definition

A **forward rate** is the rate, agreed today, for borrowing/lending in a future period.

Notation: "**1y2y forward**" = the 2-year rate starting 1 year from today.

### The no-arbitrage formula

If you can buy a 3y zero at rate r₃ or a 1y zero at r₁ then roll into a 2y zero starting in 1y at r₁₂ (the 1y2y forward), the two paths must give the same total return:

(1 + r₃)³ = (1 + r₁)¹ × (1 + r₁₂)²

So:

**r₁₂ = [(1 + r₃)³ / (1 + r₁)¹] ^ (1/2) − 1**

(In practice with EM swap rates, the formula is usually approximated linearly because the rates are quoted nominal and the maturities aren't huge.)

### Why forwards matter

The forward curve is the **market-implied path of future rates**. When you say "the market prices 100bps of cuts in 12 months," you're really reading off the 12m forward 1y rate minus the spot 1y rate (or similar).

The forward curve also tells you the **breakeven rate path**: if rates evolve exactly along the forward curve, you make zero carry on a swap. Any deviation from the forward path generates P&L.

### Two example reads

1. *"The Czech 1y1y forward is 100bps below the current 1y rate."* → Market prices ~100bps of cuts between now and 12m from now.
2. *"The Hungary 6m6m forward is above the 6m spot."* → Market prices hikes (or at least no cuts) over the 6–12m period.

Forward rates are the **engine** of curve trading. Get comfortable.

---

## Section 4 — DV01: The Risk Unit

### Why DV01 not notional

In FX, you size by notional ($1m EURUSD). In rates, you size by **DV01** — the dollar P&L from a 1bp move in rates.

Why? Because $1m notional of a 2y swap and $1m notional of a 30y swap have *vastly* different risk. The 30y has roughly 15× the DV01 of the 2y. Sizing by notional is meaningless.

### Definition

**DV01 (Dollar Value of a 01)** = the P&L on a position from a 1bp parallel shift in the yield curve.

For a swap of notional N, tenor approximately T years, DV01 ≈ N × T × 0.0001 (rough approximation).

Example: 5y MXN NDIRS, notional $10m. DV01 ≈ $10m × 5 × 0.0001 = $5,000. Translation: a 1bp move in 5y MXN rates moves your P&L by $5,000.

(For more precision, use modified duration × 0.0001 × dirty price.)

### Using DV01 to size

If your daily P&L vol target is $25,000/day, and the asset has 5bps daily volatility, your DV01 should be $25,000 / 5 = $5,000.

If the asset has 8bps daily vol, DV01 should be smaller: $25,000 / 8 = $3,125.

You **always** quote your trade in DV01 terms when pitching:

> "$5,000 DV01 in 1y2y MXN NDIRS, which is approximately $25m notional, sized to give $25k daily P&L vol."

### DV01-neutral construction

A "DV01-neutral" steepener pays short, receives long, with the two legs sized so they have *equal but opposite* DV01.

Example: 2s10s steepener in BRL.
- 2y BRL NDIRS DV01 = 1.9 per $1m notional
- 10y BRL NDIRS DV01 = 8.5 per $1m notional
- To make $5,000 DV01 of steepener: pay $5,000 DV01 in 2y ($5m × 1.9 = $9,500... wait, let me redo) → pay $2.63m notional in 2y × DV01 1.9 = $5,000. Receive $588k notional in 10y × DV01 8.5 = $5,000. Net DV01 of any parallel shift is zero; only differential moves between 2y and 10y generate P&L.

---

## Section 5 — Carry and Rolldown (Jha is religious about this)

### Why P&L isn't just direction

When you put on a rates trade, your P&L over time has multiple sources:

- **Direction**: rates moving in your favoured direction
- **Carry**: the income you earn (or pay) while holding
- **Roll**: the change in mark-to-market price as the swap ages along a fixed curve

Many EM rates trades have **positive carry + roll** of 50–100bps per year, which is a lot of free money if the curve doesn't move.

### Carry: the running yield

If you **receive** fixed in a 5y swap at 7%, and the floating leg pays 6% over the next 3 months, your **carry** is the net = 7% − 6% = +1% annualised (or +25bps over 3 months).

You're earning that whether rates move or not. That's why receivers in steep curves are powerful — they pay you to wait.

Notation:
- "Carry to 3m" = expected P&L over 3 months if the curve stays static and you hold the trade.
- Positive carry = paid to hold.
- Negative carry = costs you to hold.

### Rolldown: the curve-aging effect

Imagine you receive 5y today at 7%, and the 4y rate is 6.5%. If the curve **doesn't move** at all, in 1 year your position is now a "4y receiver at 7%" but the market 4y rate is 6.5%. You're 50bps "in the money" through pure aging — you receive 7% but the market gives 6.5%. That's **rolldown**.

So if you held the 5y receiver for 1 year with a static curve, your total P&L would be:
- Carry (running income): ~1% if the curve is upward-sloping
- Roll (mark-to-market gain from aging): another ~50bps if 5y → 4y rolldown is 50bps

Total ~150bps return. That's why "**roll + carry**" is the headline number for any rates trade.

### Reading roll+carry on Bloomberg

`<CCY> SWAP CARRY` or compute manually:
- 3m carry = (Fixed leg rate − 3m floating rate forecast) × 0.25
- 3m rolldown = (current N-year rate − current (N − 0.25) year rate) × DV01 (approx)

Aim for trades where (Direction + Carry + Roll) × probability beats (Loss) × (1 − probability).

### Donnelly's adversarial decomposition (your skill)

Run every rates trade through:

| Component | Direction | Notes |
|---|---|---|
| **Direction** | | Your view |
| **Carry** | | Free money / cost |
| **Roll** | | Aging effect |
| **Vol** | | Implied vs realised — does vol regime support? |
| **Correlation** | | What else in the book? |
| **Liquidity** | | Bid-offer, size capacity |

You should be able to articulate all six components for any trade you pitch.

---

## Section 6 — The Instruments

### IRS (Interest Rate Swap)

A swap where one party pays fixed and the other pays floating (typically a benchmark like SOFR / EURIBOR / ESTR / SONIA / TONA).

**Vanilla IRS exists in deliverable EM currencies**: KRW (CRS / IRS), CZK, HUF, PLN, ZAR, MXN (mostly deliverable), ILS, INR, IDR (NDIRS more common).

### NDIRS (Non-Deliverable IRS)

For currencies with capital controls or restricted onshore markets — BRL, IDR (still common), KRW (also has NDIRS), TWD, INR, PEN, COP — the swap settles in USD based on the differential between fixed and floating, but the local currency never crosses. Settlement is in cash USD.

**Why this matters for you:** NDIRS quotes vs onshore IRS can diverge — that's the **onshore-offshore basis**. In stress, this basis widens (offshore demand for paying outweighs supply).

### OIS (Overnight Index Swap)

Floating leg is the overnight rate (Fed funds, ESTR, SONIA, TONA, ESTR). Used for short-dated views and policy-rate path.

In EM: less common as standalone, but the front-end of curve trading often references OIS or short-tenor swap rates.

### FRA (Forward Rate Agreement)

A bilateral contract: agree today to pay (or receive) a fixed rate at a future date for a future period. "FRA 3x6" = the 3-month rate starting 3 months forward.

Less used in EM but you'll see it for explicit forward-rate expressions.

### Currency basis (cross-currency swap)

A "**cross-currency basis swap**" exchanges fixed-vs-floating in two currencies. The **basis** is the spread between the foreign-currency floating rate and the USD floating rate, that makes the swap fair.

A negative EUR/USD basis means EUR funding is *more expensive* than implied by interest-rate parity — i.e. there's a premium to borrow USD via FX swaps.

In EM, basis is a critical proxy for capital flow stress: EM currencies with sudden negative basis indicate USD funding strain.

---

## Section 7 — Real vs Nominal Curves

### The basics

- **Nominal rate** = what you actually receive on a swap.
- **Real rate** = nominal − inflation expectations.
- **Breakeven inflation** = nominal rate − real rate. The inflation rate at which nominal and inflation-linked perform the same.

### Inflation-linked bonds / swaps

In DM and some EMs, you can trade **inflation-linked bonds** (TIPS in US, ILBs in UK, ATPs in Australia, NTN-Bs in Brazil) or **inflation swaps**.

Why this matters: if you have a view on inflation specifically (not just direction of nominal rates), you trade the **breakeven** = long inflation-linked, short nominal (or vice versa).

In EM:
- **Brazil**: NTN-B (linked to IPCA) is the deepest EM inflation-linked market.
- **Mexico**: CETES are nominal; UDIs are inflation-linked (linked to UDI unit).
- **Chile**: BCU (nominal) vs BCP (UF-linked, real).
- **South Africa**: I-bonds linked to CPI.
- **Israel**: full nominal / real curve (CPI-linked since 1948).
- Most other EMs: very limited inflation-linked liquidity. You trade nominal and back out implied real.

### How to use real rates

The **ex-ante real rate** = nominal policy rate − expected inflation (1y CPI consensus).

Compare to your estimate of neutral real rate (r\*):
- Real rate >> r\* → policy is restrictive → rates will likely fall (receive)
- Real rate << r\* → policy is accommodative → rates will likely rise (pay)

This is one of the most-used heuristics in EM rates trading.

---

## Section 8 — Curve Trading Mechanics

### Why the curve matters more than the level

A directional bet on rates falling is exposed to global rate moves (Fed, ECB, risk-off). A *curve* trade — paying one tenor, receiving another — is **DV01-neutral to parallel shifts** and only reacts to relative-tenor moves. Much cleaner expression of an idea.

### The four basic curve trades

| Trade | Construction | View |
|---|---|---|
| **Steepener** | Pay short, receive long, DV01-neutral | Long-end yield will rise relative to short |
| **Flattener** | Receive short, pay long, DV01-neutral | Long-end yield will fall relative to short, or short rise |
| **Butterfly (long wings)** | Pay 2y, receive 5y (2x), pay 10y; net DV01 = 0 | The belly is expensive vs the wings — expect convergence |
| **Butterfly (short wings)** | Receive 2y, pay 5y (2x), receive 10y; net DV01 = 0 | The belly is cheap vs the wings |

### Curve in the policy cycle

| Stage | Short rate | Long rate | Curve shape |
|---|---|---|---|
| Late cycle, CB hiking | Rising fast | Slow / steady / falling | Flattening |
| End of hiking cycle | Stable, high | Falling | Bull flattener |
| Start of cutting cycle | Falling fast | Falling more slowly | Bull steepener |
| Mid-cycle / re-acceleration | Stable | Rising | Bear steepener |

### Reading curves in the workbook

When you pull a curve:
1. **Is the curve normal-shaped (upward-sloping), flat, inverted, or humped?**
2. **Where is the belly (most curved part)?** Usually 2–5y. The belly is where most of the policy-cycle uncertainty sits.
3. **Where is the 1y rate vs the spot?** → market-implied 1y average policy rate.
4. **Where is the terminal rate?** → lowest point of the forward curve.

---

## Section 9 — How EM Rates Differ from DM Rates

Critical for your case study:

| Dimension | DM | EM |
|---|---|---|
| **Curve depth** | All tenors deep | Often 1m–5y deep, longer tenors thin |
| **Settlement** | Mostly deliverable | NDIRS common for restricted currencies |
| **Onshore-offshore basis** | Negligible | Material, widens in stress |
| **Liquidity in size** | $50–100m clip easy | $10–25m clip standard, $50m+ shifts the curve |
| **Term premium volatility** | Modest | High — fiscal supply, ratings, FX stress all move it |
| **Bid-offer in stress** | Widens 1–2x | Can widen 5–10x or freeze |
| **Convexity** | Mostly linear in tenor | Non-linear — basis, fixings, capital controls bite |
| **Funding** | Repo, banks, dealers | Less efficient — funding cost matters more for size |

When pitching an EM rates trade, **always discuss liquidity / exit conditions**. Booth's 4D risk lens E (exit liquidity) catches this.

---

## Section 10 — The FX-Rates Connection

Since you're an FX guy, this is the bridge:

### Covered interest parity (CIP) and the FX forward

The FX forward rate is determined by interest-rate differentials:

**F = S × (1 + i_quote) / (1 + i_base)**

E.g. 1y USDMXN forward, S = 17.0, i_USD = 4.5%, i_MXN = 9.5%:
F = 17 × 1.095 / 1.045 ≈ 17.81

If the forward implied by CIP differs from the traded forward, there's an arbitrage — typically arbitraged out by banks. The **gap** in EM is the onshore-offshore basis / NDF basis.

### When FX and rates diverge

EM currencies sometimes show:
- **FX strong + rates rich** (yields low): foreign portfolio inflows, central bank "winning" — but vulnerable to reversal.
- **FX weak + rates rich**: CB hiking to defend FX, but markets price end-of-cycle and rates rally.
- **FX weak + rates cheap** (yields high): classic FX stress + sell-off in rates. CB likely to hike or intervene.
- **FX strong + rates cheap**: paradoxical — usually means structural inflows (commodity boom, sovereign wealth fund) + low domestic inflation. Korea / Taiwan often look like this.

### The cross-asset trade

A view on EM monetary policy is often best expressed as:
- **FX leg + rates leg combined** — e.g. long ZAR + receive 1y ZAR NDIRS (CB cuts but supportive of FX as gold-linked).
- **Real-rate trade** — receive nominal, short FX (capture real disinflation).
- **Pair across countries** — pay rates in CB-hawkish country, receive rates in CB-dovish country, DV01-neutral. Use FX hedge between the two.

---

## Section 11 — Real-World Vocabulary You'll Hear

| Term | Meaning |
|---|---|
| "Receiver" | The party receiving fixed in a swap. Profits when yields fall. |
| "Payer" | The party paying fixed. Profits when yields rise. |
| "Pay the 2y" | Pay fixed in a 2y swap (i.e. short the 2y bond synthetically). |
| "Bond rallies" | Bond price up = yield down. |
| "Bonds sell off" | Bond price down = yield up. |
| "Curve bear-steepens" | Curve steepens with long-end rising. |
| "Roll-down on the belly" | The implicit P&L from aging in the 2–5y area of the curve. |
| "Carry into the print" | Positive carry held until a data release. |
| "DV01-neutral" | The two legs of a trade have equal but opposite DV01. |
| "Riskless arb" | Almost never exists in EM rates. If something looks like one, you're missing the funding cost or capital constraint. |
| "Slippage" | Difference between expected trade price and actual fill. |
| "Steepener vs flattener" | See Section 8. |
| "Conditional trade" | Trade that only triggers if a specific event occurs (e.g. conditional receiver on Fed cut). |
| "Term premium" | Excess return for holding long-dated bonds over rolling short ones. |
| "Curve carry" | Carry on a curve trade (steepener / flattener), not outright. |
| "Basis" | Spread between two related but distinct yields (e.g. NDIRS vs IRS, swap spread). |

---

## Section 12 — Quick Drills (do these once you've read Sections 1–8)

**D1.** A 5y swap pays 6.5%. The 4y rate is 6.0%. If the curve stays static, what's your 12m rolldown on a 5y receiver, approximately?

**D2.** You receive a 2y MXN NDIRS at 9.0%. Notional $10m. What's your approximate DV01?

**D3.** The Brazil 1y2y forward is 9.0%. The 3y rate is 10.0%. What's the 1y rate?

**D4.** You want to put on a $5,000 DV01 Hungary 2s10s steepener. The 2y HUF NDIRS DV01 is 1.9 per $1m notional; the 10y is 8.7 per $1m. What notionals do you trade?

**D5.** Czech 1y rate is 4.0%. Czech expected CPI 12m forward is 2.5%. Estimated CNB neutral r\* is 1.0%. Is monetary policy restrictive, neutral, or loose?

**D6.** Korea 5y NDIRS at 3.0%. KRW depreciates 5% over the next month. BoK has zero pass-through from FX (hypothetically). What happens to 5y KRW NDIRS yield? Now assume 20% pass-through — what happens?

(Answers in Appendix.)

---

## Section 13 — Reading List Priority

For Thursday and Friday at the desk, in priority order:

1. **This file** — read it cover-to-cover, twice if you can.
2. **Jha, Chapter 1 (Yield Curve construction) + Chapter 2 (Curve Trades)** — these chapters in your `em-macro-trader` skill have the rates fundamentals.
3. **Jha, the carry+rolldown chapter** — Section in your skill called `jha-rates-mechanics-checklists.md` has the carry evaluation checklist.
4. **Willer/Chandran/Lam rates chapter** — in your `em-macro-trader` skill: `willer-chandran-lam-digest.md`, rates section (factor hierarchy applied to rates).
5. **Booth on EM-specific risk** — `booth-checklists.md` for 4D risk + blow-up indicators.

---

## Appendix — Drill Answers

**D1.** 5y rolldown ≈ (5y rate − 4y rate) × DV01 effect ≈ 50bps × DV01. As 12m P&L on $10m notional and ~5y DV01 of ~$5,000 per bp: 50 × $5,000 = $250,000 over the year. As % return on notional: ~2.5%. Plus carry separately.

**D2.** 2y MXN NDIRS, $10m notional, tenor ~2 years. DV01 ≈ $10m × 2 × 0.0001 = $2,000. (More precisely with modified duration but $2k is the right ballpark.)

**D3.** Using approximation: (1+r₃)³ = (1+r₁)¹ × (1+r₁₂)². Solve: (1.10)³ = (1+r₁) × (1.09)². 1.331 = (1+r₁) × 1.1881. So 1+r₁ = 1.120. r₁ ≈ 12.0%. (Notice the curve is steeply inverted — 1y > 3y. That's a typical late-hiking-cycle EM shape.)

**D4.** Pay 2y: $5,000 / 1.9 = $2.63m notional. Receive 10y: $5,000 / 8.7 = $575k notional. Net DV01 = 0 on parallel shift. Curve steepens by 1bp → ~+$5,000 P&L (if steepening means 10y up vs 2y).

**D5.** Real rate = 4.0 − 2.5 = 1.5%. r\* = 1.0%. Real rate > r\* by 50bps → policy is modestly restrictive. Implication: if data softens, CNB has room to cut.

**D6.** With zero pass-through: 5% FX move has no effect on rates. With 20% pass-through: 5% FX move → 1% additional CPI over 12m. If anchored at 2% target, the breach matters → BoK might hike or pause cuts → 5y rates would sell off (rise). Magnitude depends on positioning and prior expectations.

---

*End of primer. Read this twice. Practise the drills until you can do them in 30 seconds. Senior PMs spot weak rates intuition in seconds — strong rates intuition signals you're ready for a buy-side rates+FX seat.*
