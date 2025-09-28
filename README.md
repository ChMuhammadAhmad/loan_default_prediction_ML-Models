# Loan Default Prediction 🔥

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/your-username/your-repo/blob/main/loan_default_prediction.ipynb)

---

## 📌 Project Overview
Banks lose billions in loan defaults every year. Predicting whether a loan applicant will default helps reduce financial risk. This project demonstrates an **end-to-end workflow** for predicting loan defaults using **machine learning models**.

⚠️ **Note**: The notebook is written in a **raw, step-by-step style** for clarity. In production, the code should be modularized into reusable functions and classes.

---

## 📊 Dataset
- **Source**: `Loan_Default.csv`
- **Target Variable**: `Status` (loan default indicator)
- **Preprocessing Steps**:
  - Dropped `ID` and `year` columns
  - Filled missing values (`mean` for numeric, `mode` for categorical)
  - Normalized gender column (`Sex Not Available` → `Male`)
  - Applied one-hot encoding

---

## ⚙️ Feature Selection
- Used **XGBoost** feature importance ranking
- Retained **top 7 features** most correlated with loan default status

---

## 🚀 Models Implemented
1. **Logistic Regression**
   - Baseline
   - With hyperparameter tuning (`RandomizedSearchCV`)

2. **K-Nearest Neighbors (KNN)**
   - Best-performing model (due to low dimensionality)

3. **Support Vector Machine (SVM)**
   - Default & tuned models

4. **Stacking Classifier**
   - Meta-learner = KNN
   - Base models = Logistic Regression & SVM

---

## 📈 Results Summary
- **KNN achieved the best results** with:
  - F1 Score = **0.978**
  - Recall = **0.996**
- **Recall prioritized** (since missing defaulters is costlier than false alarms)

| Model         | Test Accuracy | Test F1 Score | Test Recall | Test ROC_AUC |
|---------------|---------------|---------------|-------------|--------------|
| Logistic Reg. | Moderate      | Lower         | High        | Good         |
| LR (Tuned)    | Improved      | Slightly better | High      | Good         |
| **KNN**       | **Highest**   | **0.978**     | **0.996**   | Excellent    |
| SVM           | Good          | Lower than KNN | High      | Good         |
| SVM (Tuned)   | Slightly better | Slightly better | High   | Good         |
| Stacking      | Competitive   | Strong         | Very High   | Good         |

- **Confusion Matrix Insights**:
  - KNN → 16 Type I errors, 1 Type II error
  - Stacking → 17 Type I errors, 0 Type II errors

---

## 📊 Visualizations Included
- Feature importance (XGBoost)
- Confusion matrices (for each model)
- Performance comparison bar plots:
  - Accuracy
  - F1 Score
  - Recall

---

## 🛠️ Tech Stack
- **Python**
- **Libraries**:
  - Pandas, NumPy
  - Seaborn, Matplotlib
  - Scikit-learn
  - XGBoost

---

## ▶️ Usage
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/your-repo.git
   cd your-repo
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the notebook:
   - Locally: Open `loan_default_prediction.ipynb` in Jupyter/VSCode
   - In Colab: Click the **Colab badge** above

---

## 📌 Key Learnings
- Feature selection significantly improved model performance
- Recall is the most critical metric for financial risk use cases
- KNN performs very well in low-dimensional problems

---

## 📜 License
This project is licensed under the MIT License.