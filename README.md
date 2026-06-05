# Clinical Phenotype Discovery in Dengue Patients using Gaussian Mixture Models (GMM)

# Project Summary

This project was undertaken to better understand the heterogeneity of dengue infection by identifying clinically meaningful patient phenotypes using unsupervised machine learning. The analysis was based on demographic, clinical, and laboratory variables collected at admission, with the goal of discovering hidden patient subgroups without relying on predefined labels.

A Gaussian Mixture Model (GMM) was employed to uncover latent patterns within a retrospective dengue cohort. The identified phenotypes were subsequently validated against important clinical outcomes, including ICU admission, dialysis requirement, shock, and mortality, to assess their clinical significance and potential utility in risk stratification.

# Problem Statement

Dengue patients often present with highly heterogeneous clinical manifestations ranging from mild self-limiting illness to severe disease requiring intensive care support.Traditional clinical categorization may not fully capture underlying disease variability. Therefore, this study aimed to answer the following question:
Can machine learning identify distinct dengue patient phenotypes that are clinically meaningful and associated with different outcomes?

# Dataset Description

The dataset consisted of approximately 1,396 dengue patients and contained:
# Demographic Variables:

* Age
* Sex
* Duration of Illness (DOI)

# Clinical Variables:

* Diabetes Mellitus (DM)
* Hypertension (HTN)
* Chronic Kidney Disease (CKD)
* Coronary Artery Disease (CAD/IHD)

## Laboratory Variables:

* Hemoglobin (Hb)
* White Blood Cell Count (WBC)
* Platelet Count
* Hematocrit
* Creatinine
* Urea
* Serum Albumin
* C-Reactive Protein (CRP)
* AST
* ALT
* Total Bilirubin

## Outcome Variables:

These variables were intentionally excluded from clustering and reserved for independent validation:

* ICU/HDU Admission
* Dialysis Requirement
* Mechanical Ventilation
* Shock
* 7-Day Mortality
* 28-Day Mortality

# Data Preprocessing

A structured preprocessing workflow was implemented prior to clustering.

## Data Cleaning

* Standardized missing value representations.
* Removed inconsistent textual entries.
* Corrected binary outcome variables.
* Converted categorical variables into machine-learning compatible formats.

## Data Privacy

Patient identifiers were removed before analysis to maintain confidentiality and comply with ethical data handling practices.
No personally identifiable information (PII) is included in this repository.

## Missing Value Handling

Missing numerical values were imputed using median-based imputation to reduce the impact of outliers and preserve dataset integrity.

## Feature Engineering

Laboratory variables AST and ALT demonstrated substantial positive skewness.
Logarithmic transformations were therefore applied:
* AST_log
* ALT_log
to improve distributional properties and model stability.

## Feature Scaling

Since clustering algorithms are sensitive to feature magnitude, all selected variables were standardized using StandardScaler before model training.

# Exploratory Data Analysis (EDA)

Comprehensive exploratory analysis was conducted to understand:

* Variable distributions
* Missing data patterns
* Outlier behavior
* Feature relationships
* Clinical characteristic differences

Visualizations included:

* Boxplots
* Distribution plots
* Correlation heatmaps
* Cluster profiling summaries

# Machine Learning Methodology

## Why Unsupervised Learning?

The dataset did not contain predefined phenotype labels.
Therefore, an unsupervised learning approach was necessary to discover hidden patient subgroups directly from the data.

## Why Gaussian Mixture Models (GMM)?

Gaussian Mixture Models were selected because:

* They model complex data distributions more flexibly than K-Means.
* Patients can belong probabilistically to clusters.
* Clinical populations often exhibit overlapping characteristics rather than rigid boundaries.
* GMM is particularly suitable for heterogeneous healthcare datasets.

# Cluster Selection Strategy

Multiple clustering solutions were evaluated across different values of K.
The optimal number of clusters was assessed using:

## Silhouette Score

Measures cluster separation and cohesion.

Higher values indicate better-defined clusters.

## Calinski-Harabasz Index

Evaluates the ratio of between-cluster dispersion to within-cluster dispersion.

Higher values indicate stronger clustering structure.

## Davies-Bouldin Index

Measures cluster similarity.

Lower values indicate better cluster separation.

## Adjusted Rand Index (ARI)

Used to assess agreement between clustering approaches and evaluate cluster stability.

After evaluating multiple candidate solutions, a 4-cluster solution was selected because it provided the best balance between statistical performance, cluster stability, and clinical interpretability.


# Phenotype Discovery

The final GMM model identified four distinct patient phenotypes.

## Phenotype 0 – Late Presentation Phenotype

* Longer duration of illness at presentation.
* Relatively preserved organ function.
* Moderate clinical risk profile.

## Phenotype 1 – Severe Renal–Inflammatory Phenotype

* Elevated creatinine and urea.
* Higher CRP levels.
* Increased CKD prevalence.
* Highest requirement for ICU support and dialysis.

## Phenotype 2 – Intermediate Inflammatory Phenotype

* Moderate inflammatory burden.
* Intermediate disease severity.
* Increased risk of adverse outcomes compared with mild disease.

## Phenotype 3 – Mild Dengue Phenotype

* Lower inflammatory markers.
* Better renal function.
* Lowest mortality and intervention rates.

# Outcome Validation

Phenotypes were independently validated against clinical outcomes that were not used during clustering.

The identified phenotypes demonstrated meaningful differences in:

* ICU admission
* Dialysis requirement
* Mechanical ventilation
* Shock incidence
* Short-term mortality
* Long-term mortality

These findings support the clinical relevance of the discovered phenotypes.

# Technologies Used

* Python
* Pandas
* NumPy
* Scikit-Learn
* SciPy
* Matplotlib
* Seaborn

# Key Skills Demonstrated

* Exploratory Data Analysis (EDA)
* Data Cleaning and Preprocessing
* Missing Value Imputation
* Feature Engineering
* Feature Scaling
* Unsupervised Machine Learning
* Gaussian Mixture Models (GMM)
* Cluster Validation
* Statistical Analysis
* Healthcare Analytics
* Clinical Data Interpretation
* Data Visualization

# Repository Contents

* Dengue_Phenotype_Discovery_GMM.ipynb
* requirements.txt
* README.md

# Data Availability

The original dataset is not publicly available due to patient privacy, confidentiality, and institutional data-sharing restrictions.

Only the analysis workflow and de-identified findings are shared in this repository.
