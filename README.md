# Assignment 2: Study of Models  
## California Housing Price Prediction

##  Overview
This project presents a complete **Exploratory Data Analysis (EDA)** and **Multiple Linear Regression** modeling workflow using the **California Housing dataset**.  
The task simulates a real-world **Data Analyst role in a US Real Estate firm**, focusing on data understanding, visualization, dimensionality reduction, and predictive modeling.

The implementation is done using **Python**, **pandas**, **matplotlib**, **seaborn**, and **scikit-learn** in a **Jupyter Notebook**.

---

##  Dataset Description
The dataset contains information about housing blocks in California.

| Feature | Description |
|-------|------------|
| longitude | How far west a house is (higher = farther west) |
| latitude | How far north a house is (higher = farther north) |
| housingMedianAge | Median age of houses in a block |
| totalRooms | Total rooms in a block |
| totalBedrooms | Total bedrooms in a block |
| population | Population in a block |
| households | Number of households in a block |
| medianIncome | Median household income (in tens of thousands USD) |
| medianHouseValue | Median house value (**target variable**) |
| oceanProximity | Proximity of houses to the ocean |

> **Note:** Due to temporary access issues with `sklearn.datasets.fetch_california_housing`, the dataset was downloaded manually and loaded locally.

---

##  Objectives
- Perform **thorough data exploration and understanding**
- Analyze **skewness and outliers**
- Study **feature correlations**
- Apply **Principal Component Analysis (PCA)**
- Build a **Multiple Linear Regression model**
- Evaluate the model using multiple performance metrics
- Interpret model strengths and limitations

---

##  Steps Performed

### Data Loading & Basic Exploration
- Loaded dataset using **pandas**
- Displayed:
  - Dataset shape
  - Column names
  - First 10 rows
- Used `.info()` and `.describe()` to understand structure and statistics
- Identified missing values in `totalBedrooms`
- Computed feature variances to find the **largest variance feature**

---

### Univariate Analysis (Histograms)
- Plotted histograms for all numeric features
- Experimented with **different bin sizes**
- Observed right-skewed distributions in:
  - `medianIncome`
  - `totalRooms`
  - `population`

#### Common Methods to Reduce Skewness
- Log transformation
- Square root transformation
- Box-Cox transformation
- Winsorization / clipping extreme values

(Explained as comments in the notebook)

---

### Outlier Detection (Box Plots)
- Used **box plots** to detect outliers in:
  - `medianIncome`
  - `averageRooms`
  - `population`
- Identified several high-value outliers affecting distributions

---

### Correlation Analysis
- Computed correlation matrix
- Visualized correlations using a **heatmap**
- Used correlation insights for **feature selection**
- Observed weak linear correlation of latitude and longitude with house prices

---

### Geographical Visualization
- Scatter plot:
  - **Longitude vs Latitude**
- Color mapped by **Median House Value**
- Point size scaled by **Population**
- Revealed higher house prices near coastal regions

---

### Principal Component Analysis (PCA)

#### Why Scaling is Required Before PCA
- PCA is variance-based
- Features with larger magnitudes dominate principal components
- Standardization ensures equal contribution from all features

#### PCA Workflow
- Standardized features
- Applied PCA
- Plotted **Explained Variance Ratio (Scree Plot)**
- Selected **top 2 principal components**
- Scatter plot of **PC1 vs PC2**, colored by house value

---

### Multiple Linear Regression Model
- Built a **scikit-learn Pipeline** including:
  - Feature scaling
  - Linear Regression
- **Excluded latitude and longitude** based on correlation analysis
- Extracted:
  - Regression coefficients
  - Intercept

---

### Model Evaluation
Model performance was evaluated using:
- **Mean Squared Error (MSE)**
- **Mean Absolute Error (MAE)**
- **R² Score**

#### Key Insights
- **Is high R2 score always good?** 
- **Low training loss is not always preferred**  

---

###  Diagnostic Plots
- **Predicted vs Actual values**
- **Residuals vs Predicted values**
  - Reveals limitations of linear regression

---


## ▶️ How to Run
```bash
git clone <repository-url>
cd <repository-folder>
jupyter notebook Assigment_2.ipynb
