# Firbeck Sailing Club website

A one-page website for Firbeck Sailing Club at Rother Valley Country Park, Rotherham.

Plain HTML, CSS and no build step, on purpose — anyone can open `index.html` in a
text editor, change a line, save, and the site is updated. There is nothing to
install and nothing to run to make a content change.

## Files

```
index.html       All page content and structure
css/styles.css   All styling (colours, fonts, spacing, layout)
assets/          Photos, logos, and the membership form
```

## Making common content changes

There is no separate "content file" — values are written directly into
`index.html` so the page works with no JavaScript and reads well for search
engines. A handful of values appear in **more than one place** and must be
changed together. Search for the old value in `index.html` (Ctrl+F / Cmd+F)
and replace every match:

| Value | Appears in |
|---|---|
| Membership fee (`£30`) | hero stat row, Membership heading |
| Sailing days (`Wed`, `Sat`, `Sun`) | hero stat row, "When we sail" boxes |
| Founding year / anniversary (`1976`, `50`) | hero badge, hero stat row, footer |
| Contact email | hero button, footer |
| Membership form filename | hero button `href`, Membership button `href` — and the actual file in `assets/` |
| "Coming up" notice | the yellow-edged box in the "Racing, sort of" panel |

### Updating the membership form each year

1. Replace `assets/FSC-membership-form-2026.docx` with the new year's form.
2. If the filename changes, update both `href="assets/FSC-membership-form-2026.docx"`
   attributes in `index.html` (hero button and Membership button) to match.
3. Update the button text "Download the 2026 form (Word)" and any other
   mention of the year.

### Swapping a photo

Replace `assets/boats.jpg` with a new photo of the same name, or add a new
file and update `src="assets/boats.jpg"` in the hero section. Keep photos
compressed (a few hundred KB, not multiple MB) so the page stays fast on
phones — resize to roughly 1600px wide and save as JPEG before adding.

### Adding a notice

The "Coming in summer 2026" box in the "Racing, sort of" panel is the one
place for club news. Edit `notice-kicker` and `notice-body` text directly.
This is deliberately a single item, not a noticeboard — ask before turning
it into a list.

## Design rules

The approved design is "Clubhouse Classic": navy, cream and a small amount
of yellow, traditional and calm. Colours, fonts and spacing are all defined
as CSS custom properties at the top of `css/styles.css` — change values
there rather than adding one-off styles elsewhere. Do not introduce new
colours, rounded corners, shadows, gradients, or icons.

Two accessibility-driven colour tweaks were made from the original design
reference: the meta/eyebrow greys (`#6b7079` / `#8a8f98`) were darkened
slightly (see the comment in `styles.css`) because the originals fell below
the 4.5:1 contrast ratio required for small text.

## Known gaps / things to revisit

- **Map**: embedded via a keyless Google Maps iframe for the postcode
  `S26 5PQ` (Rother Valley Country Park's general postcode). If the club has
  a more precise pin (e.g. the sailing club compound specifically), update
  the `src` on the `<iframe>` and the "Get directions" link in the Find Us
  section.
- **Logo**: `assets/logo.jpg` is a JPG with a white background box, so it
  sits on a yellow plate in the header and favicon. A transparent PNG/SVG
  from the club would look cleaner — drop the yellow plate (`.brand-logo`
  background) if one is provided.
- **Domain**: `index.html` has placeholder URLs
  (`https://www.firbecksailingclub.org.uk/`) in the canonical link and Open
  Graph tags. Update these to the real domain once hosting is set up,
  otherwise social media previews and search engines will point at the
  wrong address.
- **PDF membership form**: a PDF version would be friendlier on phones than
  the Word doc. Worth asking the club for one.

## Deploying

This is a static site — no build step. Deploy by connecting the GitHub repo
to Netlify, Cloudflare Pages, or GitHub Pages and pointing it at the repo
root. Any push to `main` will publish automatically.
