# Editing the words on the website

This is a plain step-by-step guide for changing any of the text on the
Firbeck Sailing Club website — no coding knowledge needed.

## One-off setup (Ashley does this once)

Ashley needs to add you as a collaborator on the GitHub repository so you
can save changes. Once that's done, you don't need to install anything —
everything below happens in a web browser.

## How to change some text

1. Go to `https://github.com/ashtagging/firbeck-sailing-club` and sign in.
2. Click on the file called **index.html**.
3. Click the **pencil icon** (top right of the file, "Edit this file").
4. Use your browser's **Find** (Ctrl+F or Cmd+F) to search for the words
   you want to change, exactly as they appear on the live website.
5. To make it easier to find the right spot, every editable bit of text
   has a short label just above it in grey, like this:

   ```
   <!-- EDIT: hero heading -->
   <h1 ...>A family-friendly sailing club on the water at Rother Valley</h1>
   ```

   You can also search for the label itself (e.g. "EDIT: hero heading")
   using the list below to find the right one.
6. Only change the **words between the arrows** (`>` and `<`). Leave
   everything else — the bits with `<`, `>`, `class=`, `href=` and so on —
   exactly as it is. If in doubt, only touch plain sentences you recognise
   from the live site.
7. Scroll to the bottom of the page. Under "Commit changes", leave the
   default message (or write a short note like "update fee") and click
   the green **Commit changes** button.
8. That's it — the website updates itself automatically, usually within
   a minute or two. Refresh the site to check.

If something looks broken after saving, go to the file's **History** (top
right, the clock icon) and open the previous version to see what changed
— nothing is ever really lost.

## What each label controls

| Label | What it is |
|---|---|
| `hero badge` | The "50th Anniversary" badge at the top |
| `hero heading` | The big headline at the top of the page |
| `hero statement` | The welcome line under the two top buttons |
| `reasons heading` | "Plenty of reasons to join us" |
| `reason 1 title` – `reason 6 title` | The six bold headings in the "reasons to join" grid |
| `reason 1 text` – `reason 6 text` | The sentence under each of those headings |
| `when-we-sail kicker` | Small label above "Sailing throughout the week" |
| `when-we-sail heading` | "Sailing throughout the week" |
| `when-we-sail text` | The paragraph about when members sail |
| `notice kicker` | "Coming in winter 2026" |
| `notice text` | The sentence about the new clubhouse |
| `racing kicker` | Small label above the racing heading |
| `racing heading` | "Informal races, limited rules, plenty of fun" |
| `racing text` | The paragraph about racing |
| `membership kicker` | Small label above the membership fee |
| `membership heading (the fee)` | "£30 a year for the whole family" |
| `membership part-year note` | The £10 part-year rate line |
| `membership text` | The paragraph explaining how to join |
| `membership step 1` – `membership step 3` | The three numbered steps to join |
| `membership button text` | The wording on the yellow download button |
| `find-us kicker` | Small label above "Rother Valley Country Park" |
| `find-us heading` | "Rother Valley Country Park" |
| `find-us text` | The paragraph about the venue |
| `header club name` / `footer club name` | "Firbeck Sailing Club" at the top and bottom |
| `header place name` | "Rother Valley Country Park" at the top |
| `footer address line` | The address and founding date at the bottom |
| `footer email` | The club's contact email (shown twice, both need to match) |
| `footer secretary name` | The secretary's name at the bottom |

## Things not to change here

- **Bank details** aren't on the website at all — they're only inside the
  Word membership form, so there's nothing to edit for those.
- The **membership fee amount** and **form file** should only change once
  a year, alongside a new Word form — ask Ashley if you're not sure.
- Don't add exclamation marks or change the tone too much — the club
  likes to keep things plain and warm, not "salesy".
