# Lessons

- **Custom front-matter keys can clash with Quarto's reserved ones.** An event field named `format:` broke the render ("Unknown format Hybrid") because Quarto reads `format` as the output format. Fix: renamed it to `attendance`. Rule: give custom metadata distinctive names (check the Quarto front-matter reference before using a generic name like `format`, `type`, `engine`, `execute`).
- **SVGs without `width`/`height` can collapse to zero size.** The navbar logo was invisible because an SVG with only a `viewBox` has no intrinsic size inside a flex container. Rule: always give SVG files `width` and `height` attributes.
- **Quarto only copies files it sees referenced in page content.** An image used only from listing YAML (`image-placeholder`) was missing from `_site/`. Rule: list such folders under `project: resources:` in `_quarto.yml`.
- **`quarto publish gh-pages --no-prompt` won't create the `gh-pages` branch.** Rule: create an empty orphan `gh-pages` branch with git plumbing (`git commit-tree` on the empty tree) and push it right after `main`, so `main` stays the default branch.
- **GitHub turns on Pages automatically for `<org>.github.io` repos, serving `main`.** That serves the Quarto source, not the site. Rule: switch the Pages source to `gh-pages` with `gh api -X PUT repos/OWNER/REPO/pages -f "source[branch]=gh-pages" -f "source[path]=/"`.
- **Quarto adds the site title to every page's `<title>`.** A home-page `pagetitle` that already contained the site name showed it twice. Rule: never put the site name in `pagetitle` or `title`.
