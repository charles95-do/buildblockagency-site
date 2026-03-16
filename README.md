# Build Block Agency — Website

A single-file static marketing website for **Build Block Agency**, a digital marketing agency serving local contractors in Southern Maryland and the DMV area.

## What's in the Box

```
website/
├── index.html   ← The entire website (HTML + CSS + JS, self-contained)
└── README.md    ← This file
```

That's it. One file. Drop it anywhere and it works.

---

## Before You Go Live

Search for these placeholders in `index.html` and replace them:

| Placeholder | Replace with |
|---|---|
| `(XXX) XXX-XXXX` | Your actual phone number (appears twice) |
| `Charlie@buildblockagency.com` | Your real email address |
| The fake testimonial from "Mike R." | A real client quote, or remove it until you have one |

---

## Deploy Options

### Option 1 — Netlify (Easiest, Free)

1. Go to [netlify.com](https://netlify.com) and sign up (free)
2. Drag and drop the `website/` folder onto the Netlify dashboard
3. Done — you'll get a live URL instantly like `your-site.netlify.app`
4. To use a custom domain: **Site settings → Domain management → Add custom domain**

Netlify also handles the contact form automatically if you add `netlify` to your `<form>` tag:
```html
<form netlify onsubmit="handleSubmit(event)">
```

### Option 2 — GitHub Pages (Free)

1. Create a GitHub account if you don't have one
2. Create a new repository (e.g. `buildblockagency-site`)
3. Upload `index.html` to the repo
4. Go to **Settings → Pages → Source → Deploy from a branch → main → / (root)**
5. Your site will be live at `https://yourusername.github.io/buildblockagency-site`
6. Custom domain: add it under **Settings → Pages → Custom domain**

### Option 3 — Hostinger / GoDaddy / Bluehost / Any Shared Host

1. Log into your hosting control panel
2. Open **File Manager** and navigate to `public_html/`
3. Upload `index.html`
4. Done — your site is live at your domain

### Option 4 — Any VPS or Server (nginx example)

```bash
# Copy the file to your web root
scp index.html user@yourserver:/var/www/html/index.html

# Make sure nginx is serving it
sudo systemctl restart nginx
```

---

## Contact Form Setup

The form currently has a client-side simulation (shows a success message). To make it actually send emails, choose one:

### Formspree (Easiest, Free tier available)

1. Sign up at [formspree.io](https://formspree.io)
2. Create a new form → get your endpoint URL (e.g. `https://formspree.io/f/xabcdef`)
3. In `index.html`, update the `<form>` tag:

```html
<form action="https://formspree.io/f/YOUR_ID" method="POST">
```

4. Remove the `onsubmit="handleSubmit(event)"` attribute and the JS handler (or keep the JS and just add the action attribute — Formspree works both ways)

### Netlify Forms (Free if on Netlify)

Add `netlify` attribute to your form tag:

```html
<form name="contact" netlify netlify-honeypot="bot-field" onsubmit="handleSubmit(event)">
```

Then add a hidden input inside the form:

```html
<input type="hidden" name="form-name" value="contact" />
```

Submissions will show up in your Netlify dashboard under **Forms**.

---

## Custom Domain & SSL

Most hosting platforms give you a free SSL certificate (the padlock / HTTPS). On Netlify and GitHub Pages it's automatic. On shared hosting, look for **Let's Encrypt** in your control panel — it's free and one click.

---

## Making Changes

Everything is in `index.html`. The file is organized into clearly labeled sections with CSS comments:

- **CSS variables** at the top — change colors here: `--orange`, `--navy`, etc.
- **Sections** are labeled with `<!-- HERO -->`, `<!-- SERVICES -->`, etc.
- **Pricing** — update the numbers directly in the HTML
- **Copy** — all real copy, no lorem ipsum — edit as needed

No build process. No npm. No dependencies. Just open the file, edit, save, re-upload.

---

## Tech Stack

- Pure HTML5 + CSS3 + vanilla JS
- [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts (loaded from CDN)
- No frameworks, no dependencies, no build step
- Responsive — works on mobile, tablet, and desktop
- Scroll animations via Intersection Observer API (native browser, no library)

---

## Performance Tips

- The Google Fonts link is the only external request. For max speed, you can self-host the font files instead.
- Images: none used (all icons are emoji or inline SVG) — this keeps load time fast.
- For production, run the HTML through [html-minifier](https://www.npmjs.com/package/html-minifier) to shave a few more KB.

---

## Questions?

This site was built for **Build Block Agency** — a contractor-focused digital marketing agency in Southern Maryland. 

Edit freely. Make it yours. Go get those leads. 🔧
