# Loan Default Prediction 🔥

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1HiD53YCkKR3pVApqxghYq6GfTOVULuSk)

---

## Project Overview
Banks lose billions in loan defaults every year. Predicting whether a loan applicant will default helps reduce financial risk. This project demonstrates an **end-to-end workflow** for predicting loan defaults using **machine learning models**.

⚠️ **Note**: The notebook is written in a **raw, step-by-step style** for clarity. In production, the code should be modularized into reusable functions and classes.

---

## Dataset
- **Source**: `Loan_Default.csv`
- **Target Variable**: `Status` (loan default indicator)
- **Preprocessing Steps**:
  - Dropped `ID` and `year` columns
  - Filled missing values (`mean` for numeric, `mode` for categorical)
  - Normalized gender column (`Sex Not Available` → `Male`)
  - Applied one-hot encoding

---

## Feature Selection
- Used **XGBoost** feature importance ranking
- Retained **top 7 features** most correlated with loan default status

---

## Models Implemented
1. **Logistic Regression**
   - Baseline and tuned with `RandomizedSearchCV`
2. **K-Nearest Neighbors (KNN)**
   - Best-performing model
3. **Support Vector Machine (SVM)**
   - Default and tuned models
4. **Stacking Classifier**
   - Meta-learner = KNN
   - Base models = Logistic Regression & SVM

---

## Results Summary
| Model              | Test Accuracy | Test F1 Score | Test Recall | Test ROC_AUC |
|--------------------|---------------|---------------|-------------|--------------|
| Logistic Reg.      | 0.81          | 0.72          | 1.00        | 1.00         |
| LR (Tuned)         | 0.81          | 0.73          | 1.00        | 0.95         |
| **KNN**            | **0.99**      | **0.98**      | **1.00**    | **0.98**     |
| SVM                | 0.92          | 0.86          | 1.00        | 0.95         |
| SVM (Tuned)        | 0.95          | 0.93          | 0.87        | 0.96         |
| Stacking Classifier| 0.99          | 0.99          | 0.98        | 0.96         |

- **KNN achieved the best balance of Recall and F1 Score.**
- Recall was prioritized since missing defaulters is costlier than false alarms.

---

## Visualizations Included
- Feature importance (XGBoost)
- Confusion matrices (for each model)
- Performance comparison bar plots:
  - Accuracy
  - F1 Score
  - Recall

---

## Tech Stack
- **Python**
- **Libraries**:
  - Pandas, NumPy
  - Seaborn, Matplotlib
  - Scikit-learn
  - XGBoost

---

## Usage
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

## Key Learnings
- Feature selection significantly improved model performance
- Recall is the most critical metric for financial risk use cases
- KNN performs very well in low-dimensional problems

---

## 📜 License
This project is licensed under the MIT License.

