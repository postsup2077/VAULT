# VAULT

**A physical archive manager, built by a collector for collectors.**

---

## Why I built this

I've been collecting 16mm film for years. Prints stacked in cans, reels spread across shelves, a mental inventory that only works until it doesn't. I needed to know what I had, where it was, who had borrowed it, and whether it was in good shape — all from my phone, ideally while standing in front of a pile of cans at an estate sale.

I looked for an app that could do this. Nothing fit. Everything was either too generic, too expensive, too complicated to set up, or built for libraries and institutions — not for someone who just loves the physical object.

So I built VAULT.

It started as a personal tool for my 16mm archive. Then I realized the same problem exists for anyone who collects physical media — VHS, LaserDisc, vinyl, books, Super 8, equipment. The specific fields change but the core need is the same: *know what you have, track where it is, find it fast.*

VAULT runs on Google Sheets, which means your data is yours. No subscription, no vendor lock-in, no server I'm running that disappears one day. Just a spreadsheet you own and an app that reads it.

If you're a collector, I hope this saves you the same headaches it saved me.

— Jon Milano, Los Angeles

---

## What it does

- **Barcode scanning** — scan any item in or out using a USB barcode scanner or phone camera. Works from any screen.
- **Auto-fill metadata** — pulls title, creator, year, genre, and cover art from TMDB, OMDB, Discogs, or Open Library depending on your collection type
- **Google Sheets backend** — your data lives in a spreadsheet you own and control
- **Offline support** — loads from local cache when there's no internet connection
- **PWA** — installable on iPhone, iPad, and Mac as a home screen app
- **Export** — CSV export and a clean print-ready list for insurance, lending, or sharing

---

## Collection types

| Type | Metadata Source |
|------|----------------|
| 🎞 16MM Film | TMDB + OMDB |
| 🎬 35MM Film | TMDB + OMDB |
| 🎥 Super 8 | TMDB + OMDB |
| 📼 VHS / Betamax | TMDB + OMDB |
| 💽 LaserDisc | TMDB + OMDB |
| 📀 DVD | TMDB + OMDB + UPC |
| 🔵 Blu-ray | TMDB + OMDB + UPC |
| 💿 Vinyl Records | Discogs |
| 📚 Books | Open Library |
| 🔧 Equipment | Manual |
| 🧸 Toys | Manual |
| 📦 Other | Manual |

---

## Quick Start

### Step 1 — Copy the Google Sheet template

**[→ Copy the VAULT Template Sheet](https://docs.google.com/spreadsheets/d/1uRCOK_3i2w4gE4652NLzub9KZ_QMHWf20k0VVIAiTCA/copy)**

After copying, grab your Sheet ID from the URL:  
`https://docs.google.com/spreadsheets/d/`**`THIS_IS_YOUR_SHEET_ID`**`/edit`

---

### Step 2 — Fork this repo and enable GitHub Pages

1. Click **Fork** at the top right of this repo
2. Go to your fork → **Settings** → **Pages**
3. Under *Source*, select **Deploy from a branch** → `main` → `/ (root)`
4. Click **Save**
5. Your app will be live at: `https://YOUR_USERNAME.github.io/vault/vault.html`

---

### Step 3 — Get a Google OAuth Client ID

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project (or use an existing one)
3. Go to **APIs & Services → Library** and enable **Google Sheets API**
4. Go to **APIs & Services → Credentials**
5. Click **Create Credentials → OAuth 2.0 Client ID**
6. Choose **Web application**
7. Under **Authorized JavaScript origins**, add your GitHub Pages URL:  
   `https://YOUR_USERNAME.github.io`
8. Click **Create** and copy your **Client ID**

---

### Step 4 — Get your API keys (all free)

#### TMDB (films, VHS, LaserDisc)
1. Create an account at [themoviedb.org](https://www.themoviedb.org)
2. Go to **Settings → API → Request an API Key**
3. Choose **Developer** and fill in the form
4. Copy your **API Key (v3 auth)**

#### OMDB (Rotten Tomatoes scores — 1,000 req/day free)
1. Go to [omdbapi.com/apikey.aspx](https://www.omdbapi.com/apikey.aspx)
2. Select **Free** and enter your email
3. Check your email for the key

#### Discogs (vinyl records)
1. Log in at [discogs.com](https://www.discogs.com)
2. Go to **Settings → Developers → Generate new token**

#### Open Library (books)
No key needed — it's free and open.

---

### Step 5 — Launch your archive

1. Open your GitHub Pages URL
2. The setup wizard appears on first launch
3. Choose your collection type
4. Name your archive
5. Paste your Sheet ID, OAuth Client ID, and API keys
6. Click **Launch My Archive**

Your config is saved locally — you'll never need to enter it again on that device.

---

## Google Sheet Structure

The template has two tabs:

### Items tab
| Column | Field |
|--------|-------|
| A | Title |
| B | Creator (Director / Artist / Author) |
| C | Year |
| D | Genre / Category |
| E | Score / Rating |
| F | Format |
| G | Condition |
| H | Notes |
| I | Status |
| J | Checked Out To |
| K | Date Out |
| L | Date In |
| M | Image URL |
| Y | Item ID (auto-assigned) |

### Unit Tracker tab
| Column | Field |
|--------|-------|
| A | Barcode ID |
| B | Item Title |
| C | Unit Number |
| D | Status |
| E | Checked Out To |
| F | Date Out |
| G | Date In |
| H | Notes |

> Keep tab names exactly as shown: `Items` and `Unit Tracker`

---

## Barcode scanning

VAULT works with any **USB HID barcode scanner** in keyboard wedge mode. Most scanners work plug-and-play:

1. Plug in your scanner
2. Open VAULT
3. Scan from any tab — the overlay appears automatically

**Recommended:** Tera D5100 or any scanner that appends an Enter keystroke after each scan.

---

## Tips

- **First run:** Go to Stats → 📷 Load Posters to fetch cover art for your whole collection
- **Offline:** VAULT caches your collection locally after each sync
- **Multiple devices:** Data lives in Google Sheets — every device stays in sync
- **New items:** Use Add → Auto-Fill to pull metadata, then scan barcodes for each unit
- **Reset:** Stats → ⚙ Settings → Reset & Reconfigure to change your setup. Your Sheet data is never affected.

---

## License

MIT — fork it, modify it, use it for your collection.

---

*VAULT is a personal project. TMDB, OMDB, Discogs, and Open Library are independent services with their own terms of use.*

*Built by Jon Milano · Los Angeles · 2026–2027*
