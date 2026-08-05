# Content Refresh Prioritization Using Machine Learning

## FlyRank ML Internship Capstone Research Paper

**Author:** Zain Ali Shah  
**Lane:** Content Refresh Opportunity Scoring  
**Project Type:** Machine Learning Decision-Support System  


---

# Abstract

This project investigates whether observable search performance signals can help prioritize content pages for refresh review. Using anonymized FlyRank ML Internship dataset information, a rule-based baseline and a Random Forest model were developed and compared. The approaches were evaluated using a grouped validation strategy designed to reduce information leakage between similar content sources. The Random Forest model achieved higher ranking performance than the baseline on the evaluated split, showing that combining multiple signals can improve prioritization. The output is intended as a decision-support tool for human reviewers and does not automate content decisions.

---

# 1. Problem Framing

## Research Question

Can observable search performance signals be used to rank web pages that should be reviewed for content refresh?


## Decision Supported

The system supports content teams by creating a ranked list of pages that may deserve review.

Instead of manually checking thousands of pages, reviewers can focus their attention on pages with stronger observed signals of possible improvement opportunities.


## Unit of Analysis

One row represents one content page with its observable historical performance information.


## Output

The output is:

- ranked review queue
- refresh priority score
- reason codes explaining recommendations


## Human Action

A content specialist reviews the recommended pages and decides whether updates, improvements, or monitoring are appropriate.


## Cost of Wrong Recommendation

A false recommendation may waste editorial time, while missing a useful opportunity may delay possible improvements.

The system therefore supports prioritization rather than automatic publishing decisions.

---

# 2. Data

## Dataset

This project uses the FlyRank ML Internship dataset containing anonymized search performance information.

Data source:

Built on the FlyRank ML Internship dataset.


## Data Release

The project uses the starter dataset and supporting internship warehouse release.

The dataset contains observable content and search performance signals.


## Features Used

The model uses signals such as:

- Content age
- Days since last update
- Impressions
- Average position
- Click-through rate (CTR)
- Word count
- Engagement-related metrics


## Excluded Data

The following fields were intentionally excluded:

- Client-identifying information
- Private URLs
- Raw search queries
- Product decision flags
- Future information
- Label-derived fields


These exclusions reduce leakage risk and keep evaluation honest.

---

# 3. Methodology

## Machine Learning Task

This project treats content refresh prioritization as a classification and ranking problem.


## Baseline

A transparent rule-based scoring system was created first.

The baseline uses observable signals such as:

- freshness
- visibility
- search performance


The baseline provides a simple comparison point before introducing machine learning.


## Model

A Random Forest classifier was selected because:

- it handles nonlinear relationships
- it works well with mixed signals
- feature importance can be interpreted


## Validation Strategy

A grouped validation strategy was used.

Pages from the same client group were kept together so that similar examples did not appear in both training and testing.


## Leakage Checks

Potential leakage sources were reviewed:

- future performance metrics
- target-derived fields
- product-generated decisions

Leakage experiments showed that including answer-related information can artificially increase scores.

---

# 4. Results

The model was compared against the baseline using the same validation approach.


| Method | Precision@50 |
|---|---:|
| Baseline Rule | 0.240 |
| Random Forest | 0.740 |


## Interpretation

The Random Forest model achieved higher Precision@50 than the baseline on the evaluated split.

This suggests that combining multiple observable signals can improve prioritization compared with a fixed rule.

The result is observational and intended for decision-support.

---

# Model vs Baseline Comparison

![Model vs Baseline](work/figure/model_vs_baseline.png)


---

# Feature Importance

Feature importance analysis shows which observable signals contributed most to the model's ranking decisions.


![Feature Importance](work/figure/feature_importance.png)


---

# Leakage Audit Comparison

The leakage experiment demonstrates how using information derived from the target can create unrealistic performance.


![Leakage Comparison](work/figure/leakage_comparison.png)


---

# 5. Limitations

This project has several limitations:

- It does not prove that content updates cause performance improvements.
- It does not predict search engine algorithms.
- Results may change on different datasets or future time periods.
- Recommendations require human review before action.
- The model identifies prioritization opportunities, not guaranteed wins.


---

# 6. Ranked Recommendations

The generated ranking supports the following content actions:


## Refresh outdated visible pages

Pages with strong visibility but older content may deserve review.


## Improve declining pages

Pages showing weaker observed trends may require investigation.


## Review CTR opportunities

Pages with impressions but lower CTR may benefit from metadata or presentation improvements.


## Monitor performance

Some pages should be tracked before making changes.


These recommendations are decision-support suggestions and require editorial validation.


---

# Recommended Actions Output

![Recommended Actions](work/figure/recommended_actions.png)


---

# 7. Model Interpretation

The model provides evidence about patterns in historical search performance signals.

Feature importance and error analysis help explain why certain pages receive higher scores.

The output should be interpreted as a prioritization assistant, not an automatic decision maker.

---

# 8. Reproducibility

All experiments were created using notebooks stored in the repository.

Important notebooks:

- ML-02 Research Question
- ML-03 ML Task Framing
- ML-04 Data Contract
- ML-06 Signal Audit
- ML-07 Baseline Score
- ML-08 Modeling
- ML-09 Validation Audit
- ML-10 Action Playbook
- ML-11 Capstone


The notebooks contain:

- feature preparation
- baseline creation
- model training
- validation
- recommendation generation


---

# 9. Acknowledgments and Data Credit

This work was completed as part of the FlyRank Machine Learning Internship.

Built on the FlyRank ML Internship dataset.

Data credit:

https://flyrank.ai


No client-identifying information, private URLs, or private search queries are included in this project.

---

# Conclusion

This capstone demonstrates how machine learning can support content prioritization decisions using observable search performance signals.

The system improves ranking compared with a simple baseline while maintaining responsible ML practices through validation, leakage checks, and human review requirements.

The final output is a decision-support workflow that helps teams decide where to investigate first.
