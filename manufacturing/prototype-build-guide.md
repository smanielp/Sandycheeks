# Prototype Build Guide — v0 Integration Prototype

> Step-by-step guide for building the first working prototype. The goal of v0 is
> one thing: **demonstrate that powered assist solves the soft-sand haul problem.**
> It does not need to be production-representative. It needs to work on a real
> beach with a real load so you can film it and put it in front of customers.
>
> Production design: → `manufacturing/product-and-prototype-spec.md`
> What to test when it's built: → `manufacturing/test-protocol-scorecard.md`

---

## What v0 is (and isn't)

**V0 is:** an integration of a motor, battery, and controller onto an existing
beach wagon, assembled with off-the-shelf components, hand-wired, and held
together by mounts you fabricate or buy off Amazon. It will look like a prototype.
That is fine. It is used internally — for testing, for the demo video, and to
generate data for the v1 design. It will corrode. That is expected and irrelevant.

**V0 is not:** a product to show customers, a corrosion test, a safety-certified
build, a weight-optimized design, or an indicator of what the product will look or
feel like. Do not let the v0 prototype's look discourage you or mislead stakeholders.

---

## Step 1 — Select a host cart

### Selection criteria

You are choosing a starting cart that will become the body of the prototype.
The motor, battery, and controls will be added to it. The cart itself is not
the product — it is a mule.

| Criterion | Why it matters | Minimum spec |
|-----------|---------------|-------------|
| Wheel diameter | Larger wheels float better on soft sand | ≥ 16" diameter |
| Tire type | Low-PSI balloon/fat tires reduce rolling resistance on sand | Low-PSI (≤ 8 PSI); wide (≥ 4" section width) |
| Axle access | You are mounting a motor to or near the axle | Accessible rear axle, preferably solid, round, standard diameter |
| Frame stiffness | Motor mount needs a rigid attachment point | Steel tube frame preferred; flimsy injection-molded frame is hard to mount to |
| Load capacity | Rated for your test load | ≥ 150 lbs rated (overshoot by 50% vs. your test load) |

### Candidate carts to evaluate (buy and assess before committing)

- **Mac Sports Heavy Duty Folding Utility Cart (XL)** — widely available, steel
  frame, good wheel size, folds. Axle access is the question; check before buying.
- **Sea Striker / Rio carts with balloon tires** — preferred by surf anglers;
  good wheel size; typically steel frame.
- **Gorilla Carts GOR4PS** — solid axle, steel frame, 600-lb capacity.
  Overkill structurally; good for motor mount. Wheels may need upgrade.

**Recommendation:** buy two candidates (≈$100–250 each) and evaluate axle access
in person before committing to the motor mount design. The axle is the critical
interface.

### Axle assessment

With the cart in hand:
1. Measure axle diameter (typically 5/8" or 3/4" on utility carts)
2. Check whether the axle is a single through-axle or stub axles
3. Check whether the wheel bearings are pressed onto the axle (you'll need a
   puller) or slip-fit with a nut (much easier)
4. Measure available axle length outside the wheel hub (you need ≥ 30 mm for a
   hub motor if replacing a wheel, or for a sprocket if using chain drive)

---

## Step 2 — Select motor and controller

### Motor — hub motor in rear wheel (recommended for v0)

**Target spec for v0:**
- 250–500 W BLDC hub motor
- Rated for 24 V or 36 V (match to your battery)
- Cassette or disc brake compatible (for future regen; not required in v0)
- Torque: ≥ 20 Nm

**Practical v0 approach:** adapt a bicycle or e-bike rear hub motor. E-bike hub
motors are designed for 26" bicycle wheels; your wagon likely has smaller wheel
diameters. You have two options:

**Option A — Re-lace motor into wagon wheel rim.** Strip the hub out of the
e-bike wheel, re-lace it into a balloon-tire wagon rim of similar spoke count.
This gives you the right wheel size and the right tire. Requires a spoke wrench
and a patient afternoon. **Recommended.**

**Option B — Mount motor axle-end to frame and use chain/belt drive.** Bolt a
geared motor (e.g., a brushless motor with planetary gearbox, from robotics or
e-scooter supply chain) to the frame; run a chain or belt to a sprocket on the
axle. More fabrication; better motor protection; fine for v0.

**Supplier starting point:** search "48V 500W hub motor" or "36V rear hub motor
kit" on eBay, AliExpress, or Grin Technologies (Grin is Canadian, higher quality,
more expensive but worth it for a controlled test). Budget: $100–250.

### Controller

Match the controller to your motor voltage and current rating. Get the motor and
controller from the same supplier or same ecosystem to avoid compatibility issues.

**For v0:** an e-bike controller with a thumb throttle input is sufficient. No
load sensing, no mode selection. Budget: $30–80 (often bundled with motor).

**Controller mounting for v0:** zip-tie it to the wagon frame wrapped in a
ziplock bag, then inside a plastic waterproof case. This is ugly. It is fine.

---

## Step 3 — Select battery

### Recommended for v0: adapted power-tool batteries (quickest path)

Use two Milwaukee M18 12Ah packs wired in series for 36V, 12Ah = 432 Wh.
These are available at any hardware store. You are not using them as designed;
you are adapting them. Risks:
- M18 BMS may not support continuous motor loads; it may trip. Monitor this.
- Not IP-rated for sustained water exposure. Protect them in a waterproof case.
- Wiring in series requires care: get polarity right, fuse each leg.

**Alternative for v0:** a 36V 10Ah Li-ion pack from an e-bike supplier
(AliExpress, Luna Cycle, EM3ev). Pre-built with BMS, typically in a plastic
enclosure. Budget: $80–180. Better choice if power-tool BMS tripping is an issue.

### Battery mounting for v0

Mount the battery in a **Pelican 1400 or equivalent waterproof hard case** bolted
to the wagon frame (or bungee-corded on for first iteration). Run power cables
through a waterproof gland in the case. This is not pretty. It keeps the battery
safe enough for beach testing.

Budget for Pelican or clone case: $40–80.

---

## Step 4 — Motor mounting

### Hub motor in wheel (Option A)

If you re-laced the motor into a wagon rim:
1. The motor axle replaces the original wheel axle.
2. You need axle adapters if the motor axle diameter doesn't match the wagon
   fork/bearing slots. Machine these from aluminum bar stock (a local machine
   shop can do this for $50–100).
3. Torque arms: the motor axle must not spin in the dropout. Install steel torque
   arms on both sides of the axle. These are available for e-bike conversions
   for $10–20.
4. Route the motor phase wires up the frame; zip-tie them so they can't catch
   on anything rotating.

### Geared motor on frame (Option B)

1. Weld or bolt a motor mount bracket to the wagon frame (a steel angle bracket
   from the hardware store, drilled to fit, is adequate for v0).
2. Position the motor so the output shaft aligns with the axle sprocket.
3. Tension the chain. Use a chain tensioner or eccentric motor mount if you can.
4. Protect the motor from direct sand splash with a simple sheet-metal shield
   (not airtight — just deflecting).

---

## Step 5 — Wiring

Wire the system: battery → fuse → controller → motor → throttle. Keep it simple.

**Fuse:** put a fuse between the battery positive terminal and the controller,
rated 1.5× the controller's max current draw. Do not skip this. A fused short
is a blown fuse; an unfused short is a battery fire.

**Connections:** use XT60 or Anderson SB50 connectors for all high-current
connections (motor ↔ controller, battery ↔ controller). Do not use household
wiring connectors (Wago, wire nuts) for 20+ amp DC circuits.

**Wire gauge:** use 12 AWG or heavier for all power runs. Thin wire at high
current = heat = fire.

**Weatherproofing wiring for v0:** wrap all connections in self-fusing silicone
tape after completing. This is not permanent or IP-rated; it keeps sand out of
connectors for the test duration.

**Diagram (schematic-level):**

```
[Battery +] → [Fuse] → [Controller +]
[Battery -] ─────────→ [Controller -]
[Controller] → [Phase A, B, C] → [Motor windings]
[Controller] → [Hall A, B, C + 5V + GND] → [Motor Hall sensors]
[Throttle] → [Throttle signal + 5V + GND] → [Controller]
```

---

## Step 6 — Handle controls (v0)

For v0, mount a standard thumb throttle on the handle. Route the throttle cable
inside or alongside the handle tube to the controller. Zip-tie neatly.

Do not attempt load-cell sensing for v0. The sensing refinement comes in v1.
The question for v0 is "does powered assist help?", not "is the control feel perfect?"

---

## Step 7 — Pre-beach bench test

Before going to the beach:

1. **Static motor spin test:** battery connected, controller armed, throttle
   engaged slowly. Motor should spin smoothly in both directions. No grinding,
   no cogging at low speed.
2. **Load test on pavement:** put 50 lbs of load in the wagon. Walk beside it
   with throttle at 50%. Motor should pull without overheating controller or
   tripping BMS. Run for 5 minutes continuous; check controller temperature.
3. **Ramp test on a slope:** find a steep driveway or ramp. Confirm the wagon
   doesn't free-roll when throttle is released (drag from motor or add a simple
   brake).
4. **Range estimate:** fully charge battery; run motor at 50% throttle continuous
   until BMS trips. Measure time. Extrapolate to expected beach duty cycle.

---

## Known v0 compromises (what they don't tell you)

| Compromise | What it is | What it doesn't test |
|-----------|-----------|---------------------|
| Power-tool battery | Not marine-sealed; may trip BMS | Real battery pack performance, sealing, swapability |
| Ugly mounts | Bolt-on or welded; not integrated | Structural integrity of purpose-built frame |
| No corrosion package | All exposed; will corrode immediately | Long-term corrosion resistance of v1 design |
| Passive throttle only | User controls assist level manually | E-bike-feel load sensing UX |
| Off-the-shelf wheels | May not be ideal size/type | Optimized tire-and-wheel system |

**The v0 prototype will answer:** does electric assist meaningfully reduce soft-sand
haul effort? Will customers pay for it when they see the demo?

**The v0 prototype will not answer:** how long will it last? Will the controls feel
right? Can it be manufactured at target cost? Will it survive the marine environment?

---

## Bill of materials (v0, rough)

| Item | Estimated cost |
|------|---------------|
| Host cart | $150–250 |
| Hub motor + controller + throttle (kit) | $150–250 |
| 36V 12Ah battery (e-bike pack or adapted tool batteries) | $100–180 |
| Waterproof battery case (Pelican or clone) | $40–80 |
| Axle adapters / machining | $50–100 |
| Torque arms | $15–25 |
| XT60/SB50 connectors, fuse, wiring | $30–50 |
| Misc mounting hardware, zip ties, tape | $20–30 |
| **Total estimate** | **$555–965** |

Budget $1,000–1,200 to have room for first-attempt mistakes and replacement parts.

---

## What to do when it's built

→ Run `manufacturing/test-protocol-scorecard.md` on a real beach with a measured
load. Film everything. The demo video is the primary deliverable.
