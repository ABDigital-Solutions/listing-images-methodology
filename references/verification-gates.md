# Verification gates

Seven failure classes. Every one was found in a real project, in prompts written by a competent
model that believed they were fine. Each has a mechanical test — run all seven before any prompt is
considered finished.

They share one root cause: **the prompt described the argument for the thing instead of the thing.**

---

## Gate 1 · Physics

**Failure:** the prompt describes behaviour the material does not have.

**Real case.** *"A thick continuous viscous column of seeded gel stretches from the pudding surface
to the spoon without breaking, glossy and heavy."* Chia is a weak suspension of discrete beads; it
breaks within 3–5 cm and slumps. The only materials that stretch unbroken and glossy are cheese,
honey and caramel — so the model produced something that looked like melted mozzarella.

**Test:** for every material in the prompt, name its actual behaviour and its bound. If you cannot,
you do not know it, and you must look it up rather than write confidently.

**Fix:** describe observable behaviour with numbers. Name the nearest *true* analogy explicitly —
it anchors the model far harder than adjectives do.

---

## Gate 2 · Magnitude

**Failure:** a comparison with no ceiling. The model optimises monotonically and produces caricature.

**Real case.** *"visibly inferior material"* plus *"the contrast must be immediately obvious at
thumbnail size"* produced not a competitor's product but birdseed — woody stalks, debris. The same
prompt overclaimed the good side: *"not a single fragment or foreign particle"*, on a product sold
as 99.9 % pure.

**Test:** grep for intensifiers.

```
obvious, immediately obvious, dramatic, striking, stark, extreme, perfect, flawless, pristine,
immaculate, spotless, not a single, zero, completely free of, vastly, far superior, visibly inferior,
must be clear at a glance, maximum contrast, exaggerate
```

**Fix:** delete them, then add a **ceiling sentence** stating where the difference should stop.
Quantify both sides. And say what the good side is *not* — *"still a natural product with slight
variation, not artificially perfect"* — or you get a CGI pattern that reads as fake.

> Overclaiming your own product is the same bug wearing a friendlier face. `immaculate` and
> `not a single` were both on the *good* side.

---

## Gate 3 · Observability

**Failure:** the prompt asks a camera to photograph something invisible.

**Real case.** *"a clean cut edge, the layers fanned slightly apart like pages so the kraft outer,
the barrier foil and the inner film are individually readable."* A laminate is bonded, not stacked,
and the whole structure is ~0.15–0.2 mm — two sheets of copy paper for all layers combined. At any
plausible magnification the edge is a line.

**Test:** at what magnification would a camera see this? If the answer needs a microscope, it is not
a photograph.

**Fix:** triage into three buckets.

| Bucket | Action |
|---|---|
| Photographable | Generate it — or better, actually photograph it |
| Real but invisible at human scale | **Diagram it.** Drawn, never generated. A labelled cross-section is honest *because* it is obviously a schematic |
| Not real | Do not depict it |

---

## Gate 4 · Polysemy

**Failure:** a word whose dominant visual sense is not your thing.

**Real case.** *"zip closure", "zip track", "the two interlocking plastic ridges"* — the word *zip*
appeared four times and returned a trouser zipper with metal teeth and a slider. The adjectives were
trying to steer a noun that had already decided what it was.

**For image models, nouns dominate the clauses modifying them.** You cannot fix a wrong noun with
adjectives.

**Test:** prompt the noun **alone**. If "zip" by itself returns trousers, it returns trousers inside
your paragraph too. Surrounding context is much weaker than it feels while writing.

**Fix:** replace the noun with geometry, and negate the wrong sense explicitly.

> *"a continuous double plastic rail: one rounded rib on the front panel pressing into a matching
> groove on the back. No metal teeth, no slider, no pull tab."*

Log every decision in the product glossary so it is made once, not every time.

---

## Gate 5 · Analogy bleed

**Failure:** an analogy transfers more attributes than intended.

**Real case.** *"the same kind of press-to-close seal found on a food storage bag."* The analogy was
meant to carry the *mechanism*. It also carried the *material* — a food storage bag is transparent,
so the kraft pouch came back as clear plastic.

**Test:** for every "like a…" / "the same kind as…", list what else that referent implies. Colour,
material, transparency, scale, context.

**Fix:** fence it — *"the seal mechanism only; the pouch itself is opaque kraft paper"* — or drop the
analogy and describe the geometry. Fencing is safer.

---

## Gate 6 · Verb state

**Failure:** the verb implies an action, and the action implies damage or a state you did not want.

**Real case.** *"gently pull apart"* and *"peeled it open"* returned a torn, broken package edge.
Peel and pull-apart are destructive verbs — in training data they describe tearing packaging open.

**Test:** list every verb. Does it describe a **state** or an **action**? Does that action have a
destructive reading?

**Fix:** describe the state, not the action that produced it. *"The pouch is standing open"* instead
of *"hands pull it open."* Add explicit intactness where damage is plausible: *"the edge clean and
straight, the pouch completely undamaged."*

Watch for: `pull, peel, tear, rip, force, break, split, crush, squeeze`

---

## Gate 7 · Reference competition

**Failure:** the prompt describes the product that the attached reference image already shows. The
description and the reference compete, and the description usually wins.

**Real case.** Across three correction rounds a prompt grew from ~130 to ~250 words, and the share
describing a generic kraft pouch went from ~15 words to ~110. The user's real packshot — which had
been appearing fine — vanished from the output. Each "more precise" fix pushed it further out.

**In reference mode, every sentence describing the object competes with the reference.** Describing
it more is not reinforcement. It is a rival instruction.

**Test:** with a reference attached, delete every sentence describing the product's own material,
colour, texture, typography or construction. If the prompt still makes sense, those sentences were
competition.

**Fix:** in reference mode the prompt describes only what the reference *cannot* carry — the action,
the framing, the lighting, the background, the context. Nothing else.

> **The correction trap.** Debugging only ever adds words, so iterative correction systematically
> erodes reference fidelity. After every fix, re-read and delete what the reference already shows.
> **Fix by substitution, not accumulation.**

---

## Running the gates

Record the result per prompt in `08_verification.md`:

| Gate | Pass | Note |
|---|---|---|
| 1 Physics | ✓ | gel bound stated: breaks 3–5 cm |
| 2 Magnitude | ✓ | ceiling sentence present |
| 3 Observability | ✓ | photographable at 100 mm macro |
| 4 Polysemy | ✓ | "zip" → rail geometry; logged in glossary |
| 5 Analogy | ✓ | no analogies used |
| 6 Verb state | ✓ | state-described, intactness explicit |
| 7 Reference competition | ✓ | 0 sentences describing the pack |

A failed gate is not a warning. It is a blocked prompt.

## Output verification

After generating, feed the image back with the fact base as a yes/no checklist. Failures re-roll with
the violated constraint escalated — by substitution. This is the gate that stops a pipeline shipping
a hundred wrong images at scale.
