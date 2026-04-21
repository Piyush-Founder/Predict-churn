# Churn Predictor — Render Deployment Guide

## Folder Structure
```
churn_predictor/
├── main.py
├── requirements.txt
├── render.yaml
├── xgboost_churn_model.pkl
├── feature_columns.pkl
├── static/
│   ├── home.css
│   ├── about.css
│   ├── predict.css
│   └── script.js
└── templates/
    ├── home.html
    ├── about.html
    └── predict.html
```

## Deploy to Render

1. Push this entire folder to a GitHub repository (public or private).
2. Go to https://render.com → New → Web Service
3. Connect your GitHub repo
4. Set these values:
   - **Build Command:** `pip install -r requirements.txt`
   - **Start Command:** `uvicorn main:app --host 0.0.0.0 --port $PORT`
   - **Environment:** Python 3
5. Click **Deploy** — done!

## Routes
| URL | Page |
|-----|------|
| `/` | Home |
| `/predict-page` | Prediction Form |
| `/about` | About Model |
| `/predict` | POST API endpoint |

## What was fixed for Render
- CSS links changed from `home.css` → `/static/home.css` in all templates
- JS fetch URL changed from `http://127.0.0.1:8000/predict` → `/predict` (relative)
- All nav `href` links updated to FastAPI routes (`/`, `/about`, `/predict-page`)
- `requirements.txt` pinned to stable compatible versions
- `render.yaml` added for one-click deployment
