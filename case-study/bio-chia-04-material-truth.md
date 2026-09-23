# MATERIAL TRUTH — chia gel is not cheese
*Read before writing any prompt that shows the product being used.*

---

## What happened

The first version of the Bild 2 prompt said:

> *"a thick continuous viscous column of seeded gel stretches from the pudding surface to the spoon
> **without breaking**, glossy and heavy"*

That is a description of **mozzarella**. The model rendered exactly that — because cheese, honey and
caramel are the only materials in its training data that form long unbroken glossy strands. The
output looked like a pizza.

**Where the error came from:** the physics was copied out of *Converts' own render*, which has the
same stretched column, instead of out of the product. A reference image is evidence of a
**composition**. It is never evidence of how a material behaves.

---

## The rule

Anything depicting **real use** must match real behaviour.

Overt graphic devices are exempt — nobody looks at a giant translucent "10x" and concludes their chia
will form numerals. The gel podium and the floating helix in Bild 1 are **staging**; the spoon in
Bild 2 is a **demonstration**. Only the second kind can lie.

---

## Fact sheet — chia pudding, observable behaviour

| Property | Reality | What to write in the prompt |
|---|---|---|
| Breaks at | 3–5 cm | "spoon held three or four centimetres above the surface" |
| Falls as | short lumpy ribbons | "already broken away, slumping under its own weight" |
| Surface | granular, discrete beads | "every seed a visible bead, never smooth" |
| Finish | satin | "satin, not glossy" |
| On a spoon | holds a mound, sags at the edge | "heaped, holds its own shape, sags slowly" |
| Nearest true analogy | thick Greek yoghurt, cold porridge | name it explicitly — it anchors the model |
| Sets in | 10 min at 1 : 3 | — |

---

## Forbidden analogies

Append to the negative prompt on **any** shot involving the gel:

```
cheese pull, melted cheese, stretched cheese, stringy, elastic strand, long unbroken strand,
honey drizzle, caramel, syrup, glossy sauce, soft-serve ice cream, whipped cream,
smooth glossy surface
```

This list is product-specific. A different material needs a different list — that is where most of
the value sits.

---

## If you automate this

You cannot fix this with better prompt-writing technique. The model has no idea what the product is;
it pattern-matches adjectives to the nearest cliché. The fix lives **upstream of the prompt**.

1. **Behaviour, not adjectives.** "Thick", "rich", "luxurious" are marketing words and they map to the
   wrong visual. Constraints are things a camera could verify.
2. **Put a number wherever one exists.** Distance, height, angle, ratio. *"Lifts a spoon"* is
   unbounded; *"three centimetres above the surface"* is not.
3. **Keep a per-product forbidden-analogy list**, auto-appended to the negative prompt.
4. **Add a verification pass.** Feed the output back to a vision model with this fact sheet as a
   yes/no checklist — *"does any strand exceed 5 cm unbroken? are individual seeds visible as discrete
   beads? is the surface satin or glossy?"* Failures re-roll with the violated constraint escalated.
   This is the gate that stops a pipeline shipping a hundred cheese images.
5. **Ground truth comes from the product** — from handling it, or from photographs of it. Never from
   another AI image.

---

## Why this is not pedantry

A listing image showing behaviour the product does not have is a **misleading representation**, and it
feeds the negative trigger already sitting in the VOC data — *"Angst vor schlechter Charge."*
A customer who buys off a cheese-stretch image and opens grainy pudding writes the review that costs
the next ten sales.

---

## The observability gate

*Run this before finalising any prompt.*

Three failures in this set, same shape every time: the prompt described **the argument for the thing**
instead of **the thing**. Prompt-writing is a persuasion task, so the default reasoning mode is
rhetorical — physical truth is a separate mode and it does not happen unless it is forced as its own
pass.

| Image | What the prompt said | Reality |
|---|---|---|
| Bild 2 | gel stretches to the spoon unbroken | breaks at 3–5 cm |
| Bild 4 | visibly inferior, debris-filled seed | slightly more broken seed and dust |
| Bild 6 | laminate layers fanned apart like pages | bonded, ~0.2 mm, invisible to a camera |

### The tell — purpose clauses

Every one of those three carried a **purpose clause**: a phrase stating the effect the image should
achieve.

- **B2** — *"clearly showing how it binds"*
- **B4** — *"the contrast must be immediately obvious at thumbnail size"*
- **B6** — *"so the kraft outer, the barrier foil and the inner film are individually readable"*

A purpose clause tells the model to hit an outcome. Physics was never named as a constraint, so it
bends physics to get there. This is greppable — scan every prompt for:

```
so that, so the, clearly showing, in order to, must be obvious, must be visible, readable,
at a glance, to demonstrate, the point of the picture
```

Each hit is a place where you asked for an **effect** instead of describing a **scene**. Replace with
a description plus a bound. This single check would have caught all three failures.

### Triage before you write a word

1. **Photographable** at a plausible magnification → generate it.
2. **Real but invisible at human scale** — laminate layers, purity fractions, nutrient content →
   **diagram it.** Drawn in Figma, never generated. A labelled cross-section is honest precisely
   because it is obviously a schematic.
3. **Not real** → do not depict it.

The Bild 6 error was putting a bucket-2 subject through a bucket-1 process. The laminate was always a
diagram; the prompt tried to photograph it.

### Who supplies ground truth

No model knows this pouch is 0.18 mm — and neither did the prompt that asserted a laminate structure
nobody had verified. **Any prompt asserting a physical property must trace to a source:** a supplier
spec sheet, a measurement, or a photograph of the actual product. If it does not, it is a guess and
must be marked as one, never written with confidence. Get the *Verbundaufbau* from the packaging
supplier before anything depicts the layers.

---

*Related: [`01_STYLE-DNA.md`](01_STYLE-DNA.md) · [`Bild-2_Gel-Beweis_Loeffeltest/PROMPTS.md`](Bild-2_Gel-Beweis_Loeffeltest/PROMPTS.md)*
