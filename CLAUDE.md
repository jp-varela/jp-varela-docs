# jp-varela-docs

João's personal documentation site — notes, cheatsheets, and reference pages for himself. Built with [Zensical](https://zensical.org/docs/) (a Material-for-MkDocs-style static site generator) and auto-deployed to GitHub Pages.

## Structure

- `docs/*.md` — the actual content, one file per page/topic. Each page starts with Zensical front matter, typically an icon:
  ```
  ---
  icon: lucide/rocket
  ---
  ```
- `zensical.toml` — site config (title, theme, features, palette, nav). Navigation is **implicit**: with no `nav` array defined, Zensical derives the sidebar from the `docs/` directory structure and file order. Adding a new `.md` file under `docs/` is enough for it to show up — no config edit needed unless a specific order/grouping is wanted.
- `.github/workflows/docs.yml` — on every push to `main`, builds the site with `zensical build --clean` and deploys to GitHub Pages.
- `docs/index.md` and `docs/markdown.md` are the stock example pages from `zensical new .` (admonitions, code blocks, markdown cheatsheet demo, etc.) — left as reference/scratch material, not curated personal content like `gcp.md`.

## Working on this repo

- Preview changes locally: `zensical serve` (see [README.md](README.md)).
- New topic = new file in `docs/`, front matter with a relevant `icon:` (search icons at the Zensical docs), short and skimmable — these are personal reference notes, not prose documentation.
- Keep pages terse: command snippets, short explanations, links out to canonical docs rather than reproducing them (see the style of `gcp.md`).
- No build/test step beyond `zensical build`; the GitHub Action handles deployment automatically on merge to `main`.

## Capturing pasted content

João's main workflow here: he pastes in raw notes/snippets from other sessions and expects them filed away properly.

- **Public repo — screen every paste first.** Before writing anything, check for secrets, API keys, tokens, credentials, internal hostnames/URLs, customer data, or anything else that shouldn't be public. If something looks sensitive, **stop and ask** rather than committing it — don't just redact and continue silently.
- File the content into the right `.md` under `docs/`, in the appropriate location (existing page if it fits a topic already covered, new page if it's a new topic).
- Update [docs/index.md](docs/index.md) to reflect the change (e.g. a pointer/summary entry for a new page or topic), since it's the landing page.
- Free to reorganize: split, merge, rename, delete, or restructure `.md` files as needed to keep things coherent. The one hard rule: never lose meaningful information in the process, unless João explicitly says to drop it.
- Once the edits for a request are finished, commit **directly to `main`** — no feature branches or PRs for this repo. That push is what triggers the GitHub Pages deploy.
