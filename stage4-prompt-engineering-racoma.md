# Stage 4: Structured AI Prompt  
FX Hedging Model (Forward, Money Market, Options)  
Role: Finance Technologist / Treasury Analyst  
Created by: [Kathleen Racoma]  
Updated by: [Kathleen Racoma]  
Date Created: [12/9/25]  
Date Updated: [12/12/25]  

## GOAL
Generate a fully functional Excel (.xlsx) spreadsheet that evaluates FX hedging strategies for a EUR receivable using a forward hedge, money market hedge, and option hedges (EUR put and EUR call). The model must be professional, auditable, and CFO-ready.

## CONTEXT
A U.S.-based technology services firm expects to receive 12,500,000 EUR in one year, creating EUR/USD transaction exposure. The objective is to protect USD cash flow while comparing certainty versus flexibility across hedging instruments.

Assumptions:
- European-style options only  
- Simple annual interest rates  
- Forward rate corresponds to a 1-year maturity  
- Option premiums paid upfront in USD  
- Exchange rates quoted as USD per EUR  
- No transaction, tax, or credit costs  

## INPUT VARIABLES (ALL VALUES EXPLICIT)
Use the exact values below and assign each as a named range.

| Named Range | Description | Value |
|------------|-------------|-------|
| FC_AMT | EUR receivable | 12,500,000 |
| S0_in | EUR/USD spot rate | 1.1632 |
| F0_in | 1-year forward rate | 1.0890 |
| R_USD | USD interest rate | 5.25% |
| R_FC | EUR interest rate | 3.75% |
| K_PUT | EUR put strike | 1.1632 |
| K_CALL | EUR call strike | 1.1632 |
| PREM_PUT | Put premium (USD/EUR) | 0.017 |
| PREM_CALL | Call premium (USD/EUR) | 0.022 |
| T_DAYS | Time to maturity (days) | 360 |
| T_YRS | Time to maturity (years) | =T_DAYS/360 |

## SPREADSHEET REQUIREMENTS

### Named Ranges
All inputs, assumptions, and calculations must use the named ranges exactly as listed above. Do not invent alternative naming conventions.

### Color Coding
Apply the following color scheme:
- Yellow = Inputs / decision variables  
- Blue = Assumptions  
- Green = Formula cells  
- Gray = Outputs / KPIs  

## MODEL COMPONENTS

### Forward Hedge
USD_forward = FC_AMT × F0_in

### Money Market Hedge (3-Step)
1. EUR_PV = FC_AMT / (1 + R_FC × T_YRS)  
2. USD_today = EUR_PV × S0_in  
3. USD_mm = USD_today × (1 + R_USD × T_YRS)  

### Parity Cross-Check
F_parity = S0_in × (1 + R_USD × T_YRS) / (1 + R_FC × T_YRS)

### Option Hedges

#### EUR Put Hedge
USD_put_gross = FC_AMT × MAX(S_T, K_PUT)  
Put_Premium = FC_AMT × PREM_PUT  
USD_put_net = USD_put_gross − Put_Premium  

#### EUR Call Hedge
USD_call_gross = FC_AMT × MIN(S_T, K_CALL)  
Call_Premium = FC_AMT × PREM_CALL  
USD_call_net = USD_call_gross − Call_Premium  

## SENSITIVITY ANALYSIS
Vary S_T from 0.95 × S0_in to 1.05 × S0_in in 0.01 increments. For each S_T, calculate USD proceeds for all hedge types and present results in a comparison table and line chart.

## OUTPUT REQUIREMENTS
Display USD proceeds for forward, money market, put hedge, and call hedge strategies. Clearly label all KPIs.

## VERIFICATION
Confirm parity between forward and money market hedges, confirm all named ranges exist, and return a full formula mapping for auditability.

## EXPORT
Return a downloadable Excel (.xlsx) file.

Result: [FX_Hedging_Model_EUR_Receivable.xlsx](https://github.com/user-attachments/files/24140465/FX_Hedging_Model_EUR_Receivable.xlsx)

