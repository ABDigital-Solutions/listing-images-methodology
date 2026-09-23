# The fact base

The highest-value artifact in the pipeline and the one everybody skips. Write it before any concept
and certainly before any prompt.

**Rule: every physical claim carries a source.** A supplier spec sheet, a measurement, or a
photograph of the actual product. No source means it is a guess, and a guess must be marked as one —
never written with confidence. No model knows your pouch is 0.18 mm thick, and neither do you until
you ask.

---

## Template — `01_fact-base.md`

```markdown
# Fact base — <product>

## Identity
| | | Source |
|---|---|---|
| Product | | |
| Net weight / count | | pack artwork |
| Format | | |
| Certifications | | certificate on file |

## Pack
| Property | Value | Source |
|---|---|---|
| Material | | supplier spec |
| Structure (Verbundaufbau) | | supplier spec — ASK, do not assume |
| Total thickness | | supplier spec |
| Closure type | | photograph of the product |
| Opacity / light barrier | | supplier spec |
| Dimensions standing | | measured |
| Base | | |

## Contents — observable behaviour
| Property | Reality | How to write it | Source |
|---|---|---|---|
| Appearance dry | | | photograph |
| Behaviour in liquid | | | tested |
| Time to change | | | tested |
| Breaks / holds at | | | tested |
| Surface finish | | | photograph |
| Nearest TRUE analogy | | name it explicitly in prompts | |

## Claims
| Claim | Legally supportable? | Evidence | Where used |
|---|---|---|---|

## Unverified — do not depict until resolved
- [ ] <claim> — needs <source>
```

---

## Observable behaviour, not marketing language

The "Reality" column must contain things a camera could confirm. Compare:

| Marketing language | Observable behaviour |
|---|---|
| thick and rich | breaks within 3–5 cm; slumps under its own weight |
| premium quality | whole seeds, ~0.1 % broken by mass |
| ultra-fine | 40–60 µm; feels like flour between the fingers |
| powerful barrier | opaque; no light transmission at 5000 lux |

Adjectives map to the wrong visual cliché. **Numbers and actions constrain.** Put a number wherever
one exists — distance, height, angle, ratio, time.

### Name the nearest true analogy

The single most effective line in a prompt. *"like very thick Greek yoghurt or cold porridge"*
anchors a model far harder than three sentences of adjectives, because it points at a real referent
that behaves correctly.

Choose it carefully and check it against Gate 5 (analogy bleed) — the analogy carries **everything**
about its referent, not only the property you meant.

---

## Forbidden analogies

The visual clichés a model will reach for that are wrong for *this* material. Product-specific; this
is where most of the value sits.

Derive them by asking: *what else in the world behaves roughly like this, and which of those would
be wrong?* Then negate the wrong ones explicitly.

```markdown
## Forbidden analogies — append to the negative prompt on any <material> shot
cheese pull, melted cheese, stringy, elastic strand, long unbroken strand, honey drizzle, caramel,
syrup, glossy sauce, soft-serve ice cream, whipped cream, smooth glossy surface
```

---

## Glossary — `07_glossary.md`

Words whose dominant visual sense is not your thing. Build it as you go; each entry is a decision
made once instead of every time.

| Never write | Write instead | Why |
|---|---|---|
| zip, zipper | press-to-close seal; a rounded rib pressing into a matching groove | returns a trouser zipper |
| bag | stand-up pouch with gusseted base | returns a carrier bag |
| lens | magnifying glass with a thin metal rim | returns a camera lens |
| gel | <the material's actual state> | returns hair gel |
| grain | seed | returns wheat |

**The test:** prompt the noun alone. If it returns the wrong thing on its own, it returns the wrong
thing inside your paragraph. See Gate 4.

---

## Where ground truth comes from

In priority order:

1. **The product in your hand** — photograph it, measure it, use it. Cheapest and most reliable.
2. **The supplier spec sheet** — for anything internal to the pack. Ask for it by name; in German
   packaging the laminate structure is the *Verbundaufbau*.
3. **Lab or certificate data** — for purity, nutrition, contamination limits.
4. **Nothing else.**

Explicitly **not** ground truth:

- A competitor's listing images
- An agency's concept render
- Another AI-generated image
- Your own previous prompt

> A reference render is evidence of a **composition**. It is never evidence of how a material
> behaves. Transcribing physics out of somebody else's AI image is how the cheese failure happened.
