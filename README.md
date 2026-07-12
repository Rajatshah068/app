# Snake — terminal edition

A single-file, dependency-free Snake game with a retro CRT-terminal look.
Arrow keys / WASD to move, Space to pause, on-screen d-pad on touch devices.
High score persists in the browser via `localStorage`.

## Run locally

Just open `index.html` in a browser, or serve it:

commentdcndlcndcldc

```bash
python3 -m http.server 8080
# then visit http://localhost:8080
```

## Deploy to SAP BTP Cloud Foundry

This repo is already set up for the `staticfile_buildpack` (see `Staticfile`
and `manifest.yml`) — no server code needed.

```bash
# 1. Log in to your SAP BTP Cloud Foundry environment
cf login -a https://api.cf.<region>.hana.ondemand.com

# 2. Target the right org/space
cf target -o <your-org> -s <your-space>

# 3. Push the app (from this folder)
cf push
```

`manifest.yml` uses `random-route: true` so CF assigns a unique URL —
run `cf apps` afterward to see it, or check `cf app snake-game`.

If your subaccount uses a different region, swap the API endpoint above
(find yours in the BTP cockpit under your Cloud Foundry environment
instance → "API Endpoint").

## Publish to Git

```bash
git init
git add .
git commit -m "Initial commit: terminal-style Snake game"
git branch -M main
git remote add origin <your-repo-url>   # e.g. git@github.com:you/snake-game.git
git push -u origin main
```

## Project structure

```
snake-game/
├── index.html      # game (HTML/CSS/JS, no build step)
├── Staticfile       # marks this as a static site for the CF buildpack
├── manifest.yml      # cf push config
├── .gitignore
└── README.md
```
