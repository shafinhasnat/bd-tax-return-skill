# Bangladesh Income Tax eReturn Assistant

A Claude skill that conducts an exhaustive, field-by-field interview with a Bangladeshi individual taxpayer and produces a complete, copy-paste-ready fill sheet for the NBR eReturn portal at [etaxnbr.gov.bd](https://etaxnbr.gov.bd).

Covers **AY 2025-26** (income year July 2024 – June 2025) and **AY 2026-27** (income year July 2025 – June 2026).

---

## What It Does

1. **Interviews** the taxpayer question by question — never guesses, never assumes defaults
2. **Computes** income from all heads, salary exemption, investment rebate, minimum tax, net wealth surcharge, and environmental surcharge
3. **Confirms** every collected value in a structured summary before generating any output
4. **Outputs** a tabbed fill sheet that mirrors the eReturn portal's page structure exactly — ready to copy and paste

---

## Key Facts

- The eReturn portal is **pure data entry** — it does not accept document uploads of any kind. This skill never tells you to upload anything.
- Documents (salary certificate, bank statements, DPS receipts, deeds) are kept by the taxpayer and only produced if the tax office asks later.
- The portal *issues* documents to you after submission (Acknowledgement, PSR Certificate, Challan, Return copy).

---

## What It Covers

| Area | Details |
|---|---|
| Assessment years | AY 2025-26 and AY 2026-27 |
| Tax-free thresholds | All 5 categories (General / Female / Senior 65+ / Third Gender / Freedom Fighter) |
| Income heads | Salary (govt + private), Rent, Agriculture, Business, Capital Gain, Financial Assets, Other Sources, Foreign Income, Clubbed Income |
| Rebate | MIN(3% × taxable income, 15% × eligible investment, BDT 10,00,000) |
| Minimum tax | Location-based for AY 2025-26; flat BDT 5,000 from AY 2026-27 |
| Surcharge | Net wealth (10–35%) and environmental surcharge per motor car |
| Lifestyle expenses | IT-10BB (9 categories) |
| Assets & liabilities | IT-10B full structure (15 asset categories + reconciliation check) |
| TDS / source tax | eLedger sub-system flow for claiming TDS/AIT |

---

## Setup & Configuration

### Option A — Claude Code CLI (Recommended)

Claude Code loads skills from a `skills/` directory. Each skill lives in its own named subdirectory containing `SKILL.md`. The directory name becomes the `/slash-command`.

**Personal install — available in all your projects:**

```bash
# Clone directly into your personal skills folder
git clone https://github.com/YOUR_USERNAME/bd-tax-return-skill.git \
  ~/.claude/skills/bangladesh-tax-return
```

That's it. Open any Claude Code session and type:

```
/bangladesh-tax-return
```

**Project-level install — only available in one project:**

```bash
cd your-project
git clone https://github.com/YOUR_USERNAME/bd-tax-return-skill.git \
  .claude/skills/bangladesh-tax-return
```

Commit `.claude/skills/` to version control so teammates get the skill automatically.

**Verify the skill loaded:**

```
/help
```

`bangladesh-tax-return` should appear in the skill list.

> **How it works:** Claude Code watches `~/.claude/skills/` and `.claude/skills/` for changes. No restart needed after cloning (unless the skills directory itself is brand new — in that case restart Claude Code once).

---

### Option B — Claude.ai Web (No Install)

No installation needed.

1. Open [claude.ai](https://claude.ai) and start a new conversation
2. Copy the full contents of `SKILL.md` and paste it as your first message
3. Claude will begin the interview immediately

For best results, also paste the relevant reference files (`tax-rates-ay-2026-27.md`, `investment-rebate.md`, etc.) into the same conversation before starting, or attach them as files if your plan supports it.

---

### Option C — API / Custom App

Use `SKILL.md` as the system prompt. Append reference files for full computation accuracy.

```python
import anthropic

with open("SKILL.md") as f:
    system = f.read()

for ref in [
    "references/tax-rates-ay-2026-27.md",
    "references/investment-rebate.md",
    "references/minimum-tax.md",
    "references/surcharge.md",
    "references/return-form-fields.md",
]:
    with open(ref) as f:
        system += "\n\n---\n" + f.read()

client = anthropic.Anthropic()
response = client.messages.create(
    model="claude-opus-4-7",
    max_tokens=8096,
    system=system,
    messages=[{"role": "user", "content": "I need to file my income tax return."}]
)
```

---

## Project Structure

```
tax-skill/
├── SKILL.md                          # Main skill definition — system prompt + stage flow
├── README.md                         # This file
├── references/
│   ├── tax-rates-ay-2025-26.md       # Tax slabs, thresholds, salary exemption for AY 2025-26
│   ├── tax-rates-ay-2026-27.md       # Tax slabs, thresholds, salary exemption for AY 2026-27
│   ├── minimum-tax.md                # Minimum tax rules (location-based → flat)
│   ├── surcharge.md                  # Net wealth + environmental surcharge bands
│   ├── investment-rebate.md          # Rebate formula + eligible investment categories
│   ├── return-form-fields.md         # Full IT-11GA / IT-10B / IT-10BB field reference
│   ├── ereturn-portal-tabs.md        # eReturn portal page-by-page flow
│   └── sources.md                    # Legal citations and update cadence
└── templates/
    └── output-summary.md             # Output fill-sheet template with placeholders
```

---

## Tax Law Basis

| Source | Coverage |
|---|---|
| Income Tax Act 2023 (Bangladesh) | Core statute — income heads, schedules, rebate structure |
| Finance Ordinance 2025 (gazetted 22 June 2025) | AY 2026-27 rates, thresholds, minimum tax changes |
| NBR Official Forms (IT-11GA, IT-10B, IT-10BB 2023) | Field structure and computation rules |
| NBR "Guideline for Taxpayer V.2" | eReturn portal flow confirmation |
| KPMG Rahman Rahman Huq — Finance Act summary | Primary cross-check for slabs and surcharge |
| PwC Worldwide Tax Summaries — Bangladesh | Cross-check for rebate cap and thresholds |

---

## Limitations

- This skill covers **individual taxpayers (IT-11GA)** only. It does not cover company returns, partnership firms filing separately, or trust assessments.
- Situations involving foreign income with double-tax treaties, complex capital gains (ESOP, mergers), Section 82C special businesses, or tax holiday claims are flagged as out-of-scope — the skill will recommend a Chartered Accountant.
- Exact on-screen field labels and dropdown values are reconstructed from official NBR PDFs and practitioner guides. If you find a label mismatch in the live portal, please open an issue.
- Tax law changes annually after the Finance Act gazette. Check `references/sources.md` for update cadence before using for a new assessment year.

---

## Disclaimer

This tool is provided for informational and self-help purposes. It is not legal or tax advice. For complex situations, consult a qualified tax practitioner or Chartered Accountant registered with ICAB. The authors accept no liability for errors in submitted returns.

---

## Contributing

Pull requests welcome. If you find:
- A field label that differs from the live portal
- A rate or threshold that has changed
- A new income category not covered

Please open an issue or PR with the NBR source document as evidence.

---

## License

MIT
