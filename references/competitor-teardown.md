# Competitor teardown

The reverse-engineering stage. The goal is **not** to copy the leader — it is to find the territory
nobody occupies, because that is where the conversion upside is.

Input arrives from the user in `00_input/competitors/`: listing text, bullets, main-image and gallery
screenshots, review exports. Do not scrape.

---

## 1 · Main-image teardown

One row per competitor. This table tells you the category convention and, more usefully, where
everyone is leaving legibility on the table.

| Competitor | Angle | Fill % | Shadow | Badges outside pack? | Legible at 250 px? |
|---|---|---|---|---|---|

Read out of it:

- **The convention** — what most of the category does. Deviating from it costs recognisability, so
  deviate only with a reason.
- **The under-fill** — most sellers sit well below the allowed 85–90 %. If the category average is
  60 %, filling the frame properly is free differentiation.
- **The rule-breakers** — note who ships badges and overlay text on slot 1. It is common and it is
  against policy. Do not copy it because "they do it."

## 2 · Gallery teardown

| Competitor | # images | Slots used for | Overlay text? | Lifestyle vs studio | Missing |
|---|---|---|---|---|---|

The **Missing** column is the output that matters. A slot every competitor skips is either a genuine
opportunity or a bad idea everyone already tested — the gap scoring in stage 3 decides which.

## 3 · Wording patterns

Per market leader, capture 3–5 **verbatim** listing phrases, then name the pattern.

Then write the observation that drives everything downstream: **what is the market saturated with,
and what is underrepresented?**

That paragraph is the selection rule for the whole image set. Every gallery image should sit on the
underrepresented list. If a concept does not, cut it — however good it looks.

---

## 4 · Triggers

From the review data. Frequency is an estimate from the sample; say so.

| Trigger | Frequency band | Example phrasing (verbatim) | Conversion impact |
|---|---|---|---|

Include **negative triggers** — the fears that stop a purchase. They are often the strongest images
in the set, because addressing a fear directly is territory competitors avoid.

## 5 · Gaps

| Gap | Market coverage | Opportunity /10 | Evidence |
|---|---|---:|---|

Score on: how badly the market covers it × how much buyers care × how visually demonstrable it is.
The third factor is the one people forget — a 9/10 buying concern that cannot be photographed is not
an image opportunity, it is a bullet point.

---

## 6 · From gaps to slots

Mechanical, and **write the rationale down**:

1. Sort gaps by opportunity score
2. Every 8/10 and above gets an image slot
3. Order by funnel stage: awareness → consideration → decision
4. Anything 7/10 or below goes to A+ modules, not the gallery
5. Cross-check against the triggers — a high-scoring gap with no matching trigger is a hypothesis, not a finding

Record it as an evidence trail:

```markdown
### Slot 3 — <concept>
**Gap:** <name> — 9/10
**Trigger:** <name> — 30–40 %, high impact
**Funnel:** consideration
**Why this and not the alternative:** <one line>
**Triage:** photograph / generate / diagram
```

> The rationale is the step agencies skip. Without it, nobody can later explain why an image exists,
> and the visual team quietly substitutes its own ideas between the strategy document and the
> renders. On the Bio Chia project two concepts were dropped and two invented in that gap, and none
> of it was written down.
