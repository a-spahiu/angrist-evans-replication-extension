# Children and Their Parents' Labor Supply: Replication & Extension

This repository contains the empirical replication and analytical extension of the seminal paper by **Angrist and Evans (1998)**: *"Children and Their Parents' Labor Supply: Evidence from Exogenous Variation in Family Size"*. 

The project replicates the original Ordinary Least Squares (OLS) and Two-Stage Least Squares (2SLS) estimates using sibling sex composition as an instrumental variable. Additionally, it features an econometric extension evaluating the functional form robustness of the Linear Probability Model (LPM) via an IV-Probit Control Function approach with bootstrapped inference.

For the comprehensive review of the methodology, descriptive statistics, and the full discussion of the replication and extension results, please refer to the Econ_Personal.pdf file included in this repository.

---

## Project Structure

* `Cleaning.R` – Script to filter, clean, and prepare the raw Census PUMS data.
* `Table_2.R`, `Table_3.R`, etc. – Scripts dedicated to replicating specific baseline tables, descriptive statistics, and main OLS/2SLS regression models from the paper.
* `Extension.R` – Script executing the IV-Probit robustness check, endogeneity tests, and average marginal effects (AME) calculations.
* `Econ_Personal.pdf` – Full paper review, replication analysis, and extension report.
* `data/` – Directory where the processed datasets must be stored (see Data Setup).

---

## Data Setup & Requirements

Due to file size constraints, the raw data is not hosted directly in this repository. 

1. Download the 1980 and 1990 Census PUMS datasets from the following link: https://economics.mit.edu/people/faculty/josh-angrist/angrist-data-archive.
2. Before running any script, create a folder named `data` in the root directory of this project (the same folder where the R scripts are located).
3. Place the downloaded datasets directly into the `data/` folder.

---

## Execution Guide

To replicate the analysis from scratch, run the R scripts in the following order:

### 1. Data Processing
Execute the cleaning script first to format variables, apply sample restrictions (women aged 21–35 with two or more children), and generate the instrumented variables:

`source("Cleaning.R")`

### 2. Baseline Replication
Once the data is prepared, you can run any of the standalone table scripts to replicate the paper's original findings (e.g., demographic characteristics, fertility sex-mix fractions, Wald, and 2SLS results):

`source("Table_2.R")`
`source("Table_3.R")`

### 3. Structural Extension
To evaluate the functional form properties and test the robustness of the LPM estimations against a non-linear approach, execute:

`source("Extension.R")`

---

## Key Findings & Extension Summary

* **Replication:** Consistent with Angrist & Evans, the 2SLS models confirm that an additional child significantly reduces mothers' labor supply (employment probability, hours, and earnings), while fathers' labor supply remains statistically unaffected. The negative impact is heavily concentrated among less-educated and financially constrained households.
* **Extension (IV-Probit):** Replacing the baseline LPM second-stage with an IV-Probit via a Control Function approach yields an Average Marginal Effect (AME) of **-13.6 percentage points** for the fertility indicator (`more_than_2`). This closely matches the baseline 2SLS estimate (~12 p.p.), demonstrating that the non-linear bounded nature of the dependent variable does not distort the substantive causal conclusions of the original study. Bootstrapped standard errors confirm the stability of the asymptotic inference in this large sample framework.
