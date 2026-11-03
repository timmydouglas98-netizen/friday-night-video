# Friday Night Video

A 90s video store front-end for Stremio, built to run on a Samsung TV through TizenBrew.

## What's in here

- `app/store.html` – the whole store (one file). Open it in any browser to try it with the arrow keys.
- `app/index.html` – the loader TizenBrew opens: a title card while it fetches the store, and the safety net described under "Updating".
- `release.json` – which tagged release the TVs run.
- `package.json` – tells TizenBrew the app's name and which remote buttons it uses.

Nothing else belongs at the top level: the store always lives in `app/store.html`.

## Remote controls

- Arrows: browse the shelves
- OK: pick up a case, then Rent it
- Back: put it back (from the shelves, Back steps outside)
- Red: Ask the clerk (with double features) · Green: Rewind Night · Yellow: Return slot · Blue: store sounds on/off
- On a box: Flip the box to read the back (synopsis, cast, director and IMDb rating from Stremio)
- Search: "Do you have…?" at the counter searches Stremio for movies and TV
- Front desk: rename the store, your membership card (with your rental stats), Stremio sign-in, sounds, atmosphere, weather and the front door
- Front desk > Staff only: back office: player settings, corner TV trailers or stills, the clerks' lists, Test my setup, Diagnostics, Reset this TV

## Outside the store

The whole app is drawn like a late-90s TV cartoon: painted backgrounds, inked cels, animation on twos, film grain. It opens on a title card, then the camera eases down from the sky onto the parking lot at dusk, with your store's name on the pole sign and this week's new release on the marquee. Whoever is on shift (Dave by day, Gus by night) is behind the counter in the window. Press OK and the camera pushes in on the door and irises through to the shop floor; Back from the shelves takes you outside again, and Back outside closes the app. The shelves stock themselves while you're outside. At the Front desk, "Front door" switches between Always sunset, Follows the clock (day, golden hour, sunset, night, closed after midnight) and Skip it.

## Around the store

- Television aisle, plus a seasonal aisle, banner and cardboard standee (Halloween in October, Holiday Hits in December, Summer Blockbusters in January, Date Night in February)
- Blind Date: brown-paper tapes showing only the blurb. Unwrap or rent unseen
- Put it on hold: on any box, "Put it on hold" slips a name card under a rubber band and keeps the tape behind the counter in the On Hold aisle. Signed in to Stremio, it also goes into your Stremio library so it's waiting on your phone too. Renting it picks it up
- Fresh stock: every aisle draws on several of Stremio's lists (this week's popular titles plus the featured list), restocks a little differently each day, and fills in more as you browse to the end. Each title lives in one section, so the same blockbusters don't front every aisle
- New Releases are this year's and last year's films only. Rewind Night turns them into the new releases of the year you rewound to
- Classics: popular films from eight years between 1960 and 1999, a different eight each day. Animation has its own aisle
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
2. Upload `package.json`, `release.json`, `README.md` and the `app` folder to it.
3. Publish a release: on the repository page choose **Releases > Draft a new release**, type `v2` as the tag, and **Publish**.
4. On the TV, open TizenBrew, add a module, choose GitHub and type `your-username/friday-night-video`, then pick release `v2`.
5. Launch Friday Night Video from TizenBrew.

## Updating

TVs run the release named in `release.json`, not whatever was uploaded last, so a half-finished upload never reaches the TV.

1. Upload the new `app/store.html` (into the `app` folder, replacing the old one). Bump `APP_VERSION` near the top of its script, e.g. `0.17.1`.
2. Publish a new release with the next tag (`v3`, `v4`, …).
3. Edit `release.json` so `ref` is the new tag and `version` matches `APP_VERSION`, and commit it.

Each TV picks the release up the next time it opens. It keeps the store saved, so opening the app doesn't download it again until there's a new release. A new release only replaces the saved copy once it has opened and stayed up for a few seconds. If it fails to open twice, the TV skips it and goes on using the last good one; Front desk > back office > Diagnostics shows which release the TV is on and whether it skipped one.

You only need to change the release TizenBrew points at when `app/index.html` itself changes.
