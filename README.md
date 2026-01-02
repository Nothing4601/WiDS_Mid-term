Assignment 2: Study of Models – California Housing Price Prediction
Overview

This repository contains a complete exploratory data analysis (EDA) and Multiple Linear Regression modeling workflow for predicting housing prices using the California Housing dataset. The work simulates a real-world Data Analyst role in a US Real Estate firm, focusing on data understanding, visualization, dimensionality reduction, and model evaluation.

The solution is implemented in a Jupyter Notebook using Python, pandas, matplotlib, seaborn, and scikit-learn.

Dataset Description

The dataset is based on the California Housing data with the following features:

Feature	Description
longitude	How far west a house is (higher = farther west)
latitude	How far north a house is (higher = farther north)
housingMedianAge	Median age of houses in a block
totalRooms	Total rooms in a block
totalBedrooms	Total bedrooms in a block
population	Population in a block
households	Number of households in a block
medianIncome	Median household income (in tens of thousands USD)
medianHouseValue	Median house value (target variable)
oceanProximity	Proximity of houses to the ocean

Note: Due to a temporary network issue with sklearn.datasets.fetch_california_housing, the dataset was downloaded manually and loaded locally.

Objectives

Perform thorough data understanding and EDA

Detect skewness and outliers

Analyze feature relationships using correlation

Apply PCA (Principal Component Analysis)

Build a Multiple Linear Regression model using a scikit-learn Pipeline

Evaluate model performance using multiple metrics

Interpret model results and limitations

Steps Performed
1. Data Loading & Basic Exploration

Loaded dataset using pandas

Displayed:

Dataset shape

Column names

First 10 rows

Used .info() and .describe() for structural and statistical insights

Identified missing values (totalBedrooms column)

Computed variance of numeric features to identify the feature with largest variance

2. Univariate Analysis (Histograms)

Plotted histograms for all numeric features

Experimented with different bin sizes to visualize distributions clearly

Observed right-skewness in features such as:

medianIncome

totalRooms

population

Skewness Reduction Techniques (Explained in Notebook Comments)

Commonly used methods include:

Log transformation

Square root transformation

Box-Cox transformation

Winsorization / clipping extreme values

3. Outlier Detection (Box Plots)

Used box plots to detect outliers in:

medianIncome

averageRooms

population

Identified several high-value outliers, especially in population-related features

4. Correlation Analysis

Computed correlation matrix

Visualized correlations using a heatmap

Used correlation insights to justify feature selection

Observed weak direct correlation of latitude and longitude with house prices for linear modeling

5. Geographical Visualization

Created a scatter plot of:

Longitude vs Latitude

Colored points by Median House Value

Scaled point size based on Population

This visualization clearly shows high-value clusters near coastal regions

6. PCA (Principal Component Analysis)
Why Scaling is Required Before PCA

PCA is variance-based

Features with larger scales dominate principal components

Standardization ensures equal contribution from all features

PCA Steps

Standardized numeric features

Applied PCA

Plotted Explained Variance Ratio (Scree Plot)

Selected top 2 principal components

Visualized PC1 vs PC2, colored by median house value

7. Multiple Linear Regression Model

Built a scikit-learn Pipeline including:

Scaling

Linear Regression

Excluded latitude and longitude from final model based on correlation analysis

Extracted and displayed:

Regression coefficients

Intercept

8. Model Evaluation

The model was evaluated using:

Mean Squared Error (MSE)

Mean Absolute Error (MAE)

R² Score

Adjusted R² Score

Conceptual Discussion

High R² is not always good:

Adding irrelevant features can inflate R²

Adjusted R² accounts for feature count

Low training loss is not always preferred:

May indicate overfitting

Generalization on unseen data is more important

9. Diagnostic Plots

Predicted vs Actual values

Used to assess overall prediction quality

Residuals vs Predicted values

Checked homoscedasticity

Identified patterns indicating model limitations

Technologies Used

Python

pandas, numpy

matplotlib, seaborn

scikit-learn

Jupyter Notebook

Conclusion

This project demonstrates a complete end-to-end data analytics workflow, including data understanding, visualization, dimensionality reduction, and predictive modeling. While Multiple Linear Regression provides a reasonable baseline, residual patterns and skewed distributions indicate that more advanced models (e.g., Random Forest, Gradient Boosting) could further improve performance
