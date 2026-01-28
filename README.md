
## 🎯 Objectives

Comparing Classifiers

A financial institution wants to improve the effectiveness of its telemarketing campaigns by better understanding which clients are most likely to subscribe to a term deposit.

This project aims to:

- Predict whether a client will subscribe to a term deposit (yes/no)
- Compare the performance of multiple classification models
- Evaluate model performance using metrics appropriate for imbalanced data
- Translate model results into actionable business insights

**Data task definition:**
Using bank client information and historical marketing data, build and compare multiple classification models (Logistic Regression, KNN, Decision Tree, and SVM) to predict term deposit subscription outcomes.

---
## 🔍 CRISP-DM Summary
### **1. Business Understanding**

Marketing phone calls are costly, and contacting every client is inefficient. The bank needs a data-driven approach to identify which clients are most likely to subscribe to a term deposit so resources can be allocated more effectively.

### **2. Data Understanding**

The dataset comes from a Portuguese banking institution and includes ~41,000 records of past marketing campaigns. Features include:

- Client demographics (age, job, education, marital status)
- Financial indicators (loans, credit default)
- Campaign and contact information
- Macroeconomic indicators
- Target variable indicating subscription outcome

The dataset contains no true missing values, but several categorical fields include "unknown" values. The target variable is highly imbalanced, with most clients not subscribing.

### **3. Data Preparation**

Key preparation steps included:

- Encoding the binary target variable (yes → 1, no → 0)
- One-hot encoding categorical variables
- Scaling numeric features for distance-based models
- Using pipelines to ensure consistent preprocessing across models
- Creating stratified train/test splits to preserve class balance
- Excluding leaky features (e.g., call duration) when appropriate

### **4. Exploratory Data Analysis (EDA)**

**Visual analysis showed:**

- A strong class imbalance in subscription outcomes
- Most clients fall within typical working-age ranges
- No single demographic feature is sufficient on its own to predict subscription

These findings support the need for careful metric selection and model evaluation beyond accuracy alone.

**Visualizations included:**

- Target distribution:
- images/target_distribution.png

### **5. Modeling**

Four classification models were trained and evaluated using identical preprocessing:

- **Logistic Regression**
- **K-Nearest Neighbors (KNN)**
- **Decision Tree**
- **DSupport Vector Machine (SVM / LinearSVC)**

Initial models used default parameters to establish a fair baseline.
Subsequently, GridSearchCV was applied to tune KNN and Decision Tree hyperparameters.

Because the dataset is imbalanced, F1-score was emphasized alongside accuracy.

### **6. Evaluation**

**Key observations:**

- High accuracy alone was misleading due to class imbalance
- Decision Trees showed strong training performance but clear overfitting
- Tuned KNN and Decision Tree models improved stability but still struggled to identify subscribers
- Logistic Regression provided the best balance of interpretability, stability, and minority-class detection
- Model evaluation focused on precision, recall, and F1-score, not accuracy alone.

### **7. Deployment & Business Insights**

**Business interpretation:**

- Missing a potential subscriber is more costly than making an extra phone call
- Models must prioritize recall for the positive class to be operationally useful

**Recommendations:**

1. Use Logistic Regression as a baseline decision-support model for marketing outreach
2. Incorporate additional non-leaky campaign features to improve recall
3. Adjust decision thresholds based on call-center capacity
4. Explore resampling or cost-sensitive learning techniques
5. Monitor model performance over time as customer behavior changes

## 📈 Tools & Libraries Used

- Python
- Jupyter Notebook
- pandas, numpy
- seaborn, matplotlib
- scikit-learn (LogisticRegression, KNeighborsClassifier, DecisionTreeClassifier, LinearSVC, GridSearchCV)

## Visualizations

Target distribution:
https://github.com/cheddara/practical_application_3/blob/main/images/age_distribution.png

Age distribution:
https://github.com/cheddara/practical_application_3/blob/main/images/age_distribution.png

## 📎 Notes

The dataset (bank-additional-full.csv) is not included in this repository due to size constraints. It can be obtained from the UC Irvine Machine Learning Repository as provided in the course materials.

## 👩‍💻 Author

**Annette Angel
UC Berkeley ML & AI Professional Certificate 
