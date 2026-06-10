# Canvas Template Design Kit

A reusable visual style system for building consistent, professional Canvas course pages -- developed for IS 401 but written to be course-agnostic, so any instructor can drop it into their own course.

## What's in this kit

- **`canvas-html-style-guide.md`** -- the rulebook. Documents the color palette, page structure, accessibility rules (especially Canvas dark mode), and every reusable component (headings, callout boxes, cards, tables, blockquotes, code blocks, interactive elements) with copy-pasteable HTML snippets.
- **`canvas-design-kit.html`** -- a single living "preview page." Paste this into a Canvas page (Pages > New Page > switch to HTML editor) to see every component rendered together in one place. Use it as a sandbox for trying color/spacing tweaks before applying them elsewhere.

## How to use this with an AI assistant (Claude, ChatGPT, etc.)

1. Share both files with your AI assistant when generating or editing a Canvas page.
2. Ask it to follow the conventions in `canvas-html-style-guide.md` for any new section, table, card, or callout it writes.
3. If you want to see what something looks like before publishing, ask the assistant to add it to a copy of `canvas-design-kit.html` and paste that into a Canvas page to preview.

## Viewing the design kit

Don't just double-click `canvas-design-kit.html` and open it in a browser -- it'll look plain and show up in Times New Roman, since none of Canvas's page styling is applied outside of Canvas itself.

Instead:

1. In Canvas, go to **Pages > + Page** to create a new (unpublished) page.
2. Give it a name like "Design Kit Preview" and leave it unpublished -- students won't see it.
3. Click the **</> HTML Editor** option in the page editor.
4. Paste the entire contents of `canvas-design-kit.html` into the HTML editor.
5. Click **Save**.

You should now see every component (headings, cards, tables, callouts, etc.) rendered the way it will actually look to students.

## Feedback and customization

If you'd like to tweak colors, add new components, or request additional styles, let me know -- I'm happy to add them so we can keep working from a single, cohesive design.

## Using this with Claude (or another AI assistant)

As you port your existing course pages into Canvas, share `canvas-html-style-guide.md` (and `canvas-design-kit.html` for reference) with Claude and tell it to write each new page following this style. Since every page pulls from the same rules and color palette, your pages will end up looking consistent with each other -- like they belong to the same course -- even though they're generated one at a time.

## Key rules to know before you start

- **No `<style>` blocks.** Canvas strips them on save -- all styling must be inline `style=""` attributes.
- **No SVG.** Canvas strips inline SVG; use PNG images instead.
- **Dark mode safety.** Any element with a `background`/`background-color` must also set an explicit `color`, or the text becomes illegible when a student switches Canvas to dark mode.
- **ASCII only.** No smart quotes, em dashes, or other special characters -- use `--` for an em dash and straight quotes.

## Customizing for your course

The color palette (navy primary + steel blue / indigo / teal / gray accents, with rose/green reserved for "avoid/do this" status) is just a starting point. If you'd like a different palette to match your school's branding, update the color values throughout `canvas-html-style-guide.md` and `canvas-design-kit.html` consistently -- the structure and rules will still apply.

## Questions / contributions

This kit is shared as a starting point for colleagues building AI-assisted Canvas courses. Feel free to fork, adapt, and open issues or pull requests with improvements.
