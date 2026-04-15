# Hosting & Launching Your Website — Step by Step
# Redemption Applications

---

## Overview: What You're Setting Up

| Piece | What It Is | Cost |
|---|---|---|
| Domain name | Your web address (e.g. redemptionapplications.com) | ~$12/year |
| Hosting | Where your website files live | **Free** (GitHub Pages) |
| Business email | hello@redemptionapplications.com | ~$6/month (Google Workspace) |
| Contact form | How clients reach you | **Free** (Formspree) |
| SSL certificate | The padlock/https | **Free** (included) |
| Analytics | See who visits your site | **Free** (Google Analytics) |

**Total estimated cost: ~$84/year + $6/month**

---

## Phase 1: Get Your Domain Name

### Step 1 — Buy a domain at Namecheap

1. Go to **namecheap.com**
2. Search for your desired domain name. Good options to try:
   - `redemptionapplications.com`
   - `redemptionapplications.com`
   - `redemptionapp.dev` (.dev domains are great for developers)
3. `.com` is strongly preferred for business credibility and Google search
4. Add to cart and check out — costs roughly $10–14/year
5. During checkout: **turn off auto-renew privacy** upsells you don't need; **keep** WhoisGuard (domain privacy) — it's usually free and hides your personal address

### Step 2 — Note your login credentials
Save your Namecheap username and password somewhere secure. You'll need to come back here to point your domain at GitHub Pages.

---

## Phase 2: Set Up GitHub Pages Hosting

This is where your actual website files live. GitHub Pages is free, fast, reliable, and you already know how to use GitHub.

### Step 1 — Create the website repository

In your **Redemption Applications GitHub organization**:

1. Go to github.com → your RA organization
2. Click **New repository**
3. Name it exactly: `redemptionapplications.github.io`
   - (Replace `redemptionapps` with whatever your organization's GitHub username is)
   - This exact naming pattern is what activates GitHub Pages for an organization
4. Set it to **Public** (required for free GitHub Pages)
5. Check **Add a README file**
6. Click **Create repository**

### Step 2 — Add your website files

On your Mac, in Terminal:

```bash
# Navigate to your freelance folder
cd ~/Developer/Freelance

# Create a folder for the website
mkdir redemption-website
cd redemption-website

# Initialize git
git init

# Connect to your new GitHub repo (replace USERNAME with your org name)
git remote add origin https://github.com/USERNAME/redemptionapplications.github.io.git

# Pull the initial README
git pull origin main
```

Now, put the files Claude Code generated into this `redemption-website` folder:
- `index.html`
- `robots.txt`
- `sitemap.xml`
- `assets/` folder with your logo files

Then push them up:

```bash
git add .
git commit -m "Initial website launch"
git push origin main
```

### Step 3 — Enable GitHub Pages

1. Go to your repo on GitHub
2. Click **Settings** (top nav of the repo)
3. Click **Pages** (left sidebar)
4. Under "Branch", select `main` → `/ (root)` → click **Save**
5. GitHub will give you a URL like `https://redemptionapplications.github.io` — your site is live!

It may take 1–5 minutes to appear. This URL works immediately, before you connect your domain.

---

## Phase 3: Connect Your Custom Domain

### Step 1 — Tell GitHub your domain

1. In your repo's Settings → Pages
2. Under "Custom domain", type your domain: `redemptionapplications.com`
3. Click **Save**
4. GitHub will add a `CNAME` file to your repo automatically — leave it alone

### Step 2 — Point Namecheap at GitHub

1. Log in to Namecheap
2. Click **Domain List** → click **Manage** next to your domain
3. Click the **Advanced DNS** tab
4. Delete any existing A records or CNAME records for `@` and `www`
5. Add these **4 A records** (these are GitHub's server IPs):

| Type | Host | Value | TTL |
|---|---|---|---|
| A Record | @ | 185.199.108.153 | Automatic |
| A Record | @ | 185.199.109.153 | Automatic |
| A Record | @ | 185.199.110.153 | Automatic |
| A Record | @ | 185.199.111.153 | Automatic |

6. Add one **CNAME record**:

| Type | Host | Value | TTL |
|---|---|---|---|
| CNAME Record | www | redemptionapplications.github.io. | Automatic |

(Include the trailing period after `.github.io`)

### Step 3 — Wait for DNS to propagate

DNS changes take anywhere from 15 minutes to 48 hours to spread worldwide. Usually it's under an hour.

You can check progress at: **whatsmydns.net** — type your domain and see if it's resolving.

### Step 4 — Enable HTTPS (the padlock)

Once DNS has propagated:

1. Go back to your repo's Settings → Pages
2. You should see a green checkmark next to your domain
3. Check the box: **Enforce HTTPS**
4. Done — your site now has `https://` and the padlock

---

## Phase 4: Set Up Your Contact Form (Formspree)

This makes the contact form on your website actually send you emails.

1. Go to **formspree.io** and create a free account
2. Click **New Form**
3. Name it "RA Website Contact"
4. Formspree will give you a form ID that looks like: `xpwzabcd`
5. In your `index.html`, find the line:
   ```
   https://formspree.io/f/REPLACE_WITH_YOUR_ID
   ```
6. Replace `REPLACE_WITH_YOUR_ID` with your actual ID:
   ```
   https://formspree.io/f/xpwzabcd
   ```
7. Commit and push the change:
   ```bash
   git add index.html
   git commit -m "Connect Formspree contact form"
   git push origin main
   ```
8. Test it by submitting your contact form — you should receive the email

Free Formspree tier allows 50 submissions/month, which is plenty to start.

---

## Phase 5: Set Up Google Analytics

This lets you see how many people visit your site, where they come from, and what they look at.

1. Go to **analytics.google.com**
2. Sign in with your Google account
3. Click **Start measuring** → create an account named "Redemption Applications"
4. Create a property for your website, enter your domain
5. Choose "Web" as the platform
6. Google will give you a **Measurement ID** that looks like: `G-XXXXXXXXXX`
7. In your `index.html`, find this comment near the top of `<head>`:
   ```
   <!-- Google Analytics: replace G-XXXXXXXXXX with your Measurement ID -->
   ```
8. Paste in the Google Analytics script tag with your ID
9. Push the change to GitHub

---

## Phase 6: Set Up Google Search Console

This tells Google your site exists and helps you show up in search results faster.

1. Go to **search.google.com/search-console**
2. Click **Add property**
3. Choose **URL prefix** → enter `https://www.redemptionapplications.com`
4. Verify ownership using the HTML tag method:
   - Google gives you a `<meta>` tag to paste into your `index.html` `<head>`
   - Paste it, push to GitHub, then click **Verify** in Search Console
5. Once verified, go to **Sitemaps** and submit: `https://www.redemptionapplications.com/sitemap.xml`
6. Google will start crawling and indexing your site — typically shows up in search within a few days to a few weeks

---

## Phase 7: Set Up Google Business Profile

This is what makes you show up in Google Maps and the "local results" box when someone searches for app developers.

1. Go to **business.google.com**
2. Sign in and click **Add your business**
3. Enter: **Redemption Applications**
4. Business category: "Software Company" or "Mobile App Developer"
5. For address: you can list as a service-area business (no physical address shown)
   - Select "I deliver goods and services to my customers"
   - Enter Utah as your service area
6. Add your phone number and website URL
7. Verify by phone or postcard (Google mails a postcard with a PIN — takes ~5 days)
8. Once verified, fill out your profile completely:
   - Description: copy from your website's About section
   - Services: list all your service offerings
   - Hours: your availability
   - Photos: upload your logo and any project screenshots

**This is one of the highest-ROI things you can do for local search visibility.**

---

## Phase 8: Set Up Business Email (Optional but Recommended)

Having `hello@redemptionapplications.com` instead of a Gmail address looks significantly more professional to clients.

1. Go to **workspace.google.com**
2. Start a free 14-day trial
3. Follow setup for your domain — Google will walk you through adding DNS records to Namecheap
4. Create your email: `hello@redemptionapplications.com` (or `lydia@redemptionapplications.com`)
5. Cost after trial: ~$6/month for the Starter plan (1 user)
6. Update the email address in your `index.html` contact section
7. Update your Formspree account to forward form submissions to your new email

---

## Making Updates to Your Website Later

Every time you want to change something on your site:

1. Edit the file locally on your Mac
2. In Terminal, from your website folder:
   ```bash
   git add .
   git commit -m "Brief description of what you changed"
   git push origin main
   ```
3. Wait ~1–2 minutes, then refresh your live site — the changes are live

That's it. No FTP, no hosting control panels, no complicated deployment process.

---

## Summary Checklist

- [ ] Buy domain on Namecheap
- [ ] Create GitHub repo: `username.github.io`
- [ ] Generate website files with Claude Code using `WEBSITE_SPEC.md`
- [ ] Push files to GitHub
- [ ] Enable GitHub Pages in repo settings
- [ ] Point Namecheap DNS at GitHub (4 A records + CNAME)
- [ ] Enable HTTPS in GitHub Pages settings
- [ ] Sign up for Formspree, replace ID in index.html
- [ ] Set up Google Analytics, add tracking code
- [ ] Set up Google Search Console, submit sitemap
- [ ] Set up Google Business Profile
- [ ] Set up Google Workspace email (optional)
- [ ] Test contact form end-to-end
- [ ] Submit site to Google Search Console

---

## Recommended Order (if doing this over a few days)

**Day 1**: Buy domain → set up GitHub repo → run Claude Code to generate the site → push to GitHub → enable Pages

**Day 2**: Connect Namecheap DNS → wait for propagation → enable HTTPS → set up Formspree → test the form

**Day 3**: Set up Google Analytics + Search Console → submit sitemap → start Google Business Profile

**Day 4+**: Google Business Profile verification arrives (postcard) → complete profile → start exploring Google Ads if desired
