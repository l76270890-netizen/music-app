# TuneIt

TuneIt is a local music player built with Expo. It can scan audio exposed by an Android or iOS media library, or import audio files you choose. Playback uses the on-device file; TuneIt does not include downloads or a remote streaming catalog in this version.

## Run the app

From this folder in PowerShell:

```powershell
npm install
npm run dev
```

Expo will show a QR code and available launch options. Use the Expo Go app for the development preview. Native media scanning and background playback require a native Android or iOS app; on web, use **Add audio files**. If you prefer the explicit Expo commands, use `npm run android`, `npm run ios`, or `npm run web`.

## Use the local library

Open **Local Music** and allow audio access when prompted, then choose **Scan device**. Or select **Add audio files** to import audio into TuneIt's private app storage. Select a song to play; the library, likes, playlists, and recently played list are saved on this device. In a web preview, reselect imported files after reloading the page because browsers do not keep those local file handles.

## Optional account sync backend

The FastAPI backend syncs account details and song metadata, favorites, and playlists. It does not upload audio files or local file paths. Follow [backend/README.md](backend/README.md) to run it, then copy `.env.example` to `.env` and set `EXPO_PUBLIC_API_URL` to an address reachable by the app. Restart Expo after changing `.env`.

Use `http://127.0.0.1:8000` when running the app in a desktop browser on the same computer, `http://10.0.2.2:8000` from the Android emulator, or the computer's LAN IP from a physical phone on the same Wi-Fi.

## Main routes

- `/` — home
- `/search` — search local tracks
- `/library` — device library and playlists
- `/playlists` — playlists
- `/favorites` — liked songs
- `/downloads` — local audio files available offline
- `/local-music` — scan or import audio
- `/player/:id` — player
- `/account` — optional account and sync
