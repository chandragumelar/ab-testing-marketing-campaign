# A/B Testing: Effectiveness of Advertisement vs PSA in Driving Conversions

## Overview

An A/B testing analysis using a marketing dataset (~590k users) to answer:
**Is a commercial advertisement ('ad') more effective than a Public Service Announcement ('psa') in driving conversions?**

This project showcases Product Analyst skills: experimental design, statistical testing, visualization, and business recommendations.

**Business Question**  
Does the 'ad' variant provide a significant lift? What is the estimated revenue impact if rolled out?

**Dataset**

- Source: Kaggle - Marketing A/B Testing (test group, converted, total ads, most ads day/hour).
- Link: [kaggle.com/datasets/faviovaz/marketing-ab-testing](https://www.kaggle.com/datasets/faviovaz/marketing-ab-testing)

## Key Findings (Spoiler dari analisis)

- Conversion rate 'ad': ~2.55% vs 'psa': ~1.79% → lift ~42% (statistically significant, p < 0.01 via Chi-Square).
- Effect Size: Small (Cohen’s $h \approx 0.036$), but highly powerful due to the large sample size.
- Peak Timing: Fridays and the 15:00–20:00 window show higher conversion rates.
- Frequency: Conversion increases with exposure up to ~20–30 ads, followed by diminishing returns.

## Tech Stack & Tools

- Python 3.10 (via Conda env `ab_testing`)
- Libraries: pandas, numpy, scipy, statsmodels, matplotlib, seaborn, jupyter
- Statistical tests: Chi-Square (primary), ANOVA + Tukey post-hoc, power analysis
- Visualization: seaborn barplot, heatmap, CI error bars

## Folder Structure

ab_testing/
├── data/
│ ├── raw/ # marketing_AB.csv
│ └── processed/ # (jika ada cleaned data)
├── notebooks/
│ └── ab_testing_analysis.ipynb # notebook utama analisis
├── images/ # exported charts untuk README
├── results/ # (opsional: tabel hasil, CSV export)
├── environment.yml # Conda environment specification
├── .gitignore
└── README.md

## Setup & Reproduce

1. Clone this repo.
2. Install Miniconda/Anaconda.
3. Create environment
4. Activate denvironment
5. Open VSC
6. Open Notebook `notebooks/ab_testing_analysis.ipynb`

7. Run all cells (pastikan dataset ada di `data/raw/marketing_AB.csv`).

## Results Highlights

<image-card alt="Conversion by Group" src="images/conversion_by_group_ci.png" ></image-card>
<image-card alt="By Day" src="images/conversion_by_day.png" ></image-card>
<image-card alt="Heatmap Hour" src="images/heatmap_hour.png" ></image-card>

## Recommendation (Product Perspective)

- **Roll out 'ad' variant** → lift signifikan, meski effect size kecil, volume user besar → impact revenue material.
  -Full Rollout of 'Ad' Variant Conversion lift of ~42% (1.79% PSA vs. 2.55% Ad), $p < 0.01$, with high statistical power.
  -Estimated Impact: Potential monthly revenue increase of ~Rp 760M (based on 1M users/mo at Rp 100k AOV).
  -Optimize Exposure Scheduling Prioritize Fridays and peak hours (15:00–20:00) as identified by heatmap analysis.
  -Prevent Over-Frequency Conversion flattens after 30–40 ads. Set a frequency cap (e.g., max 30 ads/week) to avoid ad fatigue and diminishing returns.
  -Next Steps Test lift across user segments (New vs. Returning) and monitor long-term retention/LTV post-rollout.

## Status Project

- [x] Data loading & cleaning
- [x] EDA & group comparison
- [x] Statistical tests lengkap (chi-square, ANOVA, power)
- [x] Visualisasi
- [x] Business impact estimation
- [x] Final README

Feel free to fork / star! 🚀
