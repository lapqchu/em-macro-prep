---
title: "EM Trade Pitch Framework"
subtitle: "From macro view to tradeable expression, with adversarial stress-testing"
date: "May 2026"
---

# EM Trade Pitch Framework

**Purpose.** Turn a macro view into a defensible trade idea you can pitch to a senior PM (or your team) without getting torn apart. This framework integrates the five-layer architecture from your `em-macro-trader` skill — Willer (Tactical), Booth (Strategic), Jha (Rates Mechanics), Donnelly (FX Execution & Trade Management), James (Options) — into a single pitch flow.

**Companion files:**
- `EM_Monetary_Policy_Notes.md` — the macro analysis layer
- `EM_Country_Framework.md` — the 90-min country recipe
- `EM_Macro_Workbook.md` — practice exercises

---

## Section 1 — The 5-Step Pitch Build (use this every time)

### Step 1: One-sentence thesis

Strip the idea to one sentence. If you can't, you don't have a trade — you have a feeling.

Template:

> *"I expect [X] over [time horizon] because [primary driver], which is being [under / over]-priced by the market."*

Examples:
- *"I expect Banxico to deliver 100bps more cuts than priced in the next 12 months, driven by real-rate over-restrictiveness as core CPI converges to target."*
- *"I expect USDZAR to fall to 17.50 over the next 3 months as gold prices remain strong and SARB resists cutting despite peer EM CBs easing."*
- *"I expect the BRL 1y2y forward to compress 75bps as BCB's terminal rate gets repriced lower."*

If you've got jargon, sub-clauses, or "I think maybe..." — strip it. One sentence. Strong verbs.

### Step 2: Apply Willer's factor hierarchy (Tactical layer)

From your `em-macro-trader` skill: which of the four factors does the trade lean on?

| Factor | What it means | Strong / Weak for the trade |
|---|---|---|
| **Carry** | The cost of being early. Positive = pay you to wait. | |
| **Momentum** | Is the move already in motion? | |
| **Growth surprises** | Is data trending in your direction? | |
| **Valuation** | Are you buying cheap / selling rich? | |

A 4-of-4 trade is rare and high-conviction (Donnelly's "Five-Star"). Most trades are 2-of-4 or 3-of-4. **A 1-of-4 trade is a low-conviction bet; size accordingly or pass.**

Also note Willer's **65/35 global-local split**: 65% of EM returns come from global (DM rates, USD, risk sentiment, commodities) — 35% local. **Stress-test your local thesis against a hostile global backdrop**: would the trade still work if DXY rallies 3%, UST 10y +30bps, S&P −5%? If no, the trade is really a *long EM beta* expression in disguise — size and structure accordingly.

### Step 3: Apply Booth's 4D risk lens (Strategic layer)

Booth's 4D risk assessment from your skill. For the country:

| Dimension | Question | Answer |
|---|---|---|
| **SDm** (Sovereign Default macro) | What's the implied sovereign default probability? Anchored or rising? | |
| **Pr** (Political risk) | Election, regime stability, fiscal credibility? | |
| **U** (Unknown unknowns) | What might you not know? Sanctions, war, scandal? | |
| **E** (Exit liquidity) | Can you get out in stress? Spread / size / NDF mechanics? | |

**Booth's investor-base test**: who owns the trade you're putting on? If real-money is heavy-positioned the same way, your edge is thinner; if leveraged money is long and overcrowded, the exit liquidity is poor. Check CFTC, fast-money positioning surveys, and broker positioning indicators.

**Blow-up indicator check**: pick the top 3 indicators from Booth's checklist (e.g. external balance deterioration, FX reserve drawdown, real rate inversion, political escalation, IMF-program drift) — score yes/no. Two or more "yes" = upgrade the risk rating and size down.

### Step 4: Apply Donnelly's adversarial process (FX Execution layer)

This is the **steel-man-then-knock-down** routine. For every trade, before you pitch:

**(a) Steel-man the OTHER side.** Write the strongest possible argument *against* your view. If you can't make the counterargument convincing, you haven't done the work. Then beat it.

**(b) Decompose P&L into 6 components.**

| Component | Direction | Notes |
|---|---|---|
| **Direction** | | What you're paid on if you're right |
| **Carry** | | Cost / payoff of holding while waiting |
| **Roll** | | Roll-down or roll-up on the curve |
| **Vol** | | Implied vs realised — does vol regime support the trade? |
| **Correlation** | | What other positions / factors does this duplicate? |
| **Liquidity** | | Bid-offer, size you can do, exit conditions |

If you can't articulate one of these, you don't fully understand the trade.

**(c) Catalyst + timeline.** What event reprices the market? When? What's the carry cost if you're early?

**(d) Stress tests.** Three scenarios:
- Global risk-off (S&P −10%, DXY +3%, VIX 40)
- Unexpected Fed (50bps surprise either direction)
- Local shock specific to country (election, fiscal slip, ratings action)

For each: what does your trade do? Are you stopped out, or is it through-the-trough resilience?

**(e) Max drawdown tolerance + stop.** The level where the thesis is invalidated, *not* where you can't take more pain. Define before entering.

### Step 5: Size with Donnelly's Type I/II/III conviction

| Type | What it is | Size range |
|---|---|---|
| **Type III** | Speculative idea, low conviction, scout position | 1% book risk |
| **Type II** | Solid setup, moderate conviction, clear catalyst | 3% book risk |
| **Type I** | Five-Star qualified, high conviction, multi-factor alignment | 6% book risk |

Apply YTD adjustment: if you're +20% YTD, you can lean into Type I sizing; if you're flat or down, downgrade by one type. Donnelly's variance vs process diagnostic kicks in if you're on a losing streak — is it variance (process intact) or broken (process failure)?

For an EM rates trade, translate to **DV01** terms (Jha's framework):

- Book size $50m, daily P&L vol target 5bps of book = $25k daily P&L vol
- Type II trade with 25% of daily vol budget = $6,250 daily P&L vol allocation
- Pick tenor with appropriate volatility (e.g. 5y SAGB with ~5bps daily vol → DV01 = 1,250)

Always express trade in DV01 not notional. Jha is religious about this.

---

## Section 2 — The Pitch Itself (60-second format)

**Lead with the trade, not the macro.** Senior PMs care about the trade first; the macro is supporting evidence.

### The 6-line pitch

1. **The trade**: instrument, tenor, direction, entry, target, stop, size, R:R
2. **The why**: one-sentence macro thesis
3. **The factor case**: which of carry/momentum/growth/valuation supports
4. **The risk**: biggest single thing that breaks the trade
5. **The catalyst & timeline**: what event reprices, when
6. **The exit**: target take, stop invalidation, time-stop if any

Example:

> *"Receive 1y2y MXN NDIRS at 9.25%, target 8.25%, stop 9.75%. R:R 2:1. Sized $400k DV01.*
>
> *Thesis: Banxico is 200bps above Taylor; market prices only 75bps of convergence in 12m. I think it's closer to 150bps.*
>
> *Carry positive (3bps/month roll on the belly), momentum supportive (core CPI down for 4 prints), growth softening (output gap closing negative), valuation cheap vs Banxico-Fed real differential.*
>
> *Biggest risk: Fed re-prices hawkish, Banxico forced to track. That's the stop.*
>
> *Catalyst: 5 June CPI print + 27 June Banxico decision.*
>
> *Time-stop: 3 months. If we haven't seen 50bps of move by August, re-evaluate."*

This is ~45 seconds spoken. Practise it out loud until it flows.

---

## Section 3 — Pitching to Your Desk

When you pitch internally to seniors / colleagues:

### Before the pitch

- **Run the trade through the 5 steps yourself.** Don't pitch with the work undone.
- **Anticipate the top 3 pushback questions.** Write down the answers in advance.
- **Bring numbers, not adjectives.** "Real rate is 4.5%" beats "real rate looks high."

### During the pitch

- Lead with the trade (1-sentence trade statement).
- Then thesis (1 sentence).
- Then proof points (3 max).
- Then "the way I'd be wrong" (proactively — they'll respect you).
- Pause for questions.

### Common pushbacks and structured responses

**"What's the catalyst?"**
> *"[X date / Y event]. Without that, I'd give it 6 months on time-stop and re-evaluate."*

**"It's already in the price."**
> *"Market prices N bps; my view is M bps; the difference is [reason — usually a positioning, factor, or framework gap]. Specifically..."*

**"Why this country / this tenor?"**
> *"Cleaner expression than [alternative] because [carry / roll / liquidity / correlation]. Also: alternatives I considered were X and Y; I rejected those because [reason]."*

**"How does it correlate with [existing position]?"**
> *"Net beta to [factor] is [positive/negative/neutral]. If we want a more orthogonal expression, the alternative is [Z]."*

**"How big can you do?"**
> *"[N] DV01 at the current bid-offer, scaling up to [M] over 2 days. Beyond that, slippage gets material."*

**"What stops you out?"**
> *"[Level + reason]. The level is calibrated to thesis-invalidation, not just discomfort."*

**"Why now?"**
> *"[Catalyst window + factor alignment + entry level]."*

---

## Section 4 — Trade Idea Generation Themes (May 2026 backdrop)

Some current themes you might investigate as candidate pitches. Pick one or two to develop into full proposals. **Don't take these as views — they're starting points. Run each through your full process before pitching.**

### Theme A — Banxico real-rate normalisation (MXN)

- Setup: Banxico held restrictive while Fed cuts. Real ex-ante rate ~6%. Core CPI converging to target.
- Question: how much room to cut more than market prices?
- Expression: receive 1y2y MXN NDIRS or 6m1y. Pay attention to USDMXN — Banxico hates a weaker peso, so FX direction is a constraint.
- Stress test: Fed pauses hiking-cycle expectations → Banxico stays restrictive. Mitigant: FX as the leading indicator.

### Theme B — BCB end-of-cycle (BRL)

- Setup: BCB has been cutting; question is *terminal* level and pace.
- Real rate still ~7%; output gap closing; FX has been steady. Disinflation broadening from food into services.
- Expression: receive 1y2y BRL NDIRS or 2y3y belly. Or sell short-end vol.
- Stress test: fiscal-credibility shock (Lula admin slippage, ratings action). Mitigant: BCB has stayed cautious; baseline cuts are credibility-anchored.

### Theme C — SARB cutting cycle (ZAR)

- Setup: SARB has been hawkish; 2/6 dissent at recent meeting; gold-driven ZAR has been firm.
- Real rate ~4%; output gap modestly negative; coalition stable post-GNU.
- Expression: receive 1y2y SAGB, or pay-receive flatten. Or long ZAR vs CNH (cleaner expression of resource tailwind vs China weakness).
- Stress test: Trump tariffs hit risk sentiment; ZAR sells off. Mitigant: gold supports the cross; could pair with a long gold tail-risk hedge.

### Theme D — PLN bear-steepener (Poland)

- Setup: NBP cutting cycle; fiscal supply at long-end on EU funding-cycle changes.
- Real rate ~3%; output gap closing; political signal volatile.
- Expression: pay 10y PLN swap vs receive 2y, DV01-neutral bear-steepener.
- Stress test: ECB cuts harder than expected — Polish long-end rallies. Mitigant: term premium at long-end has historically been resilient on supply.

### Theme E — Asian rates dispersion (KRW / TWD / THB)

- Setup: BoT cutting (1.0%), BoK measured cuts, CBC holding. Asian rates have diverged.
- Expression: pair trade — receive KRW 2y, pay TWD 2y (or vice versa depending on view); or BoT receive belly.
- Stress test: AI capex cycle reversal. Mitigant: factor-specific risk; size accordingly.

### Theme F — Curve trades you can do at the desk

- **Receivers in the front for any EM where real rate >5% and CB has paused** — typical mean-reversion play.
- **Pay short, receive long in any EM where curve is overly inverted** — bull-steepener.
- **Cross-country pairs** — Mexico vs Brazil, Poland vs Hungary, Korea vs Taiwan — where macro reaction-function diverges from market pricing.

---

## Section 5 — The Adversarial Self-Test (run before pitching)

Steal this from your `em-macro-trader` skill. Before pitching to your team, run yourself through these 12 questions:

1. **Steel-man the opposite view in 3 sentences.** Could you defend it?
2. **What's the carry?** If negative, what's the timeline before it eats the trade?
3. **What's the roll?** Working with you or against you?
4. **What positioning data do I have?** CFTC, broker positioning, fast-money lean?
5. **What's the catalyst path?** Sequence of events that reprices.
6. **Is the move correlated to anything else in the book?** If yes, am I over-exposed to the factor?
7. **Can I get out?** Bid-offer, size capacity, NDF mechanics if applicable.
8. **What's the analogous historical episode?** Has this setup happened before? What rolled out?
9. **What does the curve already price?** Be specific in bps.
10. **What's my edge?** Information, framework, positioning, time horizon — pick one.
11. **What's the worst-case loss in DV01 and dollars?** Can I survive it without forced unwind?
12. **If I lose 1% of the book on this, what was the diagnostic — bad thesis, bad execution, bad luck?** Decide *before* the trade.

If you can't answer all 12 cleanly, don't pitch yet.

---

## Section 6 — Five-Star Trade Qualification (Donnelly)

A "Five-Star" trade is the rare setup where all five factors align:

1. **Macro thesis** — clear, defensible, asymmetric
2. **Market positioning** — not crowded against you; ideally crowded with you on the way out
3. **Technical setup** — entry level reasonable, stop level defensible, target plausible
4. **Catalyst** — specific event in known time window
5. **Risk-reward** — at least 2:1 in your favour

Five-Star = Type I sizing (6% book risk).

3 or 4 stars = Type II (3%).

1 or 2 stars = Type III if you trade it at all (1%) — or pass.

---

## Section 7 — Behavioural Checks (from your skill)

Before sizing up:

- Am I trading from variance or from process?
- Am I revenge-trading after a loss?
- Am I over-exposed to a single factor (e.g. all my positions are short USD)?
- Is this trade a "story I want to be true" or a "thesis I've proven to myself"?
- What does my YTD performance suggest about sizing right now?

If any of these is off, downgrade sizing by one type or wait 24 hours.

---

## Section 8 — Practical Internal-Pitch Sequence

The actual sequence at the desk, in order:

**Day 1 (today): Idea generation.**
- Skim Section 4 above. Pick one theme that fits your current screen / data / market read.
- Apply Steps 1–3 (one-sentence thesis, Willer factors, Booth 4D).

**Day 2 (tomorrow): Build out.**
- Apply Steps 4–5 (Donnelly adversarial, sizing).
- Run Section 5 self-test.
- Draft the 6-line pitch (Section 2).

**Day 3 (over weekend): Pre-mortem.**
- Run Section 6 (Five-Star check) and Section 7 (behavioural).
- Write down the top 3 anticipated pushbacks + your answers (Section 3).

**Day 4 (next week, market-conditions permitting): Pitch.**
- Find the right moment with the right senior.
- Lead with the trade.
- Have your numbers ready.
- Listen more than you talk after the pitch.

**Day 5 (after pitch): Capture.**
- Write down what they pushed back on.
- Write down what they didn't ask about that you expected.
- Update your framework.

The point of pitching internally is *not* to convince them. It's to find the holes in your thinking by exposing it to people who have seen many trades.

---

*End. This document and your `em-macro-trader` skill together cover the full trade lifecycle. Use them in combination.*
