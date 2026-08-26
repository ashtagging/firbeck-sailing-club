# CLAUDE.md — Firbeck Sailing Club website

## What this project is

A one-page public website for **Firbeck Sailing Club**: a small, family-friendly sailing club at Rother Valley Country Park, Rotherham, UK. Founded 1976; 50th anniversary in 2026.

This is a plain static HTML/CSS site — no framework, no build step, no dependencies. See `README.md` for how content is organised and what to update where.

## The audience and the constraint that matters most

The site is for **people who might join the club** and **existing members**. It will be maintained by **volunteers who are not developers**.

Every technical decision should be judged against: *can a club volunteer still change the membership fee, add a notice, or swap a photo in two years' time, without help?* If a choice makes the site fancier but the club can no longer maintain it, it is the wrong choice.

## Stack

**A static site**: plain HTML + CSS + minimal JS, deployed to a free static host (Netlify / Cloudflare Pages / GitHub Pages). **No React, Next.js, build pipeline, CMS, database or auth.** There is no application here — it is a page. Keep it that way unless the user explicitly asks to change stack.

## Content

Values that change over time (membership fee, sailing days, contact email, form filename, notices, founding year) are written directly in `index.html` rather than a separate data file, because the content must be present in the raw HTML for SEO and to work with no JavaScript. Several of these values are intentionally duplicated in a few places — see the table in `README.md`. When editing one, check the table and update every match.

## Design rules — do not drift from these

The approved direction is **1a "Clubhouse Classic"**: traditional, calm, navy + cream with yellow as a small accent.

- **Palette**: navy `#16305c`, cream `#f7f3e8`, white, club yellow `#f2c500`. Meta/eyebrow greys were deliberately darkened from the original design reference for contrast — see `css/styles.css` for the current values. Do not introduce new colours beyond what's in the `:root` custom properties.
- **Yellow is an accent.** Small areas only — badges, kickers, one button, the logo plate. Never a yellow background band, never yellow body text.
- **Fonts**: Source Serif 4 for headings, Karla for body and UI. No substitutions.
- **Radius `2px`.** Buttons and badges are nearly square on purpose. Do not round corners further; no pill buttons.
- **No shadows, no gradients.** Separation comes from hairlines and flat colour blocks.
- **No carousels, no parallax, no auto-playing anything, no emoji, no icon set.**
- **Photography over illustration.** Only `assets/boats.jpg` exists as a real photo. If a slot needs an image and there is no photo for it, leave a clearly-marked placeholder and tell the user — do not generate images, use stock photos, or draw SVG illustrations of boats.

## Copy rules

Tone: **warm, welcoming, plain English**, British spelling. Use the club's own phrasing where it exists — don't "improve" it into marketing language. No exclamation marks, no invented statistics or testimonials. Don't invent facts. If a section feels thin, ask for real content rather than filling it.

## Hard requirements

- **Never publish bank details.** They live inside the Word membership form only.
- **Don't publish members' personal data.** The secretary's name and the club email are the only personal details cleared for the site.
- Membership sign-up is **download the Word form → pay by bank transfer → email the secretary**. Do not build an online membership form, payment flow or member login.
- **Mobile must work well.** Most visitors will be on a phone.
- **Accessibility is not optional**: heading order, real `alt` text, visible `:focus-visible` rings, 4.5:1 contrast, works at 200% zoom and keyboard-only.
- **SEO basics**: descriptive title, meta description, Open Graph image, `SportsActivityLocation`/`SportsClub` JSON-LD.
- If analytics is ever added, use a **cookieless** provider so no consent banner is needed.

## Working style

- Keep the CSS in the single `css/styles.css` file with the custom properties at the top — don't add inline styles or a second stylesheet.
- **Ask before adding sections, pages or copy.** The client (a club volunteer) knows the audience. Deferred: members' noticeboard beyond one notice item, photo gallery, committee page, event calendar, online forms.
- When something is genuinely missing (a photo, a confirmed postcode, a new PDF), list it and ask — don't paper over it.
