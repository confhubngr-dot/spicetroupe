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
| Nothing on the logo strip — those eight are real | — |
| Every past event, the four headline figures, the standing bookings | `past-events.html` |
| Nothing on pricing — Options 1–3, the add-ons and the terms are all real | — |
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

**2. Saved photographs.** The lower grid holds seven photographs served from `images/gallery/`.
That section is complete — nothing to paste.

## Pricing

`events.html` carries six service lines, nine add-ons and seven terms.

| Service | Fee |
|---|---|
| Wedding Entertainment | Base ₦2,000,000 |
| Nigerian Multicultural Displays | Base ₦2,500,000 |
| Funeral Entertainment | Base ₦2,000,000 |
| Special Welcome Experiences | Per item: ₦1,000,000 / ₦2,000,000 |
| International Displays | From ₦5,000,000 |
| Media Production | From ₦5,000,000 |

To change anything, edit the `SERVICES` or `ADDONS` list near the top of the page source. Write
amounts as plain numbers — `2000000`, not `2,000,000`. The commas and the ₦ are added for you.

A service row looks like this:

```python
("weddings", "Wedding Entertainment", "--marigold",
 "From the first guest arriving to the last dance of the night.",
 "Base fee", 2000000,
 [("Guest Welcome Performance", "A vibrant cultural welcome...", None),
  ...],                       # third value is a per-item price, or None
 ""),                         # closing note, or empty
```

Set the fee amount to `None` for a service priced per item — Special Welcome Experiences works that
way, with each item carrying its own "From" price instead of one headline figure.

If every item in a service has an empty description, the list renders as compact chips rather than
full definitions. Media Production uses this.

**Prices appear in three places.** The `SERVICES` list, the meta description at the top of
`events.html`, and the `makesOffer` block in the structured data. Change a headline figure and
update all three, or Google will show a price the page contradicts.

## Adding a past event

In `past-events.html`, each booking is one `.log-row` block. Copy a row, paste it under the right
year, change the five fields: date, event, venue and city, tradition, audience size. The colour dot
comes from `style="--hue:var(--marigold)"` — use the same variable as that tradition's card.

## The story page

Worth asking the founder before rewriting `about.html`: who the first booking was for and what went
wrong; when it stopped being a favour and started being a business; which dancer joined that changed
what the group could do; where the name came from; and what they'd be doing if it had never taken
off. Those five answers are a story page.

## Where enquiries go

The form on `contact.html` now **sends via WhatsApp**. When someone presses "Send via WhatsApp",
a small script collects every field, writes them into a tidy message, and opens a chat with
+234 813 806 7502. The sender presses send and it arrives like any other WhatsApp message.

Nothing to sign up for, nothing to pay, and no backend. The trade-off: the sender must press send
themselves, so you lose anyone who fills the form in and then abandons it.

**To receive enquiries by email instead**, sign up with Formspree, Netlify Forms or Getform (all
free at low volume). They give you a URL. In `contact.html`:

1. change `action="#"` to `action="https://formspree.io/f/YOUR-ID"` and `method="post"`
2. delete `id="waForm"` from the `<form>` tag, so the script stops intercepting the submit

You can also run both — leave WhatsApp as the main route and add a separate email form below it.

## The hero video

`images/hero.mp4` is live on the home page. The source was a 14-second vertical clip (1080x1920);
it has been cropped to a wide band, scaled to 1024x576, stripped of audio and compressed to 1.3MB.

The crop position matters: at 32% from the top the masquerade's head and the fire performers both
stay in frame. Higher and you lose the fire, lower and you decapitate the masquerade. That is set in
CSS as `object-position:center 32%`.

`images/hero.jpg` is the poster frame. It shows on mobile — where the video is deliberately disabled
to save data — on slow connections, before the video loads, and for anyone with reduced-motion on.

**To swap the video later:** supply a landscape clip if you can, since a vertical source loses about
two thirds of its frame. Otherwise 10-20 seconds, no audio track (browsers block sound on autoplay,
so it is pure dead weight), and under 2MB.

## The photographs

Seven photographs are live in `images/gallery/`, each with a real alt description and a caption.
Total 1.2MB, sized to what the grid actually displays at retina density rather than full resolution.

To swap one, keep the same filename and update the alt text and caption in `gallery.html`. Aim for
under 250KB per photo — Squoosh at quality 78 gets there.

## The logo strip

Eight client logos are in place, in `images/logos/`. They scroll continuously on the home page and
the story page, pause when someone hovers, and stop entirely for anyone with reduced-motion on.

They sit desaturated at 62% opacity and come up to full colour when the strip is hovered. That is
deliberate: eight logos in eight different colour schemes fight each other and pull attention off
the copy, so they read as a quiet row of proof until someone looks directly at them.

**Currently shown:** Nigerian Civil Aviation Authority · Government of Abia State · The Wheat Baker
Lagos · Deep Learning Indaba · Government of Anambra State · Riggs London · Billionaire Realtors ·
Aceroyal Estates.

**What was done to the files:** each was trimmed to its artwork, had its background lifted to
transparency (white, grey and black backgrounds all differed), and was scaled to a common optical
weight so no single logo dominates. The Anambra seal arrived inside a printed black frame, which was
cropped off; the NCAA seal sat on a grey disc, which was removed. All eight were then
palette-compressed — 816KB down to 176KB, which matters on mobile data.

**To add or swap one:** put a transparent PNG in `images/logos/` and edit the `LOGOS` list near the
top of the page source. The row of cells appears **twice** in the code, one after the other — that
duplication is what makes the scroll loop seamlessly, so change both copies identically or the loop
will visibly jump.

Only display logos you have permission to use. A "trusted by" strip is a claim about a working
relationship, and organisations like NCAA and state governments are exactly the ones likely to ask.

## SEO

The technical side is done: titles, meta descriptions, canonical URLs, Open Graph and Twitter cards,
LocalBusiness + PerformingGroup structured data, FAQ schema on the packages page, `sitemap.xml` and
`robots.txt`.

### Do this first, or none of it works

**Set the real domain.** Every canonical URL, the sitemap and the social cards currently point at
`https://www.spicetroupe.ng`. If the live domain differs — a different name, no `www`, or a
`.github.io` address — find and replace `https://www.spicetroupe.ng` across all seven pages plus
`sitemap.xml` and `robots.txt`. A canonical tag pointing at the wrong domain tells Google to ignore
your pages.

**Add `images/og-cover.jpg`.** 1200×630 JPEG, under 300KB, showing dancers in full costume with the
name on it. This is the image that appears when anyone shares a link on WhatsApp — which is how most
Nigerian clients will encounter the site. Without it, links share as a bare grey box.

### Then, in order of what actually moves the needle

1. **Google Business Profile** — free, at business.google.com. For "dance group near me" searches
   this outranks the website itself. Add both Lagos and Abuja, the categories "Dance Company" and
   "Entertainment Agency", real photos, and the WhatsApp number.
2. **Google Search Console** — free, at search.google.com/search-console. Verify the domain, submit
   `sitemap.xml`, and you will see the actual search terms people use to find the site. Those terms
   should then shape the copy.
3. **Reviews on the Business Profile.** Ask every client. Reviews drive local ranking harder than
   anything on the page, and unlike page copy you cannot fake them safely.
4. **Replace the invented past events.** Twenty-one real bookings with real venues and cities is
   substantial, specific, location-rich content — exactly what ranks for "cultural dance group
   Lagos". It is currently the biggest single SEO gain sitting unclaimed.
5. **Links from real places.** Event venues, planners, and any press coverage. One link from a hotel
   or festival site beats fifty directory listings.
6. **Instagram bio link** pointing at the site.

### What NOT to do

Do not add review or star-rating markup for reviews that do not exist. Google issues manual
penalties for it, and recovering takes months. The structured data here deliberately contains no
ratings.

Do not buy backlink packages. Same reason.

Do not stuff keywords. The copy already names the traditions, the cities and the event types
naturally, which is what Google rewards.

## Publishing

Drag the folder onto [netlify.com/drop](https://app.netlify.com/drop) for a free live site, or use
GitHub Pages or Cloudflare Pages. Any host that serves plain HTML works.

## Design notes

- Type is Bricolage Grotesque for headings, Karla for body, DM Mono for labels and figures.
- Styles are inlined in every page so each works on its own. Change the CSS in one file and you'll
  need to change it in all seven.
