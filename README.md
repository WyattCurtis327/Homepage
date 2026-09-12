# Homepage

Public GitHub Pages site for Wyatt Curtis: resume plus public GitHub work.

**Live:** https://wyattcurtis327.github.io/Homepage/

The page is a single `index.html` (tabs + table of contents). Private repositories are not listed.

## Maintain

Use Grok skill **github-homepage** (`/github-homepage` or `/github_homepage`).

Canonical skill file: `.grok/skills/github-homepage/SKILL.md`  
User copy (so Grok Build can invoke it from any session): `~/.grok/skills/github-homepage/SKILL.md`

```bash
git clone https://github.com/WyattCurtis327/Homepage.git
# edit index.html
git add index.html
git commit -m "Update homepage"
git push origin main
```

GitHub Pages is served from `main` `/`.
