# ML-12: Storytelling and Demo Outline

## 5-Minute Demo Outline

### 1. Problem (1 minute)

Large websites have many pages that need continuous improvement. Manual review of every page is expensive and inconsistent.

The question for this project was:

Can observable search performance signals help prioritize pages for content refresh review?

---

### 2. Method (1 minute)

I created a content refresh prioritization workflow.

The approach included:

- Defining a content page as the unit of analysis
- Building observable search performance features
- Creating a transparent baseline rule
- Training a Random Forest model
- Comparing the model against the baseline using grouped validation

The evaluation focused on honest model comparison rather than maximizing complexity.

---

### 3. Key Visualization (1 minute)

The main chart to present:

Model vs Baseline Performance Comparison

This chart shows the difference between the baseline rule and Random Forest model using Precision@50.

Supporting charts:

- Feature importance
- Leakage comparison
- Recommended action distribution

---

### 4. Honest Result (1 minute)

The Random Forest model achieved higher Precision@50 than the baseline on the evaluated split.

This suggests that combining multiple observable signals can improve prioritization.

However, the result is observational and should be interpreted as decision-support rather than a guarantee of improved search performance.

---

### 5. Recommendation (1 minute)

The recommended workflow is:

1. Review high-ranked pages first
2. Investigate reasons behind the ranking
3. Apply human editorial judgment
4. Monitor results after changes

The system supports prioritization but does not replace content experts.


---

# Social Media Post

## Machine Learning Capstone: Content Refresh Prioritization

I built a machine learning workflow to help prioritize content pages for refresh review using observable search performance signals.

The project compared a transparent baseline rule against a Random Forest model using grouped validation to reduce leakage risk.

The results showed that combining multiple signals improved ranking performance on the evaluated split. The goal was not automation, but building a trustworthy decision-support system that helps content teams focus their effort where it matters most.

Built as part of the FlyRank ML Internship.


---

# Employer-Facing Summary

I built a machine learning system for content refresh prioritization using anonymized search performance data from the FlyRank ML Internship dataset.

The project included feature engineering, baseline development, Random Forest modeling, grouped validation, leakage auditing, and recommendation generation.

The model showed improved Precision@50 compared with the baseline on the evaluated split, demonstrating how ML can support practical decision-making while maintaining honest limitations.
