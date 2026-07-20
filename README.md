# Peyton Pours — website

Static one-page site. No build step.

## Deploy to Vercel
1. Commit the contents of this `site/` folder to the root of the `peytonpours` GitHub repo (index.html, favicon.svg).
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
