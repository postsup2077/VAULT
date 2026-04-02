# VAULT Setup Guide

## What you need before you start
- A Google account (Gmail)
- 15 minutes

---

## Step 1 — Copy the Google Sheet template

This is where all your collection data will live.

1. Click this link: **[Copy the VAULT Template Sheet](https://docs.google.com/spreadsheets/d/1Fjq2U1p0yiyX_7qwoNlXvERumaW7yXkJ/copy)**
2. Google will ask you to make a copy — click **Make a copy**
3. It opens in your Google Drive as "Copy of VAULT Template"
4. Rename it to whatever you want (e.g. "My Vinyl Archive")
5. Look at the URL — it will look like this:
   `https://docs.google.com/spreadsheets/d/`**`ABC123XYZ`**`/edit`
6. Copy that bold part — that's your **Sheet ID**. Save it somewhere.

---

## Step 2 — Fork the repo and turn on GitHub Pages

This is where the app lives.

1. Go to **[github.com/postsup2077/VAULT](https://github.com/postsup2077/VAULT)**
2. Click **Fork** (top right) — this makes your own copy of the app
3. In your new fork, click **Settings**
4. In the left sidebar click **Pages**
5. Under *Build and deployment* → Source → select **Deploy from a branch**
6. Branch: **main** · Folder: **/ (root)** → click **Save**
7. Wait 3 minutes, then your app will be live at:
   `https://YOUR_GITHUB_USERNAME.github.io/VAULT/vault.html`

---

## Step 3 — Get a Google OAuth Client ID

This lets the app write back to your Google Sheet when you check things in and out. It sounds scary but takes about 5 minutes.

### 3a — Create a Google Cloud project

1. Go to **[console.cloud.google.com](https://console.cloud.google.com)**
2. Sign in with your Google account
3. At the top, click the project dropdown (it might say "My First Project")
4. Click **New Project**
5. Name it anything — "VAULT" works fine
6. Click **Create**

### 3b — Enable the Google Sheets API

1. In the left menu click **APIs & Services → Library**
2. Search for **Google Sheets API**
3. Click it, then click **Enable**

### 3c — Set up the consent screen (one time only)

1. In the left menu click **APIs & Services → OAuth consent screen**
2. Choose **External** → click **Create**
3. Fill in:
   - App name: `VAULT`
   - User support email: your email
   - Developer contact: your email
4. Click **Save and Continue** through the rest (you don't need to fill anything else in)
5. On the final screen click **Back to Dashboard**

### 3d — Create your credentials

1. In the left menu click **APIs & Services → Credentials**
2. Click **+ Create Credentials** at the top
3. Choose **OAuth 2.0 Client ID**
4. Application type: **Web application**
5. Name: `VAULT`
6. Under **Authorized JavaScript origins** click **+ Add URI**
7. Type: `https://YOUR_GITHUB_USERNAME.github.io` (replace with your actual username)
8. Click **Create**
9. A box pops up — copy the **Client ID** (it ends in `.apps.googleusercontent.com`)
10. Save it somewhere

---

## Step 4 — Get a TMDB API Key (free)

This fetches movie posters and metadata automatically.

1. Go to **[themoviedb.org](https://www.themoviedb.org)** and create a free account
2. Click your profile icon → **Settings**
3. Click **API** in the left menu
4. Click **Request an API Key**
5. Choose **Developer**
6. Fill in the form (describe it as a personal project)
7. Copy the **API Key (v3 auth)** — it's a 32-character code

---

## Step 5 — Get an OMDB API Key (free)

This fetches Rotten Tomatoes scores.

1. Go to **[omdbapi.com/apikey.aspx](https://www.omdbapi.com/apikey.aspx)**
2. Select **FREE** (1,000 requests/day)
3. Enter your email and click Submit
4. Check your email — click the activation link
5. Your key will be emailed to you — it's an 8-character code

---

## Step 6 — Launch VAULT

1. Open your app: `https://YOUR_GITHUB_USERNAME.github.io/VAULT/vault.html`
2. The setup wizard will appear
3. Choose your collection type
4. Enter your archive name
5. Paste your **Sheet ID** (from Step 1)
6. Paste your **OAuth Client ID** (from Step 3)
7. Paste your **TMDB key** (from Step 4)
8. Paste your **OMDB key** (from Step 5)
9. Click **Launch My Archive**

That's it. Your config is saved — you'll never need to enter it again on that device.

---

## Troubleshooting

**"Sign in" button does nothing**
Make sure your GitHub Pages URL is added to the authorized origins in Google Cloud Console (Step 3d). It must be `https://username.github.io` with no trailing slash.

**Posters not loading**
Go to Stats → 📷 Load Posters. This fetches cover art for your whole collection.

**Sheet not saving**
Click Sign In in the app. You need to be signed in to write changes back to your Sheet.

**OMDB says 401**
Your OMDB key has hit its daily limit (1,000 requests). It resets at midnight. Get a new key at omdbapi.com if needed.

---

*Built by Jon Milano · Los Angeles · 2026–2027*
