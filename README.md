# Sahil Ali, Mission Control portfolio

Live site: **https://sksahil03.github.io**
Content editor: **https://sksahil03.github.io/edit.html**
Repository: https://github.com/sksahil03/sksahil03.github.io (public, GitHub Pages, branch `main`, root folder)

Personal portfolio of **Shaikh Sahil Ali**, Operations Analyst at SciAstra (Noida, India).
Built as a "mission control" experience: a rocket launch countdown, a 3D planet whose satellites are
projects, a one-tap guided tour, and a "Houston, we have a problem" alert that nudges recruiters to get in touch.

This file is the single source of project context. If you are a person or an AI assistant picking this
up later (any Claude account, ChatGPT, Gemini, Cursor...), read this first.

---

## 1. Files

| File | What it is | Edit it? |
|---|---|---|
| `content.js` | **All text and numbers on the site** (`window.CONTENT = {...}`) | Yes, this is the one to change |
| `edit.html` | No-code form editor that writes a new `content.js` | Only to add new fields |
| `index.html` | The whole site: styles, 3D planet (Three.js r128 from cdnjs), sound, tour, panels | Only for design or feature changes |
| `resume.pdf` | Résumé offered by the "Download résumé" button (`about.resume`) | Replace with a newer PDF of the same name |
| `README.md`, `AGENTS.md`, `CLAUDE.md` | Project memory for humans and AI tools | Keep updated |

No build step, no framework, no server. Any push to `main` goes live in about a minute.

## 2. How to edit and update the portfolio

### A. Text, numbers, projects, jobs, tasks: use the editor (no code)
1. Open **https://sksahil03.github.io/edit.html** on a laptop. The form loads what is live.
2. Change anything. **Add a project / job / task** for new items, **Remove** to delete. Work autosaves in that browser (localStorage key `content-draft`) until it is committed.
3. **Preview** opens `/?preview`: the real site with the draft. Only that browser sees it.
4. **Copy content**, then **Open on GitHub** (opens `content.js` in GitHub's editor, signed in as `sksahil03`).
5. Click in the file, **Ctrl+A**, **Ctrl+V**, then **Commit changes**.
6. Wait about 1 minute and refresh the site (**Ctrl+Shift+R** if the old version still shows).

Each new project automatically becomes a satellite and a tour stop; empty sections stay hidden.
By hand instead: open `content.js` on GitHub, pencil icon, edit, **Commit changes**.

### B. Replace the résumé PDF
GitHub repo, **Add file**, **Upload files**, drag the new PDF **renamed exactly `resume.pdf`**, **Commit changes**.
(The owner chose to keep the phone number in the public résumé.)

### C. Design changes or new features: ask an AI
Open any AI (Claude on any account, ChatGPT, Gemini, Cursor) and say:
> Read https://github.com/sksahil03/sksahil03.github.io, start with README.md. Then [what you want].

### D. Undo a bad change
GitHub repo, **Commits**, open the last good version, and restore it (or ask an AI to revert that commit).

### E. Where things are stored
- **Source of truth: GitHub** (the repo above). Everything live comes from there, safe if the laptop is lost.
- Editor drafts: only in the browser that made them, until committed.
- The original working copy from the first Claude session was in a temporary session folder; always clone or edit from GitHub.

### Content schema (`content.js`)
```
name, brand (short name top-left), role, tagline (one sentence, <= 12 words)
headline:  [{ value, label }]               up to 3, big numbers on home
about:     { intro, skills: [], resume }     resume = "resume.pdf" or a URL
whatIDo:   [{ title, detail }]               day-to-day tasks section
projects:  [{ name, type, result, summary, tags: [], link }]  each = a satellite + tour stop
journey:   [{ when, company, role, years, points: [] }]       newest first; jobs and education
reviews:   [{ text, who, rel }]              real quotes only
impact:    { kpis: [{ label, value, delta, note }], chart?: { title, unit, points: [[label, number]] } } or null
contact:   { email, links: [{ label, url }] }
```
Empty lists (or `impact: null`) hide that section, its nav button and its tour stops automatically.
If `projects` is empty, satellites and the tour fall back to profile stops (name, tasks, jobs, contact).

## 3. Experience and features

- **Launch**: boot log, "Tap to launch" button (this tap is what unlocks audio), T-minus 10 countdown with warp stars, rumble, screen shake, "Liftoff" flash. Shown once per browser session. `?launch` replays it, Esc skips.
- **Home**: name in big type (letters drift away from the mouse), role, tagline, up to 3 headline numbers counting up, "Take the N-second tour" and a secondary button.
- **3D planet** (Three.js): dot-matrix sphere, amber glow, signal-pulse rings with a soft sonar ping, one orbiting satellite per project. Hover slows and labels a satellite; click flies the camera to it and opens that project. Mouse parallax.
- **Tour**: one tap flies to every stop with a large caption and a progress bar, ends with "Let's talk".
- **Bottom nav**: plain words (About, What I do, Projects, Impact, Journey, Reviews, Contact). One panel at a time, arrow keys or arrow buttons move between sections, Esc closes.
- **Tools** (top-right): JSON formatter, Base64, text stats, percent calculator, terminal (`help`, `tour`, `anomaly`, `sudo hire-me`...). Add a tool by adding an `APPS` entry with `tool:true`.
- **Ctrl/Cmd + K**: hidden command bar.
- **Anomaly alert**: after 45 s, then every 3 min (`ANOMALY` constant), until the visitor clicks "Get in touch".
- **Sound**: always on after the first tap (browsers forbid audio before a user gesture): ambient hum, hover ticks, open/close whooshes, countdown beeps, rumble, siren. All synthesized with Web Audio, no audio files. Pauses when the tab is hidden.
- **Custom cursor** on mouse devices; everything respects `prefers-reduced-motion`; a `<noscript>` fallback shows name, role, résumé and email.

## 4. Design system and rules

- Dark "mission control": tinted void background, one amber signal colour `#ffb020`. All colours are CSS tokens in `:root` (no literal colours elsewhere).
- Fonts: **Space Grotesk** (display), **Archivo** (body), **JetBrains Mono** (figures, code, boot log). Picked with the UI UX Pro Max skill.
- Audited with the **Hallmark** skill (`sloplint`): 0 FAIL, 0 WARN. Rules kept on purpose:
  no emoji as icons (one inline SVG stroke icon set, `ICON` map), no tracked-capital labels, no eyebrow labels above headings,
  no em dashes in visible copy, no pure black/white, spacing on a 4px scale, every control has hover, active and focus-visible states,
  never invented metrics or testimonials. Only use real numbers from the résumé or the owner.
- Run the lint (if Hallmark is installed): `node ~/.claude/skills/hallmark/scripts/sloplint.mjs index.html edit.html`

## 5. Owner profile (public facts, from résumé 2026)

- Shaikh Sahil Ali, Operations Analyst, SciAstra (Apr 2025 to now), Noida. Previously Sales Support Executive at SciAstra (Apr 2024 to Apr 2025), Business Development Associate at BYJU'S (Jan to Mar 2024), web development intern at CodeClause and YHills (2023).
- MCA, Amity University Online (2023 to 2025). B.Sc. IT & Management, Utkal University (2019 to 2022).
- Skills: Power BI, Advanced Excel, SQL, Python, predictive modeling, workflow automation, CRM, AWS (EC2, S3), Git, HTML/CSS/JS.
- Key numbers: 4,000 to 5,000 students and 10+ batches at once; ~30% faster turnaround; offline program 65 students, ₹7–8 lakhs; 10–12% of monthly revenue in sales role; 30–40 member team.
- Contact shown on site: sksahilali003@gmail.com, LinkedIn shaikh-sahil-ali-524aba22b.
- Note: the role was briefly listed as "Customer Insights Analyst"; the 2026 résumé says Operations Analyst, which is what the site uses.

## 6. Decisions log

- Concept chosen over Netflix-style and others: "Mission Control OS", later simplified for non-technical visitors (plain nav, one panel at a time, one-tap tour) while keeping the crazy parts.
- Short brand was "SSA"; replaced with "Sahil Ali" because initials were not understandable.
- Hosting: GitHub Pages, free, no card. Repo name `sksahil03.github.io` gives the root URL. Cloudflare Pages and Netlify were considered.
- Content split into `content.js` plus `edit.html` so the owner can update without touching code.

## 7. Ideas not done yet

- Real testimonials (LinkedIn recommendations) for the Reviews section.
- A monthly chart in Impact (`impact.chart`) once real monthly numbers exist.
- Project links or screenshots (anonymised dashboards) for each project.
- Custom domain (e.g. sahilali.in) pointed at GitHub Pages.
