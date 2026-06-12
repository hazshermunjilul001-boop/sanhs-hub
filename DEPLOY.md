# SANHS Teacher Innovation Hub
## Deployment Guide — Cloudflare Pages (Free Tier)

---

## 📁 What's in this package
- `index.html` — The full single-file web app
- `wrangler.toml` — Cloudflare Pages config
- `DEPLOY.md` — This guide

---

## ✏️ STEP 1 — Inject your own descriptions (optional before deploying)

Open `index.html` and search for the comment tag:
```
<!-- ✏️ INJECT DESCRIPTION HERE
```
There are **7 of these**, one per app card. Replace the placeholder text between the `<p class="card-desc">` tags with your own description. You can also leave the existing ones as-is.

---

## 🌐 STEP 2 — Deploy to Cloudflare Pages (3 ways — pick one)

---

### ✅ Option A: Drag-and-Drop (Easiest, no CLI needed)

1. Go to **https://pages.cloudflare.com**
2. Sign in (or create a free account)
3. Click **"Create a project"** → **"Direct Upload"**
4. Give the project a name, e.g., `sanhs-teacher-hub`
5. **Drag and drop the entire `sanhs-hub` folder** into the upload box
6. Click **"Deploy site"**
7. Done! Your site will be live at:
   `https://sanhs-teacher-hub.pages.dev`

---

### ✅ Option B: GitHub + Auto-Deploy (Best for future updates)

1. **Create a GitHub repo** (free):
   - Go to https://github.com/new
   - Name it `sanhs-teacher-hub`, set to Public
   - Click "Create repository"

2. **Upload your files** to the repo:
   - Click "uploading an existing file"
   - Drag in `index.html` and `wrangler.toml`
   - Click "Commit changes"

3. **Connect to Cloudflare Pages**:
   - Go to https://pages.cloudflare.com
   - Click "Create a project" → "Connect to Git"
   - Select your GitHub repo `sanhs-teacher-hub`
   - **Build settings**: Leave everything blank (no framework, no build command)
   - Set **Output directory** to `/` (root)
   - Click "Save and Deploy"

4. From now on, every time you edit `index.html` on GitHub, Cloudflare will **auto-redeploy** in ~30 seconds.

---

### ✅ Option C: Wrangler CLI

```bash
npm install -g wrangler
wrangler login
cd sanhs-hub
wrangler pages deploy .
```

---

## 🔧 STEP 3 — Custom Domain (Optional, also free)

If you want a URL like `hub.sanhs.edu.ph` or `tools.sanhs.ph`:

1. In Cloudflare Pages → your project → **Custom Domains**
2. Click "Set up a custom domain"
3. Enter your domain and follow DNS instructions

If you don't have a domain, your free URL `sanhs-teacher-hub.pages.dev` works perfectly.

---

## 🖼️ STEP 4 — Adding Real App Screenshots (Optional Upgrade)

The cards currently use **CSS-animated UI mockups** that simulate 3 preview states per app. If you want real screenshots later:

1. Take 3 screenshots of each app (different screens/states)
2. Export them as `.webp` format (use https://squoosh.app — free)
3. Name them like: `lrhub-1.webp`, `lrhub-2.webp`, `lrhub-3.webp`
4. Upload to your project folder
5. Replace the `<div class="card-thumb-frame">` blocks with `<img src="lrhub-1.webp">` tags

---

## 📝 Quick Description Cheat Sheet

Search for `INJECT DESCRIPTION HERE` in `index.html` — you'll find 7 spots:

| Card | Search Anchor |
|------|---------------|
| Learning Resource Hub | `data-app="lrhub"` |
| SMART SANHS Enrollment | `data-app="enrollment"` |
| Dept Heads Monitoring | `data-app="depthead"` |
| TeacherHub PH | `data-app="teacherhub"` |
| ILAW Lesson Plan | `data-app="ilaw"` |
| LIS (DepEd national) | `data-app="lis"` |
| Ependot | `data-app="ependot"` |

---

## 💡 Tips

- The site is fully responsive (mobile, tablet, desktop)
- All animations respect `prefers-reduced-motion` for accessibility
- Each card has an animated 3-frame app preview that cycles automatically
- Hover any card to see the **"Launch App"** button appear
- The footer credits **HAFOM** automatically

---

*Built for SANHS · SY 2026–2027 · DepEd Region XI*
