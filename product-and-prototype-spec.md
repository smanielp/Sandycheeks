# Product & Prototype Spec

> Engineering brief for Model 1 (wheeled, powered). Tracked Model 2 notes at the
> end. This is a design-intent document, not final engineering.

## Design principle

It must feel like **a better wagon, not a vehicle.** Powered assist amplifies the
puller; manual fallback stays tolerable; nothing about it reads as complicated or
fragile. Every decision serves: *get a heavy load all the way to the water with
minimal effort, and survive salt + sand for years.*

## The hard problems (design against these explicitly)

### 1. Soft-sand traction & rolling resistance — the core problem
- It's a **torque and traction** problem, not speed. Target walking pace with
  high low-end torque.
- Wide, low-PSI balloon tires to float on dry sand; correct gearing for torque.
- Worst case to design against: **dry sand at the top of the beach**, plus
  slopes and ruts (the founder's exact failure scenario).
- Decide drive layout: single vs. dual driven wheels, differential behavior in
  turns, and how it behaves when one wheel digs in.

### 2. Corrosion + sand ingress — the real moat
- Saltwater + sand destroy motors, bearings, electronics, fasteners.
- Sealed/IP-rated motor and controller; stainless or anodized hardware; sealed
  bearings; protected battery contacts; design to shed sand, not trap it.
- This is where to over-invest. It's the differentiation clones will struggle to
  copy and the thing warranty claims will hinge on.

### 3. Load-assist control UX
- **e-bike-style assist:** motor responds to the puller's effort (load/torque
  sensing on the handle) rather than a separate throttle.
- Consider: simple thumb-throttle as fallback/secondary; speed limited to brisk
  walk; smooth ramp so it doesn't lurch a loaded cart.
- Downhill behavior: regenerative or mechanical braking / drag so a loaded
  wagon doesn't run away on a slope.

### 4. Battery & safety
- **Removable, swappable** pack (charge indoors, carry spares, store off-season).
- Realistic range target: enough for a full beach day of repeated hauls
  **[VALIDATE target in Wh against measured loads]**.
- Safe to handle near water and sand; sealed contacts; clear charge state.
- Consider compatibility with a common power-tool battery ecosystem to cut cost
  and ease replacement (tradeoff vs. proprietary/branded packs).

### 5. Weight & manual fallback
- Total weight must keep the dead-battery pull tolerable and keep shipping sane.
- Hard budget the weight of motor + battery + drivetrain against the manual
  baseline. If powered-but-dead is worse than today's wagon, the design failed.

### 6. Stability, capacity, and form
- Load capacity target **[VALIDATE]** (anglers: 100+ lbs). Low center of gravity
  for slope stability. Foldability vs. rigidity tradeoff (folding sells, but
  hurts drivetrain integration and stiffness).

## MVP definition — what to build first

**Goal of the prototype: answer one question — does powered assist actually solve
the soft-sand haul, and will the beachhead pay for it?** Not to be
production-ready.

**Recommended MVP path: integration prototype.**
1. Start from a proven big-wheel / balloon-tire beach cart.
2. Add a hub or geared drive motor to the wheel(s) + removable battery + simple
   controller and throttle (assist control can be crude in v0).
3. Test on a real beach with a measured load: dry sand, slope, distance.
4. Measure effort reduction, range, and where it bogs/corrodes/ingests sand.
5. Capture the demo video (see market doc) — the single most persuasive artifact.

**Cheaper still: retrofit-kit MVP.** If capital is tight, build the drive+battery
as a kit that clamps onto existing carts. Validates demand with minimal tooling;
informs whether to graduate to an integrated product.

## Prototype bill-of-concerns (not a BOM yet)

- Drive motor (hub vs. geared), controller, throttle/torque sensor
- Battery pack + charger (proprietary vs. tool-ecosystem)
- Wheels/tires (balloon, low-PSI), axle/bearings (sealed)
- Frame/cargo bed (host cart in v0), braking/drag for downhill
- Corrosion package: coatings, fasteners, seals, gaskets
- Controls/electronics enclosure (IP-rated)

## Test protocol (make it rigorous — this is your Wirecutter edge)

- Standard load (e.g., 100 lbs), standard distances, dry vs. wet sand, flat vs.
  slope. Measure: effort (subjective + force gauge if possible), range, speed,
  time, and failure modes. Repeat across the existing competitor carts so you
  have a comparison baseline, not just an anecdote.

## Model 2 — tracked variant (later)

- Rubber-track drive for maximum soft-sand traction; positions the high end and
  earns press. Heavier, more complex, more expensive, more to corrode/jam with
  sand. **Not the launch product.** Revisit after Model 1 proves the market and
  the corrosion/control engineering is solved.

## IP to scope early

- **Design patents** on the form factor.
- **Utility patents** on the load-assist control method and the track-drive.
- File provisionals before any public demo / waitlist launch if budget allows.
