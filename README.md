# Horizon Financial Group — Credit Risk & Loan Default Analysis

## Project Overview

A Python-based credit risk analytics project examining loan
defaults across borrower characteristics, affordability metrics,
employment history, and loan purposes.

**Business goal:** Investigate default drivers and identify
opportunities to improve underwriting and portfolio monitoring.

**Dataset period:** 2024–2025.

## Executive Summary

| KPI | Result |
|---|---:|
| Loans analyzed | 601 |
| Unique borrowers | 500 |
| Defaulted loans | 146 |
| Observed default rate | 24.29% |
| Management target | 12.00% |
| Gap above target | 12.29 percentage points |

The portfolio's observed default rate exceeds management's target.
Credit score and debt-to-income ratio (DTI) show meaningful
associations with default risk.

## Data Sources

- `borrower_profiles.csv`: 500 borrower profiles, including
  income, employment, credit scores, and existing debt.
- `loan_applications.csv`: 601 loans, including loan amounts,
  purposes, terms, DTI, and repayment outcomes.

The datasets are joined on `borrower_id` using a many-to-one merge.

## Key Findings

### Credit Score

| Score range | Loans | Default rate |
|---|---:|---:|
| 520-599 | 116 | 49.14% |
| 600-649 | 93 | 29.03% |
| 650-699 | 75 | 28.00% |
| 700-749 | 86 | 16.28% |
| 750+ | 231 | 11.69% |

### Debt-to-Income Ratio

| DTI range | Loans | Default rate |
|---|---:|---:|
| Below 20% | 48 | 16.67% |
| 20-29.9% | 78 | 12.82% |
| 30-39.9% | 107 | 11.21% |
| 40-49.9% | 97 | 23.71% |
| 50-59.9% | 99 | 31.31% |
| 60%+ | 172 | 36.05% |

### Other Findings

- The highest observed loan-purpose default rate was
  Wedding loans at 32.14%.
- Borrowers with less than two years of employment had
  a 34.52% observed default rate, versus 22.63% for
  those with at least two years.
- Defaulted and non-defaulted loans had mean loan amounts
  of $22,570.55 and $22,012.75, respectively.
- Credit score had the strongest absolute measured numeric
  correlation with default (-0.286).
- There were 22 loans with reported DTI greater than 100%;
  these values warrant verification, not automatic deletion.

## Visualizations

The notebook contains:

1. Default rate by credit-score range.
2. DTI versus default status, with outcome jitter.
3. Default rate by loan purpose.

## Business Recommendations

The notebook includes a detailed
**Business Recommendations & Underwriting Improvements**
section with seven recommendations.

Primary priorities:

1. Strengthen credit-risk segmentation and reviews.
2. Improve DTI calculation verification and affordability checks.
3. Test combined credit-score and DTI review criteria.
4. Investigate employment-tenure and loan-purpose patterns.
5. Improve loan-book monitoring and data quality.
6. Validate proposed policies before implementation.

Candidate score and DTI thresholds are exploratory
review triggers, **not automatic rejection rules**.

## Technology

- Python
- pandas
- NumPy
- Matplotlib
- Google Colab / Jupyter Notebook

## Repository Structure

```text
Horizon-Financial-Credit-Risk/
├── Horizon_Credit_Risk_Analysis.ipynb
├── borrower_profiles.csv
├── loan_applications.csv
├── README.md
├── requirements.txt
└── .gitignore
```

## How to Run

1. Download or clone the repository.
2. Install dependencies:

```bash
python -m pip install -r requirements.txt
```

3. Open `Horizon_Credit_Risk_Analysis.ipynb` in Google Colab.
4. Upload both CSV files to the Colab Files panel.
5. Run the notebook cells from top to bottom.

The notebook's discovery cell uses `/content`, the normal
Colab upload directory. When running in local Jupyter,
change this path to the folder containing the CSV files.

**Colab note:** Files uploaded to session storage are temporary.
Re-upload the CSVs when the Colab runtime resets.

## Methodology & Limitations

- Results describe the supplied historical loan portfolio.
- Multiple loans can belong to the same borrower.
- Default rates may depend on loan age and observation period.
- Correlations do not prove that variables cause defaults.
- Interest rates can reflect existing lender risk assessments.
- A historical underwriting screen cannot predict the outcome
  of loans the company never approved.
- Threshold scenarios were not independently validated.
- No formal statistical significance test has been conducted
  on differences between subgroups.
- Applicant-level decisions require further model validation,
  compliance review, and applicable fair-lending safeguards.
- Repayment outcomes such as `loan_status` and
  `days_delinquent` should not be used as application-time
  predictors.

## Project Outcome

This project demonstrates data joining, segmentation,
correlation analysis, visualization, scenario testing,
data validation, and evidence-based business recommendations.

The findings are educational and exploratory, not a
production-ready credit-scoring policy.
