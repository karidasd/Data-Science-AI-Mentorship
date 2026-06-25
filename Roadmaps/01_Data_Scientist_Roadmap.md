# 01: The Modern Data Scientist Roadmap (2025) 🗺️

The role of a Data Scientist has changed drastically. You don't just build Jupyter Notebooks anymore; you are expected to write production-level code.

Here is the exact step-by-step path to getting hired today.

## 🟢 Phase 1: The Foundations (Months 1-2)
- **Math & Stats:** Linear Algebra, Calculus, Probability Distributions, A/B Testing.
- **SQL (Crucial):** CTEs, Window Functions, JOINs, Groupings. (If you don't know SQL, you won't pass the first interview).
- **Python Basics:** Data structures, OOP, Git/GitHub.

## 🟡 Phase 2: Data Manipulation & EDA (Month 3)
- **Libraries:** Pandas, NumPy, Polars (learn Polars, it's the future).
- **Visualization:** Matplotlib, Seaborn, Plotly.
- **Goal:** Be able to take a messy CSV, clean it, handle missing values, and extract business insights.

## 🟠 Phase 3: Machine Learning (Months 4-5)
- **Scikit-Learn:** Regression, Classification, Clustering.
- **Tree Models:** XGBoost, LightGBM, Random Forest.
- **Evaluation Metrics:** Precision, Recall, F1-Score, RMSE, ROC-AUC.
- **Hyperparameter Tuning:** GridSearch, Optuna.

## 🔴 Phase 4: Production & MLOps (Month 6)
*This is what separates the juniors from the Mid-Level Data Scientists.*
- **Version Control for ML:** MLflow (tracking experiments).
- **Deployment:** Wrap your model in a **FastAPI** or **Flask** API.
- **Containerization:** Write a `Dockerfile` for your API.
- **Cloud:** Deploy the Docker container to AWS (EC2/ECS) or GCP (Cloud Run).

> **💡 Mentor's Tip:** Stop doing Titanic or Iris dataset projects! Build an End-to-End project (e.g., predicting real estate prices) that includes a FastAPI backend and a Streamlit frontend, all deployed via Docker. That's what gets you hired!
