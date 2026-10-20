# Friday Night Video

A 90s video store front-end for Stremio, built to run on a Samsung TV through TizenBrew.

## What's in here

- `app/index.html` – the whole store (one file). Open it in any browser to try it with the arrow keys.
- `package.json` – tells TizenBrew the app's name and which remote buttons it uses.

## Remote controls

- Arrows: browse the shelves
- OK: pick up a case, then Rent it
- Back: put it back (from the shelves, Back steps outside)
- Red: Ask the clerk (with double features) · Green: Rewind Night · Yellow: Return slot · Blue: store sounds on/off
- On a box: Flip the box to read the back (synopsis, cast, director and IMDb rating from Stremio)
- Search: "Do you have…?" at the counter searches Stremio for movies and TV
- Front desk: rename the store, put your name on your membership card, sounds, CRT trailers or stills, Stremio sign-in, and Test my setup

## Outside the store

The app opens in the parking lot at dusk, with your store's name on the pole sign and this week's new release on the marquee. Press OK to walk in; Back from the shelves takes you outside again, and Back outside closes the app. The shelves stock themselves while you're outside. At the Front desk, "Front door" switches between Always sunset, Follows the clock (day, golden hour, sunset, night, closed after midnight) and Skip it.

## Around the store

- Television aisle, plus a seasonal aisle, banner and cardboard standee (Halloween in October, Holiday Hits in December, Summer Blockbusters in January, Date Night in February)
- Blind Date: brown-paper tapes showing only the blurb. Unwrap or rent unseen
- Late fees: anything in Continue Watching untouched for two weeks gets a LATE sticker
- After 10pm the store dims; at 11:45pm there's a closing announcement
- Leave the remote for 3 minutes and the CRT goes full screen as a demo loop

## Playing tapes

Everything plays inside the store. When you rent a tape, the store asks your Stremio addons (Torrentio with Real-Debrid included) for copies and ranks them: instant 4K non-HDR first, then the highest-quality instant copy, then plain torrents, then debrid copies that aren't cached yet. Dolby Vision-only files go to the back because Samsung TVs can't show Dolby Vision. Change the order in Front desk > Player settings.

While a tape plays: OK pauses, left and right skip 10 and 30 seconds, rewind and fast-forward jump a minute, down opens options (subtitles, audio, another copy, VHS look), and Back stops. Progress saves to your Stremio account so Continue Watching stays in sync.

Plain torrents (no debrid) need Stremio's streaming server: run Stremio on a computer at home and enter `http://that-computer's-address:11470` in Player settings.

## Your Stremio account

Open the **Front desk** and choose **Stremio: Sign in**. The TV shows a 4-letter code: go to link.stremio.com on your phone and enter it. You'll get aisles for Continue Watching, Your Shelf (your library) and catalogs from addons you've installed.

## Staff Picks from Letterboxd

Install the Stremboxd addon in Stremio (stremboxd.com/configure, username-only mode is enough) with its Popular catalog turned on. Staff Picks then fills itself from it. Without it, the Staff Picks aisle is hidden.

## Putting it on the TV

1. Make a free GitHub account and a new **public** repository called `friday-night-video`.
2. Upload `package.json`, `README.md` and the `app` folder to it.
3. On the TV, open TizenBrew, add a module, choose GitHub and type `your-username/friday-night-video`.
4. Launch Friday Night Video from TizenBrew.

When you change something, upload the new files to GitHub and refresh the module in TizenBrew.
