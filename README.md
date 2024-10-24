# House Pricing Forecast
Kaggle notebook source : https://www.kaggle.com/code/corneliuskarel/forecasting-house-pricing-with-boosting-algorithm

## Description
<p align="justify"> The real estate market is highly dynamic, and accurate price forecasts are essential for buyers, sellers, and investors to optimize decisions. However, traditional methods often fail to capture the complexity of market trends. This project's goal is to predict house prices, offering insights to help stakeholders strategize effectively using machine learning algorithms.
</p>

## Business Problem
<p align="justify"> This project aims to help stakeholders in real estate to make data-driven decisions. By analyzing historical data with relevant features (e.g., location, area, and amenities), This project leverages machine learning algorithms to predict house prices, offering insights to help stakeholders strategize effectively.
</p>

## Exploratory Data Analysis (EDA)
Exploratory Data Analysis to find insights from the dataset, using various visualization techniques and libraries, this component will be divided into 4 parts.

### How Overall Quality Affects Sale Price
![Bar Chart](img/OverallQualVsSP.png)

<p align="justify"> The chart shows a trend in here that higher 'OverallQual' leads to a higher 'SalePrice', it makes senses since quality do affects prices logically in most cases.
</p>

### How YearBuilt affects SalePrice
![Bar Chart](img/YearBuiltVsSP.png)

<p align="justify"> The plot shows that houses built after 1980 tends to have higher sale price. There's also a spike of house prices between 1880-1900, assuming there was an economic event happening in between those years where house prices spiked.
</p>

### How the Size of Garage in Car Capacity affects Sale Price
![Bar Chart](img/GarageCarsVsSP.png)

<p align="justify">The chart shows that, up to 3 GarageCars have a positive correlation with SalePrice, but 4 somehow is worse than 3 GarageCars.
</p>

### Overall Condition and Quality Analysis throughout the years
![Bar Chart](img/OverallCondVsOverallQual.png)

<p align="justify">The assumption here was 'Overall Condition' and 'Overeall Quality' could have some similarity in values, which then we can combine both of these variables, since they have similar values. Turns out 'Overall Condition' and 'Overeall Quality' doesn't represent one another very well, as the lines can be easily distinguished from each other, therefore, we will not be combining both of them.¶
</p>

## Methodologies and Tuning
- **Handle Missing Values**: <p align="justify">Imputation techniques were applied to fill in missing values for target columns based on the data card from the dataset. Some of the columns that have missing values have a meaning, for example in 'Alley' collumn, missing value means 'No Alley Access'. After filling the missing value accordingly to the data card, the rest of the missing value will be imputed using KNN Imputer, since the number of missing value is relatively small, KNN Imputer will not be computationaly expensive, therefore we will be using KNN Imputer.</p>
- **Outlier Analysis and Handling**: <p align="justify">Univariate outlier detection to find insights on how to handle it. The house pricing dataset contains few outliers throughout it's variables, however the algorithm that will be used are tree algorithms. Therefore, there is no need to impute or remove the outliers, in some cases where the algorithm is not robust to outliers and the outliers can't be dropped due to the data size, robust scaler can be used to reduce the outliers noise.</p>
- **Feature Engineering** : <p align="justify">Encoding ordinal variable using ordinal encoder and nominal variable using mean encoder to prevent curse of dimensionality and data overfitting.</p>
- **Feature Selection**: <p align="justify">Filtering highly constant features, since highly constant features hardly provides important information for machine learning algorithms to make forecasts.</p>
- **Cross Validation**: <p align="justify">Use cross validating technique to find the best machine learning model and deciding whether it is better to use scaled or unscaled data, for this project, we will be comparing few algorithms such as extreme gradient boosting(XGB), random forest, catboost, light gradient boosting(LGBM), and support vector regressor(SVR). </p>
- **Hyperparameter Tuning** : Use grid search for hyperparameter tuning and gets an improved Mean Squared Error(MSE) score. 

## Final Result 

### Pre tuned MSE result
![Scores1](img/PreTunedMSE.png)
<p align="justify">This is the Mean Squared Error(MSE) score result for our pre tuned model. The model used is CatBoost Regressor, since it has the best result from cross validation process. However, there's still room for improvement, for example, the model's hyperparameter can be tuned.
</p>

### Pre tuned visualized result
![Scores2](img/PreTunedRes.png)
<p align="justify">The chart shows that our model seems to perform well, regarding that the blue line represents the perfect regression line, although a few number of predictions fall far from the regression line.
</p>

### Post tuned MSE result
![Scores3](img/AfterTunedMSE.png)
<p align="justify">Compared to the previous non-tuned model's performance, there is a slight improvment, showing that tuning the model's hyperparameter do improve the model's performance</p>

### Post tuned visualized result
![Scores4](img/AfterTunedRes.png)
<p align="justify">The chart shows that majority of the prediction remains the same. It is to be expected, since the tuned model shows slight performance compared to the pre-tuned model's performance.
</p>

### Conclusion 
- CatBoost algorithm shows the strongest result, since the MSE score is higher than the rest of the algorithms score. 
- Hyperparameter aspect of the model has been tuned, and showed better result, indicating that the tuning is successful.

### Business Recommendations
- Real estate agents can use this model to guide pricing strategies.
- Buyers can leverage predictions to assess whether a property is fairly priced.
- Companies on real estate industry can use this model as a guide for marketing and pricing strategies.

### Skills utilized in this project
- Data Preprocessing: Imputation, encoding, and scaling.
- Machine Learning: Building and evaluating Classification Models such as extreme gradient boosting(XGB), random forest, catboost, light gradient boosting(LGBM), and support vector regressor(SVR).
- Hyperparameter Tuning: Using Grid Search to search the best hyperparameter and apply it to the classifier and shows a better result.
- Data Analysis: Analize each variables and see how it affects the target varaible and find insights on how each variables correlate to each other.
