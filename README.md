# Analyzing Information Revelation in Popular Books

This study delves into how the intricacies of information revelation, as quantified by
Kullback-Liebler divergence (KLD), influence the popularity of English-language fiction books
from Project Gutenberg. Initially, the study derived nuanced book-level KLD metrics,
including averages, variances, slopes of linear regressions across narrative segments,
medians, maximum and minimum values, skewness, kurtosis, and other statistical
properties. These metrics were pivotal in understanding how narrative complexity and
structure impact reader engagement and subsequent download metrics.

Regression analyses were pivotal in evaluating the relationship between these
comprehensive KLD metrics and log(downloads), integrating controls like sentiment
analysis, word count, and narrative speed. Notably, genre-specific investigations revealed
distinctive patterns: adventure and fantasy genres showed higher responsiveness to
narrative variance and sentiment factors, while romance and mystery genres exhibited
stronger correlations with specific KLD slopes and median values. The application of LASSO
regression further pinpointed critical variables independently predictive of log(downloads),
underscoring the pivotal role of narrative intricacy and thematic engagement in shaping
digital literary consumption preferences.

## Table of Contents
1. [Introduction](#introduction)
2. [Datasets](#datasets)
3. [Preprocessing](#preprocessing)
4. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
5. [Regression Analysis](#regression-analysis)
6. [Genre-Specific Analysis](#genre-specific-analysis)
7. [Conclusion](#conclusion)
8. [References](#references)

## Introduction
This project aims to build book-level measures of KLD divergence characteristics and relate these measures to book popularity through regression analysis. The analysis investigates heterogeneity across genres and identifies independently predictive variables for log(downloads) using LASSO regression.

## Datasets
The following datasets are used:
- `metadata.csv`: Contains metadata for books including title, author, publication year, language, download counts, and subjects.
- `KLDscores.csv`: Contains KLD divergence scores for books.
- `extra_controls.csv`: Contains additional control variables such as genre classifications, reading speed, sentiment scores, and word count.

## Preprocessing
### Steps:
1. **Loading Data**: The datasets are loaded into Pandas DataFrames.
2. **Merging Data**: The datasets are merged on the common column `id`.
3. **Cleaning Data**: Missing values are handled, and data types are adjusted as necessary.
4. **Feature Engineering**: Log transformation of download counts and extraction of KLD statistics (mean, variance, slope, median, max, min, skew, kurtosis).

## Exploratory Data Analysis (EDA)
### Key Findings:
- Distribution of KLD mean and download counts are visualized using histograms.
- Summary statistics provide an overview of the central tendencies and dispersion of key variables.

## Regression Analysis
### Linear Regression:
- Features: `kld_mean`, `kld_variance`, `kld_slope`, `kld_median`, `kld_max`, `kld_min`, `kld_skew`, `kld_kurtosis`, `wordcount`, `speed`, `sentiment_avg`, `sentiment_vol`.
- Target Variable: `log_downloads`.
- The model is trained and evaluated using Mean Squared Error (MSE), R-squared (R2), and Mean Absolute Error (MAE).

### Results:
- **Coefficients**: Display the impact of each feature on `log_downloads`.
- **Regression Equation**: Formulated based on the intercept and coefficients.
- **Model Evaluation**: Performance metrics (MSE, R2, MAE).

## Genre-Specific Analysis
### Genres Analyzed:
- Adventure
- Romance
- Fantasy
- Mystery

### Key Findings:
- Each genre shows different significant predictors for `log_downloads`.
- The R-squared values indicate the proportion of variance in `log_downloads` explained by the features for each genre.

## Conclusion
The analysis reveals that KLD divergence characteristics and other control variables significantly influence the popularity of books. The heterogeneity across genres suggests that different factors drive popularity for different types of books.

## References
- **Project Gutenberg**: Source of book metadata and KLD scores.
- **[CEUR-WS.org Paper 6166](https://ceur-ws.org/Vol-3558/paper6166.pdf)**: Details on the methodology and results referenced in this analysis.
