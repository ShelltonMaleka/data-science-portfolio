# Solubility Prediction Using Machine Learning

This project predicts the aqueous solubility of chemical compounds using molecular descriptors from the Delaney dataset.

It compares **Linear Regression**, **Support Vector Regression (SVR)**, and **Random Forest Regression** to identify the model with the best predictive performance.

## Project Objective

Build and evaluate regression models that predict experimentally measured solubility (`logS`) from molecular properties.

The project covers:

- Data exploration and preprocessing
- Regression model selection and training
- Model evaluation and comparison
- Prediction and residual visualizations
- Feature importance analysis
- Discussion of results and limitations

## Dataset

The processed Delaney dataset contains **1,128 chemical compounds**.

### Input Features

- Minimum Degree
- Molecular Weight
- Number of H-Bond Donors
- Number of Rings
- Number of Rotatable Bonds
- Polar Surface Area

### Target Variable

`measured log solubility in mols per litre`

Lower `logS` values indicate lower solubility.

The dataset contains no missing values or duplicate SMILES strings. `Compound ID` and raw `smiles` are excluded from the model inputs.

## Technologies Used

- Python
- pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
- Jupyter Notebook

## Project Workflow

1. Load and inspect the dataset.
2. Check missing values, duplicates, and data types.
3. Explore solubility distributions and feature correlations.
4. Split the dataset into training and testing sets.
5. Train a mean baseline and three regression models.
6. Evaluate models using MSE, RMSE, and R².
7. Visualize predictions and residuals.
8. Analyse feature importance and discuss limitations.

The dataset is split into **80% training** and **20% testing**, using `random_state=42`.

SVR uses a `StandardScaler` pipeline fitted only on the training data. The Random Forest uses **500 trees**.

## Model Performance

| Model | Test MSE | Test RMSE | Test R² |
|---|---:|---:|---:|
| Linear Regression | 1.437 | 1.199 | 0.696 |
| Support Vector Regression | 0.956 | 0.978 | 0.798 |
| **Random Forest Regression** | **0.815** | **0.903** | **0.827** |

Random Forest achieved the best test performance among the three models.

Its test R² of **0.827** means it explains approximately **82.7% of the variation in held-out logS** for this split. This is not a percentage of compounds predicted correctly.

The model achieved:

- **Training R²:** 0.974
- **Testing R²:** 0.827
- **Testing RMSE:** 0.903 logS

The gap between training and testing performance suggests some overfitting.

## Feature Importance

| Feature | Random Forest Importance |
|---|---:|
| Molecular Weight | 0.583 |
| Polar Surface Area | 0.248 |
| Number of Rings | 0.067 |
| Number of Rotatable Bonds | 0.059 |
| Number of H-Bond Donors | 0.039 |
| Minimum Degree | 0.004 |

**Molecular Weight** and **Polar Surface Area** have the highest importance in the fitted Random Forest.

These scores describe the model's reliance on each feature. They do not establish chemical causation or show the direction of an effect.

## Visualizations

The notebook includes:

- Distribution of measured solubility
- Feature correlation heatmap
- Model comparison by test RMSE
- Actual versus predicted solubility
- Residual plot
- Random Forest feature importance plot

## Project Files

- `Solubility_Prediction_Delaney.ipynb` — complete analysis and model evaluation
- `solubility.csv` — processed dataset
- `README.md` — project documentation


## Limitations

- Results are based on a single random train/test split.
- Chemically similar compounds may appear in both sets.
- Only six numeric molecular descriptors are used.
- Raw SMILES strings are not converted into molecular fingerprints.
- The training/test performance gap suggests some overfitting.
- Feature importance can be affected by correlated predictors.

## Future Improvements

- Assess stability using cross-validation on the training data.
- Tune model hyperparameters within training folds.
- Include additional chemical descriptors and molecular fingerprints.
- Use scaffold-based splitting to evaluate unfamiliar chemical structures.
- Investigate prediction errors across different solubility ranges.

## Reference

Delaney, J. S. (2004). *ESOL: Estimating Aqueous Solubility Directly from Molecular Structure*. Journal of Chemical Information and Computer Sciences, 44(3), 1000–1005.
