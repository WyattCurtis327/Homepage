---
name: github-homepage
description: >
  Use when the user asks to update, publish, or maintain the GitHub Pages
  homepage, the Homepage repo, resume.md, wyatt-curtis.html, the public resume
  page, or runs /github-homepage or /github_homepage.
---

# GitHub homepage

Maintain Wyatt Curtis’s **public** GitHub Pages site.

| | |
|---|---|
| Repo | https://github.com/WyattCurtis327/Homepage |
| Live | https://wyattcurtis327.github.io/Homepage/ |
| Artifact | `index.html` on `main` (Pages: branch `main`, folder `/`) |
| Resume source | `Homepage/resume.md` (editable Markdown). Mirror: `~/Documents/resume.md` |
| Local HTML copy | `~/Documents/wyatt-curtis.html` |
| Skill copies | this file; also `Homepage/.grok/skills/github-homepage/SKILL.md` |

## Rules

- **Public only.** List and describe only `visibility=public` repos under `WyattCurtis327`. Never name, link, or summarize a private repo.
- **No secrets.** No API keys, `.env`, bet ledgers, FRED keys, rate-sheet workbooks, or personal vault files.
- Keep the page a **single** `index.html` (sticky TOC + tabs). Relative URLs only (GitHub project Pages).
- GoatCounter site `wyattcurtis327.goatcounter.com` counts tab/hash views from `showTab`. Keep that snippet. No other analytics. No secrets.
- Resume comes from **`resume.md`**, not Google Drive. After editing `resume.md`, rebuild the Resume tab from it.
- After every content change: commit + push `main`, then sync the Documents copies of `index.html` and `resume.md`.

## Tabs (do not drop without asking)

1. Resume
2. GitHub repos (public inventory table)
3. mortgage-capital-markets-analytics
4. semantic-layer-docs
5. pricing-scenarios
6. nfl-ats
7. nfl-clv-ledger

Add a tab only for a **public** repo the user names. Remove a tab if that repo is deleted or made private.

## Refresh workflow

1. Clone or `git pull --ff-only` `WyattCurtis327/Homepage`.
2. Resume: read `resume.md` in the Homepage clone. Rebuild the Resume tab from that Markdown. Footer cites `resume.md`. If `~/Documents/resume.md` is newer, copy it into the clone first.
3. Repos: `gh repo list WyattCurtis327 --limit 100 --json name,description,url,isPrivate,isArchived,isFork`. Drop `isPrivate=true`. Refresh the GitHub table and any matching tabs from each public README (pricing-scenarios tab = that repo’s README).
4. Edit `index.html`. Keep navy/paper styling unless the user asks for a restyle.
5. Copy `index.html` → `~/Documents/wyatt-curtis.html` and `resume.md` → `~/Documents/resume.md`.
6. Commit, push `main`. Confirm Pages: `gh api repos/WyattCurtis327/Homepage/pages`.
7. Open the live URL and check each tab + TOC link.

## Publish (first time or Pages broken)

```bash
gh api -X POST repos/WyattCurtis327/Homepage/pages \
  -H "Accept: application/vnd.github+json" \
  -f "source[branch]=main" -f "source[path]=/"
```

If it already exists, PATCH the same source. Site is a **project** Pages URL (`/Homepage/`), not `username.github.io`.

## Common mistakes

- Publishing a private repo name “just in the table”
- Rebuilding the resume from Google Drive instead of `resume.md`
- Absolute paths (`/css/...`) that 404 on project Pages
- Editing only the Documents HTML copy and not pushing `index.html`
- Committing rate-sheet `.xlsx` files into `pricing-scenarios`
