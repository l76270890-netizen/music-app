# TuneIt FastAPI backend

This development API stores account information, local-song metadata, favorites, and playlists. Audio files and device file paths stay on the phone.

## Start the API on Windows

From the project root in PowerShell:

```powershell
py -m venv backend\.venv
backend\.venv\Scripts\Activate.ps1
py -m pip install -r backend\requirements.txt
Copy-Item backend\.env.example backend\.env
Set-Location backend
uvicorn main:app --reload --env-file .env
```

Open `http://127.0.0.1:8000/docs` for the interactive API docs and `http://127.0.0.1:8000/health` for its health check. SQLite creates `backend/music.db` on first start.

Before deployment, set `APP_ENV=production`, set `JWT_SECRET` to a random value with at least 32 characters, and use PostgreSQL through `DATABASE_URL`. The app refuses to start in production mode with the development secret. The PostgreSQL driver is included in `requirements.txt`.

## Connect the Expo app

Copy the root `.env.example` to `.env` and set `EXPO_PUBLIC_API_URL` to the address the phone can reach. Use `http://10.0.2.2:8000` for the Android emulator, `http://127.0.0.1:8000` for web on the same computer, or the computer's LAN IP (for example `http://192.168.1.20:8000`) for a physical phone on the same Wi-Fi. Restart Expo after changing `.env`.

The API supports registration, login, account lookup, local-song metadata sync, favorites, playlist CRUD, and playlist-song membership. It does not provide an audio catalog or music downloads.
