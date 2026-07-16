# Capstone Report — SEO Content Optimization

- **Author:**Umm-e-Kalsoom
- **Lane:**SEO Content Optimization
- **Repo:** https://github.com/umm319/flyrank-ml-internship
- **Date:** July 2026

> Copy this file to `work/capstone_report.md` and fill it in as you build. The eight
> sections mirror the Pass / Needs-Work rubric axes, so nothing here is optional.

## 1. Problem framing
This project supports decisions about which website pages should be updated first to improve SEO performance.

Unit of analysis: Web page

Output: A ranked list of content improvement actions with reason codes to help prioritize SEO improvements.

What decision does this support? This project helps decide which website pages should be updated first to improve SEO performance.
 Name the unit of analysis.  webpage  the output A ranked score and action recommendation for each page.
A content manager reviews the recommendations and updates the selected pages.

the action a human takes from it, and the cost of a wrong
call.If the wrong page is selected, time and effort may be wasted and important pages may not be improved.
 Why does data/ML help here at all?   Machine learning can analyze many pages quickly, identify important patterns, and prioritize pages more accu

## 2. Data safety

Which data you used and which columns you deliberately excluded (and why). Leakage risks you
considered — especially label-derived fields (`trend_direction`, `trend_pct`) and pseudonymous
IDs (grouping only, never features). Confirm nothing client-identifying appears anywhere in
`work/`.
The project uses the public FlyRank internship dataset for SEO content analysis.

The features used include CTR, impressions, clicks, average position, and other SEO-related metrics.

Label-derived fields such as trend_direction and trend_pct were excluded to avoid data leakage. Client IDs were used only for grouping during validation and not as model features.

No client names, URLs, or private search queries were included in the notebook or report. The project follows public-safe data practices.

## 3. Baseline

The transparent rule or score you built first. Why it's a fair comparison, and its numbers on
the same data and metric as your model.
The baseline model used a simple rule-based scoring system to rank web pages.

Pages with low CTR, low clicks, and poor average position received higher priority scores for optimization.

This baseline is a fair comparison because it uses the same dataset, the same features, and the same evaluation approach as the machine learning model.

The machine learning model was compared directly against this baseline using the same validation split and performance metrics.
The baseline used a simple rule-based scoring system.

Pages with low CTR and poor average position received higher priority scores for optimization.

This is a fair comparison because both the baseline and the machine learning model were evaluated using the same dataset, the same validation split, and the same performance metrics.
## 4. Model / analysis

Your method and why it fits the lane. The exact feature list (and what you left out on
purpose). The target or proxy definition, in one sentence.
## 4. Model / Analysis

I used a Random Forest Regressor because it can capture complex relationships between features and CTR. The model uses features such as impressions, average position, clicks, device, and country to predict click-through rate (CTR). The target variable is CTR.

## 5. Evaluation

Your split (grouped by client? time-aware?) and why. Metrics, model vs baseline **on the same
split**. What the errors look like — a short error analysis beats a big metric table.
## 5. Evaluation

The dataset was split into 80% training data and 20% testing data. The model was evaluated using Mean Absolute Error (MAE) and R² Score. Most prediction errors occurred on pages with very low impressions because CTR values are more unstable in those cases.

## 6. Interpretation

What the model/clusters actually found. Feature importances or cluster profiles in plain
words. Surprises and negative results — a well-understood "no effect" is a valid result.
## 6. Interpretation

The model found that average position and impressions were the most important features affecting CTR. Pages with better search positions generally received higher CTR. Some pages with high impressions but low CTR suggest that improving titles and meta descriptions may increase performance.

## 7. Recommendation

The ranked actions or decisions your output supports, and how a FlyRank editor would use them
tomorrow. State your confidence and the limits explicitly.
## 7. Recommendation

Focus on improving pages with high impressions but low CTR by optimizing titles and meta descriptions. Maintain good search rankings and monitor CTR regularly. Future work could include adding more features such as page category and keyword intent to improve prediction accuracy.

## 8. Reproducibility

The exact commands to re-run everything from a fresh clone, your random seeds, and your
environment (`pip freeze` highlights or `requirements.txt` deltas).
## 8. Reproducibility

To reproduce this project:

1. Clone the repository.
2. Open the notebook in the `work/notebooks` folder.
3. Install the required Python packages.
4. Run all notebook cells from top to bottom.
5. The trained model will generate CTR predictions and evaluation metrics.

Environment:
- Python 3.x
- pandas
- numpy
- scikit-learn
- matplotlib
- jupyter notebook

Random seed: 42

---

> **Claims checklist before submitting:** observed / measured / directional / decision-support
> **Metrics vs. base rate:** report your task's base rate (majority-class %) next to any
> precision@K or accuracy — a high score can just be a high base rate. AUC / lift over
> baseline are the honest discrimination numbers.
> language everywhere · no causal claims without an experiment or causal design · no
> "predicted Google's algorithm" · no client-identifying details · numbers in this report
> match a fresh re-run.
