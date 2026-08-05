# Content Refresh Prioritization Using Machine Learning

## Author

Zain Ali Shah

## Abstract

This project investigates whether observable search performance signals can help prioritize content pages for refresh. A baseline rule and a Random Forest model were developed using anonymized FlyRank internship data. The approaches were evaluated using grouped validation to reduce the risk of information leakage. The Random Forest model showed improved ranking performance compared with the baseline on the evaluated split. These results are observational and intended to provide decision-support for human content teams rather than automate publishing decisions.


# 1. Problem Statement

## Research Question

Can observable search performance signals be used to rank web pages that should be reviewed for content refresh?

## Decision Supported

This work supports content teams in deciding which pages should be reviewed first for possible updates.

Instead of manually reviewing thousands of pages, the system creates a ranked list based on measurable historical signals.

## Why Machine Learning Helps

Content performance depends on multiple interacting signals such as:

- content age
- impressions
- search position
- click-through rate
- historical trends

A fixed rule may miss complex patterns between these signals. Machine learning can combine multiple observations and provide a prioritization score.


# 2. Data

## Dataset

This project uses the FlyRank ML Internship dataset containing anonymized search performance information.

## Data Release

The starter dataset provided through the internship repository was used.

## Unit of Analysis

One row represents one content page with observed search performance measurements.

## Features Used

The model uses:

- Content age
- Days since last update
- Impressions
- Average search position
- Click-through rate
- Word count


## Excluded Information

The following fields were excluded:

- Client-identifying information
- Private URLs
- Private search queries
- Future performance values
- Label-derived columns
- Product decision flags


These exclusions reduce leakage risk and keep evaluation realistic.


# 3. Methodology


## ML Task

Content refresh prioritization was framed as a classification and ranking problem.

The goal was to identify pages that deserve human review.

## Target / Proxy

The target represents whether a page shows an observed declining performance pattern.

## Baseline

A transparent rule-based baseline was created using content staleness and visibility signals.

The baseline provides a simple comparison before applying machine learning.

## Model

A Random Forest model was selected because it can capture nonlinear relationships while remaining interpretable through feature importance analysis.


## Validation Design

Grouped validation was used so similar client groups were not split between training and testing.

This reduces the chance of the model learning client-specific patterns.


## Leakage Checks

Potential leakage sources were reviewed:

- future information
- label-derived columns
- product flags

Leakage experiments showed that including invalid information could artificially improve results, so these features were removed.


# 4. Results


## Model Compared With Baseline


| Method | Precision@50 |
|---|---:|
| Baseline Rule | 0.240 |
| Random Forest | 0.740 |


## Model vs Baseline

![Model vs Baseline](work/figures/model_vs_baseline.png)


The Random Forest model achieved higher Precision@50 compared with the baseline on the evaluated split.

The result suggests that combining multiple signals can improve prioritization compared with a simple threshold rule.


# Feature Importance


![Feature Importance](work/figures/feature_importance.png)


The feature importance analysis shows which observable signals contributed most to the model decisions.


# Leakage Audit


![Leakage Comparison](work/figures/leakage_comparison.png)


The leakage audit demonstrated that future or label-related information can create unrealistic performance improvements.


# 5. Limitations


This project has several limitations:

- It does not prove causal relationships between content changes and search performance.
- It does not predict search engine algorithms.
- Results may change on different datasets or future time periods.
- Recommendations require human review before implementation.


The model provides decision-support, not automatic content decisions.


# 6. Ranked Recommendations


The output produces a ranked queue of pages for review.


Recommended actions:


1. Refresh outdated content with strong historical visibility.
2. Review pages showing declining performance trends.
3. Investigate pages with strong impressions but weak CTR.
4. Improve metadata where appropriate.
5. Monitor results after content updates.


![Recommended Actions](work/figures/recommended_actions.png)


# 7. Reproducibility


All experiments are available in the GitHub repository:

Repository:

https://github.com/ZainAliShah199/flyrank-ml-internship


Important notebooks:

- ML-07 Baseline Action Score
- ML-08 Capstone Modeling
- ML-09 Validation Audit
- ML-10 Content Action Playbook
- ML-11 Capstone Report


The notebooks contain the complete workflow from feature creation to evaluation.


# 8. Artifacts


This paper includes:

- Model vs baseline comparison
- Feature importance analysis
- Leakage audit
- Ranked recommendation output
- Validation analysis
- Error review


# 9. Acknowledgments and Data Credit


This project was completed as part of the FlyRank Machine Learning Internship.

Built on the FlyRank ML Internship dataset.

Data credit:

https://flyrank.ai


No client-identifying information, private URLs, or private queries are included.
