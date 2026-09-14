# Firbeck Sailing Club website

A one-page website for Firbeck Sailing Club at Rother Valley Country Park, Rotherham.

Plain HTML and CSS, built with a tiny static site generator ([Eleventy](https://www.11ty.dev/))
so that the wording lives in one simple data file instead of scattered through
HTML tags. Netlify rebuilds the real page automatically whenever that file
changes — there's nothing to install or run locally just to make a content
change.

## Files

```
src/index.njk         The page template (structure, not wording)
src/_data/text.yaml    Every piece of wording on the site — edit this to change text
css/styles.css         All styling (colours, fonts, spacing, layout)
assets/                Photos, logos, and the membership form
admin/                 The Decap CMS editing screen (served at /admin)
.eleventy.js           Eleventy config
netlify.toml           Tells Netlify how to build the site
```

For the non-technical, step-by-step guide to changing wording via the
`/admin` screen (aimed at a volunteer with no coding background), see
[EDITING.md](EDITING.md).

## Making common content changes

All wording lives in **`src/_data/text.yaml`** — either edit it directly, or
use the `/admin` screen described in [EDITING.md](EDITING.md), which edits
the same file. A handful of values are intentionally reused in more than one
place in the template (`src/index.njk`) so they can only be wrong in one
place:

| Value | Where it lives in `text.yaml` | Also appears in |
|---|---|---|
| Contact email | `footer.email` | hero "Email the club" button, footer (twice) |
| Membership fee (`£30`) | `membership.heading` | — |
| 2026 part-year rate (`£10`) | `membership.part_year_note` | — |
| Founding year / anniversary | `hero.badge`, `footer.founded_note` | — |

The **membership form filename**, **photos**, and **meta/SEO tags**
(page title, description, Open Graph, JSON-LD) are deliberately *not*
editable from `text.yaml` or the CMS — they're technical/structural and
live directly in `src/index.njk`, to avoid an accidental typo breaking a
link or search-engine listing.

### Updating the membership form each year

1. Replace `assets/FSC-membership-form-2026.docx` with the new year's form.
2. If the filename changes, update both `href="assets/FSC-membership-form-2026.docx"`
   attributes in `src/index.njk` (hero button and Membership button) to match.
3. Update `membership.button_text` in `text.yaml` (e.g. "Download the 2027
   form (Word)") and any other mention of the year.

### Swapping a photo

Replace `assets/boats.jpg` with a new photo of the same name, or add a new
file and update `src="assets/boats.jpg"` in `src/index.njk`. Keep photos
compressed (a few hundred KB, not multiple MB) so the page stays fast on
phones — resize to roughly 1600px wide and save as JPEG before adding.

### Adding a notice

The "Coming in winter 2026" box in the "When we sail" panel is the one place
for club news — edit `notice.kicker` and `notice.text` in `text.yaml` (or via
the CMS). This is deliberately a single item, not a noticeboard — ask before
turning it into a list.

## Editing and publishing — two ways

1. **The `/admin` screen** (`firbecksailingclub.com/admin`) — a simple
   form, one box per sentence, no code. This is what the CMS ([Decap
   CMS](https://decapcms.org/)) provides, authenticated via Netlify
   Identity. See [EDITING.md](EDITING.md). Clicking **Publish** commits
   straight to `text.yaml` on the `master` branch, which triggers a Netlify
   rebuild automatically.
2. **Editing `text.yaml` directly** in a text editor or on github.com, then
   committing and pushing — same effect, useful for anyone comfortable with
   git.

Either way, Netlify rebuilds and republishes automatically, usually within
a minute or two.

## Local development

Only needed if you want to preview changes before publishing them (not
required for day-to-day content edits):

```
npm install
npm start        # serves the site locally with live reload
npm run build    # builds the site into _site/, as Netlify does
```

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
  the `src` on the `<iframe>` and the "Get directions" link in `src/index.njk`.
- **Logo**: `assets/logo.jpg` is a JPG with a white background box, so it
  sits on a yellow plate in the header and favicon. A transparent PNG/SVG
  from the club would look cleaner — drop the yellow plate (`.brand-logo`
  background) if one is provided.
- **Domain**: the site is hosted on **Netlify**, served on the custom domain
  `firbecksailingclub.com`, configured in the Netlify dashboard (Site
  settings → Domain management) with DNS pointed there from wherever the
  domain was bought. `src/index.njk`'s canonical link, Open Graph tags and
  JSON-LD `url` all point at that domain.
- **PDF membership form**: a PDF version would be friendlier on phones than
  the Word doc. Worth asking the club for one.

## Deploying

Hosted on **Netlify**, building from the `master` branch of this repo. Any
push to `master` — including a Publish from the `/admin` CMS screen —
triggers a Netlify build (`npm run build`, via `netlify.toml`) and
republishes automatically, usually within a minute or two. Check progress
under the Netlify dashboard's **Deploys** tab if a change doesn't appear.

The repo can stay public or be made private — Netlify doesn't require a
public repo the way GitHub Pages did. There's nothing sensitive in it either
way — bank details live only in the Word membership form, which is itself
meant to be publicly downloadable.
