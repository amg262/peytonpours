# Peyton Pours — website

Static one-page site. No build step.

## Deploy to Vercel
1. Commit the contents of this `site/` folder to the root of the `peytonpours` GitHub repo (index.html, favicon.svg).
2. In Vercel: New Project → import the `peytonpours` repo.
   - Framework preset: **Other**
   - Build command: *(leave empty)*
   - Output directory: *(leave empty / `.`)*
3. Deploy. Then Vercel → Project → Settings → Domains → add `peytonpours.com` and follow the DNS instructions.

## Outage notice banner
The banner at the top of the page tells visitors the form delivered nothing between
July 19 and August 7, 2026, and asks anyone who wrote during that window to resend.
It is temporary — delete the `<aside class="notice">` block and the `.notice` CSS rule
in `index.html` once it has run its course.

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

A copy of every submission also goes to andrewgunn31@gmail.com via the `_cc` field.
FormSubmit documents CC only — there is no BCC option — but nothing is exposed to the person
submitting the form, since they never receive the email; only the two recipients see the
header. The CC address does not need its own activation click. For more addresses, make `_cc`
a comma-separated list.

Note that `_cc` puts that address in the public page source, where spam scrapers can find it.
To avoid that, drop the `_cc` field and set up a forwarding filter in the peytonpours@gmail.com
inbox instead — same result, address never published.

To change the recipient, edit the address in the form's `action` in `index.html` — the AJAX
endpoint is derived from it. The new address needs its own one-time activation click.
