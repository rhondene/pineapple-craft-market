# Pineapple Craft Market — website

The website for Pineapple Craft Market Association, Main Street, Ocho Rios.
Plain HTML, CSS and a few lines of JS. No build step, no npm, nothing to
install. Open `index.html` in a browser and you are looking at the live site.

Full background and design rules: `../docs/SPEC.md` in this repository's
parent folder (not part of this site, kept alongside it for reference).

## Preview it locally

Just double-click `index.html`, or from this folder run:

```
python3 -m http.server 8000
```

then open `http://localhost:8000` in a browser. Either way works; the local
server just avoids some browsers' quirks with the `file://` protocol.

## Folder structure

```
code/
├── index.html       the whole site, one page
├── css/style.css     all styling
├── img/               photos, already resized and compressed
├── video/             culture-day.mp4
├── favicon.svg, favicon.ico   the pineapple mark
├── CNAME              the custom domain, read by GitHub Pages
└── README.md           this file
```

## Things still to fill in

Search `index.html` for these markers and replace them with real
information as the association provides it:

- `<!-- REPLACE -->` — phone number, WhatsApp, email, vendor names/quotes on
  the four maker cards, stall numbers
- `<!-- CONFIRM -->` — anything that needs to be double-checked before
  publishing (currently: the map coordinates in the structured data at the
  top of the file)
- The Google Maps `<iframe>` in the Visit section — swap it for the
  association's own embed link once the Google Business Profile is claimed.
  Full checklist of outstanding content is in `../docs/SPEC.md` section 6.

## Editing content

Everything is in `index.html`. To swap a photo: put the new file in `img/`,
then change the `src="img/…"` and `alt="…"` on the matching `<img>` tag. Keep
new photos resized to about 1300px on the long edge and compressed to
around JPEG quality 78 before adding them — there's a two-line way to do
this from Terminal on a Mac:

```
sips -Z 1300 -s formatOptions 78 your-photo.jpg
```

Don't add a photo straight from a phone (usually 3000px+ and several MB) —
it will slow the page down for visitors on cruise ship wifi.

## Deploying to GitHub Pages

1. Push the contents of this `code/` folder to the `main` branch of the
   GitHub repository (this folder should be the *root* of that repo — not
   nested inside it).
2. In the repo's Settings → Pages, set the source to the `main` branch,
   root folder.
3. Under "Custom domain" enter `pineapplecraftmarketja.com` (this matches
   the `CNAME` file already in this folder) and enable "Enforce HTTPS" once
   it's available.
4. At the domain registrar (Porkbun), point DNS at GitHub Pages:
   - Four `A` records for `@` → `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153`, `185.199.111.153`
   - One `CNAME` record for `www` → `<github-username>.github.io`
   DNS changes can take a few hours to propagate.

## Source photos and video

The full set of unprocessed phone photos and video clips the association
provided live in `../media_content/`. A few more good ones are in there
that aren't used on the site yet — useful once the P1 photo gallery gets
built (see `../docs/SPEC.md`). There's also a second, longer raw video
(`VID-20260717-WA0032.mp4`, a walkthrough of a stall interior) not currently
used; the culture day event footage on the live site was trimmed and
compressed from `VID-20260718-WA0000.mp4`.
