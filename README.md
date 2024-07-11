# Exploring the Influence of Key Media Features on Perceived Success: A Study of IMDb Ratings

Overview

This project aims to undertake a comprehensive analysis of a collection of datasets containing detailed information about movies and TV shows available on the Netflix platform. Your primary objective is to meticulously examine the provided data to extract intriguing insights. The outcomes of your analysis will be communicated through both a presentation and a well-structured written managerial report.

This Jupyter Notebook contains code and analysis related to predicting IMDb scores of movies based on various features and conducting exploratory data analysis (EDA). The notebook is organized into several sections:

## Section 1: Text Preprocessing
## Section 2: Exploratory Data Analysis
### 2.1: Boxplot of IMDb Scores
### 2.2 Bar Chart of Media Counts by Genre
## Section 3: Data Imputation (Predicting IMDb Scores from TMDB)
## Section 4: Predicting IMDB Scores from average scores of directors' other movies
### 4.1 Is the success of a director's previous movies useful in predicting the success of their future movies?
### 4.2 Predicting IMDb Scored from runtime and genre

## 1. Text Preprocessing
- In this section, we clean up the dataset by handling missing values, empty lists, NaNs, and Infs. The cleaned data is exported as new files.

### Credits Data Cleaning:
- The 'id' and 'name' columns are renamed to 'media_id' and 'person_name' for consistency.
- Text cleaning functions are applied to 'person_name' and 'role' columns to ensure uniform formatting.
- The 'character' column is processed using a specialized function that separates multiple character roles and removes '(uncredited)' tags.

### Title Data Cleaning:
- Column renaming is performed to ensure consistency: 'id' becomes 'media_id', 'title' becomes 'media_title', 'type' becomes 'media_type', and 'description' becomes 'media_description'.
- Text cleaning functions are applied to 'media_title', 'media_type', 'media_description', and 'age_certification' columns to remove special characters and ensure uniform formatting.
- The 'genres' and 'production_countries' columns are cleaned by removing brackets and spaces and splitting the values into lists.
- Valid country codes are verified for the 'production_countries' column, and invalid entries are removed.
- Age certifications are standardized to 'G', 'PG', 'M', 'MA', or 'R' format.
- The genre column is one-hot encoded to prepare the data for analysis.

___



## 2. Exploratory Data Analysis (EDA)
In this section, we perform exploratory data analysis (EDA) on the IMDb scores of the dataset. The following actions are taken:

### 2.1 Boxplot of IMDb Scores
- A boxplot is created to visualize the distribution of IMDb scores.

### Descriptive Statistics
- Descriptive statistics for IMDb scores are calculated, including:
  - Mean (Average) IMDb Score
  - Median IMDb Score
  - Mode IMDb Score
  - Minimum IMDb Score
  - Maximum IMDb Score
  - Standard Deviation of IMDb Scores

### Outlier Detection
- Outliers in IMDb scores are identified using the Interquartile Range (IQR) method.
- The lower and upper bounds for outliers are calculated. 
    - using (Q1 - 1.5 * IQR) (Q3 + 1.5 * IQR)
- The number of outliers in the IMDb scores is determined.

These EDA steps help us gain insights into the distribution and central tendencies of IMDb scores in our dataset, as well as identify potential outliers.

### 2.2 Bar Chart of Media Counts by Genre
In this section, we continue our exploratory data analysis (EDA) by examining the distribution of media counts across different genres. The following actions are taken:

- A bar chart is created to visualize the distribution of media counts for each genre.
- The chart provides insights into the prevalence of different genres in the dataset.

This analysis helps us understand the distribution of media across various genres, allowing us to identify the most common genres in our dataset.




___



## 3. Data Imputation: Predicting IMDb Scores

In this section, we perform data imputation for IMDb scores using a linear regression model. The following actions are taken:

### Data Preparation
- Data from the cleaned dataset, including 'tmdb_score' and 'imdb_score' columns, are prepared for imputation.

### Model Training and Evaluation
- A linear regression model is trained using 'tmdb_score' as the independent variable and 'imdb_score' as the dependent variable.
- The model's coefficients, intercept, mean squared error, and coefficient of determination (R-squared) are calculated to assess its performance.

### Imputation Function
- An imputation function, `imdb_score_predictor(x, y)`, is defined to predict IMDb scores (`y`) based on TMDb scores (`x`). The function uses the linear regression model for prediction.

### Imputation and Data Update
- IMDb scores with missing values are imputed using the `imdb_score_predictor` function.
- Rows with imputed IMDb scores are added to the dataset.
- Rows with missing IMDb scores are removed from the dataset.

The data imputation process enhances the completeness of IMDb scores in the dataset by predicting missing values based on TMDb scores.



___





## 4. Predicting IMDB Scores from average scores of directors' other movies

### 4.1 Is the success of a director's previous movies useful in predicting the success of their future movies?

In this section, we investigate whether the success of a director's previous movies is useful in predicting the success of their future movies. The following actions are taken:


### Data Preparation
- Data from cleaned datasets, including information about directors and their movies, is prepared for analysis.
- The dataset is split into two subsets: movies released before 2017 and movies released in 2017 and later.

### Feature Engineering
- We calculate the total IMDb score and average IMDb score for each director's previous movies.
- These features are used to assess the director's track record.

### Regression Analysis
- Linear regression is performed to analyze the relationship between the average IMDb score of a director's previous movies and the IMDb score of their future movies.
- Coefficients, intercept, mean squared error, and coefficient of determination (R-squared) are calculated to evaluate the model's performance.

### Cross-Validation
- A 5-fold cross-validation is applied to estimate the average mean squared error and coefficient of determination.
- This helps assess the robustness of the model.

The analysis aims to determine whether a director's past performance, as measured by their previous movie ratings, can be used as a predictor of their future movie ratings. This provides insights into the influence of a director's track record on movie success.




### 4.2 Predicting IMDb Scored from runtime and genre

In this section, we explore the predictive power of movie runtime and genre on IMDb scores. The following actions are taken:

### Data Preparation
- Data from the cleaned dataset, including information about movie genres, IMDb scores, and runtime, is prepared for analysis.
- The genres column is processed to extract individual genre labels.

### Feature Engineering
- The dataset is preprocessed to remove movies with missing genre or runtime information.
- Feature selection is performed using mutual information to identify relevant genres.

### Classification Using k-Nearest Neighbors (KNN)
- KNN classification is applied to predict IMDb score categories (discretized).
- Model accuracy, precision, recall, and F1 score are evaluated.
- A confusion matrix is visualized to assess classification performance.

### Cross-Validation
- A 5-fold cross-validation is applied to estimate the average accuracy, precision, recall, and F1 score.
- This helps assess the model's performance and compare it to a baseline model (Zero-R).

The analysis aims to determine whether movie runtime and genre can be used to predict IMDb score categories. This provides insights into the factors that influence IMDb ratings and the performance of the classification model.

___





