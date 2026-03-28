# Complex Survey Analysis with NFHS/DHS Data (SPSS) #
## Overview ##
This repository presents a reproducible implementation of complex survey design (CSD) analysis in SPSS using data from large-scale household surveys such as NFHS (India) and DHS. It highlights correct analytical sequencing, weighting procedures, and common pitfalls that can lead to biased estimates and incorrect inference.

These datasets use multistage stratified cluster sampling, and valid inference requires proper handling of:

- Sampling weights
  
- Stratification
  
- Clustering

Failure to account for these design elements can lead to biased estimates, incorrect standard errors, and misleading conclusions.
This repository demonstrates a structured approach to ensure methodologically sound analysis using SPSS Complex Samples procedures.

## Why Complex Survey Design Matters ##

### NFHS/DHS data are not simple random samples. They involve: ###

- Stratification to improve representativeness

- Clustering to reduce cost and operational complexity

- Unequal probabilities of selection, requiring weights

### Ignoring these features: ###

- Underestimates standard errors

- Inflates statistical significance

- Produces misleading policy conclusions

### Proper implementation ensures that estimates are: ###

- Population-representative

- Statistically valid

- Comparable across studies

- Common Pitfalls in Applied Survey Analysis

### This section highlights frequent issues observed in applied research: ###

❌ Using weights without accounting for survey design

Applying weights alone (without specifying strata and clusters) does not fully correct for the sampling design and results in incorrect variance estimation.

❌ Filtering instead of subpopulation analysis

Dropping observations before analysis alters the sampling structure.
Correct practice is to use subpopulation (domain) analysis, which preserves design information.

❌ Ignoring normalization of weights

NFHS/DHS weights (e.g., V005) must be rescaled (typically divided by 1,000,000) before use.
Failure to do so leads to incorrect population estimates.

❌ Misinterpreting weighted vs unweighted sample size

- Unweighted N: actual sample size

- Weighted N: population-representative estimate

Confusing the two can result in incorrect reporting and interpretation.

## Analytical Workflow ##

The repository follows a structured, step-by-step workflow:

### 1. Data Preparation ###

- Import dataset

- Inspect variables and distributions

- Identify target population

### 2. Variable Construction ###

- Recode key covariates (e.g., education, wealth index)

- Construct outcome variables (e.g., full immunisation)

- Ensure consistency with standard definitions (e.g., WHO guidelines)

### 3. Subpopulation Definition ###

- Define analytical sample (e.g., children aged 12–23 months)

- Use indicator variables rather than filtering

- Preserve full dataset structure for correct variance estimation

### 4. Weighting ###

- Normalize sampling weights:

- COMPUTE weight = V005 / 1000000.

- Ensure correct application in all analyses

### 5. Complex Samples Design Specification ###

Define survey design using:

- Strata (V022)

- Cluster (V021)

- Weight (V005)

- Create a Complex Samples Plan file (CSPLAN)

### 6. Analysis ###

- Descriptive statistics (weighted proportions)

- Cross-tabulations with design-based tests

- Regression modelling (e.g., logistic regression)

All analyses are conducted using SPSS Complex Samples procedures to ensure valid inference.

## Sensitivity Analysis ##

The repository also includes a sensitivity analysis using an alternative definition of immunisation (e.g., card-only records), implemented using the same analytical framework.

## Reproducibility ##

All analyses are fully reproducible using the provided SPSS syntax files.
Users can adapt the workflow to other DHS/NFHS datasets with minimal modification.

## Intended Audience ###

This repository is designed for:

- Epidemiologists

- Biostatisticians
  
- Public health researchers

- Graduate students working with survey data
  
## Final Note ##

This workflow aims to promote rigorous and transparent use of complex survey data, ensuring that statistical analyses accurately reflect population-level patterns and support reliable public health decision-making.
