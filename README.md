# The Soft Skills Lab

Interactive companion site for a soft skills mentorship practice, organized by cohort. Pure static HTML/CSS/JS — no backend, no build step, works directly on GitHub Pages.

## Structure

```
/
├── index.html              → TRUE homepage: lists all cohorts + "Talks & Links" sidebar
├── assets/
│   └── archana.jpg         → mentor headshot, used by every page's footer
├── cohort-2/
│   ├── index.html          → Cohort 2's own page: lists its sessions
│   ├── session-1/index.html
│   ├── session-2/index.html
│   ├── session-3/index.html
│   └── session-4/index.html
├── marathon-cohort-1/
│   ├── index.html          → GeeksForGeeks Placement Readiness Marathon: lists its sessions
│   ├── session-1/index.html
│   ├── session-2/index.html
│   ├── session-3/index.html
│   └── session-4/index.html
└── cohort-N/                → add new cohorts the same way
    ├── index.html
    └── session-1/index.html
```

Three levels: **Home → Cohort → Session**. The root homepage never lists individual sessions — it only lists cohorts. Each cohort has its own page listing that cohort's sessions.

## Adding a new cohort

1. Create a new folder, e.g. `cohort-3/`
2. Copy `cohort-2/index.html` into it as a starting point, then:
   - Update the `<div class="hub-strip">` link text/back-link (keep `href="../index.html"` — that's always correct, one level up from any cohort page)
   - Update the eyebrow, title, and tagline in the hero to describe the new cohort
   - Clear out the `SESSIONS` array at the bottom and rebuild it as you add sessions (see below)
   - Fix the mentor photo path: it should read `src="../assets/archana.jpg"`
3. Open the root `index.html`, find the `COHORTS` array, and add an entry:
   ```js
   {title:"Your Cohort Name", desc:"One-line description.", status:"live", href:"cohort-3/index.html", sessions:0, icon:"group"},
   ```

## Adding a new session to a cohort

1. Inside the cohort folder (e.g. `cohort-2/`), create a new folder like `session-5/`
2. Drop the session's `index.html` inside it
3. In that file's `<body>`, add the "back to cohort" strip:
   ```html
   <div class="hub-strip"><a href="../index.html">&larr; [Cohort Name]</a><span>Session 5 of 10</span></div>
   ```
4. Add the mentor footer strip before the closing `<footer>` tag (copy it from any existing session page — look for the `.about-strip` block, its CSS, and the `aboutToggle` JS). It references `../../assets/archana.jpg` (two levels up, since sessions are nested inside a cohort folder).
5. Include the copyright line in the footer: `<div class="copyright">© 2026 The Soft Skills Lab. All rights reserved.</div>`
6. Open that cohort's `index.html` and find its `SESSIONS` array. Update the entry:
   ```js
   {n:5, title:"Your Session Title", desc:"One-line description.", status:"live", href:"session-5/index.html", icon:"soon"},
   ```
7. If the cohort's card count on the root homepage should update, edit `sessions:N` on that cohort's entry in the root `COHORTS` array.

That's it — no rebuild step, just edit and push.

## Adding a talk, video, or link to the homepage sidebar

Open the root `index.html`, find the `RESOURCES` array near the top of the `<script>` section, and add an entry:
```js
{title:"Your Talk Title", meta:"YouTube", url:"https://youtube.com/watch?v=...", icon:"play"},
```
`icon` can be `play` (video), `article` (blog post/doc), or `link` (anything else). Newest entries should go last in the array — they render top to bottom. This sidebar only lives on the root homepage, not on individual cohort pages.

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
- No login, no database — anyone with the link can view any cohort or session. That's intentional for now; the access-gated version is the "proper" build for another weekend.
- Every page keeps the same visual identity (same fonts/colors) so the whole thing feels like one product even as new cohorts and sessions get added independently.
