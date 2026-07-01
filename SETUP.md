# Setup Instructions

This repo is a **GitHub Profile README** — a special repository GitHub renders on your profile page.

## 1. Confirm the special repository

1. Repository name must be **exactly** your GitHub username: `Swaraj234/Swaraj234`.
2. It must be **public**.
3. If it doesn't exist yet, create it and check "Add a README file," then overwrite it with the contents of this repo.

GitHub automatically shows the `README.md` of that repo at the top of your profile — nothing else needs to be configured for the README itself.

## 2. Push these files

```bash
git init
git remote add origin https://github.com/Swaraj234/Swaraj234.git
git add .
git commit -m "Redesign profile README — premium portfolio version"
git branch -M main
git push -u origin main
```

Folder structure:

```
Swaraj234/
├── README.md
├── SETUP.md
├── assets/
│   ├── banner.svg
│   ├── footer.svg
│   ├── wave.svg
│   ├── divider.svg
│   └── timeline.svg
└── .github/
    └── workflows/
        ├── snake.yml
        └── metrics.yml
```

## 3. What's already wired up correctly

Every URL in `README.md` already uses your real details:

| Item | Value used |
|---|---|
| GitHub username | `Swaraj234` (in all stats/graph/snake/trophy/visitor-counter URLs) |
| LinkedIn | `https://www.linkedin.com/in/swaraj-tale-58b470294` |
| Email | `officialswaraj123@gmail.com` |

## 4. The two placeholders you still need to fill in

Only two things in the whole README are placeholders, because no real values were provided for them:

1. **Project repository links** — currently point to:
   - `github.com/Swaraj234/ai-mock-interview`
   - `github.com/Swaraj234/realtime-chat-app`
   - `github.com/Swaraj234/matrimonial-platform`

   Update these to your actual repo names if they differ.

2. **"Live Demo" buttons** — currently link to `#` since no deployed URLs were provided. Point each one at your live deployment (Vercel/Render/Railway link) once it's up, or delete the button for any project that isn't deployed.

## 5. Enable the Snake Animation workflow

1. Keep `.github/workflows/snake.yml` in the repo — it's ready to run as-is.
2. Go to **Settings → Actions → General** and set **Workflow permissions** to "Read and write permissions."
3. Trigger it once manually: **Actions tab → Generate Snake Contribution Animation → Run workflow**.
4. It creates an `output` branch with the generated SVGs. The README already points to:
   `https://raw.githubusercontent.com/Swaraj234/Swaraj234/output/github-contribution-grid-snake-dark.svg`

## 6. Enable the Metrics workflow

The `metrics` plugin set in this workflow (achievements, language analysis across all repos, isocalendar) needs more read access than the default `GITHUB_TOKEN` provides.

1. Create a **classic Personal Access Token** with `read:user` and `repo` scopes: GitHub → Settings → Developer settings → Personal access tokens.
2. In this repo, go to **Settings → Secrets and variables → Actions** and add it as a secret named `METRICS_TOKEN`.
3. Trigger the workflow: **Actions tab → Generate Metrics Dashboard → Run workflow**.
4. It publishes to a `gh-pages` branch. If you'd rather embed the output as a static image instead of the live badge already in the README, grab the generated image URL from the workflow run and swap it into the `<details>` block.

If you skip this step, everything else in the README still works — only the collapsible "Metrics Dashboard" section depends on it.

## 7. Stats services used (all free, no API keys required unless noted)

| Section | Service |
|---|---|
| Typing animation | readme-typing-svg.demolab.com |
| Tech stack icons | skillicons.dev |
| GitHub stats + top languages | github-readme-stats.vercel.app |
| Streak stats | github-readme-streak-stats.herokuapp.com |
| Activity graph | github-readme-activity-graph.vercel.app |
| Contribution snake | Platane/snk (via included Action) |
| Metrics dashboard | lowlighter/metrics (via included Action, needs `METRICS_TOKEN`) |
| Trophies | github-profile-trophy.vercel.app |
| Followers / repo count | img.shields.io (GitHub API + dynamic JSON badge) |
| Project image placeholders | placehold.co |
| Visitor counter | komarev.com/ghpvc |

If any image fails to load down the line, it's usually because the underlying free service is temporarily down — refresh, or swap in an alternative badge provider. None of the services above are deprecated as of this writing.

## 8. Customizing the SVG assets

All five files in `assets/` are hand-authored, editable SVG — not exported images:

- **`banner.svg`** — hero banner: animated gradient sweep, floating particles, a server-rack illustration with blinking status LEDs, client nodes with traveling "API packet" dots, gradient name text, status pill.
- **`footer.svg`** — animated closing wave with a professional sign-off line.
- **`wave.svg`** — a slim animated wave, usable as an alternate section divider.
- **`divider.svg`** — the shimmering gradient line used between every section in `README.md`.
- **`timeline.svg`** — the 2023 → Next career timeline, with the current year pulsing.

To re-theme any of them, edit the `<stop>` colors in each file's `<defs>` block — every asset shares the same Tokyo Night palette:

```
background   #16161e → #1a1b27 → #1f2033
blue         #7aa2f7
purple       #bb9af7
cyan         #7dcfff
green        #9ece6a
text         #c0caf5
muted        #565f89
border       #2a2e42 / #414868
```

To update the timeline's milestones, edit the `<text>` content inside each `<g transform="translate(...)">` node block in `timeline.svg`.

## 9. Optional extras (not included, intentionally)

Not part of this delivery since they need external accounts to configure — add them later if you want:

- **Weekly coding activity** — needs a WakaTime account + a companion Action to generate a `waka.svg`.
- **Spotify "Now Playing"** — needs a Spotify Web API app + a deployed Now-Playing widget.
- **Latest blog posts** — needs `gautamkrishnar/blog-post-workflow` pointed at your RSS feed.
