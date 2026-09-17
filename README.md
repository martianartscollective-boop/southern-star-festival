# Southern Star Festival — Setup Guide

## Read this first: what went wrong last time

Two things broke the last deploy, and both are easy to avoid:

**1. The `admin` folder got flattened.** When files were uploaded to GitHub, the two files inside `admin/` landed loose in the main folder instead. That made the admin panel's loader become your homepage — so visitors saw a blank screen instead of the festival site. Step 3 below has the fix.

**2. Netlify had a build command it shouldn't have.** Something put `cecil build` in the build settings. Your site has nothing to build — it's plain files that just get served. The included `netlify.toml` now overrides that automatically, but Step 6 has you clear it out properly too.

## What the files do

| File | What it is |
|---|---|
| `index.html` | The festival website itself. You won't need to touch this. |
| `content.json` | All your words, prices, photos, lineup. Edited through `/admin`, not by hand. |
| `admin/index.html` | Loads the editor. **Must stay inside the `admin` folder.** |
| `admin/config.yml` | Tells the editor which fields to show you. **Must stay inside `admin`.** |
| `netlify.toml` | Tells Netlify not to try building anything. Prevents the error above. |

---

## Setup

### Step 1 — Create a free GitHub account
Go to github.com and sign up. GitHub just stores your website's files.

### Step 2 — Create a repository
Click the green **New** button. Name it `southern-star-festival`. Leave the rest default and click **Create repository**.

### Step 3 — Upload the files (the important part)

Unzip the download first. Then upload in **two separate rounds** so the folder survives:

**Round 1 — the loose files:**
1. On your repo page, click **Add file → Upload files**
2. Drag in ONLY these four: `index.html`, `content.json`, `netlify.toml`, `README.md`
3. Click **Commit changes**

**Round 2 — the admin folder:**
1. Click **Add file → Create new file**
2. In the filename box, type exactly: `admin/index.html` — typing the `/` creates the folder automatically
3. Open `admin/index.html` from your unzipped download in Notepad/TextEdit, copy everything, paste it into the big box
4. Click **Commit changes**
5. Repeat for the second file: **Add file → Create new file**, name it `admin/config.yml`, paste in the contents of `admin/config.yml`, commit

**Check your work:** your repo should show a folder named `admin` alongside the loose files. If you see `config.yml` sitting loose in the main list, the flattening happened again — delete it and redo Round 2.

### Step 4 — Create a free Netlify account
Go to netlify.com and click **Sign up with GitHub** — this links them automatically.

### Step 5 — Deploy
Click **Add new site → Import an existing project → Deploy with GitHub**, allow access, pick `southern-star-festival`.

On the settings screen, **leave the build command and publish directory empty.** Click **Deploy**. In a minute you'll get a link like `chipper-narwhal-123.netlify.app` — open it and you should see your festival site with the sunset banner.

### Step 6 — Clear any leftover build settings
Go to **Site configuration → Build & deploy → Build settings → Configure**. Make sure the build command is empty (or says `echo`) and publish directory is `.` or empty. If `cecil build` or `_site` is in there, delete it and save. The `netlify.toml` already overrides this, but clearing it prevents confusion later.

### Step 7 — Point your domain at it
**Site configuration → Domain management → Add a domain.** Enter your domain. Netlify shows you 1–2 DNS records — copy them, then log in wherever you bought your domain, find **DNS settings**, and add those records exactly. Takes anywhere from minutes to a few hours to switch over.

### Step 8 — Turn on your private login
1. **Site configuration → Identity → Enable Identity**
2. Under **Registration**, set it to **Invite only** — this stops anyone else from making an account
3. Scroll to **Services → Git Gateway → Enable Git Gateway** — this is what saves your edits back to GitHub
4. **Identity → Invite users** → enter your own email
5. Check your inbox, click the link, set a password

### Step 9 — Start editing
Go to `yourdomain.com/admin` and log in.

---

## Editing your site

Everything happens at `yourdomain.com/admin`. Regular visitors never see a login button anywhere — `/admin` isn't linked from the site, and it's hidden from Google search.

**Text:** click any field, type, click **Publish**. Live in about a minute.

**Photos:** click the image field, then drag a photo in from your computer or click to browse. Works from your phone's photo library too.

**Reordering:** lineup slots, schedule rows, ticket tiers, and slideshow photos all have drag handles — grab and drag to reorder.

**Adding/removing:** each of those lists has an **Add** button and a delete option, so you can add a 7th lineup slot or a camping ticket tier without touching code.

---

## Turning on ticket sales (Universe)

The site works fine before tickets go on sale — it shows a placeholder until you fill this in.

1. Set up your event at universe.com with your ticket types and prices
2. Go to **My Events → your event → Embeddable Widgets** → pick the **Ticket Widget** → click **Copy**
3. In `/admin`, find **Ticket Checkout (Universe)** → paste into **"Universe widget embed code"** → **Publish**

Buyers now check out without leaving your site.

**Backup option:** if you have your public Universe event link but not the embed code yet, paste the link into **"Universe event page link"** instead. The site will show a "Buy Tickets on Universe" button until you swap in the real widget.

**On fees:** Universe charges a per-ticket service fee on paid tickets — free tickets cost nothing to process, so your Kids tickets are free either way. In Universe's settings you choose whether buyers pay that fee on top, or you absorb it into your price. Since Cheatham Street Music Foundation is a nonprofit, contact Universe about their registered-charity rates before you launch.

---

## If something looks wrong

**Homepage is blank or shows a login box** — the `admin` folder got flattened. Check your repo: if `config.yml` or a second `index.html` is loose in the main list, delete them and redo Step 3, Round 2.

**Build fails with "command not found"** — a build command is set that shouldn't be. Redo Step 6.

**Edits don't show up** — make sure you clicked **Publish** (not just saved a draft), then wait a minute and refresh. If it still doesn't, check Git Gateway is enabled (Step 8.3).

**Can't log in to /admin** — Identity and Git Gateway both need to be on, and you need to have accepted your own invite email.

## Changing the design

Colors, fonts, and layout live in `index.html`. That one needs a person who writes code — come back to Claude for those. Words, prices, photos, and ordering are all yours through `/admin`.
