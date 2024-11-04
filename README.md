# TV Sales Prediction API

This project provides a FastAPI-based API to predict TV sales based on a linear regression model trained on a dataset of TV advertising spend and sales. The model is built using Python, leveraging FastAPI for the API endpoint, and scikit-learn for machine learning.

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Model Training](#model-training)
- [API Endpoint](#api-endpoint)
- [Installation](#installation)
- [Usage](#usage)
- [Example Request](#example-request)

## Project Overview
This project provides a simple linear regression model for predicting TV sales based on TV advertisement spending. The model uses FastAPI to expose the model as an API endpoint, allowing users to input TV advertising spend and receive a prediction for the expected sales.

## Dataset
The dataset used for training is `tvmarketing.csv`, which contains two columns:
- `TV`: Amount spent on TV advertising.
- `Sales`: Sales outcome (target variable).

## Model Training
The project includes:
1. **Linear Regression Model**: Trained using scikit-learn's LinearRegression.
2. **Gradient Descent**: Implemented manually to optimize the slope (`m`) and intercept (`b`) values.
3. **Model Comparison**: Comparison of Linear Regression, Decision Tree, and Random Forest models based on Root Mean Square Error (RMSE).

The model with the best performance is used in the API endpoint for predictions.

## API Endpoint
The FastAPI application exposes a single POST endpoint:
- `/predict/`: Accepts JSON input with the `tv` field (TV advertising spend) and returns a JSON response with the predicted `sales`.

## Installation

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/your-username/tv-sales-prediction-api.git
    cd tv-sales-prediction-api
    ```

2. **Install Dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

    Ensure `requirements.txt` includes:
    ```
    fastapi
    uvicorn
    scikit-learn
    numpy
    pandas
    ```

3. **Run the API**:
    Start the FastAPI server with Uvicorn:
    ```bash
    uvicorn main:app --reload
    ```

    Replace `main` with the filename of your FastAPI script, excluding `.py`.

## Usage

To use the API, send a POST request to the `/predict/` endpoint with the JSON input as shown below.

### Example Request
Use the following format to make a prediction:

- **URL**: `http://127.0.0.1:8000/predict/`
- **Method**: `POST`
- **Headers**: `Content-Type: application/json`
- **Body**:
    ```json
    {
      "tv": 150.0
    }
    ```

- **Response**:
    ```json
    {
      "predicted_sales": 14.28
    }
    ```

## Example Code
You can test the API with Python requests:
```python
import requests

url = "http://127.0.0.1:8000/predict/"
data = {"tv": 150.0}

response = requests.post(url, json=data)
print(response.json())
