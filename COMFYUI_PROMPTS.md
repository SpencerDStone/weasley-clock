# ComfyUI Asset Generation — The Stones Family Clock

Style: **Whimsical watercolor**, Mary GrandPré / Weasley clock vibe.

## Recommended setup

- **Model**: SDXL with a watercolor LoRA, OR Flux dev with an illustration LoRA
- **Sampler**: DPM++ 2M Karras, 30-40 steps
- **CFG**: 6-7
- **Output**: 1024x1024 minimum, 2048x2048 if you have VRAM

For face cameos: **IP-Adapter Plus FaceID v2** with each kid's photo as reference.

---

## Asset 1 — Aged Parchment Background

**Folder:** `/homeassistant/www/clock-assets/parchment.png`
**Size:** 2048x2048 square, PNG with no transparency
**Purpose:** Replaces the CSS gradient on the clock face

**Prompt:**
```
aged ivory parchment paper texture, watercolor wash on
handmade paper, soft sepia stains, foxing spots in warm
amber, subtle paper fibers, faint pencil sketch grid lines,
edges slightly darker with sienna patina, hand-painted
watercolor strokes, no text, no objects, antique manuscript
background, J.K. Rowling Weasley clock face, Mary GrandPré
illustration style, weathered handmade paper
```

**Negative:**
```
text, letters, numbers, words, photo, photograph,
modern, digital, clean, sharp, vibrant colors, bright,
neon, geometric, vector, sterile
```

---

## Asset 2 — Family on Broomsticks over Birmingham

**Folder:** `/homeassistant/www/clock-assets/scene.png`
**Size:** 2048x768 wide (3:1 aspect, sits above the clock)
**Purpose:** Painted scene at the top of the dial, Weasley reference style

**Prompt:**
```
whimsical watercolor illustration of a family of five flying
on broomsticks above the Birmingham Alabama skyline at golden
sunset, two parents and three young boys soaring through warm
peach and lavender clouds, the Vulcan statue and Cahaba River
visible below, hand-painted children's book art, Mary GrandPré
style, soft watercolor washes, gentle ink linework, dreamy
magical atmosphere, golden hour lighting, vintage fairy tale
storybook illustration, full of whimsy and warmth, no text,
oval composition framed by soft watercolor edges
```

**Negative:**
```
text, words, photo, realistic, harsh shadows, modern style,
3D render, anime, cartoon, vector art, cel shaded, dark,
scary, creepy
```

---

## Asset 3 — Hand Cameo Portraits (5 of these)

**Folder:** `/homeassistant/www/clock-assets/hands/[name].png`
**Size:** 512x512, PNG with transparent background
**Purpose:** Oval portrait at the tip of each clock hand

**Workflow:** Use IP-Adapter Plus FaceID v2:
1. Load each person's photo as the face reference
2. Use the prompt below
3. Crop output to a tight oval centered on the face
4. Export as PNG with alpha channel (transparent outside oval)

**Prompt (use for each family member):**
```
watercolor portrait cameo, [Daddy/Mommy/Shepherd/Elliot/Becket],
soft hand-painted illustration, oval framed portrait, gentle
watercolor brushwork, warm golden background fading to sepia
edges, vintage children's book illustration style, Mary GrandPré
style, J.K. Rowling Weasley clock cameo, ornate gold filigree
oval frame around the face, slightly stylized but recognizable,
warm and friendly expression, no text
```

Generate one per person:
- `daddy.png`
- `mommy.png`
- `shepherd.png`
- `elliot.png`
- `becket.png`

**Tip:** Use a simple background photo for each kid (face well-lit, looking forward). The IP-Adapter handles the rest.

---

## Asset 4 — Family Crest

**Folder:** `/homeassistant/www/clock-assets/crest.png`
**Size:** 1024x1024, PNG with transparent background
**Purpose:** Decorative element at the bottom of the clock

**Prompt:**
```
whimsical watercolor family crest, ornate heraldic shield with
five small icons (a key, a shepherd's crook, a music note, a
small house, a baby rattle) arranged around the shield, the
text "THE STONES" in elegant medieval calligraphy across a
banner above the shield, the year "EST. 2013" on a smaller
banner below, ornate gold filigree borders, watercolor and
ink illustration, Mary GrandPré style, soft sepia and warm
amber palette, hand-painted children's book heraldry, vintage
storybook crest, no other text
```

**Negative:**
```
photo, realistic, modern logo, 3D, vector, sharp lines,
neon, harsh colors, multiple texts, clutter
```

---

## Asset 5 — Optional Hand Tips (decorative arrows)

If you want truly painted clock hands instead of CSS shapes:

**Folder:** `/homeassistant/www/clock-assets/hand-tip.png`
**Size:** 256x768 (tall and thin)
**Purpose:** Painted brass arrow shape used as the visible part of each hand

**Prompt:**
```
ornate antique brass clock hand, vintage spear tip with
fleur-de-lis decoration, engraved filigree on the shaft,
diamond ornament near the center, counterweight at the
bottom, watercolor illustration, weathered antique gold,
sepia and amber tones, isolated on transparent background,
J.K. Rowling Weasley clock hand, hand-painted antique
clockmaker style
```

---

## File structure when done

```
/homeassistant/www/clock-assets/
  parchment.png       (2048x2048 background)
  scene.png           (2048x768 broomstick scene)
  crest.png           (1024x1024 family crest)
  hand-tip.png        (optional, painted arrow)
  hands/
    daddy.png
    mommy.png
    shepherd.png
    elliot.png
    becket.png
```

Once you generate them, drop them into HA's File Editor at those paths. I'll update the clock code to use them when they're present (and gracefully fall back to the current CSS look if any are missing).

---

## Order to generate

1. **Start with the parchment** — easiest, most universal asset, transforms the whole feel
2. **Then crest** — small commitment, clear win
3. **Then the scene** — the showpiece, may take 5-10 generations to nail
4. **Last: face cameos** — need the kids' photos, takes longest

---

## When you're ready

Generate the parchment first and drop it in `/homeassistant/www/clock-assets/parchment.png`. Tell me, and I'll push a code update that uses it. We'll iterate from there.
