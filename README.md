# AI/ML Capstone Project: Film Success Prediction

### The research question you intend to answer (in one sentence, if possible)

What are the best strategies and characteristics that can contribute to predicting how successful an upcoming film will be in order to generate the most revenue for business stakeholders and positive staying power in the minds of the average moviegoer in the general public?

### Your expected data source(s) (as either a link to existing data or a sentence describing where you will source the data from)

- Data of high grossing films of the past 25 years that were critically reviewed the most positively
- Preferred genres of film
- Language and cultural impact
- Critical success and how it affects revenue
- Survey results of general interest in physically driving to a movie theater and paying money to watch a film
The techniques you expect to use in your analysis

### Visuals: Histograms, Bar, line

### The techniques you expect to use in your analysis

- Time Series Analysis and Forecasting
- Linear regression (and model selection/regularization in genearl)
- Data preprocessing for multiple datasets
- KNN (maybe for genre classification, determining best type of film, etc.)

### The Expected Results
Determine the optimal factors that will generate the most profit for an upcoming film based on a variety of characteristics such as genre of film, critical success, timing of release, runtime, etc.

### Why this question is important

This question is mainly important to optimize risk management for investors and stakeholders. Since the topic is about best strategies for generating revenue, those involved can best determine if they want to move forward and greenlight a project. In modern times, films along with the process of making them and marketing them are becoming exponentially expensive, increasing risk and cognizance or setting realistic marketing and production budgets.

---

## Datasets

1. **IMDb Basic Movie Titles**  
   - Source: `https://datasets.imdbws.com/title.basics.tsv.gz`

2. **IMDb title ratings**  
   - Source: `https://datasets.imdbws.com/title.ratings.tsv.gz`

3. **TMDB 5000 movies (Kaggle)**  
   - Source: Kaggle dataset: `https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata`
  
## 1. Load IMDb datasets
Keep only movies


<img width="301" height="287" alt="image" src="https://github.com/user-attachments/assets/324f71a7-e721-4a50-a399-ef946c4947fd" />
<img width="301" height="192" alt="image" src="https://github.com/user-attachments/assets/48712458-cc45-4e38-b36c-a9a72b722866" />

### Merge IMDb basics + ratings and basic cleaning
Convert types and drop rows with critical NaNs



<img width="317" height="331" alt="image" src="https://github.com/user-attachments/assets/e433ce39-68ea-411c-bc46-35263d990d03" />

## 2. Load TMDB 5000 movies (Kaggle)
<img width="358" height="450" alt="image" src="https://github.com/user-attachments/assets/277c87a3-def3-4cbf-8cf8-1d61bd7c1f92" />

### Select key TMDB columns and clean
We keep core columns for EDA + modeling. Additionally, we replace zeros in budget/revenue with NaN, conver types, parse release_date and extract year, and drop rows with missing basic info.



<img width="403" height="282" alt="image" src="https://github.com/user-attachments/assets/3a17318c-8c47-49be-9501-171846779515" />

## 3. Feature engineering — extract primary genre

<img width="176" height="348" alt="image" src="https://github.com/user-attachments/assets/b089d754-4657-4db2-9261-6b8538420f43" />

## 4. EDA — distributions

<img width="697" height="343" alt="image" src="https://github.com/user-attachments/assets/e6fefd89-03e7-4a83-af25-2c9301bac32e" />

<img width="687" height="346" alt="image" src="https://github.com/user-attachments/assets/8189fcd3-0da2-47d6-b26b-9eb18c61da58" />

<img width="682" height="346" alt="image" src="https://github.com/user-attachments/assets/4c9cb61d-8f62-4e7f-9638-a66609237cdc" />

<img width="522" height="502" alt="image" src="https://github.com/user-attachments/assets/fd04ba92-1a4e-4ca4-8502-85f6eefc8c75" />

### Correlation matrix of numeric features

<img width="538" height="622" alt="image" src="https://github.com/user-attachments/assets/49b4ed9d-f054-46e0-b398-dd998562c593" />

### Primary genre counts

<img width="681" height="747" alt="image" src="https://github.com/user-attachments/assets/df83c3c9-8974-4798-a1af-9e67f2d297ba" />

## 5. Prepare dataset for baseline Linear Regression

<img width="1301" height="220" alt="image" src="https://github.com/user-attachments/assets/48e56649-afaf-444d-9634-a0f3263887aa" />

## 6. Baseline model — Linear Regression

R^2: 0.6739589034059638
MAE: 66033168.00053413

### Plot: predicted vs actual revenue

<img width="517" height="523" alt="image" src="https://github.com/user-attachments/assets/68147987-569c-449d-8f45-e644dcb84080" />













