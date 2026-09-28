# Geochemical Database and Anomaly Analysis

## Overview

This project explores the auditing, integration, and analysis of geochemical sample data from two historical datasets.

The main goal was to determine whether the datasets could be reliably joined, identify data-quality and metadata issues, and investigate unusual geochemical records using anomaly detection.

The workflow focuses on data quality, traceability, reproducibility, geospatial metadata, and responsible interpretation of statistical anomalies.

## Objectives

The project aimed to:

- Audit geochemical datasets before analysis
- Identify missing, duplicated, censored, and non-numeric values
- Build a data dictionary for important variables
- Validate sample identifiers before joining datasets
- Perform a one-to-one outer join while preserving traceability
- Examine differences in coordinate reference systems
- Apply Isolation Forest for multivariate anomaly detection
- Compare anomaly results under different feature sets
- Distinguish statistical anomalies from confirmed data errors
- Create a reproducible analysis workflow

## Dataset

Two geochemical datasets representing OLD and NEW sample records were analysed.

The main sample identifier was:

`Unique ID`

Five chemical variables were selected for detailed investigation:

- Copper (Cu)
- Zinc (Zn)
- Uranium (U)
- Iron (Fe)
- Manganese (Mn)

The OLD dataset contained 3,441 sample records.

The raw NEW dataset contained 3,442 rows. One row was identified as a metadata row containing measurement units rather than a sample observation. After separating this row, the NEW dataset contained 3,441 sample records.

## Data Quality Audit

Before joining the datasets, several checks were performed.

These included:

- Missing sample identifiers
- Duplicate sample identifiers
- Missing chemical measurements
- Censored measurements
- Non-numeric values
- Measurement units
- Coordinate reference information

Both sample tables contained zero missing and zero duplicate `Unique ID` values after the NEW metadata row was separated.

The audit also identified censored chemical measurements, including 11 censored Uranium values in the OLD dataset and 34 censored Manganese values in the NEW dataset.

Original values were preserved rather than silently replacing or deleting censored measurements.

## Data Integration

The datasets were joined using `Unique ID`.

A one-to-one outer join was used so that unmatched samples would remain visible.

The resulting join contained:

- 3,441 matched samples
- 0 OLD-only samples
- 0 NEW-only samples

A sample trace was also created to demonstrate how joined observations could be traced back to their source datasets.

## Geospatial Considerations

The two datasets use different coordinate references.

The OLD dataset contains coordinates labelled as NAD83, while the NEW dataset contains coordinates labelled as NAD27.

These coordinate values were not assumed to represent directly comparable positions without an appropriate coordinate reference system transformation.

This highlights the importance of checking spatial metadata before interpreting differences between historical datasets.

## Anomaly Detection

Isolation Forest was used to identify unusual multivariate geochemical records.

### Baseline Model

The baseline analysis used:

- Cu
- Zn
- U

The features were standardised using `StandardScaler`.

The baseline contained:

- 3,440 eligible records
- 1 excluded record

### Alternative Model

A second Isolation Forest analysis added Mn:

- Cu
- Zn
- U
- Mn

The alternative model contained:

- 3,406 eligible records
- 35 excluded records

Adding Mn substantially changed the anomaly ranking of several samples.

For example, sample `013M783296` changed from baseline rank 2601 to alternative rank 39 after Mn was included.

This demonstrates how strongly anomaly detection results can depend on feature selection.

## Interpretation

Five samples with clear classification differences between the baseline and alternative analyses were investigated further.

Rather than automatically removing these observations, they were classified as requiring further investigation.

A statistical anomaly does not necessarily represent incorrect data. It may instead represent genuine geological variation, unusual mineralisation, analytical differences, or a data-quality problem.

For this reason, anomaly detection was treated as a tool for prioritising records for investigation rather than an automatic data-cleaning rule.

## Reproducibility

The workflow records information required to reproduce the analysis, including:

- Random seed
- Input file hashes
- Python version
- pandas version
- NumPy version
- scikit-learn version
- Feature configurations
- Scaling method
- Isolation Forest configuration

The analysis used the student-number-derived random seed:

`12016`

## Technologies

- Python
- pandas
- NumPy
- scikit-learn
- Jupyter Notebook
- Isolation Forest
- StandardScaler

## Project Structure

```text
Geochemical Database and Anomaly Analysis/
│
├── README.md
├── 2539990_A1.ipynb
├── outputs/
│   ├── audit.csv
│   ├── data_dictionary.csv
│   ├── joined_samples.csv
│   ├── join_counts.csv
│   ├── five_sample_trace.csv
│   └── anomaly_decisions.csv
└── figures/