# A/B Testing: Effectiveness of Advertisement vs PSA in Driving Conversions

## Overview

Project analisis A/B testing menggunakan dataset marketing campaign (~590k users) untuk menjawab pertanyaan:  
**Apakah menampilkan iklan sebenarnya ('ad') lebih efektif daripada Public Service Announcement ('psa') dalam meningkatkan conversion rate (pembelian produk)?**

Ini adalah showcase skill Product Analyst: dari experiment design, statistical testing, visualisasi, sampai business recommendation.

**Business Question**  
Apakah variasi 'ad' memberikan lift signifikan di conversion rate? Berapa estimasi impact revenue jika di-rollout?

**Dataset**

- Sumber: Kaggle - Marketing A/B Testing
- Kolom utama: test group ('ad' vs 'psa'), converted (0/1), total ads, most ads day, most ads hour
- Link: [kaggle.com/datasets/faviovaz/marketing-ab-testing](https://www.kaggle.com/datasets/faviovaz/marketing-ab-testing)

## Key Findings (Spoiler dari analisis)

- Conversion rate 'ad': ~2.55% vs 'psa': ~1.79% → lift ~42% (statistically significant, p < 0.01 via Chi-Square).
- Effect size kecil (Cohen's h ~0.036), tapi karena sample besar → powerful.
- Hari dengan most ads: Friday cenderung conversion lebih tinggi.
- Jam peak: sekitar 15-20 punya conversion lebih baik.
- Semakin banyak ads dilihat (sampai ~20-30), conversion naik (diminishing returns setelahnya).

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
- Optimize scheduling: prioritaskan hari Jumat & jam 15-20.
- Monitor long-term: potential fatigue kalau total ads terlalu tinggi (>30).
- Next step: segmentasi user (new vs returning), A/B test lanjutan dengan variasi creative.

## Status Project

- [x] Data loading & cleaning
- [x] EDA & group comparison
- [ ] Statistical tests lengkap (chi-square, ANOVA, power)
- [ ] Visualisasi pro
- [ ] Business impact estimation
- [ ] Final README polish

Feel free to fork / star kalau berguna! 🚀
