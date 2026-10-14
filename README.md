# DriveDeck

A retro desktop-style music player that runs in the browser. It plays music from shared Google Drive folders and from your own device, with a spectrum analyzer, a 10-band equalizer and a playlist window.

**Live player:** https://ross-allchorn.github.io/drivedeck/

## Features

- **Two kinds of source in one playlist:** Google Drive folders shared as "Anyone with the link" and local files or folders. Subfolders are included, and each track is marked DRV or LOC.
- **Main window:** scrolling track title, elapsed or remaining time, bitrate, seek bar, volume and balance, shuffle and repeat (all or one track).
- **Visualizer:** spectrum analyzer with falling peaks, or oscilloscope.
- **Equalizer:** 10 bands plus preamp, with presets such as Rock, Pop, Classical and Bass boost.
- **Playlist:** search, saved playlists, track durations, and a running total.
- **Desktop layout:** drag windows by their title bars. They snap to each other and to the edges, and the layout is remembered.
- **Phone layout:** windows stack and stay fixed, with larger touch targets. Lock-screen and headphone controls work.
- **Light and dark themes:** follows your device's setting until you choose one.

It's a single static page with no build step, server or account. Everything you enter (API key, folders, playlists, layout) is stored only in your browser.

## Setup

You need a Google API key and a shared Drive folder. This takes about 10 minutes, one time.

### 1. Create a Google API key

1. Go to https://console.cloud.google.com and create a project (for example "DriveDeck").
2. Open **APIs & Services → Library**, search for **Google Drive API**, and click **Enable**.
3. Open **APIs & Services → Credentials → Create credentials → API key**.
4. Click the new key to edit its restrictions:
   - **Application restrictions:** choose **Websites**, then add `https://ross-allchorn.github.io/drivedeck/*`. If you host your own copy, use that address instead, ending with `/*`.
   - **API restrictions:** choose **Restrict key**, then select only **Google Drive API**.
5. Save, then copy the key. It starts with `AIza`.

With these restrictions, the key only works on the DriveDeck site and only for reading publicly shared Drive files. It can't access anything private in your Google account. Don't commit the key to this repository; you paste it into the player instead.

### 2. Share your music folder

1. In Google Drive, right-click your music folder and choose **Share**.
2. Under General access, choose **Anyone with the link**, with the role **Viewer**.
3. Click **Copy link**.

Anyone who has this link can see and download the music in that folder, including its subfolders.

### 3. Connect it in DriveDeck

1. Open the player and press **ADD** (or **SOURCES**).
2. Paste the API key and press **SAVE**.
3. Paste the folder link and press **ADD**. Repeat for more folders.
4. Use **RESCAN** on a folder after you add or remove songs in Drive.

### Local music

- **ADD FILES** / **ADD FOLDER**, or drag files and folders onto the player. This works in every browser, but local songs have to be added again on each visit.
- **REMEMBER A FOLDER** appears in Chrome and Edge on a computer. DriveDeck then keeps that folder between visits; click **RECONNECT** to allow access each time you open the player.
- Local files never leave your device.

## Using the player

| Key | Action |
| --- | --- |
| Z / X / C / V / B | Previous / Play / Pause / Stop / Next |
| Space | Play or pause |
| ← / → | Seek 5 seconds |
| ↑ / ↓ | Volume |
| S / R | Shuffle / Repeat |
| Enter / Delete | Play / remove the selected playlist track |

- Double-click a track to play it. On a phone, tap it.
- Click the time to switch between elapsed and remaining.
- Click the analyzer to switch between spectrum, oscilloscope and off.
- Double-click a slider to reset it.
- **EQ** and **PL** show or hide the equalizer and playlist windows.
- **RESET LAYOUT** puts dragged windows back in their original positions.
- **LISTS** saves the current playlist or loads a saved one. Drive tracks always reload; local tracks reload only when their files or folder are connected.

## Troubleshooting

The yellow message under the playlist explains most problems.

- **"This API key doesn't allow this website"**: the address in the key's website restrictions doesn't match the page. Include `https://` and end with `/*`.
- **"The Google Drive API isn't enabled"**: enable it (step 1.2) in the same Google Cloud project as the key.
- **"Folder not found"**: the folder isn't shared as "Anyone with the link", or the link was copied wrong.
- **A track won't play**: the browser may not support its format. All major browsers handle MP3, M4A/AAC, FLAC and WAV. Safari, especially older versions, may not play OGG.
- **The key or playlists are missing:** they're stored per browser. On another device or browser, enter the key again.
- **The favicon or a change doesn't show up:** do a hard refresh (Ctrl+Shift+R, or Cmd+Shift+R on a Mac). GitHub Pages can take a couple of minutes to publish an update.

## Hosting your own copy

DriveDeck is plain HTML, so any static host works.

- **GitHub Pages:** fork or copy this repository, then under **Settings → Pages** choose **Deploy from a branch**, branch **main**, folder **/ (root)**. The address is `https://<username>.github.io/<repo-name>/`.
- **Netlify Drop:** put `index.html`, `favicon.svg` and `apple-touch-icon.png` in a folder and drag it onto https://app.netlify.com/drop.

Then add the new address to your API key's website restrictions.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole player: markup, styles and script |
| `favicon.svg` | Browser tab icon |
| `apple-touch-icon.png` | Home-screen icon on phones |
