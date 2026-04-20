# Minimum Tax (Individuals)

**Source:** Finance Ordinance 2025, KPMG Salient Features

Minimum tax is the floor: if your computed net tax is below the minimum tax, you pay the minimum.

## Rules by Assessment Year

| Location | AY 2024-25 | AY 2025-26 | AY 2026-27 | AY 2027-28 |
|---|---|---|---|---|
| Dhaka N/S & Chattogram city corp | 5,000 | 5,000 | **5,000** | **5,000** |
| Any other city corporation | 4,000 | 4,000 | **5,000** | **5,000** |
| Other than city corp area | 3,000 | 3,000 | **5,000** | **5,000** |

**KEY CHANGE:** From AY 2026-27 onwards, minimum tax is a **flat BDT 5,000** for ALL locations.

**New taxpayers** (filing for the first time) — minimum tax is **BDT 1,000** for AY 2026-27 and AY 2027-28.

## Carry-Forward Adjustment

Per Section 163 (post Finance Ord 2025):
- If regular tax < minimum tax in year X, the excess (minimum tax paid – regular tax) can be carried forward
- Adjusts against surplus in a future AY where regular tax > minimum tax
- Unused carry-forward continues until exhausted

## Special Minimum Tax on Gross Receipts

For individuals with gross receipts ≥ **BDT 4 crore** (was 3 crore pre-FO 2025):
- Rate increased to **1%** (was 0.25%)
- Applies to non-tobacco assessees
- Tobacco product manufacturers retain higher rates

## Application Logic

```
net_tax_after_rebate = gross_tax - rebate
final_tax_payable = MAX(net_tax_after_rebate, minimum_tax)
```

Then add Net Wealth Surcharge and Environmental Surcharge separately.
