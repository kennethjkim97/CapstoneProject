# Film Success Prediction (ML/AI Capstone Final Project)

## Executive summary

### Project overview and goals
Studios and business stakeholders want to make better decisions *before release* about which films are likely to:
1. **Generate high revenue** (financial success), and
2. **Have staying power** (sustained engagement and positive audience memory).

This project builds machine learning models that use film metadata (budget, genre, runtime, release year, language, popularity/votes) to predict these outcomes and translate results into practical recommendations.

### Key findings
- **Budget is a strong predictor of revenue**, but it is not sufficient: the relationship is noisy and high budgets do not guarantee high revenue.
- **Genre and timing matter**: different genres have different typical budget levels and different return-on-investment patterns (ROI).
- **Audience engagement indicators** (vote counts / popularity) correlate strongly with revenue and staying power, but they can partially reflect post-release effects (marketing + distribution reach). For *pre-release* forecasting, validate carefully.

### What you can do with the results
- Build a **forecast range** (not a single number) for expected revenue based on budget + genre + other metadata.
- Use the **staying power classifier** to identify films likely to become “sticky” with audiences and plan marketing and distribution to amplify those winners.
- Use genre-level ROI summaries to guide portfolio planning (a mix of safer and riskier bets).

---

## Business Understanding

Film projects require large, irreversible investments (production + marketing). Predicting success earlier helps stakeholders:
- manage risk and allocate capital more efficiently,
- plan marketing/distribution strategies,
- optimize portfolios across genres and budget levels, and
- improve the odds that films remain culturally “sticky” (high engagement).

---

## Research questions

1. **Revenue (Regression):**  
   *Is it possible to predict box office revenue using structured pre-release metadata?*

2. **Staying power (Classification):**  
   *Is it possible to classify which films are likely to have strong staying power (high engagement + above-average rating) using metadata?*

---

## Data sources

This project uses:
- **IMDb Non-Commercial Datasets** (title basics + ratings):  
  https://datasets.imdbws.com/title.basics.tsv.gz
  https://datasets.imdbws.com/title.ratings.tsv.gz

- **TMDB 5000 Movies dataset** (budget, revenue, votes, popularity, etc.)
  https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata

---

## Methodology

### Data preparation
- Download datasets (if missing) and load the data.
- Filter to **movies** and clean missing values and numeric types.
- Create helpful features such as:
  - **Primary genre**
  - **Release year**
  - **ROI (revenue / budget)**

### Modeling
Build multiple models and compare them using cross-validation:
- **Regression models (revenue prediction):**
  - Linear Regression
  - Ridge / Lasso
  - Random Forest Regressor
  - Gradient Boosting Regressor  
  **Evaluation metrics:** RMSE and MAE (on log-transformed revenue), plus R².

- **Classification models (staying power):**
  - Logistic Regression
  - Random Forest
  - Gradient Boosting
  - SVC  
  **Evaluation metrics:** ROC-AUC and F1.

### Why cross-validation and grid search?
- Cross-validation provides a more reliable estimate of performance than one random train/test split.
- GridSearchCV finds better hyperparameters for stronger accuracy.

---

## Results and interpretation

### Revenue prediction
- Models generally learn a strong relationship between **budget and revenue**.
- Adding categorical information (genre/language) improves model accuracy.
- Adding vote-based “signal” features often improves performance.

### Staying power
- Staying power is treated as a **binary label** (high engagement + above-average rating).
- Models identify combinations of **visibility** (popularity proxies) and film attributes that are associated with stronger engagement.

---

## Recommendations / Next Steps

1. **Define business-ready thresholds**
Decide what “success” means for your stakeholders down to specifics (revenue targets, ROI targets, or engagement thresholds).

2. **Add true pre-release variables**
Marketing budget, release window (month/holiday), franchise indicators, sequel/remake flags, star power, director track record, production company, etc.

3. **Improve causal validity**
Separate variables that are known pre-release from those that are only known post-release.

4. **Calibrate predictions into ranges**
Provide prediction intervals or scenario-based forecasts (conservative/base/optimistic).

5. **Nice-to-have: Deploy as a decision tool**
A lightweight dashboard that lets stakeholders input proposed film characteristics and get forecasts + “what-if” comparisons.

---

## Repository structure

- `0_capstone_initial_report.ipynb` 
    
    Initial report of the project
- `1_capstone_data_preparation.ipynb` 

    Downloads/loads data and builds 
  `movies_modeling_dataset.csv`

- `2_capstone_EDA_feature_engineering.ipynb`  

    EDA visuals + engineered features saved to `movies_feature_engineered.csv`

- `3_capstone_modeling_revenue_regression.ipynb`  

    Regression modeling + CV + GridSearch + interpretation

- `4_capstone_modeling_staying_power.ipynb`

    Classification modeling + CV + GridSearch + interpretation

---

## How to run

1. Open Jupyter Notebooks in Google Colab in a Python runtime environment.
2. Run notebooks in order:
   1) `1_capstone_data_preparation.ipynb`  
   2) `2_capstone_EDA_feature_engineering.ipynb`  
   3) `3_capstone_modeling_revenue_regression.ipynb`  
   4) `4_capstone_modeling_staying_power.ipynb`

