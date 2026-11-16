# 0ctave.github.io

Personal site (Quarto), published to https://0ctave.github.io by GitHub Actions.

## Layout
- `index.qmd`: home page (short bio + latest writing)
- `research.qmd`: thesis summary and links (put the thesis PDF in `files/` and link it)
- `writing/<slug>/index.qmd`: one folder per post; two drafts are prepared:
  - `llm-judges-code-of-practice/`: the small study
  - `uncertainty-threshold-decisions/`: the policy note
- Posts with `draft: true` are not published. Remove that line when a post is ready.

## Preview locally
Quarto is pinned in `mise.toml` (official build; the nixpkgs package currently pairs Quarto 1.9 with a too-old pandoc
and fails with "Unknown option syntax-highlighting").
```sh
mise trust && mise exec -- quarto preview
```
If Quarto ever fails with "RangeError: could not deserialize value", delete `.quarto/` and `~/.cache/quarto`.

## Publish (one-time setup)
1. On GitHub, create a public repository named exactly `0ctave.github.io`.
2. Push this folder to its `main` branch:
   ```sh
   git init -b main && git add . && git commit -m "Site skeleton"
   git remote add origin git@github.com:0ctave/0ctave.github.io.git
   git push -u origin main
   ```
3. Wait for the "Publish site" action to finish (it creates the `gh-pages` branch), then in
   Settings > Pages choose "Deploy from a branch", branch `gh-pages`, folder `/ (root)`.
4. Every later push to `main` republishes the site.

## Before publishing a post
- Facts about me only from what is true (the candidacy repo's `data/profile.yaml`).
- Every quote from the Code or a framework checked against the source, with section and retrieval date.
- Data, code and labels of the study in their own repository, linked from the post.
