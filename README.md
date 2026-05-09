# kasrafarivari.org — deployment guide

This is the source of your personal site at **kasrafarivari.org**. This README walks you through getting it live, end to end. No coding experience required — every step is point-and-click.

If you get stuck, save where you are and ask me.

---

## What's in this folder

```
kasrafarivari-org/
├── index.html              ← Homepage
├── style.css               ← Site styling
├── headshot.jpg            ← YOUR PHOTO — you add this (see Step 0)
├── CNAME                   ← Tells GitHub your domain
├── robots.txt              ← Tells search engines they can index everything
├── sitemap.xml             ← Map of your site for Google
├── 404.html                ← Page shown for broken URLs
├── README.md               ← (this file)
└── blog/
    ├── index.html          ← Blog landing page
    ├── notes-from-a-pm-learning-ai/index.html
    ├── how-i-use-ai-to-write-better-prds/index.html
    ├── ai-user-research-synthesis/index.html
    ├── evaluating-ai-features/index.html
    └── ai-tools-i-use-every-day/index.html
```

---

## Step 0 — Save your photo (1 min)

Save the Switch headshot photo as **`headshot.jpg`** in this folder:

`/Users/kfarivari/Website/kasrafarivari-org/headshot.jpg`

The HTML already references this filename. If you save it as anything else (`.png`, `IMG_3752`, etc.), the photo won't show up.

If your photo is HEIC, convert it first. In macOS Preview: open it, File → Export → Format: JPEG → save as `headshot.jpg`.

Recommended size: at least 400x400 pixels. Square crop works best (the site shows it as a circle).

---

## Step 1 — Create the GitHub repository (5 min)

1. Go to **github.com** and log in.
2. Click the **+** in the top-right → **New repository**.
3. Repository name: enter exactly **`kasrafarivari.github.io`** (replace `kasrafarivari` with your actual GitHub username if different — it must match your username, lowercase).
4. Description: "Personal site and blog" (optional).
5. Set to **Public**. (Public means readable by everyone — it does NOT mean anyone can edit. Only you can change anything unless you invite collaborators.)
6. Check **"Add a README file"**.
7. Click **Create repository**.

You should now see an empty repo with a default README.

---

## Step 2 — Upload all the files (5 min)

1. On your repo page, click **Add file → Upload files**.
2. Open Finder, navigate to `/Users/kfarivari/Website/kasrafarivari-org/`.
3. Select **all the files inside** (don't drag the folder itself — drag the contents). Use Cmd+A inside the folder to select all.
4. Drag everything into the GitHub upload area in your browser.
5. Wait for all files to upload (you'll see a green checkmark next to each).
6. Scroll down to "Commit changes". The default message is fine.
7. Click **Commit changes**.

When it's done, you should see your files listed in the repo: `index.html`, `style.css`, the `blog/` folder, etc.

**Important:** make sure the `blog` folder uploaded correctly. Click into it — you should see 6 entries (one `index.html` and five subfolders for each post). If the subfolders didn't upload, drag those folders separately.

---

## Step 3 — Turn on GitHub Pages (2 min)

1. In your repo, click **Settings** (top right of the repo page).
2. In the left sidebar, click **Pages**.
3. Under "Build and deployment", set:
   - Source: **Deploy from a branch**
   - Branch: **main** / **(root)** → click **Save**.
4. Wait ~1 minute. Refresh the page.
5. You should see a green message: "Your site is live at `https://[your-username].github.io/`".

Click that link — your site is up. The custom domain is the next step.

---

## Step 4 — Point kasrafarivari.org at GitHub (15 min, mostly waiting)

You bought the domain at Namecheap. Here's how to point it at your new site.

1. Log in to **namecheap.com**.
2. Go to **Domain List** → find `kasrafarivari.org` → click **Manage**.
3. Click the **Advanced DNS** tab.
4. Delete any existing A records or CNAME records for `@` and `www` (use the trash icon).
5. Add **four new A records**, all with Host = `@`:

   | Type | Host | Value | TTL |
   |------|------|-------|-----|
   | A Record | @ | `185.199.108.153` | Automatic |
   | A Record | @ | `185.199.109.153` | Automatic |
   | A Record | @ | `185.199.110.153` | Automatic |
   | A Record | @ | `185.199.111.153` | Automatic |

6. Add **one CNAME record**:

   | Type | Host | Value | TTL |
   |------|------|-------|-----|
   | CNAME Record | www | `[your-username].github.io.` | Automatic |

   (Replace `[your-username]` with your actual GitHub username. Keep the trailing dot.)

7. Click the green checkmark to save each row.

Now back in your GitHub repo:

8. **Settings → Pages → Custom domain**: enter `kasrafarivari.org` → **Save**.
9. GitHub will check the DNS. This can take 5–30 minutes.
10. Once verified, the **Enforce HTTPS** checkbox becomes available — check it.

After 30–60 minutes, visit **https://kasrafarivari.org** — your site should load with HTTPS.

---

## Step 5 — Tell Google about it (10 min)

This is what makes Google start indexing your site quickly instead of taking weeks to discover it on its own.

1. Go to **search.google.com/search-console**.
2. Click **Add property** → **URL prefix** → enter `https://kasrafarivari.org`.
3. Choose verification method **HTML file**. Download the file Google gives you (e.g., `google1234abcd.html`).
4. Upload that file to your GitHub repo (same way as Step 2 — Add file → Upload files → drag → commit). It needs to live at the root of the repo, alongside `index.html`.
5. Wait 1–2 minutes for the file to deploy, then click **Verify** in Search Console.
6. Once verified, in Search Console go to **Sitemaps** in the left sidebar.
7. In the "Add a new sitemap" field, type `sitemap.xml` and click **Submit**.
8. Now go to **URL Inspection** at the top, enter `https://kasrafarivari.org/`, click **Request indexing**. Repeat for each blog post URL — there are 5.

Google won't index instantly. Expect 1–7 days for your homepage to show up in search results, and 1–4 weeks to start outranking the defamation site.

---

## Step 6 — Build the link graph (15 min)

This is the highest-leverage step for SEO. Update each of these profiles to link back to **kasrafarivari.org**. Google reads these links and uses them to confirm "this is the canonical entity":

- **LinkedIn** → Edit profile → Add `kasrafarivari.org` to your Contact info
- **About.me** → Add the URL
- **Crunchbase** → Add to "Personal Website"
- **Medium** → Settings → Customize your profile → Personal Website
- **GitHub** → Profile → Add to website field
- **X / Twitter** → Profile → Add to bio link

Also: add a link from your existing **kasra-farivari.com** site to **kasrafarivari.org** (in the "Online Profiles" section), and vice versa is already done in our footer.

---

## What to expect

- **Day 1:** Site is live. Google doesn't know about it yet.
- **Days 1–7:** Google crawls and indexes the homepage. You can see this in Search Console under "Coverage."
- **Weeks 2–4:** Posts start appearing in search results. Your name + blog post titles begin ranking.
- **Months 1–3:** With the link graph (Step 6) in place, kasrafarivari.org should appear on page 1 for "kasra farivari" searches, and likely pushes the defamation site further down.

If after 3 months it's still not ranking, the most likely fix is more backlinks — getting one editorial link from a real news/industry site is worth more than ten free profiles.

---

## Updating the site later

To edit a post or add a new one:

1. Go to your repo on github.com.
2. Click into the file you want to edit (e.g., `blog/ai-tools-i-use-every-day/index.html`).
3. Click the pencil icon (top right of the file view).
4. Make your edits in the browser.
5. Scroll down → **Commit changes**.

Site updates within ~1 minute.

To add a brand-new post: copy the whole folder of an existing post in the `blog/` directory, rename it, edit the content, and add it to `sitemap.xml` and the post lists in `index.html` and `blog/index.html`.

---

## Troubleshooting

**Site shows the GitHub README instead of my page.** You're missing or misnamed `index.html`. It must be at the root of the repo.

**Custom domain shows "DNS check unsuccessful".** Wait 30 more minutes — DNS propagation is slow. If it's still failing after an hour, double-check the A records and CNAME exactly match Step 4.

**Photo not showing.** The file must be at the root of the repo, named exactly `headshot.jpg` (lowercase, .jpg not .jpeg or .HEIC).

**HTTPS doesn't work.** GitHub auto-issues an SSL cert once DNS is verified. Wait 30 minutes, then try ticking "Enforce HTTPS" again.

**Site updated but I still see the old version.** Hard refresh: Cmd+Shift+R on Mac. Or wait a few minutes — GitHub Pages caches.
