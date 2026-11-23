# Ozark Small Engine & E-Bike Repair (Demo Website)

A complete, responsive one-page website for a **fictional** small-engine and e-bike repair shop in Nixa, Missouri.
Built as a portfolio/demo piece to show small businesses what a professional site can look like.

> All business details are placeholders. The phone number (417) 555-0123 is in the reserved fictional
> 555-01xx range, there is no street address, and the testimonial is labeled as a sample.

## What's inside

```
ozark-small-engine-demo/
├── index.html        Page content: header, hero, about, services, process, review, contact, footer
├── css/styles.css    All styling (colors and fonts are variables at the top under :root)
├── js/main.js        Mobile menu, scroll animations, active nav link, contact-form validation
├── images/           Hand-made SVG illustrations and icons (tiny, sharp at any size, no licensing issues)
└── serve.ps1         Optional local preview server (PowerShell, nothing to install)
```

No frameworks, no build step, and no npm. The only external request is Google Fonts (Archivo + Inter); if that
fails to load, it falls back to system fonts.

## Preview it locally

**Option A (easiest):** double-click `index.html`. It opens in your browser and everything works.

**Option B (closer to a real web server):** open PowerShell in this folder and run:

```powershell
powershell -ExecutionPolicy Bypass -File .\serve.ps1
```

Then visit http://localhost:8080. Press `Ctrl+C` to stop it.

## Publish it online (free options)

1. **Netlify Drop (fastest):** go to https://app.netlify.com/drop and drag this whole folder onto the page.
   You get a live URL in seconds. Create a free account to keep it and rename the URL.
2. **Cloudflare Pages:** Workers & Pages → Create → Pages → *Upload assets*, then upload this folder.
3. **GitHub Pages:** push the folder to a GitHub repo, then go to Settings → Pages → Deploy from branch.

For a real client, buy their domain (about $10–20 a year from Cloudflare, Namecheap or Porkbun) and connect it
in the host's "Custom domain" settings. HTTPS is set up automatically.

## Making the contact form actually send

Right now the form validates entries and shows a success message, but **sends nothing** (demo mode).
To make it live, choose one option:

- **Formspree** (works on any host): create a form at formspree.io, then in `js/main.js` replace the
  `showSuccess();` call in the submit handler with the commented-out `fetch(...)` example, using your form ID.
- **Netlify Forms** (if hosted on Netlify): add `name="contact" data-netlify="true"` to the `<form>` tag, then
  POST the form data to `/` with `fetch` in the submit handler. Submissions show up in the Netlify dashboard
  and can be emailed to the owner.
- **Your own backend:** any endpoint that accepts a POST and emails the shop.

Also add spam protection (a honeypot field or the service's built-in captcha) when you go live.

## Turning this into a real client's site: checklist

- [ ] Remove the dark **demo bar** at the top of `index.html` (and the demo notes in the form and footer)
- [ ] Replace the business name, logo, phone number, and service area
- [ ] Add a real address and hours **only if the owner wants them public**
- [ ] Replace the sample testimonial with real reviews (with the customer's permission)
- [ ] Swap the illustrations for real photos of the shop or work (export as `.webp`, about 1600px wide)
- [ ] Connect the contact form (see above)
- [ ] Remove `<meta name="robots" content="noindex">` from `index.html` so Google can index the site
- [ ] Set up a Google Business Profile and link it to the site
- [ ] Optional: add privacy-friendly analytics (Plausible, Cloudflare Web Analytics)

## Customizing the look

All colors live at the top of `css/styles.css`:

```css
--green-900: #16301f;   /* main dark green */
--charcoal-900: #1c1f22;
--orange-500: #e07a2e;  /* accent */
```

Change these to rebrand the whole site for a different client in a few minutes.
