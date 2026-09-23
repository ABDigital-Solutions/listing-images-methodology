# The main image

Two things get called "the main image" and they have **opposite constraints**. Decide which one you
are making before anything else.

| | Slot 1 / Hauptbild | Hero creative |
|---|---|---|
| Where | Amazon search results, listing thumbnail | Gallery slot 2, A+ header, paid ads, social |
| Rules | Locked by marketplace policy | None beyond honesty and brand |
| Creative latitude | Almost none | Full |
| AI's contribution | Minimal — this is a retouching job | High |
| What decides success | Packshot quality, angle, crop, legibility at 250 px | Concept |

**Both should be produced. Confusing them is the most common failure in this work.**

---

## Track A · Slot 1 — the compliance-locked main image

### The rules (Amazon; verify current policy for the marketplace)

- Pure white background (RGB 255,255,255)
- Product fills **85–90 %** of the frame
- Real product only — no illustration, no rendering that misrepresents
- **No props.** Nothing in frame that is not the product
- **No text overlays, no badges, no graphics outside the packaging**
- No borders, watermarks, logos that are not on the pack
- No misleading before/after, no medical symbols
- Square, ≥1600 px on the long side, 2000 px+ to enable zoom

### What this means in practice

There is nearly no creative decision here. The variables are:

1. **Angle** — frontal, very slightly elevated three-quarter is the category default. It shows the
   full front face and the standing base together, which reads as "this is a real object with volume."
2. **Fill** — push to the top of the allowed range. Most sellers under-fill and lose thumbnail legibility.
3. **Legibility at thumbnail** — this is the whole game. Open the packshot at 250 px. Can you read the
   product name and the weight? If not, nothing else about the image matters.
4. **Shadow** — a soft contact shadow under the base only. No cast shadow, no reflection.

### Why you should not generate this

The main image must be the **actual product**. A generated pouch is a different pouch. Retouch a real
packshot instead: cut out, clean, correct the white, straighten, sharpen the label.

Generation has exactly one legitimate use here — producing a **lighting and angle reference plate**
that a retoucher matches to. Say so explicitly when you produce one, so nobody mistakes it for the
deliverable.

### Deliverable for slot 1

Not a prompt. A spec:

```
05_slot-1/
├── SPEC.md          angle, fill %, shadow, background value, output size
├── RETOUCH-BRIEF.md what to fix on the supplied packshot, in order
└── thumbnail-test/  the packshot rendered at 250 px, 400 px, 800 px
```

The thumbnail test is not optional. It is the only check that matters and it takes one minute.

### Competitor teardown for slot 1

From the competitor screenshots, tabulate: angle · fill % · shadow treatment · badge usage (many
sellers break the rules; note who) · legibility at 250 px. The pattern that emerges tells you the
category convention **and** where everyone is leaving legibility on the table.

---

## Track B · Hero creative

This is where concepting belongs. No slot-1 rules apply, so props, overlay text, badges, impossible
physics and staging are all available.

### Selection

The hero creative should carry the **single strongest buying trigger** from the gaps analysis — the
one with the highest frequency band and highest conversion impact. Not the prettiest idea. Not the
one the agency liked.

Record the evidence trail: *this concept, because trigger X at 30–40 % frequency, high impact,
market coverage low.*

### Staging vs demonstration — the distinction that keeps you honest

Overtly graphic devices may be physically impossible. Depictions of real use may not.

| | Example | Can it be impossible? |
|---|---|---|
| **Staging** | a giant translucent "10×" sculpted from gel; product floating on a podium | Yes — nobody reads it as a product demo |
| **Demonstration** | a hand lifting a spoon; the product being poured, opened, eaten | **No** — this claims to show real behaviour |

A gel "10×" is fine. A spoon test that shows behaviour the product does not have is a misleading
representation. Apply Gate 1 (Physics) only to the second kind — but apply it absolutely.

### The trap: a hero that cannot be slot 1

An agency will hand you a beautiful hero with props, a hang tag and overlay text, and everyone will
assume it is the main image. It is not eligible. Say so at handoff, in writing, before anyone gets
attached to it.

*(This exact thing happened on the Bio Chia project: the written brief specified a compliant
packshot and forbade props, badges and text overlays. The renders delivered against it had all
three.)*

---

## Product legibility — the constraint that outranks composition

If the brief says the pack must be readable, the pack has to be **large**, and everything else must
be told to get out of its way. Three clauses do the work:

- on any hanging element — **"clear of the label"**
- on any background graphic — **"without crowding or overlapping the label"**
- on any base or podium — **"no taller than the product's own base"**

Left unconstrained, all three creep inward and eat the legibility the composition exists to protect.

A concept where the product sits at a third of the frame is a *gallery* image. At a 250 px thumbnail
nobody reads a label that small.
