# Churn Prediction FastAPI App

This FastAPI application allows users to upload customer data, clean it, train machine learning models, and make predictions with natural language summaries.

## Endpoints

### 1. `/upload_data` (POST)
Uploads a raw CSV file.

### 2. `/clean_data` (POST)
Cleans the uploaded dataset.
- Handles missing values
- Encodes categorical features
- Scales numeric columns
- Requires `target_column` to exclude during cleaning  Eg: Churn

### 3. `/train_model` (POST)
Trains one or more models on the cleaned data.
- Supports Logistic Regression, Random Forest, XGBoost.  Eg: logistic,randomforest,xgboost 
- Saves each model
- Returns evaluation metrics: Accuracy, Precision, Recall, F1-score, Confusion Matrix

### 4. `/predict` (POST)
Runs inference on cleaned data using a selected model.
- Accepts `model_name`   ---> give model name as logistic_model.pkl, randomforest_model.pkl, xgboost_model.pkl
- Returns prediction for each row
- Generates a GenAI-based summary explanation

## File Storage

- Uploaded raw data: `app/storage/cleaned_data/raw_uploaded.csv`
- Cleaned data: `app/storage/cleaned_data/cleaned_data.csv`
- Trained models: `app/storage/models/`

## How to Run

Command: uvicorn app.main:app --reload
