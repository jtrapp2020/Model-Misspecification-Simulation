# GLM Simulation Study: Impact of Model Misspecification

## Overview
This project is a statistical simulation study designed to evaluate the consequences of **model misspecification** in Generalized Linear Models (GLMs). Specifically, it investigates what happens when a Normal (Gaussian) linear regression model is applied to count data that follows a Poisson distribution.

The study assesses the impact of this misspecification on:
1.  **Bias:** The accuracy of the estimated mean parameter ($\hat{\lambda}$).
2.  **Variance:** The precision of the slope coefficient ($\hat{\beta}$), comparing **Naïve** vs. **Robust** (Sandwich) variance estimators.

## Study Design
The simulation runs 2,000 iterations across four distinct scenarios to test the sensitivity of the models to sample size and parameter magnitude:

* **Sample Sizes:** $N = 20$ and $N = 200$
* **True Poisson Parameter:** $\lambda = 4$ and $\lambda = 10$

### Methodology
For each iteration, the following steps were performed:
1.  **Data Generation:** Response variables ($Y$) were simulated from a Poisson distribution using a provided binary predictor variable.
2.  **Model Fitting:** Two GLMs were fit to the same data:
    * *Poisson Regression* (Correctly specified).
    * *Normal/Gaussian Regression* (Misspecified).
3.  **Evaluation:**
    * Bias was calculated as the difference between the average predicted $\hat{\lambda}$ and the true $\lambda$.
    * Standard Errors for the $\beta$ coefficients were calculated using both the standard (Naïve) covariance matrix and the Robust (Sandwich) estimator.

## Key Findings
* **Bias:** Interestingly, model misspecification had negligible impact on bias; the Normal model remained unbiased for the mean parameter.
* **Efficiency:** The primary consequence of misspecification was a drastic loss of efficiency. The Normal model produced significantly larger variances (and wider confidence intervals) compared to the Poisson model.
* **Robust Estimators:** While Robust Standard Errors provided some correction for the misspecified Normal model, they could not fully recover the precision lost by choosing the wrong likelihood distribution.

## Repository Contents
* `FinalProject.Rmd`: The primary RMarkdown source code that runs the simulation, aggregates data, and generates the analysis tables/plots.
* `x_n20-1.csv`*: The input dataset containing the binary predictor variable for the $N=20$ scenario.
* `x_n200-1.csv`*: The input dataset containing the binary predictor variable for the $N=200$ scenario.

*(Note: Ensure the CSV filenames match exactly what is in your repo)*

## How to Run
1.  Clone this repository.
2.  Open `FinalProject.Rmd` in RStudio.
3.  Ensure the following R packages are installed:
    ```r
    install.packages(c("tidyverse", "sandwich", "flextable"))
    ```
4.  Knit the document to HTML or Word to view the full simulation report.

## Author
**JT Rapp**
*December 2025*