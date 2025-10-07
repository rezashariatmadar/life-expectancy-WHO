# WHO Life Expectancy Dataset - Final EDA Report

**Comprehensive Exploratory Data Analysis Report**  
*WHO Global Health Observatory Data Repository*  
*Analysis Period: 2000-2015*

---

## Executive Summary

This report presents a comprehensive exploratory data analysis of the WHO Life Expectancy dataset, encompassing 193 countries over a 16-year period (2000-2015). The analysis reveals significant global health patterns, development disparities, and key predictive factors for life expectancy through advanced statistical analysis and machine learning techniques.

### Key Findings

- **Global Average Life Expectancy**: 69.2 years with substantial variation (36.3-89.0 years)
- **Development Gap**: 12.1-year disparity between developed (79.2 years) and developing countries (67.1 years)
- **Primary Predictors**: Education (Schooling: +0.752 correlation) and healthcare access (Adult Mortality: -0.696 correlation)
- **Positive Trends**: +0.47% annual improvement in global life expectancy from 2000-2015
- **Regional Disparities**: Europe leads (80.6 years) while Africa lags (62.0 years)

---

## 1. Dataset Overview and Quality Assessment

### 1.1 Dataset Characteristics

- **Sample Size**: 2,938 observations across 193 countries
- **Temporal Scope**: 16 years (2000-2015)
- **Feature Count**: 22 variables (20 predictors + country identifier + year)
- **Memory Efficiency**: 0.49 MB total size

### 1.2 Data Quality Analysis

The dataset exhibits varying levels of completeness across features:

**High Missing Data (>15%)**:

- Population: 22.2% missing (652 observations)
- Hepatitis B vaccination: 18.8% missing (553 observations)
- GDP: 15.2% missing (448 observations)

**Moderate Missing Data (5-10%)**:

- Total expenditure: 7.7% missing
- Alcohol consumption: 6.6% missing
- Income composition: 5.7% missing
- Schooling: 5.5% missing

**Low Missing Data (<5%)**:

- Life expectancy (target): 0.34% missing (10 observations)
- Adult mortality: 0.34% missing
- Vaccination coverage (Polio, Diphtheria): <1% missing

### 1.3 Data Quality Implications

The missing data patterns suggest systematic differences in data collection capabilities between developed and developing nations, with developing countries showing higher rates of missing socioeconomic indicators (GDP, population statistics).

---

## 2. Target Variable Analysis: Life Expectancy

### 2.1 Distributional Characteristics

- **Central Tendency**: Mean = 69.2 years, Median = 72.1 years
- **Variability**: Standard deviation = 9.5 years (CV = 13.76%)
- **Range**: 52.7 years (36.3 to 89.0 years)
- **Distribution Shape**: Left-skewed (-0.638) with light tails (-0.236 kurtosis)

### 2.2 Statistical Insights

The left-skewed distribution indicates that while most countries cluster around higher life expectancy values, a significant minority of countries experience substantially lower life expectancy, primarily in developing regions.

**Quartile Analysis**:

- Q1 (25th percentile): 63.1 years
- Q2 (50th percentile): 72.1 years  
- Q3 (75th percentile): 75.7 years

This distribution suggests that 25% of country-year observations fall below 63.1 years, highlighting the substantial global health inequalities.

---

## 3. Feature Analysis and Relationships

### 3.1 Correlation Analysis

**Strongest Positive Predictors**:

1. **Schooling**: +0.752 correlation
2. **Income Composition of Resources**: +0.632 correlation
3. **GDP**: +0.482 correlation

**Strongest Negative Predictors**:

1. **Adult Mortality**: -0.696 correlation
2. **HIV/AIDS**: -0.563 correlation
3. **Thinness (1-19 years)**: -0.458 correlation

### 3.2 Multicollinearity Assessment

**Highly Correlated Feature Pairs (|r| > 0.5)**:

- Infant deaths ↔ Under-five deaths: 0.997 (near-perfect correlation)
- Thinness 1-19 years ↔ Thinness 5-9 years: 0.939
- Percentage expenditure ↔ GDP: 0.899

These correlations indicate potential redundancy and suggest feature selection or dimensionality reduction for regression modeling.

### 3.3 Feature Importance (Random Forest Analysis)

Machine learning-based feature importance ranking:

1. **Schooling**: 0.490 (49% importance)
2. **HIV/AIDS**: 0.240 (24% importance)
3. **Adult Mortality**: 0.225 (22.5% importance)
4. **BMI**: 0.027 (2.7% importance)
5. **GDP**: 0.019 (1.9% importance)

This analysis confirms education as the most powerful predictor of life expectancy, followed by disease burden indicators.

---

## 4. Temporal Analysis (2000-2015)

### 4.1 Global Trends

**Positive Developments**:

- Life expectancy: +0.47% annual increase
- GDP growth: +5.09% annual increase
- Schooling expansion: +1.39% annual increase
- BMI improvement: +1.50% annual increase

**Health Improvements**:

- Adult mortality: -1.00% annual decrease
- Infant deaths: -2.97% annual decrease

### 4.2 Development Status Convergence

The analysis reveals a persistent but slowly narrowing gap between developed and developing countries. While both groups showed improvement, the development gap remains substantial at 12.1 years.

---

## 5. Geographic and Regional Analysis

### 5.1 Regional Performance (2015 Data)

| Region | Mean Life Expectancy | Std Dev | Country Count |
|--------|---------------------|---------|---------------|
| **Europe** | 80.57 years | 3.32 | 31 |
| **Americas** | 75.80 years | 4.06 | 24 |
| **Asia** | 72.32 years | 4.85 | 36 |
| **Other/Oceania** | 69.89 years | 7.53 | 61 |
| **Africa** | 62.02 years | 6.10 | 31 |

### 5.2 Regional Insights

- **Europe** demonstrates the highest and most consistent life expectancy (low std dev)
- **Africa** shows the lowest average with moderate variation
- **Other/Oceania** exhibits the highest variation (7.53 years std dev), suggesting diverse development levels
- **Asia** shows middle-range performance with moderate variation

---

## 6. Development Status Comparative Analysis

### 6.1 Statistical Significance Testing

All major health and socioeconomic indicators show statistically significant differences (p < 0.001) between developed and developing countries.

**Key Disparities**:

- **Life Expectancy Gap**: 12.1 years (79.2 vs 67.1)
- **Economic Gap**: GDP difference of $17,767 per capita
- **Education Gap**: 4.6 years of schooling difference
- **Healthcare Access**: 103.1 point difference in adult mortality rate

### 6.2 Development Status Distribution

- **Cluster 0** (Lower life expectancy): 60 developing countries, avg 63.9 years
- **Cluster 1** (Higher life expectancy): 91 countries (63 developing, 28 developed), avg 77.2 years

This clustering reveals that some developing countries achieve developed-country life expectancy levels, suggesting successful development models.

---

## 7. Advanced Analytics: Clustering Analysis

### 7.1 Optimal Clustering

- **Optimal Clusters**: 2 (Silhouette Score: 0.391)
- **Cluster Validation**: Moderate cohesion suggesting natural groupings

### 7.2 Cluster Characteristics

**Cluster 0 (Lower Performance)**:

- 60 countries, all developing
- Average life expectancy: 63.9 years
- Characterized by higher disease burden, lower education

**Cluster 1 (Higher Performance)**:

- 91 countries (mixed development status)
- Average life expectancy: 77.2 years
- Better healthcare access, higher education levels

---

## 8. Data Quality and Limitations

### 8.1 Missing Data Patterns

Missing data is not random but systematically related to development status, with developing countries showing higher missing data rates for economic indicators.

### 8.2 Analytical Limitations

1. **Temporal Scope**: Analysis limited to 2000-2015; recent trends unknown
2. **Causality**: Correlational analysis cannot establish causal relationships
3. **Data Completeness**: Some countries have incomplete time series
4. **Regional Representation**: Uneven country distribution across regions

---

## 9. Key Insights and Policy Implications

### 9.1 Primary Findings

1. **Education is the Strongest Predictor**: Schooling shows the highest correlation (0.752) and feature importance (49%) for life expectancy
2. **Healthcare Access Matters**: Adult mortality serves as a strong negative predictor (-0.696)
3. **Economic Development Helps**: GDP and income composition show moderate positive correlations
4. **Regional Disparities Persist**: 18.6-year gap between Europe and Africa
5. **Progress is Possible**: Global improvements demonstrate achievable gains

### 9.2 Policy Recommendations

1. **Prioritize Education**: Invest in educational infrastructure and access
2. **Improve Healthcare Systems**: Focus on reducing adult mortality rates
3. **Address Regional Inequalities**: Targeted interventions for African countries
4. **Integrated Approach**: Combine education, healthcare, and economic development
5. **Data Collection**: Improve data collection in developing countries

---

## 10. Implications for Regression Modeling

### 10.1 Feature Selection Strategy

**Primary Predictors** (High importance, low multicollinearity):

- Schooling
- Adult Mortality  
- HIV/AIDS
- Income Composition of Resources

**Secondary Predictors**:

- BMI
- GDP (consider interaction effects)
- Regional indicators

**Features to Consider Removing**:

- Under-five deaths (redundant with infant deaths)
- One of the thinness indicators (highly correlated)

### 10.2 Model Development Recommendations

1. **Handle Missing Data**: Implement sophisticated imputation for Population, Hepatitis B, and GDP
2. **Feature Engineering**: Create composite indicators for healthcare access and economic development
3. **Regional Effects**: Include regional dummy variables or separate regional models
4. **Temporal Validation**: Use time-based cross-validation (train on 2000-2012, validate on 2013-2015)
5. **Non-linear Relationships**: Consider polynomial features for GDP and BMI

### 10.3 Expected Model Performance

Based on the correlation analysis and feature importance rankings, a well-designed regression model should achieve:

- **R²**: 0.75-0.85 (strong correlations observed)
- **Primary Drivers**: Education and healthcare access
- **Regional Variation**: Model performance may vary by region

---

## 11. Conclusions

This comprehensive EDA reveals that life expectancy is primarily driven by educational attainment and healthcare access, with significant but addressable disparities between developed and developing countries. The consistent global improvements from 2000-2015 demonstrate that progress is achievable through targeted interventions.

The analysis provides a robust foundation for developing predictive models and informs evidence-based policy decisions for improving global health outcomes. The identified patterns suggest that investments in education and healthcare infrastructure offer the highest potential returns for improving population health.

**Next Steps**: Proceed with regression model development using the identified key predictors while addressing data quality issues and implementing appropriate validation strategies.

---

*Report prepared based on comprehensive statistical analysis including correlation analysis, temporal trend analysis, clustering, and machine learning-based feature importance assessment.*

**Dataset Source**: World Health Organization (WHO) Global Health Observatory  
**Analysis Period**: 2000-2015  
**Geographic Coverage**: 193 countries  
**Analysis Date**: 2024
