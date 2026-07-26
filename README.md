# Peyton Pours — website

Static one-page site. No build step, no framework — `index.html` plus an `assets/` folder.

## Structure

```
index.html              the whole site (markup, styles, script inline)
favicon.svg
assets/logo/            martini mark, icon badge, full lockup (SVG)
assets/work/            portfolio imagery (web-optimized JPEG)
```

Sections, in order: hero → services → selected work → brand proof → inquiry form.

## Local preview

```bash
python3 -m http.server 4173
```

Then open http://localhost:4173

## Deploy to Vercel
1. Commit `index.html`, `favicon.svg` and `assets/` to the root of the `peytonpours` GitHub repo.
2. In Vercel: New Project → import the `peytonpours` repo.
   - Framework preset: **Other**
   - Build command: *(leave empty)*
   - Output directory: *(leave empty / `.`)*
3. Deploy. Then Vercel → Project → Settings → Domains → add `peytonpours.com` and follow the DNS instructions.

## Contact form
The form currently shows a "thank you" state without sending anywhere.
To receive submissions at peytonpours@gmail.com, create a free form at https://formspree.io
(point it at that address), then replace `your-form-id` in `index.html`
(the `action="https://formspree.io/f/your-form-id"`) with your real Formspree endpoint.
No other changes needed.

The form includes an "interest" checkbox group (Bartending / Party design / Packer party /
Not sure yet) so inquiries arrive pre-sorted by what the person actually wants.

## Adding portfolio work

Drop a web-sized image in `assets/work/` and add a `.piece` block to the `#work` section.
Source art lives outside this repo; the images here are resized copies (long edge ~1750px,
JPEG q88) to keep the page around 1 MB. To regenerate one:

```bash
sips -Z 1750 -s format jpeg -s formatOptions 88 source.png --out assets/work/name.jpg
```

Clicking any portfolio image opens it in a lightbox, so detailed pieces like the menus
stay readable at full size.
