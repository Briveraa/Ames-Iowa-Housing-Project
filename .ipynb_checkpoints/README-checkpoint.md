# Ames Iowa, Housing Project 
![](https://ap.rdcpix.com/420048bdcc37471d81e440ed8f86b39bl-m1982390316od-w480_h360.jpg)
---
### Description
The goal of this project is to create and refine a linear regression model, with and without regualarization, for predicting housing projects in Ames, Iowa. To determine which of these models performs the best I will use root mean squared error (RMSE) and r-squared value as evalutators. 

---
### Data 
Here is the [link](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt) to the description of the data contained in the Ames housing csv files. The training set contained 81 columns and 2051 rows while the test test contained 80 columns and 878 rows. There were some outliers in the data that needed to be deleted and missing data that needed to be imputed but luckily no major issues with the data. Below is a data dictionary of the dataframes I made for this project. 

| Name of DataFrame  | Type        | Description                                                              |
|--------------------|-------------|--------------------------------------------------------------------------|
| train_ames         | int and obj | contains all 81 features                                                 |
| test_ames          | int and obj | contains all 80 features                                                 |
| numeric_df         | int         | contains only the numeric data from train set                            |
| final_num_features | int         | contains the numeric features that are highly correlated with sale price |
| categorical_df     | object      | contains only the categorical data                                       |
| complete_train_df  | int and obj | contains int and obj features for modeling                               |
| test_df            | int and obj | contains int and obj features for modeling                               |

---
### Model
I decided to pick features for my model based on the correlation maps; I kept numeric features that had a correlation value of 0.5 or greater. I only included some categorical data that I believed would have an impact on the price of a home. There are several assumptions that I checked for when running my multiple linear regression model to make sure the results valid -- Linearity, Independence, Normality, Homoscedasticity and multicollinearity.

For the most part, the relationships between sale price and the dependent variables were approximately linear. There is independence of observations by assumption and as I go through the different models I tested, I checked for the other assumptions such as normality and equality of residuals.

---
### Evaluation

| Model             | Train R-squared Score: | Test R-Squared Score: | Train RMSE | Test RMSE |
|-------------------|------------------------|-----------------------|------------|-----------|
| Linear Regression | 0.89                   | 0.87                  | 25,769     | 28,446    |
| LR + Ridge        | 0.89                   | 0.86                  | 25,822     | 28,963    |
| LR + LASSO        | 0.89                   | 0.86                  | 25,769     | 28,813    |
| Baseline          |                        |                       | 79,318     | 79,176    |

#### Conclusion
Based on the scores above, the best model turned out to be the linear regression without regularization. This model had the least varience along with lower RMSE scores. Although the R-squared score is not perfect, it can explain up to 87% of the varience in sale prices.On average, the linear regression model without regularization was off by 28,446 dollars. To improve my model I could create interaction terms between highly correlated features, though this could cause my model to become overfit because of the trade-off between bias and varience. 