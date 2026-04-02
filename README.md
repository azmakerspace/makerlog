# Makerspace Azerbaijan Blog

This repository contains the source code for the MakerLog website, built with [Hugo](https://gohugo.io/) and the PaperMod theme.

## Quick Start

1. Install Hugo Extended.
2. Clone this repo.
3. Initialize submodules:

```bash
git submodule update --init --recursive themes/PaperMod
```

Then run the local server:

```bash
hugo serve
```

Open: `http://localhost:1313`

---

## Project Structure (Simple)

- `content/` -> All pages/posts
- `static/` -> Static files copied directly (favicon, CNAME, etc.)
- `hugo.yaml` -> Main Hugo config
- `themes/PaperMod` -> Hugo theme (submodule)
- `public/` -> Generated site output for deployment (submodule to Pages repo)

---

## Common Hugo Commands

### Run local website (development)

```bash
hugo serve
```

### Run local website including drafts

```bash
hugo serve --buildDrafts
```

### Production build (optimized)

```bash
hugo --environment production --minify --gc
```

### Production build into deploy folder

```bash
hugo --environment production --minify --gc --destination public
```

---

## Create New Content

### New blog post

```bash
hugo new posts/my-new-post.md
```

### New standalone page

```bash
hugo new page/about.md
```

After creating a page/post:

- Update title/description/tags/categories in front matter.
- Set `draft: false` when ready to publish.

---

## Draft vs Published Content

- `draft: true` -> visible only with `--buildDrafts`
- `draft: false` -> included in production build

Useful check:

```bash
hugo serve --buildDrafts
```

---

## Deploy Flow Used in This Repo

This repo uses `public/` as a git submodule that points to:

- `https://github.com/azmakerspace/azmakerspace.github.io`

### 1) Build production output into `public/`

```bash
hugo --environment production --minify --gc --destination public
```

### 2) Commit and push deploy repo (`public`)

```bash
git -C public add -A
git -C public commit -m "Deploy latest site"
git -C public push origin main
```

### 3) (Optional but recommended) Commit submodule pointer in main repo

```bash
git add public
git commit -m "Update public submodule pointer"
git push origin main
```

---

## Custom Domain Notes

- Source `static/CNAME` should contain:

```text
makerspace.az
```

- GitHub Pages custom domain value should be:

```text
makerspace.az
```

(Do not include `https://` in the Pages custom domain field.)

---

## Troubleshooting

### Theme/layout errors

If you see missing layout/template warnings, ensure theme submodule is initialized:

```bash
git submodule update --init --recursive themes/PaperMod
```

### Submodule update fails because `public/` is not empty

This usually means `public/` was used as a normal folder at some point.
Use submodule-safe flow and avoid deleting unrelated files blindly.

### Hugo command not found

Install Hugo Extended and verify:

```bash
hugo version
```

You should see `+extended` in the output.

