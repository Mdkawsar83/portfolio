# Uploading this project to GitHub (one-time, ~2 minutes)

The repository already exists and is public: **https://github.com/Mdkawsar83/portfolio**

It currently contains only `README.md`, `.gitignore` and this file. The website files have to be
uploaded from the project folder on your computer, because image and document files (`.png`, `.pdf`,
`.docx`) can only be transferred file-by-file from your machine.

## What to upload

Open the project folder — the one the Coderr builder is working in:

```
…/AppData/builder/chat_1791951134856_rvhr36
```

Then upload **everything inside it**, except the `.coderr` folder (that is Coderr's internal
workspace metadata and should not be published):

| Item | What it is |
| --- | --- |
| `index.html` | Home page |
| `about.html` | About, education, skills, areas of interest |
| `projects.html` | Project index (with filters) |
| `project-nmos.html`, `project-cmos.html`, `project-fir.html` | The three case studies |
| `experience.html` | Experience, activities, certificates, CV section |
| `contact.html` | Contact details + form |
| `css/styles.css` | The whole design system |
| `js/` | `main.js`, `home.js`, `about.js`, `projects.js`, `experience.js`, `gallery.js`, `contact.js` |
| `assets/` | Profile photo, diagrams, icons, `assets/files/Md_Kawsar_CV.pdf` and `assets/files/projects/` reports |
| `icons/` | Generated app icons |
| `icon.svg`, `manifest.json` | App icon and web-app manifest |
| `README.md`, `.gitignore` | Already on GitHub — leave them as they are |

## How

1. Go to **https://github.com/Mdkawsar83/portfolio**
2. Click **Add file → Upload files**
3. Drag in the files and folders listed above (on Windows, turn on *View → Show → Hidden items*
   only if you want to include `.gitignore`, which is already there — not required)
4. Click **Commit changes**

## Publish the site (optional)

1. Repository → **Settings** → **Pages**
2. *Build and deployment → Source*: **Deploy from a branch**
3. Branch **main**, folder **/ (root)** → **Save**
4. After a minute the site appears at **https://mdkawsar83.github.io/portfolio/**

> On GitHub Pages the Coderr contact-form SDK is not available. See section 4 of `README.md` for the
> free form services (Formspree / FormSubmit) and the single function to change in `js/contact.js`.
