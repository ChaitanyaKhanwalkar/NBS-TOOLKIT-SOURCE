# NbS Toolkit Source Code Handover

This repository contains the source code for the NbS Toolkit web application developed as the Narmada Basin Decision Support Prototype.

## Project

NbS Toolkit — Guided by Nature, Powered by Science  
Narmada Basin Decision Support Prototype

Live demo: https://fascinating-macaron-c78c7d.netlify.app/

## Included files

The handover includes:

- `frontend/` — Flutter web application
- `backend/` — FastAPI backend
- `backend/data/narmada_nbs_canonical.db` — SQLite database used for the current demo deployment
- `backend/.env.example` — sample environment settings
- `deployment/free-hosting-sqlite.md` — notes on the current free-hosting setup

## Current hosting arrangement

The current demo is hosted as follows:

- Frontend: Netlify
- Backend: Render
- Database: bundled SQLite database inside the backend deployment

The backend is currently hosted on a free plan. If it has been inactive for some time, the first request may take a short while to respond.

## Backend setup

Go to the backend folder:

    cd backend
    pip install -r requirements.txt
    python -m uvicorn app.main:app --host 127.0.0.1 --port 8000

Useful test links after starting the backend:

    http://127.0.0.1:8000/health
    http://127.0.0.1:8000/health/db
    http://127.0.0.1:8000/api/v1/reference

For hosted deployment, the backend can be started with:

    gunicorn -w 2 -k uvicorn.workers.UvicornWorker app.main:app --bind 0.0.0.0:$PORT

## Frontend setup

Go to the frontend folder:

    cd frontend
    flutter pub get
    flutter build web --release --dart-define=API_BASE_URL=https://nbs-gct.onrender.com

The web build is created in:

    frontend/build/web

## Security note

Private environment files, deployment tokens, Azure credentials, Render credentials, and other account-specific secrets are not included in this source-code handover.
