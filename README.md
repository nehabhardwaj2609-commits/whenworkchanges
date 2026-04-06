# When Work Changes
**whenworkchanges.co.nz**

Research into professional identity and AI-driven role change in Aotearoa New Zealand.
Neha Bhardwaj — Masters of Technological Futures, AcademyEX, Generation 27.

---

## Project structure

```
whenworkchanges/
├── index.html            Home page
├── get-involved.html     Participant recruitment page
├── resources.html        Reading list and blog
├── proposal.html         Research proposal (Gamma embed)
├── css/
│   └── style.css         Shared styles
├── js/
│   └── main.js           Shared JavaScript
├── images/
│   └── neha.jpg          Your photo — add this file
└── README.md             This file
```

---

## Before you deploy — checklist

- [ ] Add your photo as `images/neha.jpg`
- [ ] Update the `<img src="neha.jpg"` path in `get-involved.html` to `images/neha.jpg`
- [ ] Confirm the Gamma embed on `proposal.html` loads correctly

---

## Deployment: VS Code → GitHub → Cloudflare Pages

### Step 1 — Open this folder in VS Code

File → Open Folder → select the `whenworkchanges` folder

Install the recommended extensions if prompted:
- **Live Server** (ritwickdey.LiveServer) — lets you preview the site locally before pushing

### Step 2 — Preview locally first

Right-click `index.html` → Open with Live Server

Your browser opens at `http://127.0.0.1:5500` — this is your local preview.
Check all four pages look right before pushing to GitHub.

---

### Step 3 — Initialise Git and push to GitHub

Open the terminal in VS Code (Terminal → New Terminal) and run:

```bash
git init
git add .
git commit -m "Initial site launch"
```

Now go to **github.com**:
1. Click **+** → New repository
2. Name: `whenworkchanges`
3. Visibility: Public
4. Do NOT tick "Add a README" — you already have one
5. Click **Create repository**

GitHub shows you two lines to run. Copy and paste them into your terminal:

```bash
git remote add origin https://github.com/YOUR-USERNAME/whenworkchanges.git
git branch -M main
git push -u origin main
```

Your files are now on GitHub.

---

### Step 4 — Connect Cloudflare Pages

1. Log into **dash.cloudflare.com**
2. Left menu → **Workers & Pages** → **Pages**
3. Click **Create a project** → **Connect to Git**
4. Sign in with GitHub → select `whenworkchanges` repository
5. Click **Begin setup**

Build settings:
- **Production branch:** `main`
- **Build command:** *(leave empty)*
- **Build output directory:** *(leave empty)*

Click **Save and Deploy** — takes about 60 seconds.

You get a preview URL like `https://whenworkchanges.pages.dev` — check it works.

---

### Step 5 — Add your custom domain

In your Cloudflare Pages project:
1. Click **Custom domains** tab
2. Click **Set up a custom domain**
3. Enter `whenworkchanges.co.nz`
4. Click **Continue** → **Activate domain**

Because your domain is already managed by Cloudflare, the DNS record is created automatically. Your site will be live at `whenworkchanges.co.nz` within a few minutes.

---

## Making changes after launch

Every time you update a file:

```bash
git add .
git commit -m "Brief note about what changed"
git push
```

Cloudflare automatically redeploys within 60 seconds. No manual steps needed.

---

## Adding your video

When your video is recorded and uploaded to YouTube as unlisted:

1. On YouTube: **Share** → **Embed** → copy the iframe code
2. Open `get-involved.html` in VS Code
3. Find the comment: `<!-- Replace this div with YouTube embed when video is ready:`
4. Delete the entire `<div class="video-placeholder">...</div>` block
5. Paste your YouTube iframe with these styles added:

```html
<iframe
  width="100%"
  height="100%"
  style="display:block; aspect-ratio:16/9; border:none"
  src="https://www.youtube.com/embed/YOUR_VIDEO_ID"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen>
</iframe>
```

Then push:
```bash
git add get-involved.html
git commit -m "Add recruitment video"
git push
```

---

## Adding a contact form (when ready)

Free option: **Formspree** (formspree.io) — 50 submissions/month free, no server needed.

1. Create account at formspree.io
2. New form → get your form ID (looks like `xabcdefg`)
3. In `get-involved.html`, replace the email block with:

```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
  <div class="form-group">
    <label for="name">Your name</label>
    <input type="text" id="name" name="name" required>
  </div>
  <div class="form-group">
    <label for="email">Your email</label>
    <input type="email" id="email" name="_replyto" required>
  </div>
  <div class="form-group">
    <label for="message">Anything you'd like me to know? (optional)</label>
    <textarea id="message" name="message"></textarea>
  </div>
  <input type="hidden" name="_subject" value="When Work Changes — Expression of Interest">
  <input type="text" name="_gotcha" style="display:none">
  <button type="submit" class="btn-gold">I'm interested →</button>
</form>
```

Push the change and it's live.

---

## Common commands

| Task | Command |
|---|---|
| Push changes live | `git add . && git commit -m "note" && git push` |
| Check what's changed | `git status` |
| Undo last change (before push) | `git checkout -- filename.html` |

---

*Built for whenworkchanges.co.nz · Neha Bhardwaj · 2026*
