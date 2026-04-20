# Bangladesh eReturn Fill Sheet — AY {{ASSESSMENT_YEAR}}

**Generated:** {{DATE}}
**Taxpayer:** {{NAME}}
**TIN:** {{TIN}}
**Income Year:** 1 July {{IY_START}} – 30 June {{IY_END}}

> **HOW TO USE:** Open https://etaxnbr.gov.bd, login with your TIN, and fill the pages in this order. Tick each ☐ as you fill the field. Numbers must be entered **without commas** and **without "Tk"**.
>
> **NO DOCUMENT UPLOADS REQUIRED.** The eReturn portal is pure data entry. Keep your supporting documents (salary certificate, bank statements, investment receipts, etc.) safely with you — the tax office may ask for them later, but you do NOT upload anything during submission.

---

## ☐ TAB 1 — Assessment Information

| Field | Value |
|---|---|
| Return Type | Self Return |
| Assessment Year | {{ASSESSMENT_YEAR}} |
| Return Form | IT-11GA (Individual) |
| Residential Status | {{RESIDENT}} |
| Tax-Free Income? | {{TAX_FREE_TOGGLE}} |

## ☐ TAB 2 — Personal Information

| Field | Value |
|---|---|
| Name | {{NAME}} |
| TIN | {{TIN}} |
| NID/Passport | {{NID}} |
| Date of Birth | {{DOB}} (DD/MM/YYYY) |
| Mobile | {{MOBILE}} |
| Email | {{EMAIL}} |
| Address (Present) | {{ADDRESS_PRESENT}} |
| Address (Permanent) | {{ADDRESS_PERMANENT}} |
| Circle | {{CIRCLE}} |
| Taxes Zone | {{ZONE}} |
| Special Category | {{CATEGORY}} *(determines tax-free threshold: BDT {{THRESHOLD}})* |
| Spouse Name | {{SPOUSE_NAME}} |
| Spouse TIN | {{SPOUSE_TIN}} |
| Employer Name (latest) | {{EMPLOYER}} |

## ☐ TAB 3 — Income Details

### 3.1 Salary (Schedule 1{{SCHEDULE_TYPE}})
| Field | Total | Exempt | Taxable |
|---|---|---|---|
| Basic pay | {{BASIC}} | – | {{BASIC}} |
| House rent allowance | {{HRA_TOTAL}} | {{HRA_EXEMPT}} | {{HRA_TAX}} |
| Medical allowance | {{MED_TOTAL}} | {{MED_EXEMPT}} | {{MED_TAX}} |
| Conveyance allowance | {{CONV_TOTAL}} | {{CONV_EXEMPT}} | {{CONV_TAX}} |
| Festival bonus | {{FESTIVAL}} | – | {{FESTIVAL}} |
| Other allowances | {{OTHER_ALLOW}} | {{OTHER_EXEMPT}} | {{OTHER_TAX}} |
| Perquisites | {{PERQ}} | – | {{PERQ}} |
| Employer PF contribution | {{EMP_PF}} | – | {{EMP_PF}} |
| Other facilities | {{OTHER_FAC}} | – | {{OTHER_FAC}} |
| **Total Salary Received** | **{{TOTAL_SALARY}}** | – | – |
| **Exempted Amount** | – | **{{SALARY_EXEMPT}}** | – |
| **Taxable Salary** | – | – | **{{TAXABLE_SALARY}}** |

> Auto-calc: Exempt = MIN(1/3 × Total Salary, BDT {{SALARY_CEILING}})

### 3.2 House Property Rent
{{RENT_BLOCK | "☐ Not applicable"}}

### 3.3 Agriculture
{{AGRI_BLOCK | "☐ Not applicable"}}

### 3.4 Business / Profession
{{BUSINESS_BLOCK | "☐ Not applicable"}}

### 3.5 Capital Gain
{{CAPGAIN_BLOCK | "☐ Not applicable"}}

### 3.6 Financial Assets Income
| Field | Value |
|---|---|
| Bank interest | {{INTEREST}} |
| Dividend | {{DIVIDEND}} |
| Securities profit | {{SEC_PROFIT}} |

### 3.7 Other Sources
{{OTHER_SOURCES_BLOCK | "☐ Not applicable"}}

### 3.8 Foreign Income
{{FOREIGN_BLOCK | "☐ Not applicable"}}

---

## ☐ TAB 4 — Investment / Tax Rebate (Schedule 5)

| Investment | Amount |
|---|---|
| Life Insurance Premium | {{LIP}} |
| DPS | {{DPS}} |
| Govt Securities / Mutual Fund / ETF | {{GOVT_SEC}} |
| Listed Securities (DSE/CSE) | {{LISTED}} |
| Provident Fund (PF Act 1925) | {{PF_GENERAL}} |
| Recognized PF (self + employer) | {{RPF}} |
| Super Annuation Fund | {{SAF}} |
| Benevolent / Group Insurance | {{BENEV}} |
| Zakat Fund | {{ZAKAT}} |
| Others | {{OTHER_INV}} |
| **Total Eligible Investment** | **{{TOTAL_INV}}** |

---

## ☐ TAB 5 — Tax Computation [AUTO — verify only]

| Line | Particulars | Amount (BDT) |
|---|---|---|
| 11 | **Total Income** | **{{TOTAL_INCOME}}** |
| 12 | Gross Tax on Taxable Income | {{GROSS_TAX}} |
| 13 | Tax Rebate | {{REBATE}} |
| 14 | Net Tax after Rebate | {{NET_TAX}} |
| 15 | Minimum Tax ({{MIN_TAX_BASIS}}) | {{MIN_TAX}} |
| 16 | **Tax Payable** (higher of 14 & 15) | **{{TAX_PAYABLE}}** |
| 17a | Net Wealth Surcharge | {{NW_SURCHARGE}} |
| 17b | Environmental Surcharge | {{ENV_SURCHARGE}} |
| 18 | Delay interest / penalty | {{PENALTY}} |
| 19 | **Total Amount Payable** | **{{TOTAL_PAYABLE}}** |

### Rebate calculation breakdown
- (a) 3% of taxable income = BDT {{REBATE_A}}
- (b) 15% of eligible investment = BDT {{REBATE_B}}
- (c) Cap = BDT 10,00,000
- **Rebate = MIN(a, b, c) = BDT {{REBATE}}**

### Slab-wise tax breakdown
{{SLAB_BREAKDOWN}}

---

## ☐ TAB 6 — Tax & Payment

| Line | Particulars | Amount (BDT) |
|---|---|---|
| 20 | TDS / Tax Collected at Source | {{TDS}} |
| 21 | Advance tax paid | {{ADVANCE}} |
| 22 | Refund adjustment from prior AY | {{REFUND_ADJ}} |
| 23 | Tax paid with this return (challan) | {{CHALLAN}} |
| 24 | **Total Tax Paid & Adjusted** | **{{TOTAL_PAID}}** |
| 25 | **Excess Payment / Refund** (24 – 19) | **{{REFUND}}** |
| 26 | Tax-exempted income (proof attached) | {{EXEMPT_INCOME}} |

**{{NET_RESULT}}** *(either: "Payable: BDT X" or "Refund: BDT X")*

If payable: Pay via A-Challan online before submission. Keep challan number.

---

## ☐ TAB 7 — Expenditure (IT-10BB)

{{IT10BB_REQUIRED_NOTE}}

| Sl. | Particular | Amount (BDT) |
|---|---|---|
| 1 | Personal/family fooding, clothing, essentials | {{EXP_FOOD}} |
| 2 | Housing expense | {{EXP_HOUSING}} |
| 3 | Personal transport | {{EXP_TRANSPORT}} |
| 4 | Utilities (electricity, gas, water, phone, mobile, internet) | {{EXP_UTIL}} |
| 5 | Education | {{EXP_EDU}} |
| 6 | Travel & vacation (local + foreign) | {{EXP_TRAVEL}} |
| 7 | Festival & special expenses | {{EXP_FESTIVAL}} |
| 8 | TDS deducted + last year's tax/surcharge paid | {{EXP_TDS}} |
| 9 | Personal loan interest | {{EXP_LOAN_INT}} |
| | **Total Lifestyle Expense** | **{{TOTAL_EXP}}** |

---

## ☐ TAB 8 — Assets & Liabilities (IT-10B)

{{IT10B_REQUIRED_NOTE}}

### Sources of Fund
| Field | Amount (BDT) |
|---|---|
| Total income (from main return) | {{IT10B_INCOME}} |
| Tax-exempted income | {{IT10B_EXEMPT}} |
| Gifts received | {{IT10B_GIFT}} |
| **Total** | **{{IT10B_SOURCES}}** |

### Wealth Reconciliation
| Field | Amount (BDT) |
|---|---|
| Net wealth — last day of prior income year | {{PRIOR_NW}} |
| Sources of fund + prior net wealth | {{SUM_SOURCES_NW}} |
| Less: Lifestyle expense (IT-10BB total) | {{LESS_EXP}} |
| Less: Other expenses/loss/gifts | {{LESS_OTHER}} |
| **Net wealth — last day of this income year** | **{{NEW_NW}}** |

### Liabilities (Outside Business)
| Field | Amount (BDT) |
|---|---|
| Institutional liabilities (bank loans etc.) | {{LIAB_INST}} |
| Non-institutional liabilities | {{LIAB_NONINST}} |
| Other liabilities | {{LIAB_OTHER}} |
| **Total** | **{{TOTAL_LIAB}}** |

### Gross Wealth = Net Wealth + Liabilities = {{GROSS_WEALTH}}

### Particulars of Assets (in Bangladesh)
| Field | Amount (BDT) | Notes |
|---|---|---|
| (a) Business capital | {{ASSET_BIZ}} | |
| (b) Director's shareholding | {{ASSET_DIR_SHARES}} | |
| (c) Partnership firm capital | {{ASSET_FIRM}} | |
| (d) Non-agricultural property/land/house | {{ASSET_NONAGRI}} | |
| (e) Agricultural property | {{ASSET_AGRI}} | |
| (f-i) Shares/debentures/bonds/units | {{ASSET_SHARES}} | |
| (f-ii) Sanchaypatra / DPS | {{ASSET_SANCHAY}} | |
| (f-iii) Loans given (with names + NID) | {{ASSET_LOANS_GIVEN}} | |
| (f-iv) Savings deposit / FDR | {{ASSET_FDR}} | |
| (f-v) Provident fund balance | {{ASSET_PF}} | |
| (f-vi) Other investment | {{ASSET_OTHER_INV}} | |
| (g) Motor vehicles (cost incl. registration) | {{ASSET_VEHICLE}} | {{VEHICLE_DETAIL}} |
| (h) Ornaments | {{ASSET_GOLD}} | {{GOLD_QTY}} |
| (i) Furniture and electronic items | {{ASSET_FURNITURE}} | |
| (j) Other assets | {{ASSET_OTHER}} | |
| (k-i) Bank balance | {{ASSET_BANK}} | |
| (k-ii) Cash in hand | {{ASSET_CASH}} | |
| (k-iii) Other liquid | {{ASSET_OTHER_CASH}} | |
| **Total Assets in Bangladesh** | **{{ASSETS_BD}}** | |
| Assets outside Bangladesh | {{ASSETS_ABROAD}} | |
| **TOTAL ASSETS (BD + Abroad)** | **{{TOTAL_ASSETS}}** | should equal Gross Wealth |

> ⚠️ Reconciliation check: {{RECON_RESULT}}

---

## ☐ DOCUMENTS TO KEEP SAFE (NOT for upload — for your own records)

> The eReturn portal does not allow uploads. Keep these in a folder so you can produce them if the tax office asks:

{{DOCUMENTS_LIST}}

---

## ☐ FINAL SUBMISSION

1. On the **Tax & Payment** page, answer "Did you pay any source tax?" — say **Yes** if you have any TDS/advance tax to claim
2. If Yes, you'll be redirected to **eLedger** to enter source tax claim details (TDS challan number, date, bank, branch, amount). Note: only Car AIT, iBAS++ govt salary, and Sanchaypatra TDS are auto-verified — others reviewed by officer later
3. Click **Tax Payment Status** → **Go to Return**
4. If balance still due: click **Pay Now** → choose payment method (online banking / card / bKash / Nagad / A-Challan)
5. Back on the return → click **Submit Return Online** → e-Sign with PIN
6. Download **Acknowledgement Certificate** + **PSR Certificate** immediately

## SUMMARY

| | |
|---|---|
| Total Income | BDT {{TOTAL_INCOME}} |
| Total Tax Payable | BDT {{TOTAL_PAYABLE}} |
| Already Paid (TDS + Advance + Challan) | BDT {{TOTAL_PAID}} |
| **{{NET_LABEL}}** | **BDT {{NET_AMOUNT}}** |

## WARNINGS / NOTES
{{WARNINGS}}
