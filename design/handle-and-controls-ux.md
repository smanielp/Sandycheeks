# Handle & Controls UX

> Physical handle design, control placement, engagement feel, feedback, and
> the mechanical/electrical interface between the handle and the drivetrain.
>
> Cross-cutting constraints: → `design/system-overview.md`
> Assist logic and sensing: → `design/power-assist-spec.md`
> Battery indicator UX: → `design/battery-and-charging-spec.md`

---

## Design principle

The handle is the only part of the wagon the user touches. It must feel like a
premium outdoor tool — not a converted garden cart, not a prototype. The controls
must be findable without looking, operable with wet or sandy hands, and legible
at a glance.

**The handle should not require thought.** A person hauling gear down to the water
is thinking about their day, not the wagon. Control interaction should be
2 seconds or fewer, one hand, any conditions.

---

## Physical form

### Telescope and grip

- Telescoping handle, extending from the wagon frame. Extension range: suits
  both shorter and taller users without adjustment in use (typical beach wagon
  handle range: 30"–50" extended).
- Grip material: **TPR (thermoplastic rubber) overmold** on aluminum tube.
  TPR provides grip wet, doesn't heat up in direct sun the way painted metal
  does, and is resistant to salt/UV degradation. Silicone is an alternative;
  hard rubber is not acceptable (becomes slippery when wet).
- Grip diameter: 30–35 mm (standard bicycle handlebar ergonomics as reference;
  validated for one-hand pull force)
- Handle angle: slight rearward tilt so the pull force is directed toward the
  user, not straight up. Typically 10–15° from vertical in extended position.

### Handle-to-wagon connection

This connection point is where the load sensor (if used) will live. It must:
- Withstand 150 lbs of sustained pull force without flexion or play
- Provide a mechanically stable mounting surface for sensor (no movement relative
  to both the handle tube and the wagon frame)
- Be accessible for sensor replacement/calibration without disassembling the handle

**If using a load cell at this joint:** specify a shear-beam or S-type load cell
rated to 150 lbs (67 kg) minimum, IP65-rated, with overload protection. The load
cell should be the soft point in the load path — sized to flex before any
structural member fails.

---

## Control placement

### Primary control: assist on/off or mode selector

**Location:** thumb-accessible on the right grip (dominant-hand assumption),
positioned so the thumb reaches it naturally during a pull without shifting
grip. Reference: bicycle brake lever zone (~30° forward of top-dead-center on
the grip).

**Physical format:** flush-mount rocker or single large button (≥ 20 mm
diameter). Large enough to actuate with a gloved hand or sandy thumb.

**Operation:**
- Single button: short press = on/off; long press (2 sec) = mode change
  (Eco → Max → Off cycle). Simple enough to memorize without a manual.
- Alternative: two-button (power / mode), if testing reveals single-button
  confusion. Start with single-button.

### Secondary indicator: battery level and assist status

**Location:** on the handle, facing up and toward the user. Visible at a glance
during use without changing hand position.

**Format:** 4-LED bar (battery level) + 1 status LED (assist on/off and mode).
Alternatively: small OLED or e-ink display for combined readout (adds cost; defer
to v1 unless early customer feedback demands it).

**LED meanings (example):**
| LED | State | Meaning |
|-----|-------|---------|
| Status | Solid green | Assist on, Eco mode |
| Status | Solid blue | Assist on, Max mode |
| Status | Off | Assist off |
| Status | Flashing red | Fault (low battery, overheat, sensor error) |
| Battery bar | 4 lit | 75–100% |
| Battery bar | 3 lit | 50–75% |
| Battery bar | 2 lit | 25–50% |
| Battery bar | 1 lit, slow flash | < 25% |
| Battery bar | 1 lit, fast flash | < 10%, shut down imminent |

**IP rating for handle electronics:** IP65 minimum. The indicator assembly is
exposed to rain and splash. Lens must be UV-stable.

---

## Engagement feel

### Tactile click vs. soft button

Recommendation: **tactile click (momentary switch with audible/tactile feedback).**

Rationale: soft/capacitive buttons require visual or auditory confirmation of
actuation. A tactile click tells the user "it registered" without looking.
In a noisy beach environment, auditory feedback from the switch itself is more
reliable than a beep. With sandy, wet hands, capacitive buttons miss actuations.

### Latching vs. momentary

Recommendation: **soft latching via firmware, momentary physical switch.**

- The physical button is momentary (press and release; no held-down state)
- Firmware latches the assist state — press once to turn on, press again to turn off
- This avoids the need to hold a button to keep assist active (poor ergonomics
  for a sustained pull)
- Emergency stop: press-and-hold for 3 seconds cuts assist regardless of state

**Note:** A dead-man switch (assist only while holding) was considered and
rejected for normal operation — it requires constant hand-position discipline
that is incompatible with a varied pulling motion. The emergency stop hold
provides a safety out without making the normal UX a constant hold.

---

## Safety considerations

### Runaway prevention

The speed governor in the controller is the primary protection. The handle
controls are secondary — if the user releases the handle, they cannot reach
the button, but the motor is governed to walking pace regardless.

**Optional dead-man override:** if regulatory requirements or liability review
require it, add a secondary dead-man mode: a pressure sensor in the grip itself
(grip = assist on; release = motor off). This is an additive feature, not the
default — test with users first. Most beach wagon users will find it annoying.

### Overload warning

If the controller detects motor overcurrent (stalled wheel, excessive load),
the handle status LED should flash red and the motor should cut to 50% power,
not cut off entirely. Abrupt assist cutoff under load is jarring and potentially
causes the user to stumble. Ramp down, then cut if condition persists.

---

## Interface to drivetrain (mechanical + electrical)

### If using a load cell (v1 sensing)

The load cell is mounted at the handle-to-wagon joint. It outputs an analog
voltage or current signal proportional to pull force. This signal goes to the
controller via a shielded cable running inside the handle tube.

- Cable routing: inside the handle tube, exiting at the base in a cable gland
- Connector at base: waterproof 4-pin connector (power + signal + ground + shield)
  separates when handle telescopes; must be long enough to allow full extension
  without pulling on cable.
- Calibration: zero the load cell when the wagon is on level ground, no load
  applied to handle. Calibration accessible via button sequence.

### If using passive throttle (v0)

A simple thumb throttle (borrowed from e-bike supply chain, e.g., twist or
thumb-lever style) mounted on the grip. The throttle output is a 0–5V or
Hall-effect signal to the controller. No handle modification required beyond
mounting the throttle and running the cable.

**For v0 prototype:** use an off-the-shelf e-bike thumb throttle. It will feel
prototype-grade — it is. The UX validation question is whether assist is useful,
not whether the control is polished.

---

## Open decisions

- [ ] Confirm load cell vs. passive throttle for v1 (see `power-assist-spec.md`)
- [ ] Select button format: single multi-function vs. two-button; test with users
- [ ] Confirm grip material and OD with ergonomics test (wet-hand pull force)
- [ ] Confirm handle indicator format: LED bar vs. display; cost vs. UX tradeoff
- [ ] Determine cable routing and connector spec for telescoping handle (telescoping
  adds cable management complexity if controls are on the handle)
- [ ] Evaluate dead-man grip sensor as regulatory requirement vs. optional feature
