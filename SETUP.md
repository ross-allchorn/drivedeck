# DriveDeck setup

DriveDeck is a single file, `index.html`. Setup has three parts: put it online, create a Google API key, and share your music folder. It takes about 15 minutes, one time.

## 1. Put it online

Pick one of these. Both are free.

**Netlify Drop (easiest)**
1. Put `index.html` in a folder of its own, for example `drivedeck`.
2. Go to https://app.netlify.com/drop and drag that folder onto the page.
3. Netlify gives you an address like `https://something-random.netlify.app`. Sign up (free) if you want to keep it and rename it.

**GitHub Pages**
1. Create a new repository and upload `index.html`.
2. Under Settings → Pages, set the source to the main branch and save.
3. Your address will be `https://<your-username>.github.io/<repo-name>/`.

Note the address. You need it in step 2.

## 2. Create a Google API key

1. Go to https://console.cloud.google.com and create a project (for example "DriveDeck").
2. Open **APIs & Services → Library**, search for **Google Drive API**, and click **Enable**.
3. Open **APIs & Services → Credentials → Create credentials → API key**.
4. Click the new key to edit its restrictions:
   - **Application restrictions:** choose **Websites**, then add your address followed by `/*`, for example `https://something-random.netlify.app/*`.
   - **API restrictions:** choose **Restrict key**, then select only **Google Drive API**.
5. Save, then copy the key. It starts with `AIza`.

With these restrictions, the key only works on your site and only for reading publicly shared Drive files. It can't access anything private in your Google account.

## 3. Share your music folder

1. In Google Drive, right-click your music folder and choose **Share**.
2. Under General access, choose **Anyone with the link**, with the role **Viewer**.
3. Click **Copy link**.

Anyone who has this link can see and download the music in that folder. Subfolders are included.

## 4. Connect it in DriveDeck

1. Open your DriveDeck address and press **ADD** (or **SOURCES**).
2. Paste the API key and press **SAVE**.
3. Paste the folder link and press **ADD**. Repeat for more folders.
4. Use **RESCAN** on a folder after you add or remove songs in Drive.

## Local music

- **ADD FILES / ADD FOLDER**, or drag files and folders onto the player. These work in every browser, but local songs have to be added again each visit.
- **REMEMBER A FOLDER** appears in Chrome and Edge on a computer. DriveDeck then keeps that folder between visits; you click **RECONNECT** to allow access each time you open it.
- Local files never leave your device.

## Keyboard shortcuts

| Key | Action |
| --- | --- |
| Z / X / C / V / B | Previous / Play / Pause / Stop / Next |
| Space | Play or pause |
| ← / → | Seek 5 seconds |
| ↑ / ↓ | Volume |
| S / R | Shuffle / Repeat |
| Enter / Delete | Play / remove the selected playlist track |

On a computer, drag any window by its blue title bar. Windows snap to each other and to the edges of the browser, and their positions are remembered. **RESET LAYOUT** puts them back. On phones and tablets, the windows stay stacked.

The **LIGHT / DARK** button in the main title bar switches themes. Until you press it, DriveDeck follows your device's setting.

Click the time to switch between elapsed and remaining. Click the analyzer to switch between spectrum, oscilloscope and off. Double-click a slider to reset it.

## If something doesn't work

- **"This API key doesn't allow this website"**: the address in the key's website restrictions doesn't match. Include `https://` and end with `/*`.
- **"The Google Drive API isn't enabled"**: repeat step 2.2 in the same project as the key.
- **"Folder not found"**: the folder isn't shared as "Anyone with the link", or the link was copied wrong.
- **A track won't play**: the browser may not support its format. Safari, especially older versions, may not play OGG files; all major browsers handle MP3, M4A/AAC, FLAC and WAV.
- Settings, the API key and your playlists are stored in your browser only. On another device or browser, you'll enter the key again.
