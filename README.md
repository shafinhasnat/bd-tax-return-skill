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

Claude Code supports custom slash commands via Markdown files in a `.claude/commands/` directory.

**Project-level (only available in that project):**

```bash
git clone https://github.com/YOUR_USERNAME/bd-tax-return-skill.git
cd your-project
mkdir -p .claude/commands
cp path/to/bd-tax-return-skill/SKILL.md .claude/commands/bangladesh-tax-return.md
```

Then open Claude Code in your project:

```bash
claude
```

Type `/bangladesh-tax-return` to start the interview.

**Global (available in every project):**

```bash
mkdir -p ~/.claude/commands
cp path/to/bd-tax-return-skill/SKILL.md ~/.claude/commands/bangladesh-tax-return.md
```

The skill reads its reference files at runtime. For the references and template to load correctly, also copy the supporting folders:

```bash
# if using project-level setup
cp -r path/to/bd-tax-return-skill/references  .claude/commands/references
cp -r path/to/bd-tax-return-skill/templates   .claude/commands/templates

# if using global setup
cp -r path/to/bd-tax-return-skill/references  ~/.claude/commands/references
cp -r path/to/bd-tax-return-skill/templates   ~/.claude/commands/templates
```

Or simply clone the whole repo directly into the commands folder:

```bash
# Global install (simplest)
git clone https://github.com/YOUR_USERNAME/bd-tax-return-skill.git ~/.claude/commands/bangladesh-tax-return

# Then invoke with:
#   /bangladesh-tax-return/SKILL
```

> **Tip:** After setup, run `/help` in Claude Code to confirm the command appears in the list.

---

### Option B — Claude.ai Web (No Setup)

No installation needed.

1. Open [claude.ai](https://claude.ai) and start a new conversation
2. Copy the full contents of `SKILL.md` and paste it as your first message
3. Claude will begin the interview immediately

For the best results, also paste the relevant reference files (`tax-rates-ay-2026-27.md`, `investment-rebate.md`, etc.) into the same conversation before starting — or attach them as files if your plan supports it.

---

### Option C — API / Custom App

Use `SKILL.md` as the system prompt. Pass the reference files as additional context (tool-readable files, RAG chunks, or inline in the system prompt).

```python
import anthropic

with open("SKILL.md") as f:
    system = f.read()

# Optionally append reference content
for ref in ["references/tax-rates-ay-2026-27.md", "references/investment-rebate.md"]:
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
