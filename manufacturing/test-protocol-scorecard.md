# Test Protocol & Scorecard

> Fillable scorecard for prototype beach testing. Use this for every test session.
> Fill one scorecard per vehicle per test session. Archive completed scorecards.
>
> The test protocol is designed to generate data comparable across sessions and
> across vehicles (our prototype vs. competitors). Results without a competitor
> baseline are anecdotes. Run the competitor baseline first.

---

## Setup — complete before each session

### Date and conditions

| Field | Value |
|-------|-------|
| Date | |
| Location (beach name, state) | |
| Time of day | |
| Weather: temperature (°F) | |
| Weather: wind speed / direction | |
| Tide state | |
| Sand condition: top-of-beach | [ ] Dry/fine [ ] Damp [ ] Wet |
| Sand condition: near water | [ ] Firm wet [ ] Soft wet |

### Test vehicle

| Field | Value |
|-------|-------|
| Vehicle name / ID | |
| Assist type | [ ] Powered prototype [ ] Competitor cart (manual) [ ] Competitor cart (powered) |
| Battery state (if powered) | % at start |
| Notes on vehicle condition | |

### Standard load

- **Standard test load: 100 lbs.** Use dead weight (sandbags, plate weights) for
  repeatability. Do not use loose gear that shifts.
- Record actual load weight if different from 100 lbs.

| Field | Value |
|-------|-------|
| Actual load weight (lbs) | |
| Load type | [ ] Sandbags [ ] Plate weights [ ] Gear (describe): |

### Course setup

Define and mark the course before running any vehicle. Use stakes or flags so
the same course can be reproduced in future sessions.

| Segment | Description | Distance (measured) |
|---------|-------------|-------------------|
| A — Dry sand flat | Top-of-beach, finest/driest sand, flat | meters |
| B — Dry sand slope | Top-of-beach on a grade (find a natural dune slope) | meters, ___° grade |
| C — Transition zone | From dry to wet sand | meters |
| D — Wet sand | Near water, firm sand | meters |
| **Total course** | A + B + C + D | meters |

**Photograph or video the course setup at the start of the session.** A photo
of the stakes from the start line is enough.

---

## Run 1 — Pull effort test (subjective + measured)

Run the vehicle through the full course. Stop and record at each segment.

### Effort — subjective (1–10 scale)

1 = effortless; 5 = noticeable work; 7 = hard; 9 = near-maximum; 10 = impossible

| Segment | Effort rating (1–10) | Notes on where it bogged, felt difficult, or was easier than expected |
|---------|---------------------|-----------------------------------------------------------------------|
| A — Dry sand flat | | |
| B — Dry sand slope | | |
| C — Transition | | |
| D — Wet sand | | |
| **Overall session** | | |

### Effort — measured (if force gauge available)

Attach a digital fish scale or force gauge to the handle. Record peak and average
pull force during each segment.

| Segment | Peak force (lbs) | Average force (lbs) |
|---------|-----------------|-------------------|
| A — Dry sand flat | | |
| B — Dry sand slope | | |
| C — Transition | | |
| D — Wet sand | | |

### Timing

| Segment | Time (mm:ss) | Assist status |
|---------|-------------|--------------|
| A — Dry sand flat | | [ ] On [ ] Off [ ] N/A |
| B — Dry sand slope | | [ ] On [ ] Off [ ] N/A |
| C — Transition | | [ ] On [ ] Off [ ] N/A |
| D — Wet sand | | [ ] On [ ] Off [ ] N/A |
| **Total** | | |

---

## Run 2 — Battery range and power draw (powered vehicles only)

Skip this section for manual competitors.

| Measurement | Value |
|-------------|-------|
| Battery % at start of run | |
| Battery % at end of full course | |
| Wh consumed (if controller has readout) | |
| Extrapolated range at this rate (km / course laps) | |
| Motor temperature at end of run (if measurable) | |
| Controller temperature at end of run (if measurable) | |

**Full-day range estimate:** multiply single-run Wh draw by estimated number of
hauls per day (ask customers; assume 6–10 for heavy angler use). Compare to pack
capacity.

---

## Run 3 — Downhill behavior (slope segment B, returning)

Pull the loaded vehicle back up the slope — then release and observe behavior
on the way down the slope with 100 lb load.

| Observation | Result |
|-------------|--------|
| Does the wagon free-roll on slope B? | [ ] Yes, accelerates [ ] Slight roll [ ] No roll |
| Max speed observed on free-roll | approx. mph |
| Regen braking active? | [ ] Yes, held speed [ ] No regen [ ] N/A |
| Mechanical drag effective? | [ ] Yes [ ] No [ ] N/A |
| Safety concern observed? | [ ] Yes (describe) [ ] No |

---

## Failure mode log

Record every failure, anomaly, or concern observed during the session.

| # | Failure / Observation | Segment | Severity | Root cause hypothesis |
|---|----------------------|---------|----------|-----------------------|
| 1 | | | [ ] Critical [ ] Significant [ ] Minor | |
| 2 | | | [ ] Critical [ ] Significant [ ] Minor | |
| 3 | | | [ ] Critical [ ] Significant [ ] Minor | |
| 4 | | | [ ] Critical [ ] Significant [ ] Minor | |

**Common failure modes to watch for:**
- Wheel digging in / traction loss (which wheel, which segment)
- Motor overheat or controller fault
- BMS trip / power cutout
- Sand ingress into any assembly
- Fastener loosening or loss
- Handle control failure
- Bearing noise (grinding, rough rolling)
- Assist engagement / disengagement not responding as expected

---

## Competitor comparison baseline

Run at least one manual competitor cart through the same course with the same
load before running the powered prototype. This gives the "before" number.

### Competitor 1

| Field | Value |
|-------|-------|
| Cart name / model | |
| Wheel diameter / tire type | |
| Empty weight (lbs) | |
| Effort — Segment A (1–10) | |
| Effort — Segment B (1–10) | |
| Effort — Segment C (1–10) | |
| Effort — Segment D (1–10) | |
| Peak force — Segment A (lbs) | |
| Peak force — Segment B (lbs) | |
| Total time — full course | |
| Notable failure points | |

### Competitor 2 (if tested)

*(copy Competitor 1 table)*

### Powered prototype comparison

| Metric | Competitor 1 | Competitor 2 | **Our prototype** | Delta vs. best competitor |
|--------|-------------|-------------|------------------|--------------------------|
| Effort A (1–10) | | | | |
| Effort B (1–10) | | | | |
| Effort C (1–10) | | | | |
| Peak force A (lbs) | | | | |
| Peak force B (lbs) | | | | |
| Total time | | | | |
| "Would pay for this" (observer rating, 1–10) | N/A | N/A | | |

---

## Pass/fail gates

Use these to decide whether to advance to the next prototype stage.

### Gate: advance from v0 to v1 design

| Criterion | Target | Result | Pass / Fail |
|-----------|--------|--------|-------------|
| Effort reduction vs. best competitor, Segment A | ≥ 50% reduction in reported effort | | |
| Effort reduction vs. best competitor, Segment B | ≥ 50% reduction in reported effort | | |
| Motor sustained Segment A + B without fault | 2 consecutive laps without overheat or BMS trip | | |
| Downhill behavior | No uncontrolled acceleration on Segment B | | |
| Demo video quality | Footage usable for a customer-facing video | [ ] Yes [ ] No | |
| Observer reaction | At least 1 observer unprompted says "I'd buy that" | [ ] Yes [ ] No | |

### Gate: advance from v1 prototype to pilot production

| Criterion | Target | Result | Pass / Fail |
|-----------|--------|--------|-------------|
| Full-day range | ≥ 10 hauls on a single charge (Segment A+B+C+D each) | | |
| Corrosion after 5 sessions, rinsed | No rust on fasteners; no bearing roughness | | |
| Corrosion after 5 sessions, NOT rinsed | No structural corrosion; electrical function intact | | |
| Manual fallback effort | ≤ 130% of best manual competitor | | |
| Customer feedback (5 target users, in-person demo) | ≥ 4/5 rate "would pay $800+" | | |

---

## Post-session notes

| Field | Notes |
|-------|-------|
| Tester name(s) | |
| Most important finding | |
| Biggest open question going into next session | |
| Changes to make before next test | |
| Ready to film the demo video? | [ ] Yes [ ] No — needs: |
