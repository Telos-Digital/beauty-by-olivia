# Beauty by Olivia

Static one-page site for Olivia, booth stylist at The Blonde Magnolia,
South Carolina. Single `index.html`, no build step, no dependencies.

Deployed on GitHub Pages from `main` / root, at
https://telos-digital.github.io/beauty-by-olivia/

**Pages must be enabled by the repo owner in the browser.** Collaborators on a
personal repo only get write access, so the API cannot switch it on.

## The site

One page, `index.html`, in the gingham design: Cormorant Garamond with a
Parisienne script, wine and bubblegum, scalloped dividers and floral bands.

An earlier editorial mockup was briefly live here by mistake and has been
removed. It is still in git history if it is ever wanted back:
`git show HEAD~1:index.html`.

## Live placeholders — fix these

| Where | Currently | Needs |
|---|---|---|
| Contact card | "Olivia Dixon on Facebook" | The profile URL, so it becomes a real link |
| Contact card | "South Carolina" | Street address of The Blonde Magnolia |

The fake phone number, fake email and unconfirmed Instagram handle were removed
on 2026-09-10. Nothing on the live site is invented any more. Booking is the
only contact channel, and it points at her real Mangomint page.

The booking button is live and correct: it goes to Olivia's Mangomint page at
The Blonde Magnolia (`staffId=36`).

## Launch hygiene not yet done

The mockup was pushed exactly as designed. Still worth adding before this gets
promoted anywhere: a meta description, Open Graph tags for link previews, a
favicon, and LocalBusiness structured data so she can show up in local search.
