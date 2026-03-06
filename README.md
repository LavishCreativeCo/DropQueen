# 👑 DropQueen — AI-Powered Demand & Sales Forecasting Engine

**Course:** CISC 610 — DevOps and MLOps | Mercy University | Spring 2026  
**Author:** Chastity Lewis

---

## 🚀 Quick Start

### Run with Docker
```bash
# Build and start all services
docker-compose up --build

# API will be live at:
# http://localhost:5000

# MLflow UI will be live at:
# http://localhost:5001
```

### Run locally
```bash
pip install -r requirements.txt
python app.py
```

---

## 📡 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /health | Health check |
| POST | /predict/demand | Predict product demand spike |
| POST | /predict/trend | Predict TikTok engagement level |
| GET | /products/top | Get top predicted drops |
| GET | /models/versions | List model metadata |

---

## 🧠 Models
- **Demand Spike Model** — Random Forest (87% accuracy)
- **TikTok Engagement Model** — Logistic Regression

---

## 🛠️ Tech Stack
Python · Flask · scikit-learn · Docker · GitHub Actions · MLflow · AWS
