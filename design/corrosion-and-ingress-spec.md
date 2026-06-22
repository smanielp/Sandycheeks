# Corrosion & Ingress Spec

> Material selections, IP rating targets, surface treatment decisions, and
> geometry principles for surviving the marine environment. This is the real moat.
>
> Cross-cutting constraints: → `design/system-overview.md`
> Sealing interfaces for battery bay: → `design/battery-and-charging-spec.md`
> Motor and controller IP: → `design/power-assist-spec.md`

---

## Why this document matters

Corrosion and sand ingress are where this product wins or loses long-term.
Electric motors, bearings, fasteners, and electronics in a salt + sand environment
will fail within months without explicit design choices against these failure modes.

The competition (powered utility wagons, garden carts) is not built for this
environment. That is the gap. Every decision in this document is a decision to
be harder to kill than the alternatives, and harder to copy than the electrical
system alone.

---

## IP rating targets by component

IP ratings reference IEC 60529. First digit = solids/dust; second digit = liquids.

| Component | Minimum IP | Target IP | Rationale |
|-----------|-----------|----------|-----------|
| Drive motor | IP65 | **IP67** | Runs at wheel height; direct sand/water contact in use |
| Motor controller | IP65 | IP65 | Mounted on frame; splash-exposed; not immersed |
| Battery pack housing | IP65 | **IP67** | Must survive "dropped in the shallows" scenario |
| Battery bay (in frame) | IP54 | IP65 | Supplemental protection; bay door is primary seal |
| Battery connector / charge port | IP67 | IP67 | Mated connector; cap-protected when open |
| Handle electronics (button, indicator) | IP65 | IP65 | Rain and splash but not immersion |
| All external fasteners | N/A | A4 stainless (316) | Corrosion class, not IP |
| Wheel bearings | Sealed (ABEC-5 or equiv.) | Double-sealed | No IP rating; must have internal labyrinth + lip seal |

**Testing note:** IP ratings are tested in controlled lab conditions with clean
water at specified flow rates. Salt water, sand-laden water, and UV exposure
are not part of the IEC test. Design to IP rating as a floor, not a ceiling.
Internal corrosion testing under ASTM B117 (salt fog) is the actual relevant test.

---

## Material selections

### Structural members (frame, load bed supports)

**Marine-grade aluminum (6061-T6 or 6063-T6)** as primary material.
- Lightweight, weldable, anodizable
- Corrosion-resistant to salt without coating (oxide layer); coating adds a further layer
- Avoid 2xxx and 7xxx series alloys for marine environments (lower corrosion resistance)
- Avoid bare steel (even galvanized) for any structural member in continuous salt exposure

**Alternative for frame:** powder-coated mild steel acceptable **only** if:
- All cut edges are sealed before powder coat
- Powder coat thickness ≥ 80 µm (ASTM D7091)
- All drainage paths are present so water cannot pool inside hollow sections

**Avoid:** bare aluminum in contact with steel (galvanic couple, aluminum is
anodic and will corrode). Use nylon washers or HDPE isolators at all
aluminum-to-steel interfaces.

### Fasteners

**All external fasteners: 316 stainless steel (A4 grade).**

- 316 SS contains molybdenum, which resists pitting corrosion from chlorides
- 304/A2 stainless is not adequate for sustained salt-water exposure
- No zinc-plated, cadmium-plated, or black-oxide fasteners on external surfaces
- Use nylon-insert lock nuts or thread-locking compound (Loctite 243 or 271) —
  salt environments accelerate vibration loosening

**Fastener access:** all fasteners accessible from outside without disassembly
of the cargo bed. A rusted-in-place bolt that requires cargo bed removal to
address is a warranty nightmare.

### Wheel bearings

**Double-sealed deep-groove ball bearings (e.g., 6xxx-2RS series).**

- Both inner and outer seals (2RS designation) — rubber contact seal on both sides
- Pre-greased with marine-grade grease (NLGI 2, calcium sulfonate or lithium complex)
- No open bearings (no 6xxx-ZZ or open-race bearings on any wheel or axle)
- Bearing housings: aluminum or 316 SS, not cast iron

**Replacement philosophy:** bearings should be user-replaceable with standard
tools. Proprietary bearing sizes add warranty cost and customer frustration.

### Motor housing

Hub motor or gearbox housing: **die-cast aluminum with clear anodize or powder
coat.** Not painted steel. Internal components (windings, magnets) must be
protected by the housing seal, not by individual coatings on components.

### Electronics enclosures (controller, handle PCB)

**Polycarbonate or ABS with UV stabilizer** for controller enclosure.
- UV stabilizer required — unprotected plastic becomes brittle and cracks in
  direct sun within 2–3 seasons
- Stainless steel fasteners for enclosure lid; EPDM or silicone gasket
- Cable entries via IP-rated glands (PG-series or Roxtec equivalent)

---

## Sand-shedding geometry principles

Sand is abrasive and gets into everything. Geometry that traps sand will fail
before a geometry that sheds it, even with identical materials.

**Rules:**
1. **No upward-facing pockets or channels** in the drivetrain or electronics
   areas. Sand settles in; water washes it into bearings and seals.
2. **No exposed threads** on drive components. Sand in threads = galling,
   seized fasteners, corrosion at thread roots. Use cap nuts, thread covers,
   or recessed fasteners.
3. **All cable runs exit enclosures pointing downward.** Cables running up into
   an enclosure form a water entry path (wicking + gravity). Exit down; loop up
   if needed to create a drip point outside the enclosure.
4. **Drainage paths.** Any closed cavity that can trap water (hollow frame
   sections, battery bay) must have a weep hole at the lowest point. Do not
   rely on gaskets alone to keep water out of enclosed volumes; let it drain.
5. **Smooth external surfaces.** Avoid external ledges, ribs, or undercuts that
   collect sand. Beach sand is extremely fine; it will pack into any crevice.

---

## Surface treatments by component

| Component | Treatment | Notes |
|-----------|-----------|-------|
| Aluminum frame | Hard anodize (Type III), clear or black, 25 µm min | Hard anodize > standard Type II for wear resistance; no paint needed for corrosion |
| Aluminum motor housing | Clear anodize (Type II) or powder coat | Anodize preferred; powder coat acceptable if housing edges are sealed |
| Steel fasteners | None (316 SS self-protecting) | Verify grade on every procurement batch |
| Aluminum fasteners | Do not use | Too soft, galls in 316 SS threads |
| Cargo bed (if HDPE / polypropylene) | None (UV-stabilized material) | HDPE is inherently corrosion-resistant |
| Cargo bed (if aluminum) | Powder coat or anodize | Edge sealing required |
| Electronics enclosures | UV-stable powder coat or Cerakote on exterior | |
| Handle | Anodize (if aluminum) or UV-stable nylon overmold | |

---

## Corrosion testing plan

Validate the corrosion spec before committing to a production BOM. Do not rely
on supplier IP ratings for salt-spray performance.

| Test | Standard | Pass threshold | When |
|------|---------|---------------|------|
| Salt fog — fasteners | ASTM B117 | No red rust at 500 hrs | Before finalizing fastener spec |
| Salt fog — motor housing | ASTM B117 | No structural corrosion at 500 hrs | After selecting motor supplier |
| Salt fog — full assembly | ASTM B117 | No electrical failure at 250 hrs | Pre-production validation |
| Real-world soak | Field test at beach | No functional degradation after 20 uses with rinsing | Stage 4 prototype testing |

---

## Maintenance protocol

The product should survive with minimal owner maintenance. But "minimal" is not
"none" — and setting clear expectations prevents warranty disputes.

**Owner responsibility (designed to be easy):**
- Freshwater rinse after every saltwater session. Must take < 2 minutes with a
  garden hose. No pressure washing (pressure drives water past seals).
- Remove and dry the battery pack before storage > 1 week.
- Annual: wipe bearing contact points with marine-grade grease (user-accessible
  grease nipples or zerk fittings at wheel bearings, if included).

**Product survival without maintenance (design to tolerate):**
- The product must survive 10 uses with saltwater exposure and NO rinse without
  structural corrosion or electrical failure. This is the real-world behavior for
  careless users and the basis for warranty claims.
- After season-end storage without rinsing: no permanent damage; may need a flush
  before use.

**Document clearly:** a one-page care card (and landing-page FAQ) that sets
expectations. The Yeti cooler model: clear what it survives, clear what it needs.

---

## Corrosion as the competitive moat

This section is the argument for over-investing here.

Powered utility wagons from Sun Joe, Greenworks, and Alibaba equivalents use:
- Open bearings (common): fail in sand within a season
- Zinc-plated or painted steel fasteners: corrode visibly within a few uses near salt
- Standard NEMA 4 (IP66-equivalent) or lower controller enclosures: not rated
  for submersion that occurs when a wave or tide covers the product
- No thought given to sand-shedding geometry

The first time a customer posts a photo of our competitor's rusted-out axle next
to our wagon's clean one after two seasons of use, that image is worth more than
any marketing spend.

The moat is not the motor. It's the engineering patience to spec every fastener,
every bearing seal, every cable exit direction for the worst environment they
will face.

---

## Open decisions

- [ ] Confirm frame material choice (aluminum vs. powder-coated steel) — affects
  cost, weight, and welding/forming process at manufacturer
- [ ] Select bearing grease specification and whether to include user-accessible
  grease fittings (adds servicing option; adds cost and potential ingress point)
- [ ] Confirm handle material and surface treatment (depends on handle form factor
  decision in `handle-and-controls-ux.md`)
- [ ] Source and test 316 SS fastener suppliers — verify grade on sample batch
  before committing to a BOM supplier
