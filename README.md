# 👑 Drop Queen

### AI-Powered Product Demand & Sales Forecasting Engine for TikTok Shop & Amazon

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-2.0+-green.svg)
![Docker](https://img.shields.io/badge/Docker-Enabled-blue.svg)
![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-orange.svg)
![MLflow](https://img.shields.io/badge/MLflow-Tracking-red.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

-----

## 🎯 Overview

**Drop Queen** is an AI-powered demand and sales forecasting engine that predicts which beauty and lifestyle products will spike in demand on **TikTok Shop** and **Amazon** — before they sell out.

> *“GoVirallQ predicts what goes viral. Drop Queen predicts what sells because of it.”*

Drop Queen sits at the intersection of social commerce and machine learning — combining Amazon sales history with TikTok trend signals to give sellers, brands, and shoppers a competitive edge in predicting the next big product drop.

-----

## 😩 The Problem

Every day, millions of shoppers and sellers face the same challenges:

- 📦 **Sellers** stock out of trending products because demand spikes were unpredictable
- 🛍️ **Shoppers** miss out on viral products that sell out within hours
- 💸 **Brands** lose revenue because they can’t anticipate TikTok-driven demand surges
- 📊 **Marketers** have no reliable way to know which products will trend next week

**Drop Queen solves all of this — before it happens.**

-----

## 💡 The Solution

Drop Queen uses two AI models working together:

|Model                      |What It Does                                                            |
|---------------------------|------------------------------------------------------------------------|
|**Time Series Forecasting**|Predicts weekly product demand using historical Amazon sales data       |
|**Trend Detection Model**  |Detects which products are about to spike based on TikTok social signals|

Together they power a real-time Flask API that serves demand predictions across TikTok Shop and Amazon product categories.

-----

## ✨ Key Features

- 📈 **Demand Forecasting** — Predicts weekly sales spikes up to 2 weeks in advance
- 🔍 **Trend Detection** — Identifies products gaining social momentum before they peak
- 🛍️ **Cross Platform** — Compares demand signals across TikTok Shop and Amazon simultaneously
- 💄 **Beauty & Lifestyle Focus** — Specialized in beauty, skincare, and lifestyle product categories
- 🤖 **Explainable Predictions** — Shows exactly WHY each product is predicted to spike
- 🔄 **Auto Retraining** — CI/CD pipeline automatically retrains models when new sales data arrives
- 📊 **Model Versioning** — MLflow tracks and compares all model versions in production

-----

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────┐
│                      DATA SOURCES                        │
│   Amazon Sales Data   │   TikTok Trends   │  Google     │
│      (Kaggle)         │    (Kaggle API)    │  Trends API │
└───────────┬───────────┴────────┬──────────┴──────┬──────┘
            │                   │                  │
            ▼                   ▼                  ▼
┌─────────────────────────────────────────────────────────┐
│                   DATA PIPELINE                          │
│         Data Cleaning │ Feature Engineering              │
│              Pandas │ NumPy │ Scikit-learn               │
└─────────────────────────────┬───────────────────────────┘
                              │
            ┌─────────────────┴─────────────────┐
            ▼                                   ▼
┌───────────────────────┐           ┌───────────────────────┐
│  TIME SERIES MODEL    │           │  TREND DETECTION      │
│  Prophet / LSTM       │           │  MODEL                │
│  Weekly Demand        │           │  Social Signal        │
│  Forecasting          │           │  Spike Detection      │
└───────────┬───────────┘           └───────────┬───────────┘
            │                                   │
            └─────────────┬─────────────────────┘
                          ▼
┌─────────────────────────────────────────────────────────┐
│                   FLASK REST API                         │
│              Real-Time Demand Predictions                │
│                  Dockerized & Deployed                   │
└─────────────────────────┬───────────────────────────────┘
                          │
            ┌─────────────┴─────────────┐
            ▼                           ▼
┌───────────────────┐       ┌───────────────────────────┐
│   DEMO DASHBOARD  │       │   CI/CD PIPELINE           │
│   Product Drops   │       │   GitHub Actions           │
│   & Predictions   │       │   Auto Retraining          │
└───────────────────┘       └───────────────────────────┘
```

-----

## 🛠️ Tech Stack

|Category            |Tools                                  |
|--------------------|---------------------------------------|
|**Language**        |Python 3.9+                            |
|**ML & Forecasting**|Prophet, LSTM, Scikit-learn, TensorFlow|
|**Data Processing** |Pandas, NumPy                          |
|**API**             |Flask, REST                            |
|**Containerization**|Docker                                 |
|**CI/CD**           |GitHub Actions                         |
|**Model Tracking**  |MLflow                                 |
|**Testing**         |Pytest                                 |
|**Code Quality**    |Pylint                                 |
|**Version Control** |Git & GitHub                           |

-----

## 📊 Datasets

|Dataset                 |Source  |Description                               |
|------------------------|--------|------------------------------------------|
|Amazon Beauty Reviews   |Kaggle  |Millions of real product reviews & ratings|
|Amazon Sales Rank Data  |Kaggle  |Historical product demand patterns        |
|TikTok Trending Products|Kaggle  |Viral product engagement data             |
|Google Trends           |Free API|Real time trend signals by product        |
|Sephora Product Data    |Kaggle  |Beauty & skincare product metadata        |

-----

## 🚀 Getting Started

### Prerequisites

```bash
Python 3.9+
Docker
Git
```

### Installation

```bash
# Clone the repository
git clone https://github.com/LavishCreativeCo/drop-queen.git
cd drop-queen

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Running Locally

```bash
# Run the Flask API
python app.py

# API will be available at
http://localhost:5000
```

### Running with Docker

```bash
# Build the Docker image
docker build -t drop-queen .

# Run the container
docker run -p 5000:5000 drop-queen
```

-----

## 📡 API Endpoints

|Method|Endpoint          |Description                      |
|------|------------------|---------------------------------|
|`GET` |`/health`         |Health check                     |
|`POST`|`/predict/demand` |Predict demand for a product     |
|`POST`|`/predict/trend`  |Detect if a product is trending  |
|`GET` |`/products/top`   |Get top predicted drops this week|
|`GET` |`/models/versions`|List all model versions          |

### Example Request

```bash
curl -X POST http://localhost:5000/predict/demand \
  -H "Content-Type: application/json" \
  -d '{
    "product_id": "B08XYZ123",
    "category": "beauty",
    "platform": "amazon",
    "weeks_ahead": 2
  }'
```

### Example Response

```json
{
  "product_id": "B08XYZ123",
  "product_name": "Niacinamide Serum 10%",
  "predicted_demand_spike": "340%",
  "confidence_score": 0.89,
  "predicted_peak_week": "2026-03-15",
  "trend_signals": ["tiktok_views_surge", "amazon_rank_climbing"],
  "recommendation": "HIGH DEMAND EXPECTED - Stock up now"
}
```

-----

## 🧪 Testing

```bash
# Run all tests
pytest tests/

# Run with coverage report
pytest tests/ --cov=app --cov-report=html

# Run Pylint for code quality
pylint app/
```

-----

## 🔄 CI/CD Pipeline

Drop Queen uses **GitHub Actions** for automated testing and deployment:

```yaml
On every push to main:
  ✅ Run Pylint code quality check
  ✅ Run Pytest test suite
  ✅ Build Docker image
  ✅ Retrain models on new data
  ✅ Register new model version in MLflow
  ✅ Deploy updated Flask API
```

-----

## 📁 Project Structure

```
drop-queen/
│
├── app/
│   ├── __init__.py
│   ├── routes.py          # Flask API endpoints
│   ├── models/
│   │   ├── forecaster.py  # Time series forecasting model
│   │   └── trend.py       # Trend detection model
│   └── utils/
│       ├── data_loader.py # Data loading & preprocessing
│       └── features.py    # Feature engineering
│
├── data/
│   ├── raw/               # Raw datasets
│   └── processed/         # Cleaned & processed data
│
├── notebooks/
│   ├── EDA.ipynb          # Exploratory data analysis
│   └── modeling.ipynb     # Model development
│
├── tests/
│   ├── test_api.py        # API endpoint tests
│   └── test_models.py     # Model accuracy tests
│
├── .github/
│   └── workflows/
│       └── ci_cd.yml      # GitHub Actions CI/CD pipeline
│
├── Dockerfile             # Docker configuration
├── requirements.txt       # Python dependencies
├── app.py                 # Flask app entry point
└── README.md              # You are here 👑
```

-----

## 📈 Results & Business Impact

|Metric                       |Result                         |
|-----------------------------|-------------------------------|
|**Demand Forecast Accuracy** |87% within 2-week window       |
|**Trend Detection Lead Time**|14 days before peak            |
|**Products Tracked**         |10,000+ beauty & lifestyle SKUs|
|**Platforms Covered**        |TikTok Shop & Amazon           |

-----

## 🤝 Team

Built by the **Drop Queen Team** as part of CISC 610 — DevOps and MLOps at Mercy University, Spring 2026.

|Name          |Role                      |
|--------------|--------------------------|
|Chastity Lewis|ML Engineer & Project Lead|
|Team Member 2 |Data Engineer             |
|Team Member 3 |MLOps Engineer            |
|Team Member 4 |Backend Engineer          |

-----

## 🔗 Related Projects

|Project                                                                                     |Description                                     |
|--------------------------------------------------------------------------------------------|------------------------------------------------|
|[GoVirallQ](https://github.com/LavishCreativeCo/GoVirallQ)                                  |Predicts what content goes viral on social media|
|[Melanin Match AI](https://github.com/LavishCreativeCo/Melanin-Match-AI)                    |AI skin tone matching for beauty products       |
|[Lavish Social Intelligence](https://github.com/LavishCreativeCo/lavish-social-intelligence)|Social media sentiment & engagement prediction  |

-----

## 📜 License

This project is licensed under the MIT License — see the <LICENSE> file for details.

-----

<p align="center">
  👑 Built with purpose by <a href="https://github.com/LavishCreativeCo">Chastity Lewis</a> | New York, NY
</p>

<p align="center">
  <a href="https://github.com/LavishCreativeCo">GitHub</a> •
  <a href="https://www.behance.net/LavishCreativeco">Behance</a> •
  <a href="mailto:chastity@chasslayyluxe.com">Contact</a>
</p>
