# The Soft Skills Lab

Interactive companion site for a soft skills mentorship series. Pure static HTML/CSS/JS — no backend, no build step, works directly on GitHub Pages.

## Structure

```
/
├── index.html          → homepage (session grid)
├── session-3/
│   └── index.html      → Outbound Strategy & Handling Recruiters
├── session-4/
│   └── index.html      → Interview Etiquette & First Impressions
└── session-N/          → add new sessions the same way
    └── index.html
```

## Adding a new session

1. Create a new folder, e.g. `session-5/`
2. Drop the session's `index.html` inside it
3. In that file's `<body>`, add the same "back to hub" strip the other sessions use:
   ```html
   <div class="hub-strip"><a href="../index.html">&larr; The Soft Skills Lab</a><span>Session 5 of 10</span></div>
   ```
4. Open `index.html` (the homepage) and find the `SESSIONS` array near the bottom. Update that session's entry:
   ```js
   {n:5, title:"Your Session Title", desc:"One-line description.", status:"live", href:"session-5/index.html"},
   ```

That's it — no rebuild step, just edit and push.

## Deploying to GitHub Pages

**Option A — dedicated repo (recommended), URL: `<your-username>.github.io/soft-skills-lab/`**
```bash
cd path/to/this/folder
git init
git add .
git commit -m "Initial commit: The Soft Skills Lab"
git branch -M main
git remote add origin https://github.com/<your-username>/soft-skills-lab.git
git push -u origin main
```
Then on GitHub: repo → **Settings → Pages** → Source: `main` branch, `/ (root)` folder → Save.
Your site goes live at `https://<your-username>.github.io/soft-skills-lab/` within a minute or two.

**Option B — your personal GitHub Pages root site, URL: `<your-username>.github.io/`**
Only works if you name the repo *exactly* `<your-username>.github.io`. Same steps as above, just with that repo name — this becomes your root site instead of a project subpage.

## Notes
- No login, no database — anyone with the link can view any session. That's intentional for now; the access-gated version is the "proper" build for another weekend.
- Every session page keeps its own visual identity consistent (same fonts/colors) so the series feels like one product even as new sessions get added independently.
