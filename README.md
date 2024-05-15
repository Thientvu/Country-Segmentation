# Country Development Categorization Project

## 1. Introduction

### Project Overview
This project aims to categorize countries based on socio-economic and health factors to determine their overall development. Using unsupervised learning techniques, the goal is to identify countries most in need of aid.

### Motivation
HELP International, an NGO focused on fighting poverty and providing basic amenities to underdeveloped countries, has raised $10 million. The CEO needs to allocate this money strategically to the countries most in need. This project helps identify these countries, ensuring the aid is used effectively.

### Objectives
- Source socio-economic and health data of various countries.
- Preprocess and clean the data for analysis.
- Conduct detailed exploratory data analysis using univariate and bivariate techniques, supported by comprehensive visualizations.
- Apply unsupervised learning techniques to categorize countries.
- Provide recommendations on which countries should receive aid.

## 2. Data Collection

### Data Source
The data was sourced from Kaggle and is available in CSV format. [Kaggle Dataset Link](https://www.kaggle.com/datasets/rohan0301/unsupervised-learning-on-country-data/data)

## 3. Data Cleaning and Preprocessing

### Initial Data Exploration
- The dataset contains 167 entries, representing 167 different countries.
- There are 10 columns, 9 of which are numeric, and 1 is categorical.
- No duplicates or missing data were detected.

### Cleaning Steps
- Performed log transformation on the data to handle outliers.

### Final Dataset Description
The cleaned dataset consists of several socio-economic and health indicators for each country. Key features include:
- Child Mortality
- Exports of goods and services per capita
- Spending on Health
- Imports of goods and services per capita
- Income
- Inflation
- Life Expectancy
- Total Fertility
- GDP per capita

## 4. Exploratory Data Analysis (EDA)

### Univariate Analysis
Histograms, box plots, density plots, and choropleth maps were created for the numeric data fields to determine their distribution.

#### Insights
1. **Child Mortality**: Heavily right-skewed distribution.
2. **Exports**: Moderately right-skewed distribution.
3. **Health Spending**: Right-skewed distribution.
4. **Imports**: Similar right-skewed distribution to exports.
5. **Income**: Highly right-skewed distribution.
6. **Inflation**: Right-skewed distribution with low to moderate inflation rates.
7. **Life Expectancy**: Moderately left-skewed distribution.
8. **Fertility Rate**: Right-skewed distribution.
9. **GDP Per Capita**: Highly right-skewed distribution.

### Bivariate Analysis
Pair plots, regression plots, scatter plots, and a correlation matrix were used to identify correlations between variables.

#### Insights
1. **Child Mortality vs. GDP Per Capita**: Strong negative correlation.
2. **Exports vs. GDP Per Capita**: Positive correlation.
3. **Health Spending vs. GDP Per Capita**: Positive correlation.
4. **Imports vs. GDP Per Capita**: Weak positive correlation.
5. **Income vs. GDP Per Capita**: Strong positive correlation.
6. **Inflation vs. GDP Per Capita**: Weak negative correlation.
7. **Life Expectancy vs. GDP Per Capita**: Strong positive correlation.
8. **Fertility Rate vs. GDP Per Capita**: Negative correlation.

## 5. Model Building

### Model Selection
K-Means clustering was selected due to its efficiency and ability to form distinct clusters. It provides easily interpretable results, beneficial for strategic decision-making by the NGO.

### Feature Selection
The country field was excluded for training. All other features were retained as they contribute to determining the overall development of the countries.

### Model Training
The training process involved normalizing the data. The elbow method was used to determine the optimal number of clusters.

### Configurations and Hyperparameters
The number of clusters was set to 3 based on the elbow method. Multiple initializations were performed to avoid local minima.

### Evaluation Metrics
The silhouette score was used to measure the similarity within clusters compared to other clusters.

## 6. Conclusion and Recommendations

### Key Outcomes
The K-Means clustering algorithm categorized the countries into three distinct clusters based on socio-economic and health factors. This allows for targeted recommendations on where the NGO should focus its aid efforts.

### Conclusions
- **Cluster 0: Developed Nations**
    - **Child Mortality**: Low rates.
    - **Exports and Imports**: Moderate to high.
    - **Health Expenditures**: Higher spending on health.
    - **Income**: Generally higher.
    - **Inflation**: Lower.
    - **Life Expectancy**: High.
    - **Fertility Rates**: Lower.
    - **GDP per Capita**: High, with peaks around $40,000.
- **Cluster 1: Underdeveloped Nations**
    - **Child Mortality**: High rates.
    - **Exports and Imports**: Lower.
    - **Health Expenditures**: Lower.
    - **Income**: Predominantly low.
    - **Inflation**: Higher.
    - **Life Expectancy**: Significantly lower.
    - **Fertility Rates**: Higher.
    - **GDP per Capita**: Very low, generally below $2,500.
- **Cluster 2: Developing Nations**
    - **Child Mortality**: Moderate to high.
    - **Exports and Imports**: Varied, but generally lower.
    - **Health Expenditures**: Moderate.
    - **Income**: Ranges from low to moderate.
    - **Inflation**: Varied.
    - **Life Expectancy**: Moderate.
    - **Fertility Rates**: Moderate to high.
    - **GDP per Capita**: Mostly below $10,000.

### Country Recommendations for HELP International Aid Prioritization
Based on the criteria of life expectancy, child mortality, and GDP per capita, the following countries in Cluster 2 have been identified as priorities for receiving aid from HELP International:
- Haiti
- Lesotho
- Central African Republic
- Zambia
- Malawi
- South Africa
- Mozambique
- Sierra Leone
- Guinea-Bissau
- Afghanistan

### Challenges Faced
- Varying scales of the features were a challenge, mitigated by normalizing the data.
- Determining the optimal number of clusters required careful consideration using the elbow method.

### Future Work
Potential improvements include performing a more granular analysis by considering sub-clusters within the main clusters to provide even more targeted recommendations.

## 7. References and Acknowledgments

### References
- Kaggle for the dataset.
- Pandas and NumPy for data manipulation.
- Matplotlib, Seaborn, and Plotly for data visualization.
- Sklearn for machine learning processing.
- TensorFlow for advanced modeling techniques.

### Contact Information
- [LinkedIn](https://www.linkedin.com/in/thientvu/)
- [vuthien12316@gmail.com](mailto:vuthien12316@gmail.com)
