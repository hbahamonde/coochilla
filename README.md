# Coochilla booking website

A booking dossier for venues, agents and promoters, published with GitHub Pages.

## Automatic Spotify updates

GitHub Actions reads Coochilla's public Spotify artist page every Monday at
10:15 Europe/Helsinki and republishes the website. It runs in GitHub's cloud;
no Mac, signed-in browser, API subscription or Spotify password is required.
The website does not poll every minute. It reads the published data when opened.
Code pushes and manually dispatched runs also publish and check the public counts.

Monthly listeners and followers come from exact values in the public page.
This is a public-page integration, not an official Spotify analytics API. If
Spotify changes the page or blocks access, the workflow fails visibly and
retains the previous valid data with its original check date.

The expandable Spotify for Artists snapshot contains historical private
dashboard metrics with their own reporting dates. Streams, saves, playlist
adds and monthly active listeners are **not** refreshed by the public-page job.
Refreshing those fields requires a separately supported analytics source.

## Editing

Edit `site/content.js` for band information, materials and approved shows.
Production details and footage without supplied material stay hidden.
The `site/` directory alone is deployed. Email outreach and private tour planning
do not belong in this repository.

Run `python3 tools/refresh_spotify.py` to check the public counts and
`python3 tools/validate_site.py` to validate the generated files.
