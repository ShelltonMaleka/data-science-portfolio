#  Wine Classification Using Machine Learning

##  Project Overview

This project applies supervised machine learning techniques to classify wines into three different classes based on their chemical properties.

The dataset contains **178 wine samples** described by **13 chemical features**, including alcohol content, flavanoids, colour intensity, proline, and other chemical measurements.

Two classification algorithms were implemented and compared:

- Decision Tree Classifier
- Support Vector Machine (SVM)

---

##  Objective

The main objective of this project is to determine whether the chemical properties of a wine can be used to accurately predict its wine class.

The project also investigates which chemical properties contribute the most to the classification decisions made by the machine learning models.

---

##  Dataset

The Wine dataset contains:

- **178 observations**
- **13 chemical predictor variables**
- **3 wine classes**
- **No missing values**

The target variable is `Wine`, representing **Class 1, Class 2, or Class 3**.

The target values were kept as integer class labels (`1`, `2`, and `3`) during model training because both Scikit-learn's Decision Tree and SVM classifiers treat them as class labels rather than continuous numerical values.

---

##  Machine Learning Workflow

The project follows the following workflow:

1. Data loading and exploration
2. Descriptive statistics
3. Missing value and duplicate checks
4. Exploratory data visualisation
5. Feature and target separation
6. Train-test split
7. Feature standardisation
8. Decision Tree model training
9. Support Vector Machine model training
10. Model evaluation
11. Confusion matrix analysis
12. Multiclass ROC and AUC analysis
13. Feature importance analysis
14. Model comparison and interpretation

---

##  Models Used

### Decision Tree Classifier

The Decision Tree learns a series of rules based on the chemical properties of the wines.

It was selected because it:

- Works well for classification problems
- Can capture non-linear relationships
- Is relatively easy to interpret
- Provides built-in feature importance

### Support Vector Machine (SVM)

An SVM with an **RBF kernel** was used.

The SVM attempts to create decision boundaries that separate the different wine classes based on their chemical characteristics.

Feature standardisation was applied before training the SVM because SVM models are sensitive to differences in feature scale.

---

##  Model Performance

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---:|---:|---:|---:|
| Decision Tree | 94.44% | 95.14% | 94.44% | 94.50% |
| Support Vector Machine | **97.22%** | **97.41%** | **97.22%** | **97.20%** |

The **Support Vector Machine achieved the highest test accuracy of 97.22%**.

On the 36 test observations:

- Decision Tree correctly classified **34 out of 36 wines**
- SVM correctly classified **35 out of 36 wines**

Although the SVM performed better on this test set, the difference represents only one additional correct prediction. Therefore, the result should be interpreted cautiously because the dataset and test set are relatively small.

---

##  Feature Importance

Feature importance was investigated differently for the two models.

### Decision Tree

The three most important features were:

1. **Flavanoids**
2. **Color Intensity**
3. **Proline**

Flavanoids and Color Intensity contributed particularly strongly to the Decision Tree's classification decisions.

### Support Vector Machine

Because an RBF SVM does not provide a direct `feature_importances_` attribute, **permutation importance** was used.

The most important SVM features included:

1. **Proline**
2. **Flavanoids**
3. **OD**
4. **Alcohol**
5. **Hue**

### Common Important Features

Three features appeared among the five most important variables for both models:

- **Flavanoids**
- **Proline**
- **OD**

This suggests that these chemical properties contain particularly useful predictive information for distinguishing between the wine classes.

---

##  Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Classification reports
- Confusion matrices
- ROC curves
- Area Under the Curve (AUC)

Because the dataset contains three classes, the ROC analysis was performed using a **One-vs-Rest (OvR)** approach.

---

##  Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook / Google Colab

---

## Skills Demonstrated

This project demonstrates practical experience with:

- Exploratory Data Analysis (EDA)
- Data preprocessing
- Data visualisation
- Feature scaling
- Supervised machine learning
- Multiclass classification
- Decision Trees
- Support Vector Machines
- Model evaluation
- Confusion matrices
- ROC/AUC analysis
- Feature importance
- Permutation importance
- Interpretation of machine learning results

---

##  Project Structure

```text
Wine Classification Project/
│
├── Wine_Classification.ipynb
├── wine.csv
└── README.md