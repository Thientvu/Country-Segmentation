# Country Development Categorization Project

## 1. Introduction

### Project Overview
This project aims to categorize countries based on socio-economic and health factors to determine their overall development. Using unsupervised learning techniques, the goal is to identify countries most in need of aid.

### Motivation
HELP International, an NGO focused on fighting poverty and providing basic amenities to underdeveloped countries, has raised $10 million. The CEO needs to allocate this money strategically to the countries most in need. This project helps identify these countries, ensuring the aid is used effectively.

### Objectives
- Source socio-economic and health datasets of various countries.
- Preprocess and clean the data for analysis.
- Conduct detailed exploratory data analysis using univariate and bivariate techniques, supported by comprehensive visualizations.
- Apply unsupervised learning techniques to categorize countries.
- Provide recommendations on which countries should receive aid.

## 2. Data Collection

### Data Sources
- [Country Data from Kaggle](https://www.kaggle.com/datasets/rohan0301/unsupervised-learning-on-country-data/data)
- [Global Inflation Data from Kaggle](https://www.kaggle.com/datasets/sazidthe1/global-inflation-data)
- [GDP Per Capita Data from data.worldbank.org](https://data.worldbank.org/indicator/NY.GDP.PCAP.CD)
- [Life Expectancy Data from data.worldbank.org](https://data.worldbank.org/indicator/SP.DYN.LE00.IN?locations=CO.)
- [Child Mortality Data from genderdata.worldbank.org](https://genderdata.worldbank.org/en/indicator/sh-dyn-mort)

## 3. Data Cleaning and Preprocessing

### Initial Data Exploration
- The Country Data contains 167 entries, representing 167 different countries.
- There are 10 columns, 9 of which are numeric, and 1 is categorical.
- No duplicates or missing data were detected in the initial dataset.
- Additional datasets were sourced to update inflation, child mortality, GDP per capita, and life expectancy.

### Cleaning Steps
1. **Country Data**: Loaded the initial dataset containing socio-economic and health indicators for 167 countries. Verified dataset integrity, ensuring no duplicates or missing values.
2. **Global Inflation Data**: Imported the dataset and selected inflation values for 2023.
3. **GDP Per Capita**: Imported the dataset and selected data for 2022.
4. **Life Expectancy**: Imported the dataset and selected data for 2021.
5. **Child Mortality**: Imported the dataset and selected data for 2021.

### Data Merging and Updating
- Dropped irrelevant columns and renamed columns for consistency.
- Merged the additional datasets with the main dataset using the country field.
- Updated columns in the main dataset with the most recent data from additional sources where available.

### Handling Outliers
- Performed log transformation on numeric data to handle skewness and outliers.

### Final Dataset Description
The cleaned dataset consists of the following socio-economic and health indicators for each country:
- **child_mort**: Death of children under 5 years of age per 1000 live births.
- **exports**: Exports of goods and services per capita as a percentage of GDP per capita.
- **health**: Total health spending per capita as a percentage of GDP per capita.
- **imports**: Imports of goods and services per capita as a percentage of GDP per capita.
- **inflation**: The annual growth rate of the total GDP.
- **life_expec**: The average number of years a newborn child would live if the current mortality patterns remain the same.
- **total_fer**: The number of children that would be born to each woman if the current age-fertility rates remain the same.
- **gdpp**: GDP per capita, calculated as the total GDP divided by the total population.

## 4. Exploratory Data Analysis (EDA)

### Univariate Analysis
Histograms, box plots, density plots, and choropleth maps were created for the numeric data fields to determine their distribution.

#### Insights
1. **Child Mortality**: Heavily right-skewed distribution.
2. **Exports**: Moderately right-skewed distribution.
3. **Health Spending**: Right-skewed distribution.
4. **Imports**: Similar right-skewed distribution to exports.
5. **Inflation**: Highly right-skewed distribution with low to moderate inflation rates.
6. **Life Expectancy**: Roughly symmetrical with a slight skew to the right.
7. **Fertility Rate**: Right-skewed distribution.
8. **GDP Per Capita**: Highly right-skewed distribution.

### Bivariate Analysis
Pair plots, regression plots, scatter plots, and a correlation matrix were used to identify correlations between variables.

#### Insights
1. **Child Mortality vs. GDP Per Capita**: Strong negative correlation.
2. **Exports vs. GDP Per Capita**: Positive correlation.
3. **Health Spending vs. GDP Per Capita**: Positive correlation.
4. **Imports vs. GDP Per Capita**: Weak positive correlation.
5. **Inflation vs. GDP Per Capita**: Weak negative correlation.
6. **Life Expectancy vs. GDP Per Capita**: Strong positive correlation.
7. **Fertility Rate vs. GDP Per Capita**: Negative correlation.

## 5. Model Building

### K-Means
- **Model Selection**: K-Means clustering was selected due to its efficiency and ability to form distinct clusters.
- **Feature Selection**: The country field was excluded for training. All other features were retained.
- **Model Training**: Normalized the data. Used the elbow method to determine the optimal number of clusters.
- **Configurations and Hyperparameters**: Set the number of clusters to 3. Performed multiple initializations to avoid local minima.
- **Evaluation Metrics**: Used the silhouette score to measure the similarity within clusters compared to other clusters.

### Principal Component Analysis (PCA)
- **Purpose and Implementation**: Used to reduce the dimensionality of the data features to two principal components.
- **Visualization**: Created a scatter plot of the first two principal components, where countries were colored based on their cluster assignments.

### Autoencoders
- **Model Design**: Implemented a deep learning autoencoder to learn a compressed representation of the data.
- **Training and Optimization**: Minimized the reconstruction error. Used early stopping to prevent overfitting.
- **Feature Extraction and Clustering**: Compared inertia scores from clustering on the original data and the autoencoded data.
- **Comparative Analysis**: Assessed which method provided more distinct and coherent clusters.

## 6. Conclusion and Recommendations

### Key Outcomes
The K-Means clustering algorithm categorized the countries into three distinct clusters based on socio-economic and health factors.

### Conclusions
- **Cluster 0: Developed Nations**
  - **Child Mortality**: Low rates.
  - **Exports and Imports**: Moderate to high.
  - **Health Expenditures**: Higher spending.
  - **Inflation**: Lower.
  - **Life Expectancy**: High.
  - **Fertility Rates**: Lower.
  - **GDP per Capita**: High.

- **Cluster 1: Underdeveloped Nations**
  - **Child Mortality**: High rates.
  - **Exports and Imports**: Lower.
  - **Health Expenditures**: Lower.
  - **Inflation**: Higher.
  - **Life Expectancy**: Significantly lower.
  - **Fertility Rates**: Higher.
  - **GDP per Capita**: Very low.

- **Cluster 2: Developing Nations**
  - **Child Mortality**: Moderate to high.
  - **Exports and Imports**: Varied.
  - **Health Expenditures**: Moderate.
  - **Inflation**: Varied.
  - **Life Expectancy**: Moderate.
  - **Fertility Rates**: Moderate to high.
  - **GDP per Capita**: Mostly below $10,000.

### Country Recommendations for HELP International Aid Prioritization
Based on life expectancy, child mortality, and GDP per capita, the following countries in Cluster 1 have been identified as priorities:
- Chad
- Nigeria
- Lesotho
- Central African Republic
- Côte d'Ivoire
- Guinea
- Mali
- Congo, Dem. Rep.
- Namibia
- Burkina Faso

### Challenges Faced
- **Varying Scales of Features**: Normalization was necessary.
- **Updated Data and Multiple Datasets**: Combining data from five sources posed challenges.
- **Inconsistent Data**: Missing or outdated values required careful selection and merging.
- **Determining Optimal Number of Clusters**: Required careful consideration and validation using the elbow method.

### Future Work
Potential improvements include performing a more granular analysis by considering sub-clusters within the main clusters for more targeted recommendations.

## 7. References and Acknowledgments

### References
- Kaggle and data.worldbank.org for the datasets.
- Pandas and NumPy for data manipulation.
- Matplotlib, Seaborn, and Plotly for data visualization.
- Sklearn for machine learning processing.
- TensorFlow for advanced modeling techniques.

### Contact Information
- [LinkedIn](https://www.linkedin.com/in/thientvu/)
- [vuthien12316@gmail.com](mailto:vuthien12316@gmail.com)
