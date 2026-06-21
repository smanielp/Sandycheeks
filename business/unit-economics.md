# Unit Economics

> **Status: STUB** — to be filled after the BOM is sufficiently specified to get
> real component costs (Stage 5 in the roadmap). Do not model unit economics on
> estimated costs before supplier quotes exist.

---

## When to fill this in

After:
- [ ] BOM v1 drafted with real component targets (`manufacturing/bom-template.md`)
- [ ] RFQ responses received for key components (`manufacturing/rfq-template.md`)
- [ ] Manufacturing partner engagement begun (cost-of-assembly estimate available)
- [ ] Price point validated with customers (at least a willingness-to-pay signal)

---

## Model structure (to build)

When filled in, this document will include:

### COGS per unit

| Line item | Integration path | Ground-up path |
|-----------|-----------------|----------------|
| Motor + controller | | |
| Battery pack | | |
| Frame / chassis | | |
| Wheels + bearings | | |
| Handle + controls | | |
| Wiring harness | | |
| Fasteners + hardware | | |
| Corrosion package (coatings, seals) | | |
| Assembly labor | | |
| Packaging | | |
| **Total COGS** | | |
| Inbound freight (landed cost) | | |
| **Landed COGS** | | |

### Margin model

| Channel | Price point | Landed COGS | Gross margin |
|---------|------------|-------------|-------------|
| DTC (direct) | $X | | |
| Retail (50% margin to retailer) | $X | | |

### Accessory attach

| SKU | Price | COGS | Gross margin | Attach rate assumption |
|-----|-------|------|-------------|----------------------|
| Spare battery | | | | |
| Extended range battery | | | | |
| Cargo accessories (to be defined) | | | | |

### Warranty / returns assumption

| Item | Assumption | Source |
|------|-----------|--------|
| Return rate | % | Industry benchmark [VALIDATE] |
| Warranty claim rate (year 1) | % | Estimate |
| Avg warranty cost per claim | $ | Estimate |
| Net warranty cost per unit sold | $ | |

---

## Placeholder observations from existing docs

From `business/concept-and-business-brief.md`:
- Target price range: $800–$2,000+ depending on model
- Integration path (B) vs. ground-up (C) have meaningfully different capital profiles
- Accessories and replaceable batteries as margin add-ons

These need to be tested against actual COGS once BOM is quoted.
