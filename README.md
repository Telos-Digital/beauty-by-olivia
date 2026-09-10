# Beauty by Olivia

Static one-page site for Olivia, booth stylist at The Blonde Magnolia,
South Carolina. Single `index.html`, no build step, no dependencies.

Deployed on GitHub Pages from `main` / root.

## Two designs are live

| Design | File | URL |
|---|---|---|
| Editorial (current main site) | `index.html` | https://jimmyardis.github.io/beauty-by-olivia/ |
| Gingham / romantic | `gingham.html` | https://jimmyardis.github.io/beauty-by-olivia/gingham.html |

Same content and the same booking link in both. They differ only in art
direction: the editorial version is Fraunces over Work Sans in dusty rose, the
gingham version is Cormorant Garamond with a Parisienne script in wine and
bubblegum, with scalloped dividers and floral bands.

To make the gingham version the main site: `git mv gingham.html index.html`
(after moving the editorial one aside), commit, push.

**Weight warning:** `gingham.html` is 3.3 MB because two decorative PNGs are
embedded as base64 data URIs, one of them 2.4 MB. That is slow on a phone.
Extract them to real image files and compress before this becomes the main
site.

## Live placeholders — fix these

| Where | Currently | Needs |
|---|---|---|
| Contact card | `(000) 000-0000` | Real phone, or delete the line |
| Contact card | `hello@beautybyolivia.com` | Confirm this mailbox exists |
| Contact card | `@beautybyolivia` | Confirm the Instagram handle |
| Contact card | "South Carolina" | Street address of The Blonde Magnolia |
| Gallery | Five "photo coming soon" tiles | Real photos of her work |

The booking button is live and correct: it goes to Olivia's Mangomint page at
The Blonde Magnolia (`staffId=36`).

## Launch hygiene not yet done

The mockup was pushed exactly as designed. Still worth adding before this gets
promoted anywhere: a meta description, Open Graph tags for link previews, a
favicon, and LocalBusiness structured data so she can show up in local search.
