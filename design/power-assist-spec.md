# Power Assist Spec — Drivetrain & Controls

> Engineering design intent for the motor, controller, sensing, and assist logic.
> Not final engineering — use this to brief a motor/controls supplier or evaluate
> COTS e-bike/scooter drive components for adaptation.
>
> Cross-cutting constraints: → `design/system-overview.md`
> Physical controls and handle UX: → `design/handle-and-controls-ux.md`

---

## Assist philosophy

**Amplify the puller, don't replace them.**

The motor responds to the effort the person is already making — when they pull
harder, it helps more. When they stop, it stops. This is the e-bike model
applied to a wagon. It is not a throttle-first, operator-drives model.

Why this matters for the product: it keeps the wagon feeling like a wagon. The
person is in control; the motor is a multiplier. This is a product character
decision, not just a UX preference — it differentiates the product from powered
utility carts and from the "walk-behind robot" category.

---

## Motor options

### Option A — Hub motor in driven wheel(s)

A hub motor replaces the wheel hub on one or both rear wheels. The motor housing
is the wheel hub; the tire mounts on the outside.

| Pros | Cons |
|------|------|
| No drivetrain between motor and wheel (fewer parts, fewer failure points) | Motor is exposed to worst-case sand and water ingress |
| Simple integration into existing wheel assembly | Wheel replacement = motor replacement (serviceability concern) |
| Well-understood from e-bike supply chain | Limits balloon-tire selection to hubs with matching ERD |
| Self-contained IP package | Heavier unsprung mass |

**IP packaging:** the motor housing must achieve IP67 minimum (immersion to 1 m).
Marine-specific hub motors exist (bilge pump / trolling motor heritage). Standard
e-bike hub motors are not adequate — they are designed for rain, not submersion
or salt spray sustained exposure.

### Option B — Geared motor to axle

A sealed geared motor (similar to a power-tool gearbox) drives the axle via a
chain, belt, or direct coupling. Motor is mounted to the frame, not in the wheel.

| Pros | Cons |
|------|------|
| Motor can be positioned away from worst-case splash zone | Drivetrain between motor and wheel (chain/belt/coupling) |
| Easier to seal the motor enclosure (not rotating relative to wheel) | More parts, more potential failure and ingress points |
| Motor is serviceable independently of wheels | Belt/chain tension and alignment management in sand |
| Wider motor selection | Coupling to axle adds complexity |

**Preferred direction for v1:** hub motor, marine-spec, single rear driven wheel
as a starting point. Revisit dual-drive if traction testing shows single rear
wheels digging in on soft sand under load.

---

## Dual vs. single driven wheel

| Configuration | Traction | Turning | Cost | Complexity |
|--------------|---------|---------|------|-----------|
| Single rear | Adequate on firm sand | Balanced (free-rolling front wheels) | Lower (1 motor, 1 controller) | Lower |
| Dual rear | Better on soft/deep sand; less digging | Requires electronic differential or slip | Higher (2 motors or 1 motor + diff) | Higher |

**Recommendation:** Start with single rear driven wheel. If beach testing reveals
consistent wheel-digging on soft sand with 100-lb load, graduate to dual drive.
Electronic differential is preferable to mechanical differential for corrosion
resistance.

---

## Controller

### Speed governing

Maximum speed: **4–5 km/h (2.5–3 mph)** — brisk walking pace. Governed in
firmware, not mechanically. The governor is a product character decision; it
keeps the wagon feeling like assist, not transport.

Implementation: closed-loop speed control in the controller firmware. PID with
ramp limiting (see ramp section below). Target: cannot exceed governed speed
regardless of assist level or terrain.

### Torque sensing vs. load sensing vs. current sensing

The controller must know "how hard is the person pulling?" to deliver
proportional assist. Three options:

| Method | How it works | Pros | Cons |
|--------|-------------|------|------|
| **Handle torque/load sensor** | Strain gauge or load cell at handle-to-wagon connection; measures pull force | Direct measurement of actual intent; responsive | Mechanical complexity at handle; sensor must be IP-rated; calibration |
| **Motor current sensing** | Controller monitors motor current draw; infers load | No extra sensor; uses existing controller data | Lags behind actual pull; less intuitive feel; hard to tune |
| **Passive throttle (v0)** | Simple thumb throttle — user sets assist level manually | Simplest for prototype; no sensing needed | Not e-bike-style assist; user is the control loop; less intuitive |

**Recommendation:**
- **v0 prototype:** passive throttle. Focus on proving the motor/traction
  concept, not the control finesse.
- **v1 product:** handle load sensor. The e-bike-feel is a differentiator;
  it requires real sensing. Brief this to controls supplier as a key spec.

### Ramp-up behavior

The motor must **not lurch** when assist engages. A loaded wagon jerking forward
is a safety problem and a product experience failure.

Spec:
- Ramp from 0 to full assist torque in ≥ 500 ms (tune to feel in testing)
- Deceleration ramp: ≥ 300 ms from full to zero (no abrupt stop)
- No step changes in torque output; all transitions are rate-limited

### Assist modes

**Recommended v1 configuration: two modes + off.**

| Mode | Behavior | Use case |
|------|---------|---------|
| Off | Motor fully disengaged; freewheeling | Manual pull; dead battery |
| Eco | ~50% max motor torque; longer range | Flat/firm sand; longer haul |
| Max | Full motor torque; shorter range | Dry sand; slopes; heavy load |

Mode selection via handle-mounted button — see `design/handle-and-controls-ux.md`.

A single on/off mode is acceptable for v0. Multiple modes add complexity to the
control system and the handle UX; defer to v1.

---

## Downhill behavior

A loaded wagon on a slope can accelerate past walking pace without the motor
doing anything — gravity does the work. This is a **safety problem**: a 100-lb
wagon running away on a sandy slope will cause injury or gear loss.

Two options:

| Option | How | Pros | Cons |
|--------|-----|------|------|
| **Regenerative braking** | Controller runs motor in generator mode when wagon exceeds governed speed; returns energy to battery | Controlled deceleration; recovers energy; elegant | Requires controller with regen capability; more complex firmware |
| **Mechanical drag / drum brake** | Friction brake on axle, spring-loaded to a light drag | Simple; reliable; no firmware | Constant drag on flat ground (efficiency loss); wears; heat |

**Recommendation:** regenerative braking if controller supports it (most modern
BLDC controllers do). Tune regen drag so the wagon holds to walking pace on a
10° slope with 100-lb load. Test this explicitly in the beach test protocol.

---

## Failure modes — design against these

| Failure | Effect | Mitigation |
|---------|--------|-----------|
| Motor seized (corrosion) | Wagon becomes very hard to pull | Freewheeling design; manual disconnect |
| Controller failure | No assist | Fail-safe to zero torque; freewheeling mode |
| Battery depleted | No assist | Manual pull must be acceptable (see system-overview weight constraint) |
| Torque sensor drift | Assist always on or always at wrong level | Deadband in firmware; sensor calibration routine |
| Over-speed on slope | Wagon runs away | Speed governor + regen braking as primary; mechanical drag as backup |

---

## Component specification targets (for supplier briefing)

| Component | Spec target | Notes |
|-----------|------------|-------|
| Motor type | BLDC hub or geared, 250–500 W continuous | 500 W peak acceptable for slopes; continuous rating matters for range |
| Motor IP | IP67 minimum | IP68 preferred |
| Motor torque | ≥ 25 Nm at wheel | For 100-lb load on dry sand; validate with torque model |
| Controller | FOC (field-oriented control) BLDC; speed + torque governed | FOC gives smoother low-speed control than block commutation |
| Controller IP | IP65 minimum | Mounted on frame, exposed to splash |
| Speed governor | Firmware-configurable; default 4.5 km/h | |
| Regen braking | Required for v1; optional for v0 | |
| Operating voltage | 24 V or 36 V DC nominal | Match to battery spec; 36 V preferred for higher power headroom |

---

## Open decisions

- [ ] Confirm single vs. dual driven wheel after soft-sand traction test
- [ ] Select motor topology (hub vs. geared) before BOM
- [ ] Confirm operating voltage with battery spec (see `battery-and-charging-spec.md`)
- [ ] Confirm sensing method for v1 (load cell vs. current sensing)
- [ ] Source marine-rated BLDC hub motor candidates and evaluate IP/torque/cost
