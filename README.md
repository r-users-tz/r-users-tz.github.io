# Tanzanian R Users: community website

The website of **Tanzanian R Users** (*Jumuiya ya Watumiaji wa R Tanzania*), built with [Quarto](https://quarto.org/).

**Live site:** <https://r-users-tz.github.io>

## Preview the site on your computer

You need [Quarto](https://quarto.org/docs/get-started/) and R, with the `knitr`, `rmarkdown`, `dplyr` and `ggplot2` packages.

```bash
quarto preview
```

This opens the site in your browser and reloads it whenever you save a file. In RStudio, open `Rcommunity-website.Rproj` and use the **Render** button.

## What's where

| Path | What it is |
|---|---|
| `_quarto.yml` | Site settings: title, navigation bar, footer, theme |
| `_variables.yml` | **Links and contact details used across the site.** Edit these first |
| `index.qmd` | Home page |
| `about.qmd`, `resources.qmd`, `join.qmd`, `code-of-conduct.qmd` | The main pages |
| `events.qmd` + `events/` | Events list and one folder per event |
| `blog.qmd` + `posts/` | Blog list and one folder per post |
| `_templates/` | Templates for new events and posts, and the event-list layout |
| `theme/` | Colours and styles (`light.scss`, `dark.scss`, `common.scss`) |
| `images/` | Logo, placeholder images and the social-media preview card |
| `_freeze/` | Saved results of R code. **Commit this folder** |
| `_site/` | The built website. Generated: don't edit, don't commit |

## Before you launch

Every placeholder contains `TODO`. List them all with:

```bash
grep -rn "TODO" --include="*.qmd" --include="*.yml" .
```

1. **`_variables.yml`**: community email, WhatsApp and Meetup links and the talk-proposal form.
2. **`_quarto.yml`**: uncomment the social icons you use (GitHub and LinkedIn are already on).
3. **`about.qmd`**: write the "Our story" section in your own words, and add organiser photos to `images/people/`.
4. **`events/2026-12-12-launch-meetup/`**: confirm the date, time and venue, and add the registration link. Delete the folder if you don't want this event.
5. **Posts**: change `author:` in the two starter posts if you'd like them under your name.

## Add an event

1. Copy `_templates/event-template.qmd` to `events/YYYY-MM-DD-short-name/index.qmd`.
2. Fill in the fields at the top: `title`, `date`, `time`, `location`, `attendance`, `description`.
3. Render or preview the site.

Events are sorted automatically. An event is listed under **Upcoming** until its date has passed, then moves to **Past** the next time the site is rebuilt. The GitHub workflow rebuilds the site every Monday so this happens on its own. After an event, add links to slides and recordings on its page.

## Add a blog post

1. Copy `_templates/post-template.qmd` to `posts/YYYY-MM-DD-short-name/index.qmd`, and put any images in the same folder.
2. Write the post. R code chunks are run when you render.
3. Run `quarto render`, then commit the post **and** the new files in `_freeze/`.

## Publishing

The site is hosted on GitHub Pages from the [`r-users-tz/r-users-tz.github.io`](https://github.com/r-users-tz/r-users-tz.github.io) repository:

- `main` holds the source (this folder).
- `gh-pages` holds the built site. Don't edit it by hand.

Every push to `main` rebuilds and republishes the site automatically, and so does a weekly run every Monday (see `.github/workflows/publish.yml`). Check progress in the repository's **Actions** tab. To publish straight from your computer instead, run `quarto publish gh-pages`.

To use your own domain (for example `tanzania-r.org`), add it under **Settings → Pages → Custom domain** and set `site-url` in `_quarto.yml` to match.
