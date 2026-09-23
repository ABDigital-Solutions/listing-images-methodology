# Prompt craft

## The two modes

Every generated image needs **two** prompt forms, and confusing them is the fastest way to lose the
real product from your output.

| | Reference mode | Text-to-image |
|---|---|---|
| When | The real packshot is attached — **the default** | Concept exploration only |
| Length | Short. 80–150 words | Long. 150–300 words |
| Describes | Action, framing, lighting, background | Everything, including the product |
| Contains the real product | Yes | **Never** |

### Reference mode is short on purpose

**Every sentence describing the object competes with the reference image.** Describing it in more
detail is not reinforcement — it is a rival instruction, and it usually wins.

Delete from a reference-mode prompt: material, colour, texture, construction, typography, finish,
proportions. The reference carries all of it. Keep only what it cannot: what is happening, how it is
framed, where the light is, what is behind it.

Open with a possession clause so the model knows the reference is the subject:

> *"Using the pouch from the reference image, unchanged in material, colour, texture and finish: …"*

### Match the reference framing to the target framing

A full-length packshot is a poor reference for an extreme close-up — you are asking the model to
invent most of the frame from a thin strip of pixels. Crop the reference to approximately the
intended framing before attaching it.

---

## Prompt structure

Order matters. Models weight the opening more heavily.

1. **Subject** — what the picture is
2. **Action / state** — what is happening
3. **Composition** — framing, angle, what is sharp
4. **Light and background**
5. **Style block** — camera, finish, palette
6. **Constraint sentence** — what must be true, phrased positively

The style block goes **last** and stays identical across the whole set. That, plus a locked seed, is
what makes a set of images read as one campaign rather than seven stock photos.

---

## Negative prompts

**Not every model has a negative field.** Gemini-family and other instruction-following models do
not. Seedream and Flux-lineage models do.

> **Never paste a negative list into a prompt box that has no negative field.** Naming things summons
> them. Write `mould, dirt, insects, pills` into an instruction-following model and you have a fair
> chance of getting mould, dirt, insects and pills.

Where there is no negative field, convert exclusions into positive constraints:

> *"The only text in the image is the product's own label."*
> *"The pouch is completely undamaged — the edge clean and straight."*

### Base negative

```
watermark, captions, subtitles, badges, stickers, price tags, arrows, callouts, infographic elements,
UI, borders, frames, extra fingers, deformed hands, malformed fingers, plastic skin, waxy skin,
uncanny face, distorted face, blurry, low resolution, jpeg artifacts, oversaturated, HDR, harsh
flash, hard shadows, dark moody lighting, teal-orange grade, clutter, busy background, messy props,
medical symbols, pills, before-after comparison, fake certification seals, cartoon, illustration,
cgi plastic, video game, anime
```

Add `text, letters, words, typography, logo, brand name, label text` **except** where the image needs
legible text — a readable label, or numerals that are the subject. Banning text on an image whose
hero is a giant "10×" deletes the subject.

Then append the product's **forbidden analogies** from the fact base.

---

## Text in images

No model reliably renders German, and umlauts, ß and long compounds are where it breaks. Default:
**generate clean plates, set type in Figma.**

Strong current models can manage a short headline. If you try it:

- Give the exact string and instruct character-level fidelity
- Name the specific characters at risk — umlauts, ß, the decimal comma (models default to `.`)
- **Verify letter by letter before it ships.** A misspelled word on a listing image is worse than no
  headline at all
- Do not retouch a mis-rendered word. Regenerate clean and set the type properly

---

## Model selection

Match the model to the constraint, not to a general preference.

| Constraint | Choose |
|---|---|
| The real product must be legible | The best **reference-fidelity** model available |
| Photoreal humans | The model tuned for people and skin |
| Macro texture, clean product | The sharpest product model, native 2K+ |
| Short text rendered in-image | The strongest text model — then verify |

Model names change fast. Pick by capability, and settle ties empirically rather than by reputation:

> **The 20-minute test.** Same trivial prompt — *"this exact product on a pale oak table, soft window
> light from the left"* — through two or three candidates with the same reference. One variable: does
> the label survive. Zoom in on the brand name. Whichever model keeps it legible is your product
> model; whichever loses it tells you which images must be composited instead.

Settings to record with every prompt: model · aspect ratio · resolution · edit-vs-generate mode ·
batch size · seed.

---

## Getting the real product into the image

Three routes. None of them is "a better prompt."

| Route | Best for | Quality |
|---|---|---|
| **Photograph it** | Anything you own and can shoot — macro, texture, packaging detail | Perfect |
| **Composite** | Product sits at a distance in a scene | Perfect, brand-exact |
| **Reference generation** | Product is front-on and large in frame | Good; verify the label |

Ask **"could a camera just take this?"** before generating anything. On a typical seven-image set at
least two slots are ordinary photographs that got sent to an image model out of habit — and came
back worse, after several rounds of correction.

---

## Iterating without losing the product

Correction rounds only ever add words, and added words push the reference out. After every fix:

1. Re-read the whole prompt
2. Delete anything the reference already shows
3. Check the word count has not grown

**Fix by substitution, not accumulation.** If a prompt has grown by half since the first version,
that is a bug regardless of what the last generation looked like.
