# GIKI-Connect (Data Analysis + Modeling Only)

This repository now contains only the data workflow for the Theory of Data Science project:
- Data cleaning and preparation
- Statistical analysis (including chi-square and correlation)
- K-Means training and derived model outputs

## Main files

- `GIKI_Connect_Notebook.ipynb`: full pipeline (cleaning, feature engineering, chi-square, correlation, clustering, and visuals)
- `output/merged_dataset.csv`: cleaned/merged dataset
- `output/combined_with_clusters.csv`: dataset with predicted clusters
- `output/model/cluster_profiles.json`: cluster-wise derived summaries

## Install and run

```bash
pip install -r requirements.txt
jupyter notebook
```

Then run `GIKI_Connect_Notebook.ipynb` from top to bottom.

## Training source of truth

Model training is notebook-first. Run `GIKI_Connect_Notebook.ipynb` top to bottom to regenerate all analysis and model artifacts.

## Presentation-ready project flow

1. Data collection and cleaning
   - Load survey data, standardize columns, handle missing values.
   - Build core social-mixing signal `Silo_Index = (p + f) / 2`, where:
     - `p` = same-province proportion
     - `f` = same-faculty proportion

2. Dataset preparation
   - Merge real and synthetic-compatible records for stable analysis.
   - Save cleaned result to `output/merged_dataset.csv`.

3. Exploratory analysis (EDA)
   - Visualize distribution of siloing, faculty trends, society patterns, and comfort relationships.
   - Create interpretable silo bands/labels for reporting.

4. Statistical testing
   - Chi-square test for association between society membership and high/low silo categories.
   - Pearson correlation between society participation hours and `Silo_Index`.

5. Feature engineering for clustering
   - Convert hobbies to one-hot `h_*` columns.
   - Combine hobby features with `SocHours`, `ComfortScore`, and `Silo_Index`.
   - Standardize features using `StandardScaler`.

6. Choose K and train K-Means
   - Evaluate K via elbow and silhouette curves.
   - Train final K-Means model (project reports K=4 interest tribes).

7. Derived results and model artifacts
   - Assign each student to a cluster.
   - Generate cluster profiles (size, top hobbies, average silo).
   - Save:
     - `output/combined_with_clusters.csv`
     - `output/model/kmeans.pkl`
     - `output/model/scaler.pkl`
     - `output/model/feature_cols.pkl`
     - `output/model/cluster_profiles.json`
