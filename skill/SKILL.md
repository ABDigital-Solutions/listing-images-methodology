---
name: listing-images
description: "When the user wants to create, plan, or fix e-commerce product listing images — Amazon main image, gallery images, A+ module visuals — from a product plus its competitors. Also use when the user mentions 'listing images,' 'main image,' 'hero image,' 'Hauptbild,' 'gallery images,' 'Bildstrecke,' 'product images for Amazon,' 'A+ content images,' 'reverse engineer competitors,' 'competitor listing teardown,' 'image concepts from market data,' 'prompts for Higgsfield,' 'prompts for Seedream,' 'prompts for Nano Banana,' 'AI product photography,' 'my generated image looks fake,' 'the AI got my packaging wrong,' or 'why does my product image look wrong.' Use this whenever someone is turning market research into product imagery, or debugging an image prompt that produced something false. For ad creative copy, see ad-creative. For brand voice and visual identity, see brand."
metadata:
  version: 1.0.0
---

# Listing Images

You turn a product and its competitors into listing imagery that is **true, on-brand, compliant, and actually generatable**.

The analysis half of this job is easy and LLMs do it well. The hard half is downstream: turning a
concept into a prompt that yields a truthful image containing the *real* product. Most of this skill
is about that second half, because that is where the work fails.

## The governing rule

> **Describe the thing, not the argument for the thing.**

Prompt-writing is a persuasion task, so the default reasoning mode is rhetorical. Physical truth is a
separate mode and it does not happen unless you force it as its own pass. Every failure this skill
guards against is a variant of this one error.

---

## Before you start

Gather (ask only for what is missing):

1. **The product** — packshot (front, high-res, white or transparent), print artwork, spec sheet,
   the claims you are legally allowed to make, certifications
2. **The competitors** — listing text and bullets, main-image screenshots, gallery screenshots,
   review exports. The user supplies these; do not scrape.
3. **The marketplace and locale** — Amazon DE, US, etc. Compliance rules differ.
4. **Brand assets** — colours, type, logo. Check for `docs/brand-guidelines.md` and
   `assets/design-tokens.css` in the repo before asking.

If a product fact base already exists from a previous run, read it instead of re-deriving it.

---

## Pipeline

Run these in order. Do not skip stage 1 — every later stage depends on it.

### Stage 1 · Fact base
**→ load `references/fact-base.md`**

Write down what is physically true about the product, **with a source for every claim**. Materials,
behaviour, dimensions, what it does when handled. This is the single highest-value artifact in the
whole pipeline and the one people skip.

Also build, in the same file:
- **Forbidden analogies** — the visual clichés a model will reach for that are wrong for this material
- **Glossary** — words whose dominant visual sense is wrong for this product

Output: `01_fact-base.md`, `07_glossary.md`

### Stage 2 · Competitor teardown
**→ load `references/competitor-teardown.md`**

Reverse-engineer what the market is doing: main-image conventions, gallery patterns, wording
patterns, what everyone claims and how. The goal is to find the **unoccupied territory**, not to
copy the leader.

Output: `02_teardown.md`

### Stage 3 · Gaps and triggers
Score the market by opportunity, using the competitor set and the review data:

- **Triggers** — what buyers actually respond to, with a frequency band and a conversion-impact rating
- **Gaps** — what the market underserves, scored /10 for opportunity, each with evidence

The gaps table drives image selection. Nothing else does.

Output: `03_gaps.md`

### Stage 4 · Concept selection
**→ load `references/main-image.md`**

Two separate tracks, because they have opposite constraints:

- **Slot 1 / main image** — compliance-locked. Almost no creative decision. Produce a packshot spec
  and a retouch brief, not a concept.
- **Slots 2–7 and off-Amazon hero** — free. One image per top-scoring gap, in funnel order.

**Record the rationale for every slot.** Which gap, which trigger, which score. This is the step
that agencies skip and it is why nobody can later explain why an image exists.

Then triage each slot before writing any prompt:

| Bucket | Action |
|---|---|
| Photographable, and you own the product | **Photograph it.** Do not generate. |
| Needs cast, location or is physically impossible | Generate |
| Real but invisible at human scale | **Diagram it.** Drawn, never generated. |

Ask *"could a camera just take this?"* for every slot. It is usually yes for at least two of them,
and generating those wastes money and produces worse images.

Output: `04_concepts.md`

### Stage 5 · Prompt craft
**→ load `references/prompt-craft.md`**

Write two prompt forms per generated image:
- **Reference mode** (short) — used when the real packshot is attached. This is the default.
- **Text-to-image** (long) — concept exploration only, will never contain the real product.

Plus per-image negatives, model choice and settings.

Output: one `PROMPTS.md` per image slot

### Stage 6 · Verification gates
**→ load `references/verification-gates.md` — MANDATORY**

Seven gates. A prompt is not finished until all seven pass. Each has a mechanical test.

1. **Physics** — does the material actually do this?
2. **Magnitude** — is there a ceiling on every comparison?
3. **Observability** — could a camera see this at all?
4. **Polysemy** — what does each noun return on its own?
5. **Analogy** — does any analogy transfer more than intended?
6. **Verb state** — do the verbs imply an action you did not intend?
7. **Reference competition** — does the prompt describe what the reference already carries?

Then run the compliance check → **load `references/compliance.md`**

Output: `08_verification.md` — gate results per prompt

### Stage 7 · Generate, then verify the output
Generate. Then feed the result back with the fact base as a yes/no checklist:

> *Does any strand exceed 5 cm unbroken? Are individual seeds visible as discrete beads? Is the
> product's own label legible and unaltered?*

Failures re-roll with the violated constraint escalated — **by substitution, not by adding words.**
See the reference-competition gate for why that distinction matters.

---

## Project scaffold

Create this per product:

```
<product>/
├── 00_input/
│   ├── product/          packshot, artwork, spec sheet, claims, certificates
│   └── competitors/      listing text, screenshots, review exports
├── 01_fact-base.md       product truth, every claim sourced
├── 02_teardown.md        competitor main-image + gallery + wording patterns
├── 03_gaps.md            triggers (frequency) + gaps (opportunity score)
├── 04_concepts.md        slot → concept → evidence trail
├── 05_slot-1/            main image spec + retouch brief
├── 06_slots/             one folder per gallery image, PROMPTS.md in each
├── 07_glossary.md        polysemy fixes + forbidden analogies
└── 08_verification.md    gate results
```

---

## Hard rules

- **Never let the model render body copy in a non-English language.** Umlauts, ß and long compounds
  break in every model. Generate clean plates; set type in Figma. Short headline text in a strong
  model is worth *trying*, but verify character by character before it ships.
- **A text prompt cannot produce the user's packaging.** Ever. It is definitional, not a quality
  issue. The real pack arrives by reference image or by compositing — never by better wording.
- **Every physical claim needs a source.** Supplier spec sheet, measurement, or a photograph of the
  actual product. No source means it is a guess and must be marked as one.
- **A reference render is evidence of a composition, never of how a material behaves.** Do not
  transcribe physics out of somebody else's AI image.
- **Fix by substitution, not accumulation.** Correction rounds naturally add words, and added words
  push the reference image out of the result. After any fix, delete what the reference already shows.

## Working reference

`4. Design/Brandbook/Higgsfield - Bio Chia 500g/` is a completed run of this pipeline, including the
failure post-mortems in `04_MATERIAL-WAHRHEIT.md`. Read it when you need a worked example.
