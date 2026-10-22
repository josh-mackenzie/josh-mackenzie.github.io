# josh-mackenzie.github.io
Website hosting for joshmackenzie.co.uk

## Running locally

Needs Ruby 3.3 with DevKit (`winget install RubyInstallerTeam.RubyWithDevKit.3.3`).

```sh
cd docs
bundle install        # first time only
bundle exec jekyll serve --livereload
```

Then open http://localhost:4000. Edits reload automatically, except `_config.yml`, which needs a restart.

## Updating the CV

All CV content lives in `docs/_data/cv.yml`. It feeds both the homepage and the printable CV at `/cv/`.

After editing it, regenerate the PDF from the local server (with `jekyll serve` running) and commit it alongside the change:

```sh
"/c/Program Files/Google/Chrome/Application/chrome.exe" --headless=new --virtual-time-budget=5000 \
  --no-pdf-header-footer --print-to-pdf=docs/assets/pdf/josh-mackenzie-cv.pdf http://localhost:4000/cv/
```

Or open http://localhost:4000/cv/ in a browser and print to PDF with margins set to "None". Check it's still one page.

## Link preview image

`docs/assets/img/og.png` is the image shown when the site is shared (LinkedIn, Slack, etc.). Its source is `tools/og-card.html`; after editing, regenerate it:

```sh
"/c/Program Files/Google/Chrome/Application/chrome.exe" --headless=new --hide-scrollbars --virtual-time-budget=6000 \
  --window-size=1200,630 --screenshot=docs/assets/img/og.png "file:///$PWD/tools/og-card.html"
```
