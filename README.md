# Support Committee Theme

A Jekyll theme for prisoner/defendant support committee websites — built to
be cloned, configured, and published by people who don't necessarily want
to touch code. Almost everything on the site is controlled from one file:
**`_config.yml`**.

Built and tested for **GitHub Pages** (the "safe mode" plugin whitelist —
no custom Ruby plugins beyond what GitHub Pages itself supports), so a
fork of this repo can be published for free with no build server of your
own. It also runs fine with a local/self-hosted Jekyll build if you'd
rather host elsewhere.

## Quick start (GitHub Pages)

1. Fork or use this repo as a template.
2. Edit `_config.yml` — see below for what each section does.
3. Replace `assets/images/example.jpg` with your own photo (any dimensions
   — the theme doesn't crop it, it just scales to fit the column).
4. In your repo's **Settings → Pages**, set the source to the `main`
   branch. GitHub will build and publish the site automatically.
5. If you're publishing to `username.github.io/reponame` rather than a
   custom domain, set `baseurl: "/reponame"` in `_config.yml`.

## Quick start (local preview)

```
bundle install
bundle exec jekyll serve
```

Then visit `http://localhost:4000`. Requires Ruby and Bundler installed;
see [jekyll's install docs](https://jekyllrb.com/docs/installation/) if
you're starting from scratch.

## Editing `_config.yml`

Every section is commented, and **almost everything is optional** — if a
field is blank or removed, the box/section/link that depends on it just
doesn't render. Nothing breaks. The main things you'll want to fill in:

- `title` — the site name, shown in the banner (e.g. "Support EXAMPLE")
- `photo` / `photo_alt` — the hero photo
- `alert` — an optional urgent-call-to-action stamp on the photo (hunger
  strike, upcoming hearing, call-in campaign). Clear `alert.line1` to
  hide it.
- `bio_teaser` — the short bio shown on the front page (the full bio
  lives in `bio.md`)
- `mail` — address, mailing rules, topics of interest, and a statement
  from them. The `/send-a-letter/` page always exists regardless of
  what's set here (like bio); this just controls whether the
  front-page box mirroring it also shows.
- `donate` — PayPal, Venmo, Cash App, Zelle, Bitcoin, a GoFundMe link,
  facility commissary-deposit instructions, and an Amazon wishlist
  link. Each is independently optional. `donation_embed` takes a raw
  HTML snippet (a real PayPal button, Donorbox, GiveButter, whatever
  your processor gives you) and renders it directly, as-is.
- `codefendants` — optional list of non-cooperating co-defendants to
  link to. Leave the list empty if not relevant.
- `social` / `friends` / `contact_email` — footer content
- `color_scheme` — pick a key from the `color_schemes` list further down
  in the same file (12 built in — see below)

## Pages vs. posts

- **Posts** (`_posts/`, filename `YYYY-MM-DD-title.md`) are news updates.
  They show up as previews on the front page (newest 5 by default,
  `front_page_post_count` in `_config.yml`) and in full on `/news/`.
  Give a post `featured: true` in its front matter to make it the
  highlighted banner under the bio box on the front page — if more than
  one post is flagged featured, the most recent one wins automatically.
- **Pages** are everything else. `bio.md` and `send-a-letter.md` are the
  two pages every site needs — both always exist and always show up in
  navigation, the same way. `case-summary.md` is optional — set
  `case_summary_page: false` in `_config.yml` and delete the file if you
  don't want it.
- **Adding a new page** (a FAQ, a legal-fund breakdown, whatever): copy
  `event.md`, change the front matter (`title`, `permalink`, `preview`),
  write the content, done. Any page with `nav: true` and
  `show_on_homepage: true` in its front matter automatically appears
  both as a box at the bottom of the front page's right column *and* in
  the page-navigation block on every other page — no template edits
  needed. `nav_order` controls where it sits in that list.

## Color schemes

12 are built in, covering a range of aesthetics (environmentalist
greens, punk, insurrecto black-and-red, Pan-African, transhumanist blue,
and so on) — see the `color_schemes` section of `_config.yml` for the
full list and their hex values. Set `color_scheme:` at the top of the
file to any of those keys.

**To add your own scheme:** copy an existing block under
`color_schemes`, give it a new key, and change the 10 hex values
(`paper`, `paper_dim`, `ink`, `ink_soft`, `accent`, `accent_dark`,
`accent_2`, `line`, `line_soft`, `white`). That's it for most schemes —
everything else derives from those 10. A few schemes also set an
`overrides` block for one or two specific colors (the comments in
`assets/css/style.css` explain what each override does) — you'll only
need that if a component looks wrong with your new palette (most often:
if your background is dark, make sure `white` — used for card
backgrounds — is a dark tone too, not a literal light color).

## Fonts

Anton, JetBrains Mono, and Lora are self-hosted in `assets/fonts/`
(vendored via the `@fontsource` npm packages) rather than pulled from
Google Fonts — no third-party requests, nothing sent off-site when
someone loads the page.

## A note on future WordPress support

This theme's design is deliberately kept in a fairly plain, portable
shape — plain HTML/CSS with Liquid doing the templating, no
Jekyll-specific tricks beyond what's documented here — since the same
design is planned to eventually get a WordPress theme as well. Nothing
in this repo depends on that yet.
