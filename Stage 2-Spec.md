# [Spec Title] – Technical Specification Template

**Created by:** [Kathleen Racoma]  
**Updated by:** [Kathleen Racoma]  
**Date Created:** [11/7/25]  
**Date Updated:** [11/7/25]  
**Version:** [0.0]
**LLM Used:"" [LLM] (optional if LLm used)

**Role:** Financial Analyst / Treasury Analyst  
**Audience:** CFO or Director of Treasury  

**Purpose:** Provide a professional, quantitative specification outlining the analytical structure for evaluating FX hedging alternatives.

---

## 1. Problem Statement

Our U.S. based technology services firm expects to receive 12,500,000 euros in one year for services rendered to a European client, creating exposure to potential EUR/USD exchange rate fluctuations. This specification outlines the analytical framework for quantifying and evaluating three hedging strategies which are a forward contract, a money market hedge, and an options hedge. With this, we'll be able to protect the USD value of this receivable while allowing comparison of certainty versus flexibility.

Details:
- Exposure type: Foreign currency receivable (EUR) 
- Foreign currency amount: 12,500,000 Euros
- Time horizon: 1 year
- Objective: Protect USD cash flow
- Decision context: Corporate treasury

---

## 2. Inputs (Known Variables)

| Variable | Description | Unit | Example | Source |
|-----------|-------------|------|----------|--------|
| `FC_AMT` | Foreign-currency receivable | EUR | 1,200,000 | Company data |
| `S₀` | Current EURUSD spot rate | USD/EUR | 1.1632 | Market data |
| `F₀` | 1-year EURUSD forward rate | USD/EUR | 1.0890 | Provided |
| `r_USD` | USD 1-year interest rate | % | 5.25 | Market data |
| `r_EUR` | EUR 1-year interest rate | % | 3.75 | Market data |
| `t` | Time to maturity | Years | 1 | Derived |
| `K_put` | EUR Put strike | USD/EUR | 1.1632 | Analyst choice |
| `K_call` | EUR Call strike | USD/EUR | 1.1632 | Analyst choice |
| `Premium_put` | Put premium | USD per contract | 0.017 | Scenario |
| `Premium_call` | Call premium | USD per contract | 0.022 | Scenario |

---

## 3. Assumptions & Constraints

List:
- Spot and forward rates are assumed to remain stable during hedge execution
- No early exercise or path dependency for options (European-style options)
- Interest rates are quoted on a simple annual basis.  
- Forward rate provided represents a 1-year maturity.  
- Transaction and credit costs are excluded.  
- Option premiums are paid upfront in USD.  
- Exchange rates expressed as USD per EUR.  

---

## 4. Calculation Flow

Describe the logic and sequencing of your analysis — as if briefing a junior analyst or AI model builder. Focus on **order of operations**, not formulas.

Flow:
1. Multiply the EUR receivable by the forward rate to determine fixed USD proceeds
2. Discount the EUR receivable using the EUR interest rate to find today's EUR present value
3. Convert that EUR PV to USD at the current spot rate
4. Invest USD proceeds at the USD rate to project 1-year USD value
5. Cross check against forward parity
6. Compute USD proceeds under EUR put hedge across possible spot rates (S_T)
7. Compute USD proceeds under EUR call hedge across S_T
8. Adjust each by subtracting the respective option premium cost
9. Compare USD results across hedges at the base case and across sensitivity scenarios.  
10. Compare results across the various hedges
11. Highlight and summarize trade offs.

---

## 5. Outputs

| Output | Description | Format | Purpose |
|---------|--------------|---------|----------|
| `USD_forward` | USD proceeds from forward hedge | Numeric | Certainty benchmark |
| `USD_mm` | USD proceeds from money market hedge | Numeric | Cross-check and validation |
| `USD_put` | USD proceeds from EUR put hedge | Table | Downside protection analysis |
| `USD_call` | USD proceeds from EUR call hedge | Table | Upside case |
| `Chart_1` | Hedge outcomes vs. S_T | Line chart | Visual comparison of strategies |
| `Summary` | Written conclusion | 1–2 paragraphs | Executive-ready interpretation |

---

## 6. Sensitivity Plan

Define how you will test and visualize FX outcomes.

Example:
> Vary EURUSD spot at maturity \(S_T\) from 0.95×S₀ to 1.05×S₀ in increments of 0.01.  
> For each value, compute USD proceeds under all hedge strategies.  
> Present results as a comparison table and line chart.

> *Professional analysts always test sensitivity — it shows how robust their recommendations are.*

---

## 7. Limitations & Next Steps

Briefly note any analytical limits (e.g., volatility ignored, credit risk excluded) and outline your immediate next step (e.g., model build in Stage 3).

Example phrasing:
> This specification does not incorporate implied volatility or transaction costs. The next phase will involve constructing an Excel model implementing this logic to quantify results under each hedge structure.

---

# 🧭 Writing a Strong Specification

**Your spec should:**
- **Communicate like a professional:** clear, structured, and jargon-free.  
- **Think one stage ahead:** your spec should feed directly into your Excel build or AI prompt.  
- **Be internally consistent:** variables, labels, and steps must align.  
- **Be reproducible:** a new analyst should be able to implement your plan without your help.  
- **Be executive-relevant:** the CFO should understand *what you’re doing* and *why it matters*.

---

## 🔗 How This Sets You Up for Later Stages

| Stage | What This Spec Enables |
|-------|------------------------|
| **Stage 3** | Each “Input” and “Output” becomes a spreadsheet cell or named range. |
| **Stage 4** | Your “Calculation Flow” becomes an AI prompt instruction block. |
| **Stage 5** | Your “Outputs” drive the interpretation and recommendation. |

> *Treat your specification as the bridge between business insight and technical execution — the CFO should be confident your plan is sound even before seeing the numbers.*
