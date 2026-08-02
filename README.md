# Spice Troupe — site files

A seven-page site for a Lagos cultural dance group.

`index.html` · `styles.html` · `events.html` · `past-events.html` · `gallery.html` ·
`about.html` · `contact.html`

Keep all seven in one folder. Open `index.html` in a browser to view it. No build step, no
dependencies apart from Google Fonts and the Instagram embed script.

## What is real and what is invented

**Real:** the name, the WhatsApp number (+234 813 806 7502), the Instagram handle, the Lagos base
and nationwide travel.

**Invented — must be replaced before this goes live:**

| What | Where |
|---|---|
| The whole origin story, the timeline, the founder quote | `about.html` — marked with a comment |
| Every past event, the four headline figures, the standing bookings | `past-events.html` |
| Guide prices (₦350,000 / ₦650,000 / ₦1,500,000) | `events.html` |
| All five testimonials and references | `index.html`, `past-events.html` |
| Dancer names and roles | `about.html` |
| Email address `hello@spicetroupe.ng` | every page footer, plus `contact.html` |
| CAC / RC number | `about.html` |

## The eight dance traditions

Bàtá (Yoruba), Atílògwù (Igbo), Ekombi (Efik), Swange (Tiv), Koroso (Hausa & Kanuri), the Ohafia
war dance / ikpirikpi ogu (Igbo), Afrobeats & street, and commissioned contemporary work.

These were chosen and described from published sources, not from the troupe. **Have the founder read
`styles.html` before it goes live.** Which traditions they actually perform, how they describe them,
and what they are comfortable claiming are theirs to decide — particularly the Ohafia war dance,
which commemorates something specific and is described here as a staged piece.

Each tradition has a fixed colour that runs through the whole site: the ribbon under the hero, the
style cards, the past-events dots, the gallery tiles. Add a ninth and give it its own colour in the
`:root` block at the top of each page.

## The WhatsApp button

Green button, bottom-right, on all seven pages. Opens a chat with a first message already typed.
To change the number or that message, edit the link — it appears three times per page (floating
button, footer, and on `contact.html` the details list and the green button):

```
https://wa.me/2348138067502?text=Hi%20Spice%20Troupe%2C%20I%27d%20like%20to%20check%20a%20date...
```

Digits only, no plus sign, country code first. The `text=` part is URL-encoded: spaces are `%20`,
a comma is `%2C`, an apostrophe is `%27`. Works on phones and WhatsApp Web, no Business account
needed.

## Getting the Instagram content in

Instagram blocks automated downloading, so the media has to come from you. Two routes, and the
gallery page is built for both.

**1. Live embeds.** Six dashed boxes on the gallery page. On any post or reel, tap "..." → Embed →
copy → paste over the box. Photos and reels both work; captions come across. The `embed.js` script
is already on the page. The account must stay public.

**2. Saved photographs.** Embeds are slow on a weak connection and Instagram crops them. For the
best half-dozen shots, download the originals, put them in an `images` folder beside these pages,
and swap each coloured tile for the commented-out `<img>` tag just above it. Write a real `alt`
description for each.

If you'd rather it fill itself with no pasting, Behold, SnapWidget and LightWidget all have free
tiers.

## Adding a past event

In `past-events.html`, each booking is one `.log-row` block. Copy a row, paste it under the right
year, change the five fields: date, event, venue and city, tradition, audience size. The colour dot
comes from `style="--hue:var(--marigold)"` — use the same variable as that tradition's card.

## The story page

Worth asking the founder before rewriting `about.html`: who the first booking was for and what went
wrong; when it stopped being a favour and started being a business; which dancer joined that changed
what the group could do; where the name came from; and what they'd be doing if it had never taken
off. Those five answers are a story page.

## The enquiry form

The form in `contact.html` doesn't send anywhere yet. Formspree, Netlify Forms and Getform all have
free tiers — change the form's `action` to the URL they give you and `method` to `post`. There's a
comment beside the form. Most enquiries will come through WhatsApp anyway.

## Publishing

Drag the folder onto [netlify.com/drop](https://app.netlify.com/drop) for a free live site, or use
GitHub Pages or Cloudflare Pages. Any host that serves plain HTML works.

## Design notes

- Type is Bricolage Grotesque for headings, Karla for body, DM Mono for labels and figures.
- Styles are inlined in every page so each works on its own. Change the CSS in one file and you'll
  need to change it in all seven.
