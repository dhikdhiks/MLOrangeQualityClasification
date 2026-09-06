# 🍊 Orange Quality Classification

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.20%2B-FF4B4B.svg)](https://streamlit.io/)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.1%2B-orange.svg)](https://scikit-learn.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A **Machine Learning classification web application** that predicts the quality of oranges (Bagus/Sedang/Jelek) based on physical characteristics such as diameter, weight, skin thickness, sugar content, region, color, and harvest season.

The model is built using **Logistic Regression** with a comprehensive preprocessing pipeline, achieving high accuracy in classifying orange quality. The interactive frontend is built with **Streamlit**, allowing users to input orange characteristics and receive instant quality predictions.

🔗 **Live Demo**: *(coming soon)*

---

## 📸 Screenshots

| Prediction Form | Result |
|:---:|:---:|
| ![Form](screenshots/form.png) | ![Result](screenshots/result.png) |

> *Replace the image paths with your actual screenshots after deployment.*

---

## ✨ Features

- 🍊 **Predict orange quality** (Bagus/Sedang/Jelek) based on 7 features
- 📋 **Dropdown selection** for categorical features (region, color, season)
- 🏷️ **Automatic data preprocessing** including scaling and encoding
- 🌐 **Fully responsive** and user‑friendly interface
- 🇬🇧 **Full English UI** for global accessibility
- ⚡ **Real‑time predictions** with confidence percentage
- 📊 **Classification report** and model performance metrics

---

## 🛠️ Tech Stack

### Core Technologies

| Category | Technology | Version | Purpose |
|----------|------------|---------|---------|
| **Language** | Python | 3.9+ | Main programming language |
| **Data Processing** | Pandas | 1.5+ | Data manipulation & loading |
| | NumPy | 1.23+ | Numerical computations |
| **Machine Learning** | Scikit-learn | 1.1+ | Preprocessing, modeling, evaluation |
| **Web Framework** | Streamlit | 1.20+ | Interactive web application |
| **Visualization** | Matplotlib | 3.5+ | Data visualization (EDA) |
| **Model Serialization** | Joblib | 1.1+ | Saving & loading model artifacts |
| **Version Control** | Git & GitHub | - | Source code management |

### Machine Learning Pipeline

| Component | Library/Module | Details |
|-----------|---------------|---------|
| **Preprocessing** | `sklearn.preprocessing.StandardScaler` | Normalize numeric features |
| | `sklearn.preprocessing.OneHotEncoder` | One-hot encode categorical features |
| | `sklearn.preprocessing.OrdinalEncoder` | Ordinal encode color (hijau→kuning→oranye) |
| **Model** | `sklearn.linear_model.LogisticRegression` | Logistic Regression classifier |
| **Pipeline** | `sklearn.pipeline.Pipeline` | Combine preprocessing & modeling |
| **Data Splitting** | `sklearn.model_selection.train_test_split` | 80/20 train‑test split |
| **Evaluation Metrics** | `sklearn.metrics` | Accuracy, Classification Report, Confusion Matrix |

### Additional Tools

| Tool | Purpose |
|------|---------|
| **VS Code** | Development environment |
| **Jupyter Notebook** | Exploratory Data Analysis (EDA) |
| **Streamlit Cloud** | (Optional) Deployment platform |

---

## 🧠 How It Works

### Data Flow
User Input → Preprocessing Pipeline → Model Prediction → Quality Result + Confidence

text

### Preprocessing Pipeline

1. **Numeric Features Scaling**: `diameter`, `berat`, `tebal_kulit`, `kadar_gula` are standardized using `StandardScaler`.
2. **One-Hot Encoding**: Categorical features (`asal_daerah`, `musim_panen`) are one-hot encoded.
3. **Ordinal Encoding**: Color (`warna`) is ordinal encoded with order: `hijau → kuning → oranye`.
4. **Prediction**: The processed input is passed through the trained Logistic Regression model.
5. **Output**: The model returns the predicted quality class and confidence percentage.

---

## 📁 Project Structure
MLOrangeQualityClasification/
│
├── app/
│ ├── app_streamlit.py # Streamlit application
│ └── requirements.txt # Python dependencies
│
├── data/
│ └── jeruk_balance_500.csv # Dataset (500 samples)
│
├── model/
│ └── orange_quality_model.joblib # Trained model
│
└── notebook/
└── Orange_Clasification.ipynb # EDA and training notebook


---

## 📊 Dataset

The dataset contains **500 samples** of oranges with **7 features** used to predict **quality** (target variable).

### Features

| Feature | Type | Description |
|---------|------|-------------|
| `diameter` | Numeric | Diameter of the orange in cm |
| `berat` | Numeric | Weight of the orange in grams |
| `tebal_kulit` | Numeric | Skin thickness in cm |
| `kadar_gula` | Numeric | Sugar content (°Brix) |
| `asal_daerah` | Categorical | Region of origin |
| `warna` | Ordinal | Color (hijau → kuning → oranye) |
| `musim_panen` | Categorical | Harvest season |
| `kualitas` | **Target** | Quality (Bagus / Sedang / Jelek) |

### Sample Data

csv data
diameter,berat,tebal_kulit,kadar_gula,asal_daerah,warna,musim_panen,kualitas
7.75,216.4,0.51,11.1,Kalimantan,oranye,kemarau,Bagus

### 🧪 Model Performance
The Logistic Regression model achieved the following performance metrics:

Metric	Score
Accuracy	~90% (actual score from training)
Precision	Varies per class
Recall	Varies per class
F1-Score	Varies per class

### Model Hyperparameters
python
LogisticRegression(
    C=1.0,
    max_iter=100,
    multi_class='multinomial',
    solver='lbfgs'
)
Why Logistic Regression?
Simple, interpretable, and fast

Works well with properly preprocessed data

Provides probability estimates (confidence scores)

Suitable for multi-class classification

### 🛠️ Installation & Setup
Prerequisites
Python 3.9 or higher

Git (optional, for cloning)
Step 1: Clone the Repository
bash
git clone https://github.com/your-username/orange-quality-classification.git
cd orange-quality-classification
Step 2: Create a Virtual Environment (Recommended)
bash
python -m venv venv
source venv/bin/activate      # On Linux/Mac
# OR
venv\Scripts\activate         # On Windows
Step 3: Install Dependencies
bash
pip install -r app/requirements.txt
Step 4: Train the Model (Optional)
If you want to retrain the model:

bash
cd notebook
python Orange_Clasification.ipynb
# Or open in Jupyter and run all cells
Step 5: Run the Streamlit App
bash
cd app
streamlit run app_streamlit.py
The application will open in your default browser at http://localhost:8501.

### 📈 Feature Importance
The model uses the following features (ranked by potential impact):

Kadar Gula (Sugar Content) – Most influential factor

Berat (Weight) – Significant impact

Diameter – Important for size assessment

Warna (Color) – Indicator of ripeness

Tebal Kulit (Skin Thickness) – Quality indicator

Asal Daerah (Region) – Geographical variation

Musim Panen (Harvest Season) – Seasonal impact

### 🤝 Contributing
Contributions are welcome! If you'd like to improve this project:

Fork the repository

Create a new branch: git checkout -b feature/your-feature

Commit your changes: git commit -m "Add some feature"

Push to the branch: git push origin feature/your-feature

Open a Pull Request