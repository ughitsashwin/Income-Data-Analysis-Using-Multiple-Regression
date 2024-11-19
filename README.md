# Income-Data-Analysis-Using-Multiple-Regression

## Project Overview

This project focuses on analyzing the factors that influence income using a **Multiple Linear Regression** model. The dataset consists of 4508 observations with 13 variables, including the dependent variable *income* and 12 independent variables. The goal is to build an optimal model to predict income and understand the relationships between income and other factors.

### Key Concepts:
- **Multiple Linear Regression**: A statistical method used to model the relationship between one dependent variable and multiple independent variables.
- **Gauss-Markov Assumptions**: These assumptions ensure the validity of the regression model, including linearity, homoscedasticity, no autocorrelation, and independence between predictors and errors.

## Dataset Description

The dataset contains 13 variables:

| Variable   | Description                          |
|------------|--------------------------------------|
| `age`      | Age in years                         |
| `yrsed`    | Years of education                   |
| `edcat`    | Level of education                   |
| `income`   | Income of individuals (Dependent)    |
| `yrsempl`  | Years with current employer          |
| `creddebt` | Credit card debt in thousands        |
| `othdebt`  | Other debt in thousands              |
| `default`  | Ever defaulted on a bank loan (0/1)  |
| `jobsat`   | Job satisfaction (1-5 scale)         |
| `homeown`  | Home ownership (0/1)                 |
| `address`  | Years at current address             |
| `cars`     | Number of cars owned/leased          |
| `carvalue` | Value of primary vehicle             |

### Descriptive Statistics

- The dataset shows a variety of distributions across variables. For example, variables like *income*, *creddebt*, and *othdebt* are positively skewed, while categorical variables like *default* and *homeown* are binary.
- The dependent variable *income* has a mean of 55.41 with a standard deviation of 56.51.

## Model Building Process

### Step 1: Initial Model
We began by fitting an initial multiple regression model using all independent variables. However, multicollinearity was detected, particularly with the variable *edcat*. This led to the removal of *edcat* from subsequent models.

### Step 2: Refined Model
After removing *edcat*, we re-ran the model and further removed variables like *homeown*, *cars*, and *address* due to collinearity. The remaining variables showed a more linear relationship with income.

### Step 3: Handling Heteroscedasticity
The presence of heteroscedasticity was detected using the **ncvTest**, indicating that errors did not have constant variance. To address this, we transformed some variables (e.g., applying logarithmic transformations to *income* and square root transformations to *creddebt* and *othdebt*).

### Step 4: Final Model
After removing outliers using Cook's Distance and applying transformations, we arrived at a final model that satisfies all Gauss-Markov assumptions:
- Linearity was confirmed using diagnostic plots.
- Homoscedasticity was verified with random bands around horizontal lines in residual plots.
- No autocorrelation was detected (Durbin-Watson statistic close to 2).
- Multicollinearity was reduced (VIF values below 5).

## Final Model Summary

The final model achieved an **Adjusted R-squared** value of **92.66%**, indicating that it explains a significant portion of the variance in income. The p-values for all predictors were statistically significant, confirming their importance in predicting income.

### Key Results:
- **Adjusted R-squared**: 92.66%
- **Durbin-Watson Statistic**: 1.92 (indicating no autocorrelation)
- **Variance Inflation Factor (VIF)**: All values below 5, indicating low multicollinearity.
  
### Final Model Equation:
$$
\log(\text{income}) = \beta_0 + \beta_1 \sqrt{\text{creddebt}} + \beta_2 \sqrt{\text{othdebt}} + \beta_3 \text{default} + \beta_4 \log(\text{carvalue})
$$

## Conclusion

This project successfully built a multiple regression model that predicts income with high accuracy. By addressing issues such as multicollinearity, heteroscedasticity, and outliers, we developed a robust model that meets all necessary statistical assumptions.

Citations:
[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/41251817/316bdd2a-f481-4c47-9b13-a1adf6ee0616/x19151381-Assessment-Report.pdf
