---
title: "EM Macro — Quick Modeling Drills"
subtitle: "Excel + Python templates for fast on-the-day modeling"
date: "May 2026"
---

# Quick Modeling Drills

**Why this matters.** Under time pressure (90 mins), you cannot waste 20 mins fumbling with Excel formulas or trying to remember matplotlib syntax. You need muscle memory for the 5–6 things you might need to compute or visualise:

1. Taylor-implied rate with adjustable inputs
2. Real rate vs neutral comparison
3. Forward rate from spot rates
4. CPI / FX / GDP time-series chart
5. Carry + roll on a swap
6. Pass-through regression / scatter

This file gives you ready-made templates. **Drill them at the desk this week** so they're automatic.

**Method:** for each drill, the goal is to do it in ≤ 5 minutes from a blank workbook / blank Python file.

---

## Drill 1 — Taylor-Rule Calculator in Excel (Target: ≤ 3 min)

### Setup

Open Excel. Create the following:

```
Cell A1:    Parameter
Cell B1:    Value
Cell A2:    r*
Cell B2:    [input, e.g. 1.5%]
Cell A3:    π* (inflation target)
Cell B3:    [input, e.g. 3.0%]
Cell A4:    π (current inflation)
Cell B4:    [input, e.g. 4.5%]
Cell A5:    Output gap (%)
Cell B5:    [input, e.g. -0.2%]
Cell A6:    Coef on inflation gap
Cell B6:    1.5
Cell A7:    Coef on output gap
Cell B7:    0.5
Cell A9:    Taylor-implied rate
Cell B9:    =B2 + B3 + B6*(B4-B3) + B7*B5

Cell A11:   Actual policy rate
Cell B11:   [input]
Cell A12:   Gap (Actual − Taylor)
Cell B12:   =B11 - B9
Cell A13:   Interpretation
Cell B13:   =IF(B12>0.5%,"Restrictive vs rule",IF(B12<-0.5%,"Accommodative vs rule","~Neutral"))
```

### Stretch — sensitivity table

In G1:K6, build a 2-way data table:
- Rows: r\* assumption from 0.5% to 3.0% in 0.5% steps
- Cols: inflation gap from −1% to +3% in 1% steps
- Values: Taylor rate

This shows you the sensitivity to r\* assumption — critical because **r\* is your biggest unknown** in EM.

### Practice

Copy-paste data for **Czech (CZK)** today:
- r\* = 1.0%
- π\* = 2.0%
- Latest core CPI = pull from Bloomberg `CZGGSCYY Index` or `CZIRYY Index`
- Output gap = pull from latest CNB Inflation Report or IMF Article IV
- Coef on inflation: 1.5 (standard) — also try 1.0 and 2.0
- Coef on output gap: 0.5

Compare Taylor-implied to actual CNB 2-week repo.

Repeat for **Hungary (HUF)**, **Colombia (COP)**, **Korea (KRW)**.

---

## Drill 2 — Real Rate Panel (Target: ≤ 5 min)

### Goal

Build a 1-page Excel panel showing real ex-ante rates for a panel of EM countries, sorted high-to-low.

### Setup

```
Cell A1:    Country
Cell B1:    Policy rate
Cell C1:    Expected 12m CPI
Cell D1:    Real ex-ante rate
Cell E1:    Neutral r* estimate
Cell F1:    Real rate − Neutral

Rows 2–10: countries (CZK, HUF, PLN, ZAR, COP, MXN, BRL, INR, IDR)
Column B:   pull from Bloomberg
Column C:   pull from Bloomberg `<CCY>CPI 1Y INDEX` or consensus
Column D:   =B − C
Column E:   manual (use Reference card)
Column F:   =D − E
```

Conditional format Column F: red below −0.5%, green above +0.5%.

### Use

Countries with the largest +F gap have the most restrictive policy → most likely to cut. Countries with the largest −F gap have loose policy → vulnerable to hikes or FX stress.

This is a **5-minute screen** you can build live in a case study and use to position the country in peer context.

---

## Drill 3 — Forward Rate from Spot Rates in Excel (Target: ≤ 3 min)

### The formula

For semi-annual / continuous compounding, the discrete approximation is good enough:

**f(t1, t2) ≈ [r(t2) × t2 − r(t1) × t1] / (t2 − t1)**

E.g. 3y rate = 6.0%, 1y rate = 7.5%. 1y2y forward = (6.0 × 3 − 7.5 × 1) / 2 = (18 − 7.5) / 2 = 5.25%.

### Excel build

```
A1: Tenor (years)
B1: Spot rate

A2: 0.5    B2: [input]
A3: 1      B3: [input]
A4: 2      B4: [input]
A5: 3      B5: [input]
A6: 5      B6: [input]
A7: 10     B7: [input]

D1: From tenor    E1: To tenor    F1: Forward rate
D2: 1             E2: 2           F2: =(B4*A4 - B3*A3) / (A4-A3)
D3: 1             E3: 3           F3: =(B5*A5 - B3*A3) / (A5-A3)
... etc
```

Now you have a forward rate calculator. Plug in any EM curve and read off the implied forward.

### Practice

For each of Czech, Hungary, Colombia, Korea — pull the spot curve via `<CCY>SO1 Index`, `<CCY>SO2 Index`, etc. (or your local broker function).

Compute the 1y1y, 1y2y, 6m6m. Sense-check vs market consensus on policy rates.

---

## Drill 4 — Time-Series Chart in Python (Target: ≤ 5 min)

### The reusable template

```python
# Save this as a Python template you can paste
import pandas as pd
import matplotlib.pyplot as plt

# 1. Load — from CSV exported from Bloomberg, or from Excel
df = pd.read_csv("data.csv", parse_dates=["Date"])

# 2. Quick chart
fig, ax = plt.subplots(figsize=(10, 5))
ax.plot(df["Date"], df["CPI_YoY"], label="Headline CPI", color="navy")
ax.plot(df["Date"], df["Core_CPI"], label="Core CPI", color="orangered", linestyle="--")
ax.axhline(2.0, linestyle=":", color="gray", label="Target")
ax.set_title("Czech CPI vs Target")
ax.set_ylabel("YoY %")
ax.legend(loc="best")
ax.grid(alpha=0.3)
plt.tight_layout()
plt.savefig("czech_cpi.png", dpi=150)
plt.show()
```

### What to drill

Practice this once on each of: CPI (headline + core), FX (vs USD), output gap (IMF estimate), and a yield curve snapshot. The point isn't art — it's a clean readable chart in 5 minutes flat.

### Excel alternative (if Python isn't available on the day)

In Excel: paste your time-series data into columns A:C. Highlight → Insert → Line Chart. Right-click axis to set target line via "Format Axis → Add Reference Line". Add labels. Done.

---

## Drill 5 — Carry + Rolldown on a Swap (Target: ≤ 3 min)

### Setup

```
Cell A1:    Item              Cell B1: Value
Cell A2:    Tenor (yrs)       B2: 5
Cell A3:    Notional ($)      B3: 10000000
Cell A4:    Fixed rate (current swap) B4: 6.5%
Cell A5:    Floating rate (3m fwd estimate) B5: 5.5%
Cell A6:    DV01 ($/bp)       B6: =B3*B2*0.0001  [approximate]

Cell A8:    Carry (% annualised)  B8: =B4-B5
Cell A9:    Carry over 3m ($)     B9: =B8*B3*0.25

Cell A11:   Roll: next tenor rate (e.g. 4y) B11: [input]
Cell A12:   12m rolldown (bps)    B12: =(B4-B11)*100
Cell A13:   Rolldown P&L over 12m ($) B13: =B12*B6   [approximate]
```

### Practice

Use the Czech 5y receiver as an example. The Czech curve is usually flat-to-modestly inverted, so carry may be slightly negative. Roll depends on whether 5y → 4y rolldown is positive (downward sloping at that part of curve) or negative.

Compare to Hungary 5y receiver — typically positive carry + roll due to steeper curve.

---

## Drill 6 — Pass-Through Regression in Python (Target: ≤ 8 min)

### The model

Estimate FX pass-through by regressing CPI changes on FX changes:

ΔCPI_t = α + β · ΔFX_t + γ · ΔFX_{t-1} + ε

Pass-through coefficient = β + γ.

### Template code

```python
import pandas as pd
import statsmodels.api as sm

# 1. Load data — monthly CPI YoY % and FX change MoM %
df = pd.read_csv("data.csv", parse_dates=["Date"])
df["FX_lag1"] = df["FX_change_pct"].shift(1)
df = df.dropna()

# 2. Regression
X = df[["FX_change_pct", "FX_lag1"]]
X = sm.add_constant(X)
y = df["CPI_change_pct"]

model = sm.OLS(y, X).fit()
print(model.summary())

# 3. Pass-through coefficient
pass_through = model.params["FX_change_pct"] + model.params["FX_lag1"]
print(f"Estimated 1m+lag pass-through: {pass_through:.2%}")
```

### Use

This produces an empirical pass-through estimate from data. Compare to your textbook estimate from the table in Notes / Reference. If your empirical is much higher than textbook, the regime might be in an "unanchored" phase — adjust your trade conviction.

### Faster alternative for the day

If regression is too slow, use the **table from `EM_Macro_Reference.md`** directly. The textbook numbers are usually within 30% of empirical estimates.

---

## Drill 7 — Curve Plot in Python (Target: ≤ 5 min)

### Code

```python
import matplotlib.pyplot as plt
import numpy as np

# Tenors in years
tenors = [0.25, 0.5, 1, 2, 3, 5, 7, 10]
# Rates (input from Bloomberg)
rates_today = [4.50, 4.40, 4.20, 4.10, 4.05, 4.00, 4.05, 4.20]   # example: flat-to-inverted CZK
rates_1m_ago = [4.60, 4.50, 4.30, 4.15, 4.10, 4.05, 4.10, 4.25]  # example

fig, ax = plt.subplots(figsize=(10, 5))
ax.plot(tenors, rates_today, marker="o", label="Today", color="navy")
ax.plot(tenors, rates_1m_ago, marker="s", linestyle="--", label="1 month ago", color="gray")
ax.set_xlabel("Tenor (yrs)")
ax.set_ylabel("Yield (%)")
ax.set_title("CZK Swap Curve")
ax.legend()
ax.grid(alpha=0.3)
plt.tight_layout()
plt.show()
```

### Practice

Pull today's CZK / HUF / COP / KRW IRS curves from Bloomberg (use `<CCY>SO N Index` series — e.g. `CZSO5 Index` for Czech 5y). Plot the four side-by-side using `plt.subplots(2, 2)`.

---

## Drill 8 — Speed Round (do all 5 in under 25 min total)

Day 2 drill. Set a 25-min timer. In Excel and/or Python, produce:

1. **Taylor table** for 4 countries (Drill 1, applied across 4) — 5 min
2. **Real rate panel** for 8 EM countries (Drill 2) — 5 min
3. **CZK CPI vs target chart** (Drill 4) — 4 min
4. **CZK forward 1y1y, 1y2y, 6m6m** (Drill 3) — 3 min
5. **CZK 5y carry + roll** (Drill 5) — 3 min
6. **CZK swap curve plot** (Drill 7) — 5 min

If you do this 2–3 times, on the day you'll be at 60% of this time.

---

## Section 9 — What to Have Ready

Before Monday, save these files **on your phone, on your personal email, or on a USB you bring**:

- `taylor_template.xlsx` — the Drill 1 Excel sheet, pre-filled and tested
- `curve_template.xlsx` — the Drill 3 forward-rate sheet, pre-tested
- `time_series.py` — the Drill 4 Python template
- `curve_plot.py` — the Drill 7 Python template

You won't actually need to "build from scratch" if you have these. You just need to load fresh data and adjust labels.

If laptop access on the day doesn't allow personal files, you'll build from scratch — these drills are how you make that fast.

---

## Section 10 — Bloomberg Cheat for Speed

| Task | Bloomberg input |
|---|---|
| Country macro snapshot | `<COUNTRY>ECFC` |
| CPI YoY | `<CCY>CPI YOY Index` (e.g. `CZCPIYOY Index`) |
| Core CPI | `<CCY>CPCY Index` or `<CCY>CPYY Index` |
| Unemployment | `<CCY>UE Index` |
| FX spot | `<CCY> Curncy` (e.g. `CZK Curncy`, `HUF Curncy`) |
| FX history | `<CCY> GP <go>` |
| Swap rates | `<CCY>SO N Index` (e.g. `CZSO5 Index`) |
| Policy rate path (WIRP) | `<CCY> WIRP <go>` |
| Yield curve | `YCGT<country> <go>` or `<COUNTRY> YCRV` |
| Implied vol | `<CCY>1MV Index`, `<CCY>3MV Index` |
| Forward FX | `<CCY>1M, 3M, 6M, 12M Curncy` |
| News on country | `TOP <country> <go>` |

---

*End. Drill these once per evening Thursday and Friday. By Sunday these should be muscle memory.*
