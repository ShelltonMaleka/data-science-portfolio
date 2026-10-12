# Hydrocarbon Property Prediction Using RDKit

## Overview

This project explores the use of machine learning to predict the melting and boiling points of hydrocarbons from their molecular structures.

Using RDKit, molecular descriptors are calculated from SMILES strings and used as inputs to regression models. The project combines cheminformatics, exploratory data analysis and supervised machine learning to investigate how molecular structure relates to physical properties.

## Objectives

- Process molecular structures using RDKit.
- Calculate molecular weight and aromatic ring count.
- Investigate missing measurements and repeated canonical SMILES.
- Explore relationships between molecular descriptors and physical properties.
- Train and evaluate Linear Regression and Random Forest models.
- Compare the prediction of melting point and boiling point.
- Test additional molecular descriptors to investigate potential improvements.

## Dataset

The dataset contains 194 hydrocarbons across different structural classes.

The initial predictors are:
- Molecular weight
- Aromatic ring count

The target variables are:
- Boiling point (°C)
- Melting point (°C)

Density, flash point and autoignition temperature are excluded from the model inputs because they are measured properties rather than descriptors calculated from molecular structure.

## Methodology

1. Load and inspect the dataset using pandas.
2. Convert SMILES strings into molecular representations using RDKit.
3. Calculate molecular descriptors and investigate repeated canonical SMILES.
4. Explore the data using scatter plots.
5. Train Linear Regression and Random Forest models.
6. Evaluate predictions using RMSE and R² on held-out data.
7. Investigate molecules with identical descriptor values but different melting points.
8. Compare the original descriptors with an extended set of molecular features.

## Technologies Used

- Python
- pandas and NumPy
- RDKit
- Matplotlib and Seaborn
- scikit-learn
- Jupyter Notebook

## Project Structure

```text
hydrocarbon-property-prediction/
├── data/
│   └── hydrocarbons.csv
├── hydrocarbon_property_prediction.ipynb
├── README.md
└── 
```

## Results

The notebook reports the test-set RMSE and R² for both regression models and both target properties. It also compares the original and extended descriptor sets.

The final results and conclusions will be documented here after the experiments have been completed.

## Limitations

The dataset is relatively small, and the initial models use only two molecular descriptors. Molecular weight and aromatic ring count cannot fully capture molecular shape, branching, symmetry and crystal packing, which can influence physical properties.

The evaluation also depends on the selected train-test split. Additional validation and a larger dataset would help establish how well the models generalise to unseen molecules.

## Future Improvements

- Evaluate additional molecular descriptors.
- Compare more regression algorithms.
- Use cross-validation for more robust evaluation.
- Investigate descriptor importance and prediction errors.
- Explore larger molecular property datasets.

