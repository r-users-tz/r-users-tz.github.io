# Lessons

- **Custom front-matter keys can clash with Quarto's reserved ones.** An event field named `format:` broke the render ("Unknown format Hybrid") because Quarto reads `format` as the output format. Fix: renamed it to `attendance`. Rule: give custom metadata distinctive names (check the Quarto front-matter reference before using a generic name like `format`, `type`, `engine`, `execute`).
- **SVGs without `width`/`height` can collapse to zero size.** The navbar logo was invisible because an SVG with only a `viewBox` has no intrinsic size inside a flex container. Rule: always give SVG files `width` and `height` attributes.
- **Quarto only copies files it sees referenced in page content.** An image used only from listing YAML (`image-placeholder`) was missing from `_site/`. Rule: list such folders under `project: resources:` in `_quarto.yml`.
