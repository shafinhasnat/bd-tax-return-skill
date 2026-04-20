# eReturn Portal (etaxnbr.gov.bd) — Submission Flow

**Source:** Official "Guideline for Taxpayer V.2" PDF (NBR / Taxes Zone Rajshahi); cross-checked with TNP Legal eReturn FAQ, PiHR guide, VATax BD walkthrough.

---

## ⚠️ KEY FACT — NO DOCUMENT UPLOADS

**The eReturn portal does NOT accept document uploads anywhere in the flow.**

- No salary certificate upload
- No bank statement upload
- No DPS/insurance receipt upload
- No deed or registration upload

Taxpayers enter **numbers and text only**. Supporting documents are kept by the taxpayer and only produced if the tax office requests them later (e.g., during audit).

After submission, the portal **issues** (not accepts) PDFs to the taxpayer:
- Acknowledgement Slip
- Tax Certificate / PSR (Proof of Submission of Return)
- Challan (if tax was paid via the portal)
- Return copy

---

## Portal URL & Access

- Landing: `https://etaxnbr.gov.bd/#/landing-page`
- Submission portal: `https://etaxnbr.gov.bd/`
- eLedger (source tax claim): redirected from within the Tax & Payment page
- Tax payment: `eTaxPayment` link → eTDS/A-Challan
- Verification: `Return Verify/PSR` button

## Account Setup (one-time)

1. Click **Registration**
2. Enter TIN + biometric-verified mobile number + CAPTCHA
3. Receive OTP on phone → set password
4. Sign in with TIN + password

---

## Two Submission Modes

After signing in, click **Submission menu** and choose:

### A) Single Page Return
- One simple form
- Suitable for: salaried employees with no rental/business income, no investments, no IT-10B trigger
- Auto-fills most data from TIN database

### B) Regular (Detail) Return
- Multi-page wizard with **Save Draft** + **Save & Continue** between pages
- Required if: business income, multiple income heads, IT-10B applicable, complex investments
- Walks through each income head and computation

The skill should target **Detail Return** by default (covers all cases). Single Page Return is mentioned as a simpler option for very basic taxpayers.

---

## Detail Return — Page Sequence

Based on the official guide + cross-referenced practitioner walkthroughs:

### Page 1 — Assessment Information
- Return type (Self / Notice / Revised)
- Assessment year (e.g., 2026-2027)
- Income year (auto)
- Residential status (Resident / Non-resident)
- Special category check (Female / Senior 65+ / Disabled / Third Gender / Freedom Fighter / Parent of disabled)
- Has tax-free income? (toggle)
- Six income heads — tick which ones apply (drives which sub-pages appear)
- IT-10B requirement check (drives whether asset section appears)

### Page 2 — Personal Information
Auto-populated from TIN database; verify and edit if needed:
- Name, NID/Passport, DOB
- Father's name, Mother's name (for some categories)
- Spouse name + spouse TIN (if applicable)
- Address (present + permanent)
- Mobile, Email
- Circle, Taxes Zone (auto)
- Employer name (if salaried)
- Organization name + BIN (if business)

### Page 3 — Income Details
Sub-pages appear only for ticked heads (from Page 1):

**3a. Salary (Schedule 1)** — by component:
- Basic pay
- House rent allowance (with calculated exempt portion)
- Medical allowance (with exempt portion)
- Conveyance allowance (with exempt portion)
- Festival bonus
- Other allowances / perquisites / facilities
- Employer's RPF contribution
- (Auto) Total salary, exempt amount, taxable salary

**3b. Rent / House Property (Schedule 2)** — per property:
- Property location, description, ownership %
- Rent received / annual value
- Advance rent
- Vacancy allowance
- Allowable deductions (repair @ 30%/25%, municipal tax, land revenue, loan interest, insurance, others)
- (Auto) Net income

**3c. Agriculture (Schedule 3)** — sales, gross profit, expenses, net profit

**3d. Business (Schedule 4)** — income side + balance sheet side

**3e. Capital Gain** — per transaction (asset, dates, cost, sale price, computed gain, applicable rate)

**3f. Financial Assets Income** — bank interest, dividend, securities profit

**3g. Other Sources** — royalty, license fees, honorarium, govt incentive, etc.

**3h. Foreign Income** — taxable income earned abroad

**3i. Clubbed Income** — minor / non-taxpayer spouse income

### Page 4 — Investment / Tax Rebate (Schedule 5)
Enter actual amounts per category:
- Life insurance premium
- DPS
- Government securities, mutual fund, ETF
- Listed securities (DSE/CSE)
- Provident Fund (PF Act 1925)
- Recognized PF (self + employer)
- Super Annuation Fund
- Benevolent / Group Insurance
- Zakat Fund
- Others

System auto-applies: rebate = MIN(3% × taxable income, 15% × eligible investment, 10,00,000)

### Page 5 — Expenditure (IT-10BB)
Required if total income > BDT 5,00,000 OR IT-10B is required.
- Personal/family food, clothing, essentials
- Housing expense
- Personal transport
- Utilities (electricity, gas, water, phone, mobile, internet)
- Education
- Travel & vacation (local + foreign)
- Festival/special expenses
- TDS deducted + last year's tax/surcharge paid
- Personal loan interest
- (Auto) Total

### Page 6 — Assets & Liabilities (IT-10B)
Mandatory if any of: assets > 40 lakh / motor car owned / house in city corp area / assets abroad / shareholder-director / public servant.

Sources of fund + prior year's net wealth − expenses = new net wealth.
Plus liabilities = gross wealth.

Asset items per IT-10B Section 8 (a–k); liabilities under Section 6.

Reconciliation: Gross Wealth must equal Total Assets minus Total Liabilities.

### Page 7 — Tax & Payment
Auto-computed:
- Gross tax (slabs)
- Rebate
- Net tax
- Minimum tax
- Tax payable (max of net & minimum)
- Net wealth surcharge (if applicable)
- Environmental surcharge (if multiple cars)
- Total amount payable

**Source tax claim question:** "Did you pay any source tax?"
- If YES → redirected to **eLedger** sub-system to claim TDS/AIT
- If NO → can't use eLedger; only enter net tax payable

### eLedger Sub-System (for TDS/AIT claims)
Auto-verified categories (system can confirm):
1. **Car AIT**
2. **iBAS++ Salaried Source Tax** (for government employees)
3. **Sanchaypatra interest TDS**

Other TDS/AIT claims (private salary TDS, bank interest TDS, etc.) — entered manually with challan/certificate details (number, date, bank, branch, amount). These are NOT auto-verified — tax officer reviews during assessment.

After eLedger entries → click **Tax Payment Status** → **Go to Return** → back to main flow.

### Page 8 — Payment (if balance due)
Click **Pay Now**. Options:
- Online Banking
- Debit/Credit Card
- Mobile Financial Services (bKash, Nagad, etc.)
- A-Challan via designated bank

After payment → return to portal to complete submission.

### Page 9 — Submit
- **Save Draft** — keeps form for later editing
- **Submit Return Online** — final submission with e-signature/PIN
- After submit: instant Acknowledgement & PSR Certificate displayed → download

---

## Post-Submission

From the **Tax Record and Documents** menu, taxpayer can download anytime:
- Acknowledgement Certificate
- Challan
- Submitted Return copy
- PSR (Proof of Submission of Return) — required for many services (passport, bank loans, license renewal)

---

## Input Format Rules (eReturn portal)

- **Numbers without commas, no "Tk" prefix** — system rejects formatted figures
- **Dates** in DD/MM/YYYY (or as the date picker requires)
- **Dropdown values** must be selected from list — typed values not accepted
- Use **desktop or laptop** browser — mobile UI lacks some sections

## Mandatory vs Optional Fields

The portal enforces:
- All Personal Info fields (Name, TIN, NID, DOB, Address, Circle, Zone) — auto-filled but must be confirmed
- At least one income head must have data (cannot submit blank)
- Investment/rebate is optional (skip if no eligible investment)
- IT-10BB required only if income > 5L or IT-10B applies
- IT-10B required only if any of the 6 trigger conditions met
- Tax & Payment page mandatory
- Final e-signature/PIN mandatory
