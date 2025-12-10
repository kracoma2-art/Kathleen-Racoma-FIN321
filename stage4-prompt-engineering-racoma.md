# Stage 4 – Structured AI Prompt  
Created by: Kathleen Racoma  
Role: Financial Analyst / Treasury Analyst  
Audience: CFO / Director of Treasury  

---

# GOAL
Generate a fully functional Excel model for hedging a 1-year EUR receivable using forward, money market, and option strategies. The model must strictly follow named ranges, color coding, layout, and calculation logic defined in Stage 2.

---

# CONTEXT (FROM STAGE 2 SPECIFICATION)
Our U.S.-based technology services firm expects to receive **12,500,000 EUR in one year**, creating EUR/USD FX exposure.  
Objective: Protect USD cash flow and compare three hedging strategies:

- Forward hedge  
- Money Market hedge  
- Option hedge (put/call)

Assumptions:
- European-style options  
- Simple annual interest rates  
- Forward rate corresponds to 1-year maturity  
- Premiums paid upfront in USD  
- Exchange rate quoted as USD/EUR  
- No transaction costs or credit charges  

---

# INPUT VARIABLES (USE EXACT VALUES)
Assign these as **named ranges**:
FC_AMT = 12,500,000

S0_in = 1.1632

F0_in = 1.0890

R_USD = 5.25%

R_FC = 3.75%

K_PUT = 1.1632

K_CALL = 1.1632

PREM_PUT = 0.017

PREM_CALL = 0.022

T_DAYS = 360

T_YRS = 1

---

# SPREADSHEET REQUIREMENTS

## 1. Named Ranges (must match exactly)
FC_AMT

S0_in

F0_in

R_USD

R_FC

K_PUT

K_CALL

PREM_PUT

PREM_CALL

T_DAYS

T_YRS


## 2. Color Coding
- **Yellow** = Inputs  
- **Blue** = Assumptions  
- **Green** = Formulas  
- **Gray** = Outputs / KPIs  

## 3. Required Model Components
- Forward hedge  
- 3-step Money Market Hedge  
- Option hedge (payoff + premium cost)  
- Sensitivity table with S_T from **0.95 × S0_in to 1.05 × S0_in** in **0.01 increments**  
- Summary table comparing strategies  
- Line chart: hedge outcomes vs. S_T  
- Cross-checks:
  - Forward vs MM parity  
  - Named range validation  
  - Formula map  

---

# MODEL LOGIC (PSEUDOCODE)

### Forward Hedge
USD_forward = FC_AMT * F0_in

### Money Market Hedge
PV_FC = FC_AMT / (1 + R_FC * T_YRS)
USD_today = PV_FC * S0_in
USD_mm = USD_today * (1 + R_USD * T_YRS)


### Option Hedge (per S_T)
PUT_payoff = MAX(K_PUT - S_T, 0) * FC_AMT
CALL_payoff = MAX(S_T - K_CALL, 0) * FC_AMT

USD_put = PUT_payoff - (PREM_PUT * FC_AMT)
USD_call = CALL_payoff - (PREM_CALL * FC_AMT)


### Sensitivity
For S_T in {0.95×S0_in → 1.05×S0_in, step = 0.01}, compute:
- USD_forward  
- USD_mm  
- USD_put  
- USD_call  

---

# FORMATTING & LAYOUT
- Inputs panel (yellow) at top-left  
- Assumptions panel (blue)  
- Main calculations (green)  
- Outputs + sensitivity table (gray)  
- Clear section headers and borders  
- Single line chart comparing strategies  

---

# VERIFICATION REQUIREMENTS
The AI must generate the following inside the workbook:

1. **Named Range Audit Table**  
2. **Formula Map Tab** listing formulas as text  
3. **Forward–MM Parity Check**  
4. **Option Logic Check** (MAX functions used correctly)  
5. **Validation that all formulas reference named ranges**  

---

# EXPORT
Return a downloadable Excel file named:
FX_Hedge_Model_Racoma.xlsx


The file must:
- contain live formulas  
- include all named ranges  
- include sensitivity table + chart  
- open without warnings  

---

# END OF PROMPT
[FX_Hedge_Model_Racoma.xlsx](https://github.com/user-attachments/files/24067246/FX_Hedge_Model_Racoma.xlsx)

