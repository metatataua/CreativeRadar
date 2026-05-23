# MyDrama — AI Research Dashboard

A research tool for creative producers. Enter a setting + genre/tropes → get organic content patterns, trending hooks, and AI strategy summary in seconds.

---

## Deploy in 5 minutes (Vercel)

### 1. Create a GitHub repo
- Go to github.com → New repository → name it `mydrama-dashboard`
- Upload all files from this folder (drag and drop works fine)

### 2. Deploy to Vercel
- Go to vercel.com → Log in with GitHub
- Click **Add New Project** → Import your `mydrama-dashboard` repo
- Click **Deploy** (no build settings needed)

### 3. Add your Anthropic API key
- In Vercel dashboard → your project → **Settings** → **Environment Variables**
- Add: `ANTHROPIC_API_KEY` = your key (starts with `sk-ant-...`)
- Click **Save**, then go to **Deployments** → **Redeploy**

### 4. Share the URL
- Vercel gives you a URL like `mydrama-dashboard.vercel.app`
- Share it with anyone — no login needed

---

## File structure

```
/api/research.js      ← Backend: calls Anthropic API securely
/public/index.html    ← Frontend: the full dashboard UI
/vercel.json          ← Routing config
/package.json         ← Project metadata
```

---

## What's live vs stubbed

| Source | Status | How to connect |
|---|---|---|
| Organic content (AI) | ✅ Live | Works out of the box |
| AI Summary | ✅ Live | Works out of the box |
| Social Peta | 🟡 Stub | Add Apify scraper → call from `/api/research.js` |
| Internal base (Drive) | 🟡 Stub | Add Google Drive OAuth → read docs from Drive |

---

## To add Social Peta via Apify
1. Sign up at apify.com
2. Find the Social Peta scraper actor
3. Add `APIFY_TOKEN` to Vercel env vars
4. In `api/research.js`, add a new `type: 'socialpeta'` branch that calls the Apify API

## To add Google Drive internal base
1. Create a Google Cloud project → enable Drive API
2. Add `GOOGLE_SERVICE_ACCOUNT_JSON` to Vercel env vars
3. In `api/research.js`, add a `type: 'internal'` branch that reads a specific Google Doc/Sheet
