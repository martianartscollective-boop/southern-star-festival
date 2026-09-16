# Southern Star Festival — Setup Guide

This site is now split into two pieces:

- `index.html` — the page itself (design, layout, code). You won't touch this again.
- `content.json` — all the actual words, prices, photos, and lineup slots. This is what you'll edit, through a friendly form at `yoursite.com/admin` — not by opening the file.

Nobody visiting your normal site will ever see a login button. `/admin` isn't linked from anywhere — you just have to remember the URL, and it requires an account that only you can create (see step 4).

## One-time setup (about 20 minutes)

**1. Put this folder on GitHub (free)**
- Create a free account at github.com if you don't have one.
- Create a new repository (e.g. "southern-star-festival") and upload every file in this folder, keeping the `admin` folder intact.

**2. Connect it to Netlify (free)**
- Create a free account at netlify.com.
- Click "Add new site" → "Import an existing project" → connect your GitHub account → choose your new repository → Deploy.
- In a minute or two you'll get a working `something.netlify.app` link — click it to confirm the site loads.

**3. Point your existing domain at it**
- In Netlify: Site settings → Domain management → Add a domain → enter your domain.
- Netlify will show you 1–2 DNS records to add. Go to wherever you bought your domain (GoDaddy, Namecheap, etc.), find DNS settings, and add those records.
- This can take up to a few hours to fully switch over, but usually it's much faster.

**4. Turn on the private admin login**
- In Netlify: Site settings → Identity → click "Enable Identity."
- Under Registration, set it to **"Invite only"** — this is the important part. It means no one can create their own account; only people you personally invite can ever log in.
- Scroll to Services → Git Gateway → click "Enable Git Gateway." (This is what lets the admin panel save your edits back to the site automatically.)
- Go to Identity → Invite users → enter your own email address. You'll get an email — click the link, set a password.

**5. Start editing**
- Go to `yourdomain.com/admin`
- Log in with the account you just made
- Edit any text, swap any photo, drag lineup/ticket/schedule items to reorder them, then hit **Publish**
- Your live site updates within about a minute — no re-uploading anything, and no need to come back to Claude for routine changes

## Setting up ticket sales (Universe)

Do this whenever you're ready — the site works fine before tickets go on sale.

**1.** Create a free account at universe.com and set up your Southern Star Festival event, adding your ticket types (General Admission, VIP, Kids) with their prices.

**2.** In Universe, go to **My Events** → your event → **Embeddable Widgets** in the left menu. Choose the **Ticket Widget** (it shows all your ticket types right on your page), customize the button color/text if you want, then click **Copy**.

**3.** Go to `yourdomain.com/admin`, find the **Ticket Checkout (Universe)** section, and paste that code into **"Universe widget embed code."** Hit Publish. Your checkout is now live on your own site — buyers never get redirected away.

**Note on fees:** Universe charges a per-ticket service fee on paid tickets (free tickets are free to process, so your Kids tickets cost nothing). You can choose in Universe's settings whether to pass that fee to buyers or absorb it into your ticket price. Since Cheatham Street Music Foundation is a nonprofit, contact Universe directly — they offer discounted rates for registered charities.

## A few notes

- If you ever want to invite a second person to help edit (a co-organizer, etc.), just repeat step 4's invite for their email — no code changes needed.
- Photos you upload through the admin panel get stored in the `images` folder in your GitHub repo automatically.
- If you ever want to change the actual design (colors, fonts, layout) rather than the words/photos, that still means editing `index.html` — come back to Claude for that part.
