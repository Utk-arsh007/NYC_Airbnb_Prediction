# 🏙️ NYC Airbnb Room Type Predictor

> **An AI-powered web application that predicts the type of Airbnb listing in New York City using machine learning.**

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-API-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![Scikit--learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Processing-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![JavaScript](https://img.shields.io/badge/JavaScript-Frontend-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](#-license)

---

## ✨ Overview

**NYC Airbnb Room Type Predictor** is a full-stack machine-learning application that predicts the room type of an Airbnb listing based on its location, pricing, booking requirements, review activity, host information, and availability.

The application accepts listing information through an interactive web interface and sends the data to a **FastAPI backend**, where a pre-trained **scikit-learn machine-learning pipeline** generates:

- 🏠 Predicted room type
- 📊 Probability for each room category
- 🎯 Model confidence
- 💡 Prediction insights

The supported room types are:

| Room Type | Description |
|---|---|
| 🏠 **Entire home / apt** | The guest gets the complete property |
| 🚪 **Private room** | The guest has a private room within a property |
| 🛏️ **Shared room** | The guest shares the room with others |

---

## 🚀 Live Demo

### 🌐 Frontend

> Add your deployed frontend URL here.

**[🔗 Open Live Application](#)**

### ⚡ API

The prediction API is deployed using FastAPI and can be accessed at:

`https://nyc-airbnb-room-type-predictor.onrender.com`

> Replace the URL above if your deployment URL changes.

---

## 🎬 What the Application Does

```text
             Airbnb Listing
                   │
                   ▼
        ┌─────────────────────┐
        │   Web Interface     │
        │ HTML + CSS + JS     │
        └──────────┬──────────┘
                   │
                   │ JSON
                   ▼
        ┌─────────────────────┐
        │      FastAPI        │
        │    /predict API     │
        └──────────┬──────────┘
                   │
                   ▼
        ┌─────────────────────┐
        │ ML Pipeline (.pkl)  │
        │   scikit-learn      │
        └──────────┬──────────┘
                   │
                   ▼
        ┌─────────────────────┐
        │ Prediction +        │
        │ Probabilities       │
        └──────────┬──────────┘
                   │
                   ▼
        ┌─────────────────────┐
        │ Interactive Result  │
        │ Visualization       │
        └─────────────────────┘
```

---

# 🧠 Machine Learning

The model uses listing-level Airbnb information to classify the property into one of three room categories.

### Input Features

The API accepts **10 features**:

| Feature | Description |
|---|---|
| `latitude` | Geographic latitude |
| `longitude` | Geographic longitude |
| `price` | Price per night in USD |
| `minimum_nights` | Minimum number of nights required |
| `number_of_reviews` | Total number of reviews |
| `reviews_per_month` | Average monthly review activity |
| `calculated_host_listings_count` | Number of listings managed by the host |
| `availability_365` | Number of available days per year |
| `neighbourhood_group` | NYC borough |
| `neighbourhood` | Specific NYC neighbourhood |

### Prediction Classes

```text
Entire home/apt
Private room
Shared room
```

The model is loaded from:

```text
Model_Pipeline.pkl
```

and used directly by the FastAPI application.

---

# ⚡ API

## `GET /`

Health-check endpoint.

### Response

```text
Hello Guyss
```

---

## `POST /predict`

Predicts the room type of an Airbnb listing.

### Request

```json
{
  "latitude": 40.7484,
  "longitude": -73.9857,
  "price": 120,
  "minimum_nights": 2,
  "number_of_reviews": 84,
  "reviews_per_month": 2.3,
  "calculated_host_listings_count": 1,
  "availability_365": 210,
  "neighbourhood_group": "Manhattan",
  "neighbourhood": "Midtown"
}
```

### Response

```json
{
  "Predicted_room_type": "Entire home/apt",
  "Probability": [
    0.87,
    0.10,
    0.03
  ]
}
```

> The probability array corresponds to the classes returned by the trained scikit-learn model.

---

# 🎨 Frontend

The frontend is designed as a modern AI dashboard rather than a basic HTML form.

### Features

- 🌃 NYC-inspired dark interface
- ✨ Animated AI prediction interface
- 📍 Location inputs
- 💰 Pricing and stay information
- ⭐ Review and host information
- 🎚️ Interactive availability slider
- ⚡ Real-time API health indicator
- 🔄 Example listing generator
- 📊 Probability visualization
- 🏢 Animated building visualization
- 🎯 Confidence indicator
- 💡 Automatic prediction insight
- 📱 Responsive mobile layout
- ♿ Reduced-motion-friendly animations

---

# 🛠️ Tech Stack

### Backend

- **Python**
- **FastAPI**
- **Pydantic**
- **Pandas**
- **Joblib**
- **Scikit-learn**
- **Uvicorn**

### Frontend

- **HTML5**
- **CSS3**
- **Vanilla JavaScript**
- **Google Fonts**
- **Fetch API**

### Deployment

- **Render** — FastAPI backend
- Any static hosting platform can be used for the frontend

---

# 📂 Project Structure

```text
NYC_Airbnb_prediction_project/
│
├── main.py
│
├── model.pkl
│
├── index.html
│
├── style.css
│
├── script.js
│
├── requirements.txt
│
└── README.md
```

> If your model is named `Model_Pipeline.pkl` instead of `model.pkl`, keep the filename consistent with the name used in `main.py`.

---

# 💻 Run Locally

## 1. Clone the repository

```bash
git clone https://github.com/Utk-arsh007/NYC_Airbnb_Prediction.git
```

Move into the project:

```bash
cd NYC_Airbnb_Prediction
```

---

## 2. Create a virtual environment

### Windows

```bash
python -m venv venv
```

Activate it:

```bash
venv\Scripts\activate
```

### macOS / Linux

```bash
python3 -m venv venv
```

```bash
source venv/bin/activate
```

---

## 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## 4. Start FastAPI

```bash
uvicorn main:app --reload
```

The API will run at:

```text
http://127.0.0.1:8000
```

---

## 5. Open API documentation

FastAPI automatically provides interactive API documentation.

### Swagger UI

```text
http://127.0.0.1:8000/docs
```

### ReDoc

```text
http://127.0.0.1:8000/redoc
```

---

# 🔌 Frontend Configuration

The frontend communicates with the FastAPI backend through:

```javascript
const API_BASE_URL =
    "https://nyc-airbnb-room-type-predictor.onrender.com";
```

For local development, change it to:

```javascript
const API_BASE_URL =
    "http://127.0.0.1:8000";
```

Then open:

```text
index.html
```

in your browser.

---

# 🔄 Prediction Workflow

The complete prediction process is:

### 1️⃣ User enters listing details

The frontend collects:

```text
Location
Price
Minimum nights
Reviews
Host listings
Availability
```

### 2️⃣ JavaScript creates JSON

```javascript
const payload = {
    latitude,
    longitude,
    price,
    minimum_nights,
    number_of_reviews,
    reviews_per_month,
    calculated_host_listings_count,
    availability_365,
    neighbourhood_group,
    neighbourhood
};
```

### 3️⃣ Request is sent to FastAPI

```text
POST /predict
```

### 4️⃣ Pydantic validates the request

Invalid values are rejected before reaching the model.

### 5️⃣ Pandas creates a DataFrame

The API converts the request into the format expected by the ML pipeline.

### 6️⃣ Model generates prediction

```python
prediction = model.predict(row)
```

### 7️⃣ Model calculates probabilities

```python
probability = model.predict_proba(row)
```

### 8️⃣ Frontend visualizes the result

The UI displays:

```text
Predicted Room Type
        ↓
Confidence
        ↓
Probability Breakdown
        ↓
Visual Room Representation
```

---

# 🧪 Example Listings

The application includes built-in examples so users can test the model without manually entering every feature.

### Manhattan Example

```text
Location: Midtown
Price: $120
Minimum nights: 2
Reviews: 84
Availability: 210 days
```

### Brooklyn Example

```text
Location: Bedford-Stuyvesant
Price: $55
Minimum nights: 1
Reviews: 210
Availability: 300 days
```

### Queens Example

```text
Location: Flushing
Price: $38
Minimum nights: 3
Reviews: 12
Availability: 90 days
```

---

# 🔐 API Validation

The backend uses **Pydantic** to validate incoming data.

Examples:

```text
Latitude       → -90 to 90
Longitude      → -180 to 180
Price          → > 0
Minimum nights → 1 to 365
Availability   → 0 to 365
Reviews        → ≥ 0
```

This prevents invalid input from being passed directly to the machine-learning model.

---

# 📈 Future Improvements

Potential improvements for future versions:

- [ ] Add model accuracy and evaluation metrics
- [ ] Add confusion matrix visualization
- [ ] Add feature importance visualization
- [ ] Add historical prediction tracking
- [ ] Add NYC map visualization
- [ ] Add batch CSV prediction
- [ ] Add authentication
- [ ] Add database for prediction history
- [ ] Add automated model retraining
- [ ] Add Docker deployment
- [ ] Add CI/CD pipeline
- [ ] Add automated API testing
- [ ] Add model versioning
- [ ] Add monitoring and logging

---

# 🧩 Challenges Solved

### 🔹 Connecting ML with a Web Application

The project integrates a trained machine-learning pipeline with a REST API using FastAPI.

### 🔹 Data Validation

Pydantic ensures that incoming user data follows the expected format and constraints.

### 🔹 Model Serialization

The trained scikit-learn pipeline is serialized using Joblib and loaded by the API.

### 🔹 Frontend ↔ Backend Communication

The frontend communicates with FastAPI using asynchronous JavaScript and JSON requests.

### 🔹 Probability Visualization

Instead of showing only the predicted class, the application exposes the probability distribution to provide more context around the model's decision.

---

# 👨‍💻 Author

**Utkarsh Kumar**

🎓 Information Technology Student  
🏫 IIIT Bhopal

### Connect with me

- GitHub: [@Utk-arsh007](https://github.com/Utk-arsh007)
- LinkedIn: *Add your LinkedIn profile here*

---

# ⭐ If You Like This Project

If you found this project interesting:

**⭐ Star the repository**

**🍴 Fork the repository**

**📢 Share it with others**

---

# 📄 License

This project is available under the **MIT License**.

---

<p align="center">

### 🏙️ Built with Python · FastAPI · Scikit-learn · JavaScript

**Predict smarter. Understand the listing.**

</p>
