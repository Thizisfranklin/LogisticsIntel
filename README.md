# 🚚 Logistics Intelligence System: ML Delay Prediction API
 > (🚧 Currently in Active Development)

**The Business Problem:**  
When logistics teams operate on a reactive model, everyone loses. Finding out a shipment is delayed after it's already stuck in transit means missed SLAs and wasted money. More importantly, chronic delays directly drive customer churn. If consumers and business partners cannot rely on estimated delivery windows, they will take their business to a competitor.

**The Solution:**  
This project shifts supply chain management from reactive to predictive. I built a machine learning pipeline and REST API that flags high-risk ( forecast shipment delays) shipments before a truck ever leaves the dock. By analyzing historical transit data, routing constraints, and congestion signals, the system acts as an early-warning radar. It gives dispatchers the lead time they need to reroute freight, prevent the delay, and protect the customer experience.

## 📦 Core Architecture

This system is designed as a modular, production-oriented pipeline that moves from raw logistics data → predictive modeling → real-time decision support.


### 🧠 Predictive ML Engine (`train.py`)

Trains an XGBoost classification model on engineered routing features such as transit variability, route complexity, and congestion patterns.  

Outputs a probability score indicating the likelihood of a shipment missing its delivery window, enabling proactive intervention before delays occur.


### 🔌 Production Microservice (`main.py`)

Deploys the trained model as a FastAPI-based microservice for real-time inference.  

Allows external systems (e.g., dispatch or planning tools) to send shipment data via API requests and receive instant delay risk predictions.


### 🛠️ Feature Engineering Pipeline (`preprocessing.py`)

Automates cleaning, transformation, encoding, and scaling of raw logistics data.  

Ensures consistency between training and inference data, making the system robust to messy, real-world inputs.

---
## 🧰 Tech Stack

### 🧠 Machine Learning
- XGBoost
- Scikit-Learn
- Pandas
- NumPy

### 🔌 API & Deployment
- FastAPI
- Uvicorn

### 🧪 Testing & Validation
- Postman
- Swagger UI

### 💻 Language
- Python

```logistics-intelligence-system/
│
├── data/
│   ├── raw/                  # Original shipment, routing, and logistics data
│   ├── processed/            # Cleaned + feature-engineered datasets
│
├── notebooks/
│   ├── eda.ipynb             # Exploratory data analysis
│   ├── modeling.ipynb        # Model experiments and validation
│
├── src/
│   ├── preprocessing.py      # Data cleaning + feature engineering
│   ├── train.py              # Model training (XGBoost)
│   ├── predict.py            # Inference logic
│   ├── utils.py              # Helper functions
│
├── models/
│   └── xgboost_model.pkl     # Saved trained model
│
├── app/
│   ├── main.py               # FastAPI app (API endpoints)
│   └── schemas.py            # Request/response validation (Pydantic)
│
├── configs/
│   └── config.yaml           # Model params, thresholds, feature settings
│
├── tests/
│   ├── test_api.py           # API tests
│   └── test_model.py         # Model validation tests
│
├── requirements.txt
├── Dockerfile                # (optional) containerization
├── README.md ```


