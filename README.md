# AI Salary Compass — DACH Statistical Analysis

This project conducts a descriptive statistical analysis of AI salaries across the DACH region (Germany, Austria and Switzerland) using crowdsourced salary data from ai-jobs.net. It examines how compensation varies across experience levels, work modes, job titles and countries through summary statistics, visualisations and hypothesis testing. The dataset is filtered to DACH employers, converted to EUR using live ECB exchange rates and analysed using a reproducible Jupyter notebook workflow.

**Dataset:** AI Salary Data — DACH Region, filtered from ai-jobs.net (873 rows after cleaning)  
**Source:** [ai-jobs.net Salary Dataset](https://raw.githubusercontent.com/foorilla/ai-jobs-net-salaries/main/salaries.csv) - published under CC0 (public domain)

---

## How to Run the Project

**1. Clone the repository**

    git clone https://github.com/n1n4ch/statistical-analysis.git
    cd statistical-analysis

**2. Install dependencies**

    pip install -r requirements.txt

**3. Open and run the notebook**

    jupyter notebook analysis.ipynb

Run all cells in order via **Kernel → Restart & Run All**

> The notebook fetches live EUR exchange rates from the Frankfurter API on execution. An internet connection is required.

---

## Project Structure

| File | Description |
|------|-------------|
| `analysis.ipynb` | Main analysis notebook |
| `salaries_dach.csv` | Filtered DACH salary dataset |
| `requirements.txt` | Python dependencies (generated via `pip freeze`) |
| `Module Summary Statistical Analysis.pdf` | Written report with citations |
| `viz_descriptive_stats.png` | Salary distributions and experience-level boxplot |
| `viz1_avg_salary_by_role.png` | Average salary by top 10 job titles |
| `viz2_salary_by_remote.png` | Salary distribution by work mode |
| `viz3_correlation_heatmap.png` | Correlation heatmap of numeric variables |

---

## Analysis Summary

The notebook covers the following tasks:

- **Descriptive statistics** — summary statistics, categorical value counts and distribution exploration across all key variables
- **Currency conversion** — all salaries normalised to EUR using live ECB exchange rates via the [Frankfurter API](https://www.frankfurter.app/)
- **Outlier handling** — two entries removed: one below €15,000 (likely part-time) and one implausible value of €753,480
- **Visualisations** — five charts covering salary distributions, experience level, job titles, work mode, and variable correlations
- **Hypothesis test** — one-way ANOVA testing whether work mode (on-site / hybrid / remote) has a statistically significant effect on salary (F=4.56, p=0.0107)

---

## Key Findings

- Remote roles in the DACH region pay significantly more on average (€89,685) than on-site roles (€74,994), a difference confirmed by ANOVA (p=0.0107)
- Austrian salaries cluster notably lower than German ones, likely reflecting a smaller and less internationally exposed AI market
- Switzerland shows fewer entries but a wider salary spread, with several roles above €150,000
- The dataset is right-skewed, with the majority of roles falling between €40,000–€100,000 annually

---

## Data Bias and Responsible Use

This dataset is crowdsourced and relies on voluntary, anonymous submissions, meaning it is not a representative sample of the DACH AI labour market. Certain roles, seniority levels, or industries may be systematically over- or under-represented. The unequal group sizes across work modes (on-site n=730, hybrid n=42, remote n=98) limit the reliability of group-level comparisons. Salaries reported in USD by DACH-based employers may reflect internationally benchmarked compensation rather than local market norms and should not be interpreted as typical regional salaries. Results should not be used to draw conclusions about individual employers or to make hiring or salary decisions.

---

## Requirements

Regenerate with:

    pip freeze > requirements.txt
