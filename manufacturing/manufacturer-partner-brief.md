# Manufacturer Partner Brief

> A self-contained document for potential manufacturing partners. Describes what
> we're building, what we're looking for in a partner, what we bring to the
> engagement, and how the relationship would work.
>
> Status: **Draft — for partner conversations at Stage 4+ (post-prototype validation)**
> Do not share before the demo video exists and demand has been validated.

---

## Product overview

We are developing a **powered beach wagon** — a marine-grade, electric-assist cart
designed for hauling heavy loads over soft sand. Think of it as the e-bike of
beach carts.

The product assists the person pulling it (load/torque sensing, similar to
e-bike pedal assist) rather than replacing them with a remote-controlled vehicle.
The electric system makes soft-sand hauling effortless; the manual fallback works
without power. The entire product is engineered against the most demanding beach
environment: salt water, wet and dry sand, direct sun, and repeated cycles.

**This is not a powered garden cart or lawn utility vehicle.** Those exist and are
not competitive with what we're building. The gap in the market is a product built
from the ground up for the beach environment, with the engineering and brand to match.

### Model lineup

| Model | Drive system | Target use | Stage |
|-------|-------------|-----------|-------|
| Model 1 — Wheeled | Hub motor, balloon tires | General beach hauling, surf anglers | Launch product |
| Model 2 — Tracked | Rubber-track drive | Extreme soft sand, halo product | Post-launch |

This brief focuses on Model 1.

### Key specifications (target — subject to revision)

| Parameter | Target |
|-----------|--------|
| Motor | 250–500 W BLDC, IP67 |
| Battery | 36 V, 350–500 Wh, removable, IP67 |
| Max assist speed | 4–5 km/h (governed) |
| Cargo capacity | 150 lbs |
| Gross weight (no cargo) | ≤ 65 lbs |
| IP rating — drivetrain | IP67 minimum |
| IP rating — frame/cargo area | IP54 |
| Fasteners | 316 stainless throughout |
| Frame | Marine-grade aluminum (6061 or 6063) |

Detailed engineering specs: → `design/` folder (system overview, power-assist
spec, battery spec, corrosion spec, handle/controls UX).

---

## What we're looking for in a partner

We are looking for a manufacturing partner, not a contract assembler. The right
partner has domain expertise in at least three of the following five areas, and
genuine capability (not just claimed) in all five.

### 1. Small-lot electric motor and drivetrain integration

You have experience integrating BLDC motors with controllers and battery systems
into products — not sourcing these as separate commodities and hoping they work
together. You understand motor selection for a given torque/speed curve, controller
tuning, and the failure modes of motor systems in harsh environments.

**Evidence we'll look for:** show us a product you built that integrates an electric
drive system with custom enclosures and IP protection.

### 2. IP-rated enclosure design and manufacturing

You know the difference between IP65 and IP67, how to achieve and test each, and
where seals fail in practice. You've designed gasket interfaces, cable glands, and
drain paths. You have access to salt-spray or water-ingress test capability.

**Evidence we'll look for:** show us a product you build that carries an IP65+ rating
on the motor or electronics enclosure, and how you validate it.

### 3. Marine-grade finishing

You work with 316 stainless hardware, anodized aluminum, marine-grade powdercoat,
and UV-stable plastics. You know what "marine-grade" means in practice vs. the
marketing claim. You have suppliers for these materials and a finishing line or
trusted finishing subcontractor.

**Evidence we'll look for:** show us finished goods from your line that have been
in salt-water environments and held up.

### 4. Small-batch prototyping with a path to volume production

We are at prototype stage. We need a partner who can build 5–20 units for
validation without requiring a production tooling investment upfront — and who
has a credible path from there to 500–5,000 units annually. We are not looking
for a prototype shop that has no production capability, or a volume factory that
can't be bothered with small runs.

**Evidence we'll look for:** describe your minimum prototype batch and your typical
ramp from prototype to production. What changes between the two? What tooling is
required to get to volume?

### 5. Battery pack manufacturing or a qualified battery partner

Custom Li-ion packs with BMS, IP-rated housing, and relevant certifications
(UN38.3, UL 2271 or equivalent). Either in-house or with a named, qualified
subcontractor you have a working relationship with.

**Evidence we'll look for:** show us a battery system you've integrated or
managed through certification.

---

## What we bring

We are not looking for someone to design the product for us. We bring:

- **Design intent and specs.** Detailed engineering requirements, subsystem specs,
  and material selections. We are looking for a partner to manufacture to our
  design, refine it where they have better process knowledge, and contribute
  manufacturing expertise.

- **IP.** Provisional patents (design and utility) filed before any public launch.
  We own the design; the manufacturer does not receive IP rights.

- **Demand validation.** By the time we're having this conversation, we have
  demonstrated customer interest: interview data, a waitlist, and a demo video
  showing the product working. We are not asking you to bet on an idea; we
  have a signal.

- **Brand and distribution.** We are building a brand-led, premium product.
  The product is designed for DTC and select retail; we are not racing to the
  commodity market. This matters to you because it means volume is achievable
  at a margin that supports quality manufacturing.

- **A committed engagement, not shopping.** We are evaluating 2–3 potential
  partners. The partner we choose will be our manufacturing partner for the
  product lifecycle — not a one-time sample run. We are looking for a
  relationship, not a transaction.

---

## Engagement model

We propose the following stages for the partnership:

### Stage 1 — Evaluation (4–6 weeks)

- Share full design package; factory provides a DFM (design for manufacturing)
  review and initial cost feedback
- Factory visits; Q&A on capabilities
- No commitment required; both sides evaluate fit

### Stage 2 — Engineering prototype (6–12 weeks)

- Manufacture 3–5 engineering samples to our design spec
- Joint review: what works, what doesn't, what needs to change for production
- We fund tooling and materials for this run at agreed rates

### Stage 3 — Pilot production (12–24 weeks)

- 20–50 units; first sellable inventory
- Defines production tooling requirements and lead times
- Milestone: a unit that passes our test protocol (`manufacturing/test-protocol-scorecard.md`)

### Stage 4 — Production

- Annual volume commitment discussed at end of Stage 3
- Based on demand validation from Stage 4 prototype customer feedback

---

## Questions for you (for our evaluation)

We'll ask these during a first call or factory visit. Please come prepared to discuss:

1. **IP-rated product experience:** what is the most demanding environment your
   products operate in? What IP rating have you achieved, and how do you test for it?

2. **Marine/outdoor product experience:** have you built products for salt-water,
   sun, and sand exposure? What materials and surface treatments did you use?
   What failed and what held up?

3. **Motor and electronics integration:** can you integrate a motor, controller,
   and battery system, or do you contract this out? If contracted, who is your
   partner and how do you manage quality?

4. **Minimum order quantities:**
   - Engineering samples: minimum qty and lead time?
   - Pilot production: minimum qty and lead time?
   - Volume production: minimum annual qty for your standard pricing?

5. **Tooling cost estimates:** rough estimate for tooling required to take our
   design (aluminum frame, battery enclosure, electronics housing) from prototype
   to a 500-unit/year run. We are not asking for a quote; we are asking for order-
   of-magnitude to determine fit.

6. **Certifications:** what certifications have your products achieved (UL, CE, FCC,
   etc.)? Do you support customers through the certification process or expect
   them to handle it independently?

7. **Battery:** do you manufacture battery packs in-house or use a subcontractor?
   Who, and what is your experience with UN38.3 / UL 2271?

8. **Lead times:** for a pilot run of 50 units, what is a realistic lead time from
   approved design to finished goods at port?

---

## Evaluation criteria for choosing a partner

We will evaluate candidates on the following. These are weighted, not equal.

| Criterion | Weight | Notes |
|-----------|--------|-------|
| IP-rated product track record | High | Demonstrated, not claimed |
| Marine/outdoor environment experience | High | This is a hard environment; we need experience with it |
| Motor/electronics integration capability | High | In-house preferred; qualified subcontractor acceptable |
| Prototype-to-volume ramp capability | High | Must be able to do small runs now and grow |
| Battery capability | Medium | In-house preferred; matters for quality control and IP rating |
| Certification support | Medium | We will need UL/CE; partners who have done this before save time |
| Communication and transparency | Medium | We need a partner who says "this won't work" before we commit, not after |
| Price | Lower | We are building a premium product. Cheapest is not the goal. |

---

## Next step

If this brief describes a project that fits your capabilities and interests,
we'd like to schedule a 60-minute call to discuss your experience in the areas
above. Following that, we'll invite 1–2 finalists for a factory visit.

[Contact information to be added]
