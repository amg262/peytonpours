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
Submissions are emailed to **peytonpours@gmail.com** via [FormSubmit](https://formsubmit.co)
(no account, no API key — the address is the endpoint).

**One-time activation:** the first time the live form is submitted, FormSubmit emails
peytonpours@gmail.com a confirmation link. Click it once and every submission after that
lands in the inbox. Until it's clicked, submissions are not delivered — so after deploying,
send one test inquiry from the site and then confirm from the inbox.

The visitor stays on the page (the JS posts to FormSubmit's AJAX endpoint and swaps in the
thank-you state); if JS or the network fails it falls back to a normal form POST, which lands
on FormSubmit's own thank-you page. Spam handling is a hidden `_honey` honeypot field.

To change the recipient, edit the address in the form's `action` in `index.html` — the AJAX
endpoint is derived from it. The new address needs its own one-time activation click.
