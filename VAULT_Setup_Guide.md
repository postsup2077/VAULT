# VAULT Setup Guide

## What you need before you start
- A Google account (Gmail)
- 15 minutes

---

## ⚠️ Most Common Error — Read This First

**Error 400: redirect_uri_mismatch** when signing in means your Google Cloud credentials have the wrong URL.

In Google Cloud Console, under **Authorized JavaScript origins**, you must enter **exactly**:

```
https://YOUR_GITHUB_USERNAME.github.io
```

❌ **Wrong:** `https://username.github.io/VAULT`  
❌ **Wrong:** `https://username.github.io/` (trailing slash)  
✅ **Correct:** `https://username.github.io`

Just the root domain. No path. No trailing slash. This is the #1 setup error.

If you already got this error — go back to Google Cloud Console, fix the URL, save, wait 5 minutes, try again.

---

## Step 1 — Copy the Google Sheet template

1. Click: **[Copy the VAULT Template Sheet](https://docs.google.com/spreadsheets/d/1Fjq2U1p0yiyX_7qwoNlXvERumaW7yXkJ/copy)**
2. Click **Make a copy**
3. The Sheet opens in your Google Drive
4. From the URL copy the Sheet ID — the long code between `/d/` and `/edit`:
   `https://docs.google.com/spreadsheets/d/`**`THIS_IS_YOUR_ID`**`/edit`
5. Save it somewhere

---

## Step 2 — Fork the repo and enable GitHub Pages

1. Go to **[github.com/postsup2077/VAULT](https://github.com/postsup2077/VAULT)**
2. Click **Fork** (top right)
3. In your fork → **Settings → Pages**
4. Source: **Deploy from a branch** → `main` → `/ (root)` → **Save**
5. Your app will be live in ~3 minutes at:
   `https://YOUR_USERNAME.github.io/VAULT/vault.html`

---

## Step 3 — Get a Google OAuth Client ID

### 3a — Create a project
1. Go to **[console.cloud.google.com](https://console.cloud.google.com)**
2. Click the project dropdown → **New Project** → name it "VAULT" → **Create**

### 3b — Enable Google Sheets API
1. **APIs & Services → Library**
2. Search **Google Sheets API** → click it → **Enable**

### 3c — Set up consent screen
1. **APIs & Services → OAuth consent screen**
2. Choose **External** → **Create**
3. Fill in: App name = `VAULT`, your email for both fields
4. Click **Save and Continue** through all screens
5. Click **Back to Dashboard**

### 3d — Create credentials
1. **APIs & Services → Credentials → + Create Credentials → OAuth 2.0 Client ID**
2. Application type: **Web application**
3. Name: `VAULT`
4. Under **Authorized JavaScript origins** → **+ Add URI**
5. Enter: `https://YOUR_GITHUB_USERNAME.github.io`
   ⚠️ Root domain only — no `/VAULT`, no trailing slash
6. Click **Create**
7. Copy the **Client ID** (ends in `.apps.googleusercontent.com`)

---

## Step 4 — Get a TMDB API Key (films/video — free)

1. Create account at **[themoviedb.org](https://www.themoviedb.org)**
2. Profile icon → **Settings → API → Request an API Key → Developer**
3. Fill in the form (personal project)
4. Copy the **API Key (v3 auth)**

---

## Step 5 — Get an OMDB API Key (RT scores — free)

1. Go to **[omdbapi.com/apikey.aspx](https://www.omdbapi.com/apikey.aspx)**
2. Select **FREE** → enter your email → Submit
3. Check your email → click the activation link
4. Key will be in the email

---

## Step 6 — Launch VAULT

1. Open: `https://YOUR_USERNAME.github.io/VAULT/vault.html`
2. Setup wizard appears
3. Choose collection type → name your archive
4. Paste your Sheet ID, OAuth Client ID, TMDB key, OMDB key
5. Click **Launch My Archive**

Done — your config is saved locally forever.

---

## Troubleshooting

**Error 400: redirect_uri_mismatch**  
Your authorized JavaScript origin is wrong. See the top of this guide.

**Sign In button does nothing**  
Same cause — wrong authorized origin URL in Google Cloud.

**Posters not loading**  
Go to Stats → 📷 Load Posters to fetch cover art.

**OMDB 401 error**  
Your OMDB key hit its daily limit (1,000 req/day). Resets at midnight. Get a new key at omdbapi.com if needed.

**Sheet not saving changes**  
Make sure you're signed in (tap Sign In in the app).

**App shows 404**  
GitHub Pages may still be deploying. Wait 3-5 minutes and refresh. Check Settings → Pages to confirm it's enabled.

---

*Built by Jon Milano · Los Angeles · 2026–2027*  
*github.com/postsup2077/VAULT*
