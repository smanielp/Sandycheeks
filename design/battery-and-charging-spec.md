# Battery & Charging Spec

> Design intent for the energy storage system: pack, BMS, enclosure, contacts,
> charging, and charge-state indication.
>
> Cross-cutting constraints: → `design/system-overview.md`
> Battery enclosure interface to frame: → `design/corrosion-and-ingress-spec.md`
> Battery contact location and indicator UX: → `design/handle-and-controls-ux.md`

---

## Energy budget (to be validated)

These are estimated values. **[VALIDATE]** against measured motor current draw
during actual beach testing before finalizing pack design.

| Parameter | Estimate | Basis |
|-----------|---------|-------|
| Motor power (continuous) | 250–350 W | 500 W motor at ~60% average load on soft sand |
| Target range | 2–3 beach days of typical use | ~5 km total haul distance per day, multiple trips |
| Usable Wh target | **300–500 Wh** | 350 W × 1 hr continuous = 350 Wh; with 30% derating for temperature and pack aging |
| Operating voltage | 36 V nominal (10S Li-ion) | Preferred; matches motor spec. 24 V (7S) acceptable for v0 |
| Pack capacity (36 V) | ~10–14 Ah for 360–500 Wh | Standard e-bike pack territory |

**Note:** "A full beach day" is not continuous motor operation. Typical use is
repeated short hauls (100–300 m) with rest between. Wh target should be modeled
as duty-cycled, not continuous. **[VALIDATE with user interviews: what is actual
haul frequency and distance per day?]**

---

## Pack form factor

**Hard requirement: removable and swappable.**

The pack must be removable by the user without tools, to enable:
- Indoor charging (keep moisture/heat away from the electronics bay)
- Carrying spare packs for all-day use
- Off-season storage without leaving a battery in a weather-exposed bay
- Servicing and replacement without returning the wagon

### Removal mechanism

Target: single-action release (lever or button), no tools. Pack slides or
lifts out in one motion. Same action to install.

Electrical connection: latching waterproof connector that mates automatically
when pack is seated, breaks automatically when removed. No exposed terminals when
pack is removed. See contact sealing spec below.

### Pack location on wagon

Preferred: low and centered (center of mass stability), recessed into the frame
(protected from impact), accessible from the rear or side (not underneath).
The bay door is the primary sealing challenge — see `corrosion-and-ingress-spec.md`.

---

## Battery platform decision

**Open decision.** Two paths with meaningfully different tradeoffs:

### Path A — Proprietary pack (custom design)

Custom lithium-ion pack designed and specified for this product.

| Pros | Cons |
|------|------|
| Full control over cell selection, capacity, voltage, form factor | Higher NRE cost to develop and certify |
| Can optimize IP sealing for the marine environment | Customer must buy replacement packs from you |
| BMS can be tuned for the exact load profile | Smaller initial production run = higher per-unit cost |
| Brand touchpoint (pack is part of the product experience) | UN38.3 / UL certification adds time and cost |

### Path B — Power-tool ecosystem (e.g., Milwaukee M18, DeWalt 20V, Makita 18V)

Design the battery bay to accept a common power-tool battery platform.

| Pros | Cons |
|------|------|
| Customer can buy replacement batteries anywhere | Platform control: spec changes at Milwaukee's discretion |
| Lower SKU complexity; no custom pack NRE | Max capacity per pack (~12 Ah / ~216 Wh at 18 V) may require dual packs |
| Familiar UX; customer already knows how to charge it | BMS in power-tool pack not designed for sustained motor loads; may trigger protection early |
| Avoids UN38.3 battery certification for own pack | Voltage (18–20 V nominal) is lower than preferred 36 V |

**Recommendation:** proprietary pack for v1 production. Power-tool ecosystem for
**v0 prototype only** — it dramatically simplifies the prototype build (off-the-shelf
charger, no custom pack, no BMS work) while proving the motor/traction concept.

**v0 prototype note:** two Milwaukee M18 12Ah packs in series (36 V, 12 Ah =
432 Wh) as a quick-and-dirty power source is a reasonable integration prototype
approach. Seal them in a weatherproof case; do not trust the power-tool pack IP
rating for sustained marine exposure.

---

## Weatherproofing

The battery system is the highest electrical-energy component in a wet, sandy
environment. A failure here is a safety event, not just a warranty claim.

### Bay sealing

- Bay door: gasket-sealed, latching closure. Gasket material: EPDM or silicone
  (salt/UV resistant). No foam-only seal — foam compresses and loses seal over time.
- Bay drain: a small weep hole at the lowest point of the bay ensures condensation
  drains out rather than pooling on the pack. Not a weakness — it's a feature.
- Connector: bulkhead-style waterproof connector (Anderson SB or Deutsch DT
  series, IP67 rated). Connector mates before bay door closes; bay door is not
  the primary electrical isolation.

### Contacts and connectors

- No exposed banana jacks or blade connectors
- All contacts covered when pack is removed (blade cover or recessed design)
- Connector keyed (can only be inserted one way)
- Contact material: gold-plated or silver-plated for corrosion resistance; do not
  use bare copper exposed to salt air

### Pack housing

- Pack housing: sealed enclosure, IP67 minimum. Not relying on the bay door for
  primary pack protection — the pack itself must be independently sealed.
- Pressure equalization: small Gore-Tex vent (or equivalent) to equalize internal
  pressure across temperature changes without letting water in.

---

## Charging

### Charge connector

- External charge port on the wagon (user does not need to remove the pack to
  charge, though removing it is preferred for indoor storage)
- Port location: accessible, on a face protected from direct splash (side, rear,
  or recessed top)
- Connector: IP67-rated charging connector with protective cap when not in use.
  Consider: Anderson SB50 with sealed cap, or a marine-spec DC socket.
- Charge via standard external charger (included in product); not USB-C (power
  levels require dedicated charging hardware)

### Charge time target

- Full charge from 0 to 100%: ≤ 4 hours (overnight charge scenario)
- At 500 Wh pack, 4 hr charge = 125 W charger minimum. A 3A / 42V charger
  (standard e-bike spec at 36V/10S) achieves this.

### Charge state indication

- Charge indicator on the pack itself (LED bar or ring): visible without removing
  the pack from the bay when bay door is open
- Optionally: charge indicator on the handle (see `handle-and-controls-ux.md`)
- Indicator levels: 4-segment (25% increments) is sufficient; more is a cost add

---

## Safety

### BMS requirements

The BMS is a hard requirement, not optional. It must protect against:
- Overcurrent (motor stall or short circuit)
- Overtemperature (discharge and charge)
- Over/undervoltage per cell
- Cell balancing (passive or active)

**Temperature management:** in direct sun on a black sand beach, ambient
temperatures can exceed 50 °C. Li-ion cells should not be charged above 45 °C
(standard BMS limit). The BMS must disable charging (not discharging) if pack
temperature exceeds this threshold. A thermal indicator (warning light or app
notification if Bluetooth-enabled) is strongly recommended.

### Near-water handling

- User must be able to remove the pack with wet hands without risk of shock.
  All live contacts must be recessed, shrouded, or behind the connector face.
- Pack should survive a drop into 1 m of fresh water for 30 minutes (IEC
  60529 IPX7) without safety event. This is a "dropped in the shallows" scenario,
  not a design-to-be-submerged spec.
- Saltwater immersion is a damage event, not a design scenario. Recovery protocol
  should be documented in maintenance guide.

### Regulatory path (plan for)

- UN38.3 (transport safety for lithium batteries) — required for shipping
- UL 2271 or equivalent (batteries for light electric vehicles) — required for
  retail/DTC in most markets
- CE marking (if EU market) — requires relevant EMC and safety standards
- **Start the certification conversation with the pack manufacturer early.
  Retroactive certification is expensive.**

---

## Open decisions

- [ ] Confirm operating voltage (24 V vs. 36 V) with motor supplier
- [ ] Proprietary vs. power-tool platform for v1 (recommend proprietary; revisit after COGS model)
- [ ] Confirm Wh target after bench test of motor under load (don't finalize pack until motor draw is measured)
- [ ] Select charge connector standard
- [ ] Identify pack manufacturer candidates (custom Li-ion pack with IP-rated housing + BMS)
