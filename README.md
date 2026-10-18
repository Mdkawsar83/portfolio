# Md Kawsar — Microelectronics Engineering Portfolio

A lightweight, premium dark-themed personal website built with **plain HTML5, CSS3 and vanilla JavaScript**.
No frameworks, no build step, no npm install — open `index.html` and it runs.

The site supports three goals:

1. **Master's degree and scholarship applications** — a clear academic profile, education record and areas of interest.
2. **Academic networking and future research opportunities** — an honest "areas being explored" section, contact form and LinkedIn.
3. **Engineering job and internship applications** — technical skills, detailed project pages and a professional experience section.

---

## 1. What is in the project

```
portfolio/
├── index.html              Home — hero, what I work on, areas of interest, featured projects, contact CTA
├── about.html              About me, education, technical skills, areas of interest
├── projects.html           All projects (rendered from a JS data structure, with filters)
├── project-nmos.html       NMOS device simulation with Silvaco TCAD — full case study
├── project-cmos.html       CMOS inverter / VLSI design flow (Cadence Virtuoso, gpdk045) — full case study
├── project-fir.html        FIR digital filter project using MATLAB — full case study
├── experience.html         Professional experience, activities/certificates and the CV section
├── contact.html            Contact details + working contact form
├── css/
│   └── styles.css          The whole design system (colours, type, spacing, layout, components)
├── js/
│   ├── main.js             Shared: mobile menu, sticky header, active nav, scroll reveals,
│   │                       back-to-top, image fallbacks, lightbox, CV link guard, year stamp
│   ├── home.js             Home-page behaviour
│   ├── about.js            About-page behaviour (section highlighting, chips)
│   ├── projects.js         The PROJECTS data structure + project grid rendering and filters
│   ├── experience.js       Certificate gallery + CV section behaviour
│   ├── gallery.js          Accessible lightbox for the certificate gallery
│   └── contact.js          Contact-form validation, submission and status states
├── assets/
│   ├── icons/              favicon.svg
│   ├── images/
│   │   ├── md-kawsar-profile.png     Your profile photo, shown unedited in the hero
│   │   ├── profile-placeholder.svg   Monogram fallback used only if the photo fails to load
│   │   ├── pattern-circuit.svg       Tiling circuit-trace background pattern
│   │   ├── projects/                 Diagram placeholders for the project pages
│   │   └── activities/               Certificate card placeholders + page artwork
│   └── files/
│       ├── Md_Kawsar_CV.pdf          The CV served by every Download CV button
│       ├── projects/                 The real coursework reports linked from the project pages
│       ├── README.md                 Instructions for the CV and reports
│       └── PUT_YOUR_CV_HERE.txt      Folder note
├── icon.svg                App icon (flat MK monogram)
├── manifest.json           Auto-generated app manifest — do not edit by hand
└── README.md               This file
```

**Content is separated from presentation** where it matters: the project list lives in one clearly commented
array at the top of `js/projects.js`, and everything personal is plain HTML with clearly marked placeholders.

---

## 2. Running it locally

No installation is required.

- **Simplest:** double-click `index.html` — it opens in your browser. Most things work; the contact form and a
  few browser security features behave better over a local server.
- **Recommended (local server):** from the project folder run one of these, then open the printed address
  (e.g. `http://localhost:8000`):

```bash
python3 -m http.server 8000        # Python 3
npx serve .                        # if you have Node.js
php -S localhost:8000              # if you have PHP
```

---

## 3. How to edit your information

Everything you need to change is marked in the HTML. Search the project for `[Add` and for
`placeholder-note` — those are the slots waiting for your real details.

| What to update | Where |
| --- | --- |
| Your profile photo | Your photograph is already in place at `assets/images/md-kawsar-profile.png` and is shown unedited in the hero. To swap it, replace that file with your new photo (keep the same name, or update the `src` in `index.html`). |
| Your CV | Already in place at `assets/files/Md_Kawsar_CV.pdf` — every Download CV button serves it. Replace that file to update the CV everywhere. |
| GitHub profile | Already linked — every GitHub link in the site points to `https://github.com/Mdkawsar83`. |
| Study period, expected graduation, courses, achievements | `about.html` → `#education` — the dashed placeholder rows. Delete a row if it does not apply. |
| Job details (dates, responsibilities) | `experience.html` → `#experience` — Marketing Executive at PencilEdu, January 2026 – present, already filled in. |
| Project reports | `assets/files/projects/` — the submitted NMOS, CMOS/VLSI and FIR reports are linked from the matching project pages. |
| School name, volunteering details, certificate titles and dates | `experience.html` → `#activities`. |
| Certificate images | Replace `assets/images/activities/certificate-gala-2025.svg` and `-2026.svg` with scans (JPG/PNG) and update the `src`/`data-lightbox-src` values. |
| Project figures | The three `project-*.html` pages and the `PROJECTS` array in `js/projects.js`. Replace every placeholder figure with your own exported plot and delete the slot if it is not applicable. |
| Skills | `about.html` → `#skills`. Add a new tool by copying one `<li>` inside the matching category. |
| Add a whole new project | Add an entry to the `PROJECTS` array in `js/projects.js` and copy one `project-*.html` page as a template. |
| Colours, fonts, spacing | The design tokens at the top of `css/styles.css` (`:root`). |
| Social preview / canonical URL | Already set to `https://mdkawsar83.github.io/portfolio/` in the `<!-- SEO -->` block of every page. Update them if you rename the repository or add a custom domain. |

> **Authenticity note:** the site deliberately contains **no invented grades, dates, employer names, project
> results, publications or statistics**. Results and screenshots are only shown once you provide them, so
> nothing on the page can be challenged in an application.

---

## 4. The contact form — how messages are actually delivered

A plain HTML form cannot deliver email by itself. This project ships with a **real, working** delivery path:

- `contact.html` loads the Coderr SDK (`https://coderr.site/sdk/coderr.js`) and `js/contact.js` calls
  `coderr.forms.submit('portfolio-contact', data)`.
- Messages are stored privately for the site owner and are read in the **Coderr dashboard → Forms**.
- There is a hidden honeypot field (`_hp`) for spam, plus rate-limit handling (`too_many_requests`) and an
  honest error state — it never shows a fake "message sent" confirmation.
- Every failure state offers a **mailto fallback** link (`mdkawserbiswas83@gmail.com`) so a visitor can always
  reach you.

**If you host somewhere else (for example GitHub Pages)** where the SDK is not available, swap the single
`sendMessage()` function in `js/contact.js` for a form service. All of these are free and need no backend:

1. **Formspree** — create a form at formspree.io, then post to `https://formspree.io/f/YOUR_FORM_ID`.
2. **FormSubmit** — no signup: post to `https://formsubmit.co/mdkawserbiswas83@gmail.com`.
3. **Netlify Forms** — add `netlify data-netlify="true"` to the `<form>` tag and deploy on Netlify.
4. **Your own endpoint** — post JSON to any server you control.

In every case keep the validation and status handling that is already in `js/contact.js`, and remember:
**never put a secret API key in browser JavaScript.** Only public form IDs belong in a static site.

---

## 5. Publishing with GitHub Pages

### 5.1 Your GitHub account and repository

Both already exist:

* Account: <https://github.com/Mdkawsar83>
* Repository: <https://github.com/Mdkawsar83/portfolio> (public, so GitHub Pages can serve it on the free plan)

If you ever want the repository private: **Settings → General → scroll to Danger Zone → Change visibility**.
Note that GitHub Pages needs a public repository on the free plan.

### 5.2 Upload the site files (only once)

See section 5.3 below.

### 5.3 Upload the files

**Option A — the website (no terminal):**

1. In your repository click **Add file → Upload files**.
2. Drag in *everything inside this folder* (the HTML files, `css/`, `js/`, `assets/`, `README.md`, `icon.svg`, `.gitignore`).
3. Commit the changes.

**Option B — Git from the terminal:**

```bash
cd portfolio
git init
git branch -M main
git add .
git commit -m "Initial portfolio"
git remote add origin https://github.com/Mdkawsar83/portfolio.git
git pull --rebase origin main
git push -u origin main
```

Then for every later update:

```bash
git add .
git commit -m "Update projects"
git push
```

### 5.4 Turn on GitHub Pages

1. Repository → **Settings** → **Pages**.
2. Under *Build and deployment* → *Source*, choose **Deploy from a branch**.
3. Branch **main**, folder **/ (root)** → **Save**.
4. Wait a minute; your site appears at
   `https://mdkawsar83.github.io/portfolio/`
   (or at the root `https://mdkawsar83.github.io/` if you rename the repository to `Mdkawsar83.github.io`).

> The contact form's Coderr SDK path only works inside Coderr hosting. On GitHub Pages use one of the form
> services in section 4 — a small change in `js/contact.js`.

### 5.5 Update the SEO URLs

The canonical, Open Graph and Twitter URLs in every page are already filled in with
`https://mdkawsar83.github.io/portfolio/`. If you rename the repository or add a custom domain, replace that
string in the `<!-- SEO -->` block of each page — that is what search engines and link previews use.

### 5.6 Add a custom domain later (optional)

1. Buy a domain (Namecheap, Cloudflare, Porkbun…).
2. Repository → **Settings** → **Pages** → *Custom domain*, enter `www.yourdomain.com`.
3. At your DNS provider add a `CNAME` record for `www` pointing to `mdkawsar83.github.io`, and for the bare
   domain four `A` records: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`.
4. Wait for DNS, then tick **Enforce HTTPS**.

### 5.7 Keeping it up to date

Update the site whenever something real changes: a finished simulation, a new result, a new certificate, a new
skill, or a new employer. Keep placeholders out of the published version — if a detail is missing, delete that
row instead of filling it with a guess.

---

## 6. Manual testing checklist

Run through this after your edits, on a desktop browser and on a phone.

- [ ] All eight navigation links open the right page/section; the current page is highlighted.
- [ ] On a phone (or a narrow window) the menu button opens and closes the menu; Escape closes it; the links work.
- [ ] The hero shows your photo (or the monogram placeholder) — never a broken image.
- [ ] Every project card opens its detail page, and the "next project" links work.
- [ ] Project figures open in the lightbox and close with Escape / the close button.
- [ ] The Download CV buttons download `Md_Kawsar_CV.pdf`.
- [ ] LinkedIn, email and GitHub links open correctly (and the GitHub link points at **your** account).
- [ ] The contact form: empty submit shows errors, an invalid email shows an error, a valid message submits and
      shows an honest success state; the mailto fallback works.
- [ ] Tab through the page — every control has a visible focus ring and can be reached by keyboard.
- [ ] With "reduce motion" enabled in your OS, animations are minimal.
- [ ] Browser console is free of errors on every page.
- [ ] Check the layout at ~390 px (phone), ~768 px (tablet) and 1280 px+ (desktop) — no horizontal scrolling.

---

## 7. Credits and licence

Design and code written for Md Kawsar. Fonts: Space Grotesk, Inter and JetBrains Mono (Google Fonts, OFL)
with system-font fallbacks (Segoe UI, Arial, Consolas) so the site renders correctly even if the font
request cannot be reached. All diagrams and the profile placeholder are original SVG drawn for this site —
replace them with your own screenshots and photos.
