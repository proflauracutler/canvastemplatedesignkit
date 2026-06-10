# Canvas HTML Style Guide

This file documents the visual conventions used in Canvas reading pages for this course.
Follow these patterns consistently across all modules. This guide is intentionally
course-agnostic -- it can be shared with other instructors/courses to keep a consistent
look across Canvas pages, regardless of subject matter.

---

## General Structure

- Outer wrapper: `<div id="dp-wrapper" class="dp-wrapper dp-flat-sections variation-2">`
- Header bar: BYU blue `#002e5d`, white text, title format: **"Module XX Reading"** (nothing else)
- Each section: `<div class="dp-content-block" style="background-color: #ffffff;">` with a Font Awesome icon and h3 heading -- the explicit white background overrides the "variation-2" theme's default alternating section colors, so every section reads as a plain white card on the light gray page background
- Font Awesome 5 CDN: `https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css`
- All text: dark `#333`, no special characters (use `--` not em dash, straight quotes only)

---

## Accessibility: Always Pair `background` With `color`

**Rule: any element with an inline `background` or `background-color` must also set an explicit `color` in that same `style` attribute.**

Why: students can switch Canvas into dark mode. Dark mode forces page text to a light color, but it does **not** touch colors you've set explicitly inline. If you set a light `background-color` (like `#f0f4f8`) without also setting `color`, the text on top of it gets switched to white by dark mode and becomes illegible -- white text on a light blue box.

```html
<!-- WRONG: no color set -- text disappears in dark mode -->
<p style="background-color: #f0f4f8; border-left: 4px solid #002e5d; padding: 12px 16px;">
  This text vanishes in dark mode.
</p>

<!-- RIGHT: color is explicit, so dark mode can't override it -->
<p style="background-color: #f0f4f8; border-left: 4px solid #002e5d; padding: 12px 16px; color: #333;">
  This text stays readable in dark mode.
</p>
```

This applies everywhere a background color appears: callout boxes, cards, table rows/cells, numbered step blocks, code blocks, etc. Default body text color is `#333`. Where a heading or label inside a colored box already has its own accent color (e.g., a card title in `#002e5d`), that's fine -- just make sure every element that sets a `background` also carries its own `color`.

---

## Section Headings (dp-has-icon format)

Use this exact pattern for all section h3 headings -- it produces the line-with-icon divider Canvas renders natively:

```html
<h3 class="dp-has-icon" style="border-color: #002e5d; border-width: 2px;">
  <i class="dp-icon fas fa-bullseye" style="border-color: #002e5d; border-width: 2px; color: #002e5d;" aria-hidden="true">
    <span class="dp-icon-content" style="display: none;">&nbsp;</span>
  </i>Section Title
</h3>
```

Common icon choices: `fa-book-reader` (reading intro), `fa-bullseye` (purpose/goals), `fa-list-ol` (instructions/steps), `fa-lightbulb` (key concepts), `fa-chart-bar` (data/analysis), `fa-comments` (discussion), `fa-tasks` (assignments), `fa-paper-plane` (submission), `fa-check-square` (grading), `fa-puzzle-piece` (synthesis/closing), `fa-search` (research), `fa-sitemap` (systems/structure), `fa-link` (closing/summary)

---

## Callout Boxes

Three callout types, used sparingly. Default to the navy "Key Rule" box for most callouts -- the other two are for genuinely distinct situations.

```html
<p style="background-color: #f0f4f8; border-left: 4px solid #002e5d; padding: 12px 16px; margin: 16px 0; border-radius: 0 6px 6px 0; color: #333;">
  <strong>Key Rule:</strong> The default callout. Use for important rules, definitions to remember, or framing statements.
</p>

<p style="background-color: #f0fdfa; border-left: 4px solid #0d9488; padding: 12px 16px; margin: 16px 0; border-radius: 0 6px 6px 0; color: #333;">
  <strong>Tip:</strong> Use teal for helpful tips, shortcuts, or "in practice" notes that are useful but not essential.
</p>

<p style="background-color: #fef2f2; border-left: 4px solid #9f1239; padding: 12px 16px; margin: 16px 0; border-radius: 0 6px 6px 0; color: #333;">
  <strong>Watch Out:</strong> Use the muted rose/red callout only for real warnings -- common mistakes that will cost students points, or steps that are easy to get wrong.
</p>
```

---

## Blockquote

```html
<blockquote style="border-left: 4px solid #002e5d; background: #f0f4f8; font-style: italic; padding: 12px 20px; margin: 16px 0; border-radius: 0 6px 6px 0; color: #333;">
  "Quote text here."
  <cite style="display: block; margin-top: 6px; font-style: normal; font-size: 0.88em; color: #555;">- Speaker Name, Title</cite>
</blockquote>
```

Style: light navy background (`#f0f4f8`), `4px solid #002e5d` left accent border, italic text. Use a single hyphen before the speaker name in the `<cite>` line. Since every section now sets an explicit white background, this light navy fill reads as a distinct card against the section's white background.

---

## Multi-Color Cards (Small Groups of Related Items)

Used for: any small set of categories, phases, principles, or types that belong together as a group -- typically 3-5 items, but the rotation below cycles so it works for any number.

```html
<div style="display: flex; flex-wrap: wrap; gap: 12px; margin: 16px 0;">
  <div style="flex: 1; min-width: 180px; border-left: 5px solid #16a34a; background: #f0fdf4; padding: 14px 16px; border-radius: 0 6px 6px 0; color: #333;">
    <div style="font-size: 1.05em; color: #15803d; margin-bottom: 6px; font-weight: bold;">Card Title</div>
    <p style="margin: 0; font-size: 0.95em; color: #333;">Card body text goes here.</p>
  </div>
  <!-- repeat for each card with different colors -->
</div>
```

**Color rotation** (border color / background / title color) -- cycle through these 5 in order. Navy and Gray are placed at opposite ends so two low-saturation neutrals never sit next to each other. If a framework needs more than 5 slots, repeat the rotation from #1:

| Slot | Border | Background | Title text |
|------|--------|------------|------------|
| 1. Navy | `#002e5d` | `#f0f4f8` | `#002e5d` |
| 2. Steel Blue | `#2563eb` | `#eff6ff` | `#1e40af` |
| 3. Indigo | `#5b21b6` | `#f5f3ff` | `#5b21b6` |
| 4. Teal | `#0d9488` | `#f0fdfa` | `#0f766e` |
| 5. Gray | `#6b7280` | `#f9fafb` | `#374151` |

Most frameworks have 3-4 parts, so in practice you'll usually only use slots 1-4 (Navy, Steel Blue, Indigo, Teal). Card body text is always `#333` regardless of card color (per the dark-mode rule above).

**Status colors** (use sparingly, only for "correct/incorrect" or "go/avoid" meaning -- not as routine card colors):

| Meaning | Border | Background | Title text |
|---------|--------|------------|------------|
| Good / correct | `#16a34a` | `#f0fdf4` | `#15803d` |
| Needs work / avoid | `#9f1239` | `#fef2f2` | `#9f1239` |

No orange/yellow anywhere in the palette. Red/rose is reserved for the "needs work / avoid" status color and real warning callouts -- not used as a routine 4th or 5th card color.

---

## Numbered Step Blocks (for assignments)

Each step uses a circle number + left-bordered card, all inline. Alternate the background between `#f0f4f8` and `#ffffff` for readability:

```html
<div style="display: flex; align-items: flex-start; gap: 16px; margin-bottom: 14px; background: #f0f4f8; border-left: 5px solid #002e5d; border-radius: 0 6px 6px 0; padding: 16px 20px; color: #333;">
  <div style="background: #002e5d; color: #fff; font-weight: bold; border-radius: 50%; min-width: 30px; width: 30px; height: 30px; line-height: 30px; text-align: center; font-size: 0.88em; flex-shrink: 0;">1</div>
  <div>
    <div style="font-weight: bold; color: #002e5d; font-size: 1.05em; margin-bottom: 6px;">Step Title</div>
    <p style="margin: 0; font-size: 0.95em; line-height: 1.6; color: #333;">Step body text.</p>
  </div>
</div>
```

---

## Tables (sequences, comparisons, rubrics)

Used for: step-by-step sequences, worked examples, side-by-side comparisons, and rubric/grading tables. **All of these share one table style** -- only the columns and the presence of a conclusion row change.

**Table Rules (apply to every table on this list):**
- **Header row**: solid navy `#002e5d` background, white text, with the cell border color matching the header background so the header reads as one solid block.
- **Body cells**: `1px solid #d0dae8` border on every cell, and an explicit `color` (rows commonly set `color: #333` so it's inherited by every cell in that row).
- **Banding**: only alternate row backgrounds if a table has **more than 2 body rows**. When banding, start with `#f0f4f8` (light blue), then `#ffffff`, repeating. Tables with 1-2 body rows are **not banded** -- all body rows are plain `#ffffff`.

```html
<table style="width: 100%; border-collapse: collapse; margin: 16px 0; font-size: 0.95em;">
  <thead>
    <tr>
      <th style="background: #002e5d; color: #ffffff; padding: 10px 14px; text-align: left; border: 1px solid #002e5d;">Item</th>
      <th style="background: #002e5d; color: #ffffff; padding: 10px 14px; text-align: left; border: 1px solid #002e5d;">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background: #f0f4f8; color: #333;">
      <td style="padding: 10px 14px; border: 1px solid #d0dae8; font-weight: bold; color: #002e5d; white-space: nowrap; vertical-align: top;">First item</td>
      <td style="padding: 10px 14px; border: 1px solid #d0dae8; vertical-align: top;">Description text.</td>
    </tr>
    <!-- if more than 2 body rows, alternate #f0f4f8 / #ffffff / #f0f4f8 ... -->
    <tr style="background: #ffffff; color: #333;">
      <td style="padding: 10px 14px; border: 1px solid #d0dae8; font-weight: bold; color: #002e5d; white-space: nowrap; vertical-align: top;">Second item</td>
      <td style="padding: 10px 14px; border: 1px solid #d0dae8; vertical-align: top;">Description text.</td>
    </tr>
  </tbody>
</table>
```

**Variations:**
- **Comparisons**: add more columns (e.g., "Aspect / Option A / Option B"). Same header, border, and banding rules.
- **Rubrics**: add a "Points" column and center-align both the header and the cells in that column.
- **2 or fewer body rows**: skip banding -- every row is `background: #ffffff; color: #333;`.

**Narrow label columns (e.g., a "Why 1?" / "Step 1" column):** don't rely on the `width: 1%` + `white-space: nowrap` "shrink-to-fit" trick -- Canvas's table rendering (likely `table-layout: fixed` from its theme CSS, and/or stripping `white-space` from inline styles) can ignore both and let the label wrap onto two lines anyway. Instead, give the column a real percentage width sized to fit its content, e.g. `width: 8.27545%;` for a "Why N?" column in a two-column table. Keep `font-weight: bold; color: #002e5d;` for these label cells.

**If there's a summary/conclusion row at the bottom** (common for sequences that build to a takeaway), add one final row spanning all columns, styled solid navy with white text:

```html
<tr>
  <td style="padding: 12px 16px; font-weight: bold; color: #ffffff; background: #002e5d; border: 1px solid #002e5d; font-size: 0.85em; text-transform: uppercase; letter-spacing: 0.04em; white-space: nowrap;">Conclusion</td>
  <td style="padding: 12px 16px; background: #002e5d; color: #ffffff; border: 1px solid #002e5d; font-weight: bold;">Conclusion text.</td>
</tr>
```

---

## "Avoid vs. Do This" Comparison Table

Use when contrasting a wrong/weak approach with a correct/strong one (e.g., vague vs. precise requirements). Only the header cells carry color -- rose (`background: #fef2f2; color: #9f1239`) for "Avoid", green (`background: #f0fdf4; color: #15803d`) for "Do This Instead". Body rows follow the same banding rule as any other table (plain white if 2 rows or fewer).

```html
<table style="width: 100%; border-collapse: collapse; margin: 16px 0; font-size: 0.95em;">
  <thead>
    <tr>
      <th style="background: #fef2f2; color: #9f1239; padding: 10px 14px; text-align: left; border: 1px solid #fecaca; width: 50%;">
        <i class="fas fa-times-circle" style="margin-right: 6px;" aria-hidden="true"></i>Avoid
      </th>
      <th style="background: #f0fdf4; color: #15803d; padding: 10px 14px; text-align: left; border: 1px solid #bbf7d0; width: 50%;">
        <i class="fas fa-check-circle" style="margin-right: 6px;" aria-hidden="true"></i>Do This Instead
      </th>
    </tr>
  </thead>
  <tbody>
    <tr style="background: #ffffff; color: #333;">
      <td style="padding: 10px 14px; border: 1px solid #d0dae8;">Vague version</td>
      <td style="padding: 10px 14px; border: 1px solid #d0dae8;">Precise version</td>
    </tr>
  </tbody>
</table>
```

---

## Code Blocks

For any block of source code, use Canvas's default `<pre><code>` styling (do not change the background or text color) and only bump the font size to 16px -- the default monospace size renders too small in Canvas:

```html
<pre style="font-size: 16px;"><code>def greet(name):
    return f"Hello, {name}!"

print(greet("world"))</code></pre>
```

For a short inline code reference within a sentence, use `<code>inline_code()</code>` with Canvas's default styling -- no extra background or color needed.

---

## Interactive Elements (`<details>` / `<summary>`)

Canvas renders native `<details>`/`<summary>` as an expandable disclosure widget -- no JavaScript needed. Use it for two things: revealing answers, and embedding runnable "Try It" code sandboxes.

### Reveal an Answer

```html
<details style="margin: 16px 0;">
  <summary style="cursor: pointer; font-weight: bold; color: #002e5d;">Show Answer</summary>
  <div style="padding: 12px 16px; margin-top: 8px; background: #f0f4f8; border-left: 4px solid #002e5d; border-radius: 0 6px 6px 0; color: #333;">
    <p style="margin: 0;">The answer text goes here. Students click the summary line to expand this box.</p>
  </div>
</details>
```

### "Try It" Embedded Code Sandbox (Trinket)

Use this to embed a runnable code exercise inline using [Trinket](https://trinket.io). Trinket embeds require a saved trinket -- you can't pass arbitrary code via the URL. To create one:

1. Go to https://trinket.io, create a free account if needed, and start a new trinket in the language you need (e.g., "Python" for `python3`).
2. Write/paste the starter code for the exercise and save the trinket.
3. Click **Embed** (or **Share > Embed**) and copy the embed URL it gives you -- it will look like `https://trinket.io/embed/python3/<trinket-id>`.
4. Paste that URL into the `src` attribute below, replacing `<trinket-id>`.

```html
<details style="margin: 16px 0;">
  <summary><strong>Try It: Variables</strong></summary>
  <div style="padding: 8px 0; color: #333;">
    <p>Instructions here -- describe what the student should change and run.</p>
    <iframe src="https://trinket.io/embed/python/3d8d7ce66b"
      width="100%" height="350" frameborder="0"
      marginwidth="0" marginheight="0" allowfullscreen></iframe>
  </div>
</details>
```

`showInstructions=true` shows any instructions text saved with the trinket; `start=result` runs the program automatically when the embed loads. Adjust `height` based on how much output the program produces (250-400px is typical).

---

## Module Title Convention

Header always reads: **"Module XX Reading"** (or "Unit XX Reading" / "Week XX Reading" /
"Module XX Group Project", depending on the course's terminology and the page type).
No subtitle. No topic name. Just the unit label and the page type.

---

## Canvas Compatibility Notes

- **No SVG inline elements** -- Canvas strips them on upload. Use PNG files instead (generate with matplotlib, upload separately).
- **No `<style>` blocks** -- Canvas strips the entire `<style>` block when you save a page. ALL styling must use inline `style=""` attributes. CSS classes defined in a `<style>` block will have no effect.
- **No localStorage or sessionStorage**
- External CSS (Font Awesome CDN) is fine via `<link>` tag.
- Any element with a `background`/`background-color` must also set `color` explicitly (see "Accessibility" section above) so dark mode doesn't make text illegible.
