# Lumi Nexus

Lumi Nexus is a premium AI workspace project with three main parts:

- A local Windows desktop assistant built with Python
- A premium web AI chat interface built with HTML, CSS, and JavaScript
- A mobile companion web app / PWA for Android and iPhone

The project is structured so it can be uploaded to GitHub cleanly without committing machine-specific cache files or large downloaded model assets.

## Features

### Desktop assistant

- Wake word support: `lumi`
- Female system voice preference when available
- Local text-to-speech with `pyttsx3`
- Offline speech recognition with `vosk`
- Desktop UI with a premium control-center style
- Windows actions like opening apps, folders, websites, and system tools

### Web AI interface

- Premium dark/light product UI
- Collapsible sidebar
- Chat bubbles for user and AI
- Typing indicator
- Copy buttons for assistant replies
- Markdown-style rendering for bold text, lists, inline code, and code blocks
- Sound feedback and animated particle background

### Mobile app

- Touch-first premium UI
- Installable PWA for Android and iPhone
- Home screen support
- Offline caching through a service worker
- Browser voice support where available

## Project Structure

```text
.
|-- index.html              # Main premium web UI
|-- styles.css              # Main web UI styles
|-- src/
|   |-- app.js              # Main web UI logic
|   |-- prototype.js        # Older prototype script
|   |-- gameLogic.js        # Existing utility/test logic
|-- lumi/
|   |-- actions.py          # Desktop assistant command routing
|   |-- config.py           # Desktop config
|   |-- speech.py           # Voice, model loading, TTS
|   |-- ui.py               # Premium desktop assistant UI
|-- apps/
|   |-- mobile/
|   |   |-- index.html      # Mobile companion UI
|   |   |-- styles.css      # Mobile styles
|   |   |-- app.js          # Mobile interaction logic
|   |   |-- manifest.webmanifest
|   |   |-- sw.js
|   |   |-- icons/
|-- run_lumi.py             # Desktop app entry point
|-- requirements.txt        # Python dependencies
|-- tests/
|-- esp32_wifi_ble_scanner/ # Existing Arduino-related project folder
```

## Run the Desktop App

Install Python dependencies:

```powershell
python -m pip install -r requirements.txt
```

Start Lumi:

```powershell
python run_lumi.py
```

Notes:

- The first voice start downloads a Vosk model locally into `models/`
- The `models/` directory is ignored in Git so the repository stays lightweight

## Run the Web UI

Open the file directly:

```powershell
Start-Process .\index.html
```

Or run a local server:

```powershell
python -m http.server 8000
```

Then open:

- `http://localhost:8000/` for the premium web UI
- `http://localhost:8000/apps/mobile/` for the mobile app

## Example Desktop Commands

- `lumi open notepad`
- `lumi open settings`
- `lumi open downloads`
- `lumi search google for weather in delhi`
- `lumi search youtube for lofi music`
- `lumi lock laptop`

## GitHub Upload Notes

This repo is prepared for GitHub with:

- `.gitignore` to exclude caches, virtual environments, logs, and downloaded speech models
- `requirements.txt` for easy Python setup
- `.gitattributes` for consistent line endings

Recommended upload flow:

```powershell
git init
git add .
git commit -m "Initial commit: Lumi Nexus"
git branch -M main
git remote add origin <your-github-repo-url>
git push -u origin main
```

## Important Notes

- This project is designed to stay free and local where possible
- iPhone `.ipa` builds require macOS with Xcode
- Android `.apk` builds require Android tooling that is not currently installed in this workspace
- The mobile app is currently delivered as a PWA, which can be installed on Android and iPhone home screens
