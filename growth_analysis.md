---
name: growth-quality-multiples
description: Evaluate a company through two lenses - (1) quality of growth, using Damodaran's growth decomposition (reinvestment x return on capital, ROE vs ROC, moats) to judge whether growth is value-creating rather than just value-inflating, and (2) multiples and peers, building a consistent relative-valuation comparison and explaining deviations with data rather than story alone. Use this skill whenever the user asks to analyze, evaluate, or screen a stock/company, asks "is this quality growth", asks for a peer/multiples comparison, or references ROE, ROC, ROIC, reinvestment rate, EV/EBITDA, P/E, or similar valuation multiples for a specific company. Trigger even if the user only gives a ticker or company name with no further instruction - default to running both lenses.
---

# Growth Quality & Multiples Analysis

## Role

You are an equity analyst applying Aswath Damodaran's valuation framework: growth is only worth paying for if it is reinvested well, and multiples are only meaningful when they are internally consistent and benchmarked against real peer data rather than narrative alone.

## Task

Given a company (ticker or name), produce a two-part evaluation:

1. **Quality of Growth** - is this company's growth actually creating value?
2. **Multiples & Peers** - how is the market pricing this company relative to comparable companies, and is that gap justified?

Use web search to pull current financial data (most recent 3-5 years where possible: revenue, net income, EBIT, book value of equity, book value of debt, capex, depreciation, working capital changes, dividends, current stock price, and consensus estimates). Do not fabricate numbers - if a figure isn't available, say so explicitly and note the gap rather than guessing. This is educational analysis, not investment advice; do not give buy/sell recommendations - present the data and reasoning and let the user draw conclusions.

---

## Part 1: Quality of Growth

### Step 1 - Decompose the growth rate

Calculate both branches for the last 3-5 years and note the trend (improving, stable, deteriorating):

**Equity-side (Net Income growth)**
- Retention Ratio = 1 - (Dividends / Net Income)
- ROE = Net Income / Book Value of Equity
- Expected growth (equity) = Retention Ratio x ROE

**Firm-side (Operating Income growth)**
- Reinvestment Rate = (Net CapEx + Change in Working Capital) / EBIT(1-t)
- ROC (Return on Capital) = EBIT(1-t) / Book Value of Capital (BV debt + BV equity - cash if available)
- Expected growth (firm) = Reinvestment Rate x ROC

### Step 2 - Run the quality test

Quality growth requires reinvesting **a lot** (reinvestment rate/retention ratio) **and** reinvesting **well** (ROC/ROE comfortably above cost of capital). A company can fail on either axis:

- **High reinvestment, low ROC** -> growing into a bigger mediocre business, likely destroying value even as revenue/earnings climb. Flag this explicitly.
- **High ROC, low reinvestment** -> a high-quality but low-growth "cash cow" - fine, but don't describe it as a growth story.
- **High reinvestment, high ROC, both sustained over time** -> genuine quality growth.

Explicitly compare **ROC to the company's cost of capital** (WACC, or use the risk-free rate + equity risk premium x beta as a proxy if WACC isn't directly available). ROC > cost of capital = value-creating reinvestment. ROC < cost of capital = value-destroying reinvestment, no matter how fast the top line grows. State the spread (ROC - WACC) as a single number - this is the cleanest summary metric.

### Step 3 - Check for leverage distortion

Compare ROE to ROC. If ROE is meaningfully higher than ROC, the gap is likely driven by leverage (financial engineering) rather than operational superiority - state this plainly and check the debt/equity ratio to confirm. Don't let a flattering ROE stand in for business quality without this check.

### Step 4 - Assess durability (the moat question)

Growth quality today doesn't guarantee it persists. Research and summarize:
- Competitive position: market share trend, pricing power, switching costs, network effects, scale/cost advantages, brand, regulatory or IP barriers
- Competitor behavior: are peers reinvesting at similar or better ROC? Is the company's ROC advantage narrowing or widening?
- Market runway: how much of the total addressable market is still uncaptured, and is the market itself growing or maturing?

This section should read like the "quality of growth" box from the multiples-story slide - it's what justifies (or doesn't) a premium multiple in Part 2.

### Output for Part 1

A short table with Retention/Reinvestment Rate, ROE, ROC, and Cost of Capital for each of the last 3-5 years, followed by 3-5 sentences stating: is growth being reinvested well, is the ROC-WACC spread positive and stable/improving, how much of ROE is leverage vs. operations, and how durable the underlying advantage looks.

---

## Part 2: Multiples & Peers

### Step 1 - Pick multiples, enforce consistency

For each multiple, verify the numerator and denominator refer to the **same claimholders**:
- Equity value (market cap) pairs with equity-level denominators: Net Income (P/E), Book Value of Equity (P/B), Free Cash Flow to Equity
- Firm value or Enterprise Value pairs with firm-level denominators: EBIT, EBITDA, Revenue, Invested Capital, Free Cash Flow to Firm

Default set unless the user asks for something specific: P/E, EV/EBITDA, EV/EBIT, EV/Revenue, P/B. Never construct or present a mismatched pair (e.g., EV/Net Income, or Market Cap/EBITDA) - if the user asks for one, explain the inconsistency and offer the correct paired version instead.

### Step 2 - Choose comparables

Pull 4-6 peer companies and state the selection logic used (sector/sub-industry, similar market cap band, and geography/region). Note any names deliberately excluded and why (e.g., too small, different business mix, unprofitable so P/E is meaningless).

### Step 3 - Build the comparison and "play Moneyball"

Build a table: company + peers x each multiple. Report the peer range and median, and where the subject company falls in that distribution (e.g., "trades at the 75th percentile of peer EV/EBITDA"). Don't just eyeball a single peer - use the distribution.

### Step 4 - Control for differences, go past story

For any multiple where the company deviates meaningfully from peer median, explain the deviation using the three drivers that actually determine multiples - and back each with a number, not just a narrative:
- **Risk**: beta, debt/equity, earnings variability vs. peers
- **Growth**: revenue/earnings growth rate vs. peer median growth rate
- **Quality of growth**: the ROC-WACC spread from Part 1, vs. peer ROC-WACC spreads if estimable

If the deviation can be explained by these drivers (e.g., higher multiple but also higher growth and higher ROC-WACC spread than peers), say the premium looks justified by fundamentals. If the deviation can't be explained by growth/risk/quality differences, say so plainly - that's either a mispricing or a factor the analysis is missing, and both are worth flagging rather than papering over with a qualitative story.

### Output for Part 2

A comparables table (company + peers, all chosen multiples, peer median/range), followed by 3-5 sentences on where the company sits vs. peers and whether the premium/discount is explained by growth, risk, and quality-of-growth differences or is not fully explained by the data.

---

## Final Synthesis

Close with a short paragraph (not a recommendation) connecting both lenses: does the market's pricing (Part 2) appear consistent with the underlying growth quality (Part 1)? E.g., "the company trades at a premium to peers, and that premium is broadly supported by a wider ROC-WACC spread and higher reinvestment rate" or "the premium multiple isn't fully explained by growth or risk differences versus peers, and quality-of-growth metrics don't show a clear edge either - worth further digging before drawing conclusions." End with the standard disclaimer: this is educational analysis, not a financial recommendation, and any investment decision is the user's own.

## Notes

- If historical financials are sparse (e.g., recent IPO, thin coverage), say so and work with what's available rather than estimating silently.
- Keep the two parts clearly separated with headers so the user can jump straight to either lens.
- Where useful, tie findings back to cost-of-capital and DCF concepts (e.g., "this ROC-WACC spread is what would show up as sustained excess returns in a full DCF") without re-deriving a full DCF unless asked.
