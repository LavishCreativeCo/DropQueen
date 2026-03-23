# 👑 Drop Queen

### AI-Powered Product Demand & Sales Forecasting Engine for TikTok Shop & Amazon

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-2.0+-green.svg)
![Docker](https://img.shields.io/badge/Docker-Enabled-blue.svg)
![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-orange.svg)
![MLflow](https://img.shields.io/badge/MLflow-Tracking-red.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

**Course:** CISC 610 — DevOps and MLOps | Mercy University | Spring 2026
**Author:** Chastity Lewis

-----

## 🎯 Overview

**Drop Queen** is an AI-powered demand and sales forecasting engine that predicts which beauty and lifestyle products will spike in demand on **TikTok Shop** and **Amazon** — before they sell out.

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

Drop Queen uses two ML models working together:

|Model                      |What It Does                                                                                               |
|---------------------------|-----------------------------------------------------------------------------------------------------------|
|**Demand Spike Model**     |Random Forest classifier — predicts weekly product demand using historical Amazon sales data (87% accuracy)|
|**TikTok Engagement Model**|Logistic Regression — detects which products are about to spike based on TikTok social signals             |

Together they power a real-time Flask API that serves demand predictions across TikTok Shop and Amazon product categories.

-----

## ✨ Key Features

- 📈 **Demand Forecasting** — Predicts weekly sales spikes up to 2 weeks in advance
- 🔍 **Trend Detection** — Identifies products gaining social momentum before they peak
- 🛍️ **Cross Platform** — Compares demand signals across TikTok Shop and Amazon simultaneously
- 💄 **Beauty & Lifestyle Focus** — Specialized in beauty, skincare, and lifestyle product categories
- 🔄 **Auto Retraining** — CI/CD pipeline automatically retrains models when new data arrives
- 📊 **Model Versioning** — MLflow tracks and compares all model versions in production

-----

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────┐
│                      DATA SOURCES                        │
│   Amazon Sales Data   │   TikTok Trends   │  Google     │
│      (Kaggle)         │    (Kaggle)        │  Trends API │
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
│  DEMAND SPIKE MODEL   │           │  TIKTOK ENGAGEMENT    │
│  Random Forest        │           │  MODEL                │
│  87% Accuracy         │           │  Logistic Regression  │
│  Weekly Forecasting   │           │  Spike Detection      │
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
│   MLFLOW          │       │   CI/CD PIPELINE           │
│   Model Tracking  │       │   GitHub Actions           │
│   & Versioning    │       │   Auto Retraining          │
└───────────────────┘       └───────────────────────────┘
```

-----

## 📁 Project Structure

```
DropQueen/
│
├── .github/
│   └── workflows/
│       └── ci_cd.yml               # GitHub Actions CI/CD pipeline
│
├── 01_EDA_DropQueen.ipynb          # Exploratory data analysis
├── 02_data_cleaning_DropQueen.ipynb # Data cleaning & preprocessing
├── 03_model_training_DropQueen.ipynb # Model training & evaluation
├── 04_flask_api_DropQueen.ipynb    # Flask API development
├── 05_docker_cicd_DropQueen.ipynb  # Docker & CI/CD setup
│
├── drop-queen-architecture.html    # Interactive architecture diagram
├── Dockerfile                      # Docker container configuration
├── docker-compose.yml              # Multi-service Docker setup
├── requirements.txt                # Python dependencies
└── README.md                       # You are here 👑
```

-----

## 📊 Datasets

|Dataset                 |Source  |Description                       |
|------------------------|--------|----------------------------------|
|Amazon Beauty Reviews   |Kaggle  |Product reviews & ratings         |
|Amazon Sales Rank Data  |Kaggle  |Historical product demand patterns|
|TikTok Trending Products|Kaggle  |Viral product engagement data     |
|Google Trends           |Free API|Real-time trend signals by product|

-----

## 🛠️ Tech Stack

|Category            |Tools                                           |
|--------------------|------------------------------------------------|
|**Language**        |Python 3.9+                                     |
|**ML Models**       |Random Forest, Logistic Regression, Scikit-learn|
|**Data Processing** |Pandas, NumPy                                   |
|**API**             |Flask, REST                                     |
|**Containerization**|Docker, Docker Compose                          |
|**CI/CD**           |GitHub Actions                                  |
|**Model Tracking**  |MLflow                                          |
|**Cloud**           |AWS                                             |
|**Version Control** |Git & GitHub                                    |

-----

## 🚀 Getting Started

### Prerequisites

```
Python 3.9+
Docker & Docker Compose
Git
```

### Installation

```bash
# Clone the repository
git clone https://github.com/LavishCreativeCo/DropQueen.git
cd DropQueen

# Install dependencies
pip install -r requirements.txt
```

-----

## 🐳 Deployment

### Option 1 — Run with Docker Compose (Recommended)

```bash
# Build and start all services
docker-compose up --build

# API will be live at:
http://localhost:5000

# MLflow UI will be live at:
http://localhost:5001
```

### Option 2 — Run Locally

```bash
# Install dependencies
pip install -r requirements.txt

# Start the Flask API
python app.py

# API will be available at:
http://localhost:5000
```

### Option 3 — Run with Docker Only

```bash
# Build the Docker image
docker build -t drop-queen .

# Run the container
docker run -p 5000:5000 drop-queen
```

### Environment Variables

Create a `.env` file in the root directory with the following:

```
FLASK_ENV=production
MLFLOW_TRACKING_URI=http://localhost:5001
KAGGLE_USERNAME=your_kaggle_username
KAGGLE_KEY=your_kaggle_api_key
```

### MLflow Tracking

```bash
# Start the MLflow tracking server
mlflow ui --port 5001

# View model versions and experiments at:
http://localhost:5001
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

## 🔄 CI/CD Pipeline

Drop Queen uses **GitHub Actions** for automated testing and deployment. On every push to `main`:

```
✅ Run code quality checks
✅ Run test suite
✅ Build Docker image
✅ Retrain models on new data
✅ Register new model version in MLflow
✅ Deploy updated Flask API
```

The pipeline configuration is located at `.github/workflows/ci_cd.yml`.

-----

## 🧠 Models

|Model                  |Algorithm          |Accuracy|Purpose                     |
|-----------------------|-------------------|--------|----------------------------|
|Demand Spike Model     |Random Forest      |87%     |Predicts weekly sales demand|
|TikTok Engagement Model|Logistic Regression|—       |Detects trending products   |

-----

## 📈 Results

|Metric                       |Result                  |
|-----------------------------|------------------------|
|**Demand Forecast Accuracy** |87% within 2-week window|
|**Trend Detection Lead Time**|14 days before peak     |
|**Platforms Covered**        |TikTok Shop & Amazon    |
|**Product Categories**       |Beauty & Lifestyle      |

-----

## 🤝 Team

Built as part of **CISC 610 — DevOps and MLOps** at Mercy University, Spring 2026.

|Name          |Role                      |
|--------------|--------------------------|
|Chastity Lewis|ML Engineer & Project Lead|

-----

## 📜 License

This project is licensed under the MIT License.

-----

👑 Built with purpose by [Chastity Lewis](https://github.com/LavishCreativeCo) | New York, NY