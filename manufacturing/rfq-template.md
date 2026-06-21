# RFQ Template — Request for Quote

> **Status: STUB** — to be filled after the v1 design is sufficiently complete to
> specify components with enough precision to get meaningful quotes. Do not send
> an RFQ before the BOM is at least 80% specified.

---

## When to use this

Send this template (customized per component category) to potential suppliers
after the design is stabilized enough to specify real requirements. The goal is
to get comparable quotes from multiple suppliers so you can finalize the BOM
costs and run the unit-economics model.

---

## Template structure (to be filled in)

### Header

- Company name: [your company name — TBD with naming decision]
- Contact: [name, email, phone]
- Date:
- RFQ #:
- Response deadline:

### Product context

*(1 paragraph: what the product is, what environment it operates in, why the
specification is what it is. Help the supplier understand why you're asking for
marine-grade spec rather than just sending a table.)*

### Component specification

*(For each component category, one RFQ:)*

| Field | Value |
|-------|-------|
| Component | |
| Quantity — sample / pilot | |
| Quantity — annual production estimate | |
| Technical specification | (reference design doc or attach spec sheet) |
| Required certifications | (IP rating, UL, CE, etc.) |
| Packaging / labeling requirements | |
| Delivery location | |
| Requested lead time | |

### Questions for supplier

1. Are you able to meet the specification as written? If not, what modifications
   would you propose?
2. What certifications does this component currently hold?
3. What is your minimum order quantity at the sample/pilot quantities above?
4. What is your lead time from PO to delivery for each quantity tier?
5. What quality control documentation do you provide with each shipment?
6. Do you have experience with similar products in salt/water/sand environments?
7. What are your payment terms?

### Evaluation criteria

*(Supplier will not see this section — internal use.)*

- [ ] Meets spec (IP rating, material, capacity)
- [ ] Certified (or certifiable)
- [ ] Lead time within production plan
- [ ] Price within COGS target
- [ ] References / track record in relevant environment
- [ ] MOQ acceptable

---

## Component categories to RFQ (once BOM is finalized)

- Drive motor (D1)
- Motor controller (D2)
- Battery pack with BMS (B1/B2)
- Battery connectors and charge port (B3/B4)
- Frame fabrication (F1) — this is typically an RFQ to a manufacturing partner, not a component supplier
- Fasteners — 316 SS lot (F7)
- Wheel bearings (F5)
- Cable glands (F10)
- Handle assembly (F8)
