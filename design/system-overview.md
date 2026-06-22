# System Overview — Model 1 (Wheeled, Powered)

> The reference document. Every sub-spec must be consistent with the constraints
> and interface points defined here. When this document and a sub-spec conflict,
> update the sub-spec — not this document — unless the conflict reveals a flaw in
> the top-level constraint.

## The product in one sentence

A marine-grade powered beach wagon that amplifies the puller's effort over soft
sand, feels like a better wagon (not a vehicle), and survives years of salt,
sand, and sun.

---

## Three subsystems

### S1 — Drivetrain & Controls

Everything that converts stored energy into wheel torque, plus the user's
interface to that conversion.

Key components: motor(s), controller, torque/load sensor, speed governor,
handle-mounted controls, braking/drag mechanism.

Design brief: → `design/power-assist-spec.md`, `design/handle-and-controls-ux.md`

### S2 — Battery & Charging

Everything that stores and delivers energy, including the enclosure, contacts,
BMS, and charge-state indication.

Key components: cell pack, BMS, battery enclosure + sealing, charge port (sealed),
indicator LEDs, charger (off-board).

Design brief: → `design/battery-and-charging-spec.md`

### S3 — Structure, Wheels & Corrosion Package

The chassis, cargo bed, wheel assemblies, and all material/finish decisions that
determine whether the product survives the marine environment.

Key components: frame, axles, sealed bearings, balloon-tire wheel assemblies,
all fasteners, surface treatments, and the sealing architecture across all three
subsystems.

Design brief: → `design/corrosion-and-ingress-spec.md`

---

## Subsystem interface points

| Interface | S1 ↔ S2 | S1 ↔ S3 | S2 ↔ S3 |
|-----------|---------|---------|---------|
| **Physical** | Battery bay connector (waterproof, locking) | Motor mount to axle/frame; controller enclosure mount | Battery bay mount in frame; charge port location |
| **Electrical** | DC power rail; BMS fault signal to controller | Motor ground to frame (corrosion risk — isolate) | Charge port to BMS; indicator to exterior |
| **Sealing** | Connector IP rating must match motor IP rating | Motor cable gland to controller enclosure | Bay door / gasket spec; drain path from battery bay |

**Ground loop warning:** the motor chassis must not be used as a current return
path through the frame. Use an isolated ground run back to the battery to prevent
electrolytic corrosion at every grounded fastener.

---

## Cross-cutting constraints

These apply to all three subsystems simultaneously. A change in any sub-spec
must be checked against this table.

| Constraint | Target | Notes |
|-----------|--------|-------|
| **Gross weight** | ≤ 65 lbs fully loaded (motor + battery + frame, no cargo) | Dead-battery manual pull must be tolerable. Validate against measured baseline wagon. |
| **Drivetrain weight budget** | ≤ 20 lbs (motor + controller + wiring) | Remaining budget: frame/wheels ~30 lbs, battery ~15 lbs |
| **IP rating — minimum** | IP65 (dust-tight, water jet resistant) for motor, controller, battery bay | IP67 (submersion to 1 m) preferred for motor and battery contacts |
| **Max speed** | Brisk walking pace (~4–5 km/h / 2.5–3 mph) | Governed in firmware. Not a safety spec — a product character spec. |
| **Manual fallback** | Must be pullable by one adult without motor assist | Freewheeling motor (no drag) or torque below 2 Nm unassisted |
| **Cargo capacity** | 100 lbs minimum (angler use case) | Structural spec for frame and wheel assemblies |
| **Operating environment** | Salt air, wet sand, fresh + salt water splash, direct sun, 0–50 °C | Thermal management required for battery in direct sun |
| **Salt spray survival** | ASTM B117 / ISO 9227 salt fog, 500 hrs, no structural failure | Fasteners and motor housing are highest-risk items |

---

## Design decisions still open

These are unresolved as of the current version. Each has a blocking sub-spec
decision that must be made before the BOM can be finalized.

| Decision | Options | Where to resolve | Impact |
|----------|---------|-----------------|--------|
| Motor topology | Hub motor in driven wheel(s) vs. geared motor to axle | `power-assist-spec.md` | Wheel serviceability, motor IP packaging, torque curve |
| Single vs. dual driven wheels | Single rear vs. dual rear | `power-assist-spec.md` | Traction in soft sand, turning behavior, cost |
| Battery platform | Proprietary pack vs. power-tool ecosystem (e.g., Milwaukee M18) | `battery-and-charging-spec.md` | BMS control, waterproofing, cost, brand |
| Assist sensing method | Torque sensor on handle vs. current sensing vs. load cell in axle | `power-assist-spec.md`, `handle-and-controls-ux.md` | Control feel, complexity, cost |
| Folding vs. rigid frame | Folding (retail appeal) vs. rigid (drivetrain integration, stiffness) | `manufacturing/product-and-prototype-spec.md` | Drivetrain architecture, structural integrity |

---

## Manual-fallback design principle

The powered mode is a feature. The wagon must work without it. Failure modes
that degrade manual operation below a bare wagon are product failures:

- Motor drag when unpowered: freewheeling design required or explicit spec
- Added weight: every pound over baseline is paid twice (assist effort + dead battery)
- Control system in the pull path: handle must not require the electronics to work

---

## Version notes

This document reflects the integrated product vision (not a retrofit kit). The
v0 integration prototype will not meet all constraints here — that is expected
and intentional. The prototype answers "does powered assist solve the problem?"
This document asks "what does a shippable product need to look like?"
