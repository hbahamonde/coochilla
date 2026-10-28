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

## Live photography

The four supplied concert photographs appear near the top of the dossier.
Select a thumbnail, use the arrow buttons or keyboard arrows, or swipe on a
touchscreen. Opening a photo displays a full-size viewer with a download link;
Escape closes it. Portrait and landscape images are shown without cropping.
The gallery has no automatic rotation. Original JPEGs are in `site/assets/`,
and `site/gallery.js` controls the viewer. Image links also work without JavaScript.

## Technical rider

The production section includes the audience-view stage plot and a six-feed
band input list, with drum inputs added to suit the agreed kit. Both guitarists
sing backing vocals; lead vocals are central, with bass back-left and drums
back-right. Both guitars and bass use DI/IR routing, with PA-only operation
and optional house cabinets by advance.

PDF downloads and the SVG plot are in `site/assets/`. Rebuild them with
`python3 tools/build_rider.py` in an environment with ReportLab installed.
Set length, exact instrument outputs, drum/backline supply, monitor allocation
and cabinet amplification are agreed with each venue.
