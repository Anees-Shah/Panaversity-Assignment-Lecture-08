---
name: nico-meela-thumbnails
description: >
  Generates vertical Instagram/Reels thumbnail images for the recurring
  'Nico & Meela' kids' content series, in a 3D Pixar/Disney animation style.
  Use this skill whenever the user gives a scenario involving Nico and/or
  Meela (e.g. Nico bakes cookies and Meela burns them, next thumbnail Nico
  waters the plants and Meela kills them, make the cover for this week's
  episode), asks for a thumbnail, cover, or title card for this series, or is
  producing a batch of these images and wants the two characters to look the
  same from post to post. Always consult this skill before drawing or
  generating any image of Nico or Meela — it holds the locked character
  model sheet, the reference image, and the title-text style that must stay
  identical across every thumbnail in the series.
---

# Nico & Meela Thumbnail Generator

Nico and Meela are the two recurring stars of an ongoing series of split-screen
"contrast" thumbnails: one side shows a kid succeeding at a task, the other
shows a kid struggling with the exact same task. The format only works if
viewers recognize the two characters instantly, post after post — which means
every generation has to reproduce the same face, hair, outfit, and title-text
style even though each thumbnail is otherwise a brand new image with no memory
of the last one. This skill exists to be that memory: copy the descriptions
below into the generation prompt every time rather than reconstructing them
from scratch, since small unintentional drift (a different shade of hair, a
missing necklace) is exactly what breaks the illusion of a consistent show.

## Step 1 — Get the scenario

The user will hand you a short scenario, usually a task where one character
succeeds and the other doesn't (e.g. "Nico ties his shoes & Meela can't get
hers on"). Pull out of it:
- **The task** (what activity is happening)
- **Who succeeds and who struggles** — default to Nico succeeding / Meela
  struggling, matching the established pattern, but follow the user's
  scenario exactly if they reverse it or frame it differently
- **Any props or setting details the task implies** (a shovel for gardening,
  a mixing bowl for baking, etc.)

If the scenario is just a phrase with no other direction, that's enough to
proceed — don't stop to ask for more detail than the format needs.

## Step 2 — The cast (copy verbatim, every time)

These descriptions are the locked model sheet. Never let a scenario change
hair color, outfit, accessories, or relative age/height — only pose,
expression, and props should vary by scenario.

### Nico
- Boy, about 10–12 years old
- Short dark brown hair, neatly tousled with a side part
- Round glasses with tan/light-gold frames
- Warm, confident, closed-mouth smile
- Thin silver chain necklace
- Oversized cream/off-white crew-neck t-shirt
- Sage-green pants, cuffed at the ankle
- Clean white sneakers
- Default energy: confident and put-together — stands tall, one hand on hip,
  the other free for a prop or a thumbs-up
- His signature color for title text is **bright green**

### Meela
- Girl, about 7–8 years old — noticeably younger and shorter than Nico
- Long straight brown hair, worn loose
- Red short-sleeve t-shirt worn under a blue denim overall dress (pinafore
  style)
- White ankle socks
- White sneakers
- Default energy: overwhelmed and flustered — a hand on her head, worried
  eyebrows, mouth slightly open; body language reads as stressed rather than
  sad
- Her signature color for title text is **hot pink**

## Step 3 — Use the reference image

`assets/nico_meela_reference.jpeg` is the actual approved image of both
characters together and is the visual ground truth for face shape,
proportions, and outfit colors — more reliable than any text description,
including the one above.

- If the image-generation tool available to you accepts a reference image
  (image-to-image, character-reference, or a "consistent character" feature),
  always pass this file in alongside the prompt.
- If it's text-prompt-only, look at the reference image yourself first and
  make sure the text prompt matches what you see (exact hair shade, glasses
  color, necklace, outfit colors) rather than relying on the summary above
  from memory.

## Step 4 — Constant visual style

Every thumbnail, regardless of scenario, shares this art direction:
- 3D animated feature-film look (Pixar/Disney/DreamWorks-style): big round
  expressive eyes with catchlight highlights, soft rounded facial
  proportions, smooth glossy skin shading
- Warm, bright, cheerful cinematic lighting with a soft rim light
- Vertical 9:16 canvas (1080×1920) — sized for an Instagram Reels/Story cover
- Clean, polished, slightly glossy rendering — not painterly or sketchy

## Step 5 — Composition template

The frame is a single scene split down the middle by a vertical torn-paper
seam, so it reads as one moment literally torn in two:

- **Left half** — the character who succeeds. Bright, tidy, sunlit version of
  the setting; sparkle/shine decorations near the character; confident pose.
- **Right half** — the character who struggles. The same setting gone wrong
  in a way that visually shows the specific task failing (scattered leaves,
  spilled items, a knocked-over object relevant to the task); squiggles,
  exclamation marks, or motion-lines drawn near the character's head;
  stressed pose.
- Both halves share the same background architecture (same house/yard style)
  so they read as two sides of one location, not two unrelated places.
- Keep both characters at roughly the same scale and vertical placement so
  the torn-paper seam feels like it split one continuous image.

Swap which side is "succeeding" only if the user's scenario explicitly says
Meela succeeds and Nico struggles — otherwise Nico takes the left/success
side and Meela takes the right/struggle side, matching the established
format.

## Step 6 — Title text system

Bold, glossy, bubble-style 3D lettering stacked across the top third of the
frame, thick black outline, soft drop shadow, rounded comic/cartoon typeface
— matching the reference image exactly.

**Pattern:** `[NICO] [TASK VERB] & [MEELA] [OUTCOME PHRASE]`, usually stacked
across 3 lines (name+verb / "&" / name+outcome).

**Default color-coding** (keep this consistent across the whole series — it's
part of what makes the thumbnails instantly recognizable as the same show):
- "NICO" → bright green
- the verb/phrase describing his side → white
- "&" → black/white
- "MEELA" → hot pink
- the outcome phrase describing her side → golden yellow

Reword the verb/outcome phrase to match whatever task the scenario describes
(e.g. "BAKES" / "BURNS IT", "PLANTS" / "KILLS IT") — the color pattern and
lettering style are what stay fixed, not the words.

## Step 7 — Assemble the generation prompt

Combine everything above into one prompt, roughly in this order: art style →
both character model sheets → composition/split-screen layout → this
scenario's specific left-side and right-side details → title text with its
color-coding → reference image attached if supported. Don't paraphrase the
character descriptions down to save space — precision here is the entire
point of the skill.

## Step 8 — Generate the image

Check what's actually available in the current session before doing
anything else, since this varies by environment:

1. If a connected image-generation tool or MCP connector is available,
   use it, passing the reference image in if the tool supports it.
2. If none is connected but one could be (e.g. via the MCP registry), search
   for it and offer it the way you normally would for a third-party tool,
   rather than assuming.
3. If no image-generation capability exists in this session, don't fabricate
   or mock up a fake image. Instead, hand back the fully assembled prompt as
   the deliverable, tell the user plainly that this environment can't render
   it directly, and let them know they can paste the prompt (plus the
   reference image) into whatever image generator they use.

## Step 9 — Consistency check before delivering

Before presenting a generated thumbnail, compare it against
`assets/nico_meela_reference.jpeg`:
- Same hair color/length for both characters?
- Nico's glasses, necklace, and outfit colors intact?
- Meela's outfit colors (red top, blue denim overall) intact?
- Nico still visibly older/taller than Meela?
- Title text uses the same color-coding pattern as previous thumbnails in
  the series?

If something has drifted, regenerate rather than shipping it — the whole
value of this series is that the characters look the same every time.