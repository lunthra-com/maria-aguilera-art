# Deploy via GitHub → Netlify (continuous deploy, ~15 min one-time setup)

After this is done, every `git push` to `main` auto-publishes the site in ~30 seconds. No more drag-and-drop.

---

## Step 1 — Fill in the placeholders (5 min)

Open `index.html` and find/replace these tokens. They appear multiple times — use Find & Replace All in your editor:

| Placeholder      | Replace with                                                |
| ---------------- | ----------------------------------------------------------- |
| `[ARTIST NAME]`  | Mom's full name as she signs work (e.g., *Maria Aguilera*)  |
| `[FIRST NAME]`   | Just first name (e.g., *Maria*)                             |
| `[CITY, STATE]`  | Where she paints (e.g., *Los Angeles, CA*)                  |
| `[VOTE_URL]`     | Her direct vote link from peoplesartist.org                 |
| `[SITE_URL]`     | The final site URL (come back and fill in after Step 4)     |
| `[EMAIL]`        | Contact email                                               |

Update the **About the Artist** section with her real bio. Update each painting's title + medium line.

Drop image files into `images/` (see `images/README.txt` for filenames).

---

## Step 2 — Create the GitHub repo (3 min)

### Option A: GitHub web UI (no command line)

1. Go to **https://github.com/new**
2. Name: `mom-art-site` (or `maria-aguilera-art` — whatever you want, this is the repo URL)
3. Visibility: **Public** (Netlify free tier requires public, OR connect with GitHub login for private — public is simpler)
4. **Do NOT** check "Add a README" — we already have one
5. Click **Create repository**
6. On the next page, click **uploading an existing file**
7. Drag the entire contents of the `mom-art-site` folder (the files, not the folder itself — open it first, select all, drag) onto the page
8. Scroll down, type a commit message ("initial site"), click **Commit changes**

### Option B: Git CLI (faster if you've used it before)

```bash
cd path/to/mom-art-site
git init
git add .
git commit -m "initial site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/mom-art-site.git
git push -u origin main
```

(Create the empty repo on GitHub first with no README/gitignore/license.)

---

## Step 3 — Connect Netlify to the repo (4 min)

1. Go to **https://app.netlify.com/start** (sign up with GitHub — easiest)
2. Click **Import from Git** → **GitHub**
3. Authorize Netlify to read your GitHub
4. Pick the `mom-art-site` repo
5. Build settings: leave everything blank (the included `netlify.toml` handles config) — publish directory will auto-detect as `.`
6. Click **Deploy site**
7. Wait ~30 seconds — you'll get a URL like `https://amazing-curie-12345.netlify.app`
8. **Site configuration → Change site name** → pick something readable (e.g., `maria-aguilera-art`)

From now on, every push to `main` auto-deploys. No further action needed for content updates.

---

## Step 4 — Custom domain (~$10/year, 5 min)

1. Buy at **https://www.cloudflare.com/products/registrar/** — search for the domain you want
   - Suggested: `firstnamelastname.art` (the `.art` TLD is fitting and ~$15/yr) or `firstnamelastname.com` (~$10/yr)
2. In Netlify: **Domain management → Add a domain** → paste the domain
3. Netlify shows you DNS records to add (a CNAME and/or A records)
4. In Cloudflare: **DNS → Records → Add record** for each line Netlify gave you
   - Set Cloudflare proxy status to **DNS only** (gray cloud, not orange) for the first hour while SSL provisions; you can switch back to proxied afterward if you want
5. SSL auto-provisions in ~5 minutes — you'll see a green padlock when ready

---

## Step 5 — Update the site URL and re-push (2 min)

1. Open `index.html`, find `[SITE_URL]`, replace with your real URL (`https://yourdomain.com`)
2. Commit + push:
   - **Web UI:** edit the file directly on github.com, commit
   - **CLI:** `git add index.html && git commit -m "set site url" && git push`
3. Netlify rebuilds in ~30 seconds — share buttons now work correctly

---

## Step 6 — Launch (May 4)

Text/post the link. Voting opens **May 4** and runs to **August 6**.

---

## Updating later

**Add a painting:**
1. Drop the image file into `images/`
2. Copy one `.piece` block in `index.html`, update title + image filename
3. Commit + push → live in 30 seconds

**Edit text:**
1. Edit `index.html` (web UI works fine — github.com → click the file → pencil icon)
2. Commit → live in 30 seconds

**Or ask Claude:** once the GitHub MCP is connected here, you can say *"add a new painting called Sunset to mom's site, image attached"* and I'll commit it for you.

---

## Fallback: drag-and-drop deploy (no Git)

If GitHub feels like too many steps, you can skip Steps 2–3 entirely:

1. Go to **https://app.netlify.com/drop**
2. Drag the `mom-art-site` folder onto the page
3. Done — get a URL immediately

Trade-off: every future update means re-dragging the whole folder. The Git path is worth the one-time setup if mom plans to add paintings often during the contest.
