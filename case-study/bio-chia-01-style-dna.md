# STYLE DNA — Naturacereal Bio Chia Samen 500 g
*The reusable building blocks. Every image prompt in this folder inherits from here.*

---

## 1. The STYLE BLOCK (paste at the end of every prompt)

> Shot on a Phase One with a 100mm macro lens, f/5.6. High-end German commercial food photography.
> Soft diffused north-window daylight from the left, gentle shadow falloff, subtle warm bounce fill
> from the right, no harsh specular hotspots. Warm off-white (#FAFAF7) seamless background,
> natural oak and matte bone-ceramic surfaces. Colour palette limited to bone white, kraft beige,
> warm oak, charcoal-grey chia speckle and a single fresh leaf-green accent (#7BB332).
> Clean, uncluttered, generous negative space, editorial Scandinavian styling.
> Photorealistic, ultra-sharp seed texture, realistic subsurface scattering in the gel,
> 8k, natural colour science, no colour cast.

**Short version** (when you need to save prompt length):
> `commercial food photography, 100mm macro f/5.6, soft diffused window daylight from left, warm off-white #FAFAF7 background, oak + bone ceramic, kraft beige and charcoal chia palette, single green accent, clean negative space, photorealistic 8k`

---

## 2. The NEGATIVE PROMPT (paste into every generation)

```
text, letters, words, typography, watermark, logo, brand name, label text, captions, subtitles,
badges, stickers, price tags, arrows, callouts, infographic elements, UI, borders, frames,
extra fingers, deformed hands, mutated hands, malformed fingers, plastic skin, waxy skin,
uncanny face, distorted face, crossed eyes, blurry, low resolution, jpeg artifacts, noise,
oversaturated, HDR, harsh flash, hard shadows, dark moody lighting, teal-orange grade,
clutter, busy background, messy props, mould, dirt, insects, spilled mess,
medical symbols, pills, supplements, before-after comparison, fake certification seals,
cartoon, illustration, 3d render look, cgi plastic, video game, anime
```

**Why "text" is in the negative:** no AI model reliably renders German umlauts and long compound
words (*Wiederverschließbarer*, *Quellfähigkeit*). **All German overlay copy is added afterwards in
Figma / Photoshop**, in brand type. Generate clean plates, letter them yourself.


### Two exceptions — read before you paste

**Image 1 is different.** Its hero is a "10x" sculpted from gel, and the pack carries a label. Banning
`text, letters, words, typography, logo, brand name, label text` there deletes the subject. Use the
trimmed negative in the Bild 1 sheet.

**Nano Banana and the Gemini-family models have no negative prompt field.** They follow instructions;
they do not take a negative channel. Do **not** paste the list into the prompt box — naming things
summons them, and you will get the mould, the insects and the pills. Convert exclusions into positive
instructions instead: *"the only text in the image is the pouch's own label."*

### Material truth

Before writing any prompt that shows the product in use, read
[`04_MATERIAL-WAHRHEIT.md`](04_MATERIAL-WAHRHEIT.md). Describing chia gel as *"thick, continuous,
glossy"* produced an image of melted cheese. Describe **behaviour with numbers**, never adjectives.

---

## 3. Fixed settings

| Setting | Value | Note |
|---|---|---|
| Model (scene plates) | **Higgsfield Soul** | best photoreal skin + food |
| Model (pack must be exact) | **Nano Banana** or **Seedream 4** in Higgsfield | image-edit mode, upload the packshot |
| Aspect ratio | **1:1** | Amazon main + gallery |
| Output | **2000 × 2000 px min.** | upscale in Higgsfield if the model outputs 1024 |
| Batch | 4 per prompt | pick, then re-roll the winner with a fixed seed |
| Seed | free first, then **lock the winner** | keeps images 2–7 looking like one campaign |

Secondary crops to export from the same plate: **4:5** (mobile A+), **16:9** (A+ module banner).

---

## 4. The packshot problem — read this once

Higgsfield will **not** invent the real Naturacereal pack. Three ways to solve it, in order of quality:

1. **Composite (best, and what Converts did).** Generate the scene with the pack area left clean or
   with a neutral stand-up pouch. Drop the real 500 g packshot in afterwards in Photoshop, match the
   shadow and the white balance. 100 % brand-accurate, Amazon-safe.
2. **Image-edit reference (fast).** Use Nano Banana / Seedream 4 inside Higgsfield, upload
   `00_Produkt-Referenz/` packshot as reference, and use the **Prompt C** in each sheet.
   Good for concepting, still check the label letter by letter before publishing.
3. **Blank pouch (concept only).** Prompt a plain kraft stand-up pouch, no label. Fine for internal
   review, never for a live listing.

Put the official 500 g packshot (transparent PNG, front view) into `00_Produkt-Referenz/`
before you start — it is the one asset that is not in this folder yet.

---

## 5. Brand facts the images must stay true to

| | |
|---|---|
| Product | Naturacereal Bio Chia Samen, **500 g** |
| Pack | Kraft-brown resealable stand-up pouch, zip, white label panel |
| Seals | DE-ÖKO Bio hexagon + EU organic leaf |
| Claims allowed | 99,9 % rein · starke Quellfähigkeit · vegan · glutenfrei · wiederverschließbar |
| Claims **forbidden** | any health/medical promise, before-after, weight-loss, "heilt", "wirkt gegen" |
| Green | `#7BB332` · Brown `#522B04` · Ground `#FAFAF7` · Stone `#E8E4DC` |
| Type | SansCulottes (display) · Ubuntu (headline) · Open Sans (body) |
| Ratio | 1 EL Chia : 3 EL Flüssigkeit · 10 Min. quellen |

---

## 6. Amazon compliance per slot

- **Bild 1 (main):** pure white background, product fills 85 %, **no props, no overlay text, no badges
  outside the pack**. The 10x / cascade concepts are gallery-grade, not main-image-safe — see the
  Bild 1 sheet for the compliant Variant C.
- **Bild 2–7 (gallery):** props, text overlays and badges allowed.
