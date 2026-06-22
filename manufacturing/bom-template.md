# Bill of Materials — Template

> Pre-structured BOM template organized by subsystem. Component entries reflect
> the "bill of concerns" from the product spec — real specs and costs TBD pending
> motor supplier selection, battery platform decision, and frame material choice.
>
> Instructions: fill in Spec/Target as design decisions are made; fill in
> Unit Cost after RFQ or procurement; fill in Supplier Candidates as sourced.
>
> Version: v0 template (not a validated BOM)

---

## Subsystem 1 — Drivetrain & Controls

| # | Component | Description | Spec / Target | Supplier Candidates | Unit Cost (est.) | Notes |
|---|-----------|-------------|--------------|--------------------|-----------------:|-------|
| D1 | Drive motor | BLDC hub motor or geared motor | 250–500 W, 36 V, IP67, ≥ 25 Nm | Grin Technologies, QS Motor, Bafang | TBD | Hub preferred; marine-spec required; verify IP rating independently |
| D2 | Motor controller | FOC BLDC controller w/ regen | 36 V, 20–30 A continuous, FOC, IP65, throttle + Hall inputs | Grin, KT, ASI (BAC) | TBD | Match to motor; regen capability required for v1 |
| D3 | Torque/load sensor | Load cell at handle joint | 0–150 lb range, IP65, analog or CANbus output | Futek, Omega, Interface | TBD | v1 only; v0 uses passive throttle |
| D4 | Throttle (v0 only) | Thumb throttle | Hall-effect, 0–5V output, IP54 | Generic e-bike supply | $8–15 | v0 prototype only; replaced by load sensor in v1 |
| D5 | Speed governor | Firmware in controller | Max 4.5 km/h; configurable | N/A (firmware) | — | Spec to controller supplier |
| D6 | Mode selector switch | Assist mode button on handle | Momentary SPST, IP65, tactile click, ≥ 20 mm | E-Switch, C&K, NKK | $3–8 | Qty 1 per unit; see handle UX spec |
| D7 | Braking / drag | Regen (preferred) or drum brake | Regen: firmware in controller; drum: spring-loaded friction | Controller (regen), Hayes (drum) | TBD | Regen preferred; drum as backup if controller doesn't support |
| D8 | Motor cable assembly | Phase + Hall cable from motor to controller | 3-phase + 5-wire Hall, IP67 glands, ≥ 1.5 m | Custom / motor supplier | TBD | Specify with motor; cable gland at enclosure entry |
| D9 | Controller enclosure | Weatherproof housing for controller | IP65, UV-stable polycarbonate, stainless fasteners | Hammond, Bud Industries | $15–30 | Frame-mounted; cable gland entries |

---

## Subsystem 2 — Battery & Charging

| # | Component | Description | Spec / Target | Supplier Candidates | Unit Cost (est.) | Notes |
|---|-----------|-------------|--------------|--------------------|-----------------:|-------|
| B1 | Battery pack | Li-ion pack with BMS | 36 V nominal (10S), 350–500 Wh, IP67 housing, removable | Custom (preferred); Luna Cycle, EM3ev | TBD | BMS must support motor load; see battery spec for details |
| B2 | BMS | Battery management system (if custom pack) | 10S, ≥ 30A continuous, temp cutoff at 45°C charge | Daly, JBD (LLT), Orion | TBD | Often integrated into pack; spec separately if custom cell assembly |
| B3 | Battery bay connector | Waterproof power connector, battery to controller | 36 V, 30A+, IP67, locking, keyed | Anderson SB50, Deutsch DT, Amphenol | $8–15/pair | Mating connector on battery and on frame harness |
| B4 | Charge port | External charge input on wagon | 36 V / 42 V charge voltage, IP67, capped when not in use | Neutrik, Switchcraft, custom | $10–20 | Frame-mounted; spring-loaded cap |
| B5 | Charger | External Li-ion charger | 42 V CC/CV, 3A output, US/global plug, UL listed | Generic e-bike 10S charger, Grin Satiator | $30–60 | Included with product; not waterproof (for indoor use) |
| B6 | Charge indicator | LED bar on battery / wagon | 4-segment, visible in daylight, IP65 | Bivar, custom PCB | $5–12 | On battery housing or bay exterior |
| B7 | Pressure vent | Gore-Tex or equiv. vent for battery housing | IP67 vent, ≥ 10 mm diameter | Gore (PTFE vent), Donaldson | $2–5 | Prevents pressure differential buildup; allows condensation equalization |
| B8 | Battery latch / release | One-action locking release for battery removal | Single-action (lever or button), no-tools, positive lock | Southco, Sugatsune, custom | $8–15 | Must lock positively; cannot rattle loose over rough terrain |

---

## Subsystem 3 — Frame, Wheels & Corrosion Package

| # | Component | Description | Spec / Target | Supplier Candidates | Unit Cost (est.) | Notes |
|---|-----------|-------------|--------------|--------------------|-----------------:|-------|
| F1 | Frame | Main wagon chassis | 6061-T6 aluminum, hard-anodized (Type III), welded | Local fab / manufacturer | TBD | Drivetrain and battery bay must be designed in, not bolted on |
| F2 | Cargo bed / body | Load-bearing platform | HDPE or 6061 aluminum; UV-stable; corrosion-proof | Manufacturer | TBD | 150 lb capacity; drain holes at corners |
| F3 | Rear wheels (driven) | Hub motor integrated or drive wheels | 16"+ diameter, low-PSI balloon tires (≤ 8 PSI), sealed bearings | (Hub motor replaces rear hub) | See D1 | Specify rim ERD to match hub motor spoke count |
| F4 | Front wheels (free-rolling) | Passive front castors or fixed wheels | Match rear diameter or close; balloon tires; sealed bearings | (Match to manufacturer's platform or source separately) | TBD | Swiveling castors for maneuverability on sand |
| F5 | Wheel bearings (all) | Deep-groove ball bearings, double-sealed | 2RS designation, ABEC-5, marine grease, standard dimensions | SKF, FAG, NSK | $5–12/each | All 4 wheel positions; replace on the driven side with motor |
| F6 | Axle (front) | Front wheel axle | 316 SS or anodized 6061; matches bearing ID; through-axle preferred | Stock rod / manufacturer | TBD | |
| F7 | All external fasteners | Screws, bolts, nuts for all external-facing hardware | 316 stainless (A4 grade) throughout | Fastenal, McMaster-Carr (SS section) | $0.10–1.00/ea | Verify grade on every procurement lot; no substitutions |
| F8 | Handle assembly | Telescoping handle with grip | Aluminum tube, TPR overmold grip, 30–35 mm OD, 30–50" extension range | Custom / manufacturer | TBD | Load sensor or cable routing per UX spec |
| F9 | Bearing grease | Marine-grade grease for initial fill and service | NLGI 2, calcium sulfonate base (e.g., Mobilgrease XHP 222) | Mobil, Castrol, WD-40 Specialist | $8–15/tube | Specify for bearing supplier pre-fill and for customer service kit |
| F10 | Cable glands | IP-rated cable entry for all enclosures | PG-thread or metric, IP68 rated, nylon or brass | Roxtec, Pflitsch, Wiska | $1–4/ea | One per cable entry in each enclosure |
| F11 | EPDM gaskets | Sealing gaskets for battery bay door, electronics lids | EPDM (saltwater + UV resistant), molded or cut-to-profile | McMaster-Carr, Parker | $2–10/ea | Not foam; compression-set resistant |

---

## Electronics & Wiring

| # | Component | Description | Spec / Target | Supplier Candidates | Unit Cost (est.) | Notes |
|---|-----------|-------------|--------------|--------------------|-----------------:|-------|
| E1 | Main wiring harness | Power and signal wiring through frame | 12 AWG power (30A+); 20 AWG signal; UV-stable jacket | Custom (manufacturer) | TBD | Route inside frame tubes where possible |
| E2 | Main fuse | In-line fuse between battery and controller | Blade fuse, 30–40A, with IP-rated fuse holder | Littelfuse, Eaton | $3–8 | Also consider Midi fuse for higher current versions |
| E3 | Handle PCB | Controls and indicator board | IP65-compatible potting or conformal coat; I²C or SPI to display | Custom | TBD | LED bar + status LED + button + load cell ADC (v1) |
| E4 | Status LED | Assist status indicator | IP65, weatherproof, visible in daylight, green/blue/red capable | Dialight, Cree (epoxy-packaged) | $1–3 | Part of handle PCB assembly |

---

## Consumables & Packaging (not detailed here)

- Charger (see B5 above; included in box)
- Quick-start card / care guide (1 page, waterproof stock)
- Packaging (protective; shipping box spec TBD based on final dimensions)

---

## BOM version control

| Version | Date | Changes |
|---------|------|---------|
| v0 template | 2026-06-21 | Initial template; all costs TBD; specs are targets |
| | | |

---

## Instructions for the next version

When design decisions are finalized (motor, battery platform, frame material):
1. Replace "TBD" costs with quotes from suppliers (see `manufacturing/rfq-template.md`)
2. Lock supplier selections and add part numbers
3. Calculate total COGS including assembly labor estimate
4. Feed into unit-economics model (`business/unit-economics.md`)
