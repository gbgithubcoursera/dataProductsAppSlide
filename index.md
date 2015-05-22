---
title       : Linear Prediction Model 
subtitle    : Comparison Between Calculated (Regression Formula)  and predict() R function
author      : Authored by  GB
job         : Potential Data Scientist
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides

---

## Introduction 

In this presentation both the dependent variable (y) and independent variable (y) are simulated. The random uniform distribution funtion runif() is used to simulate the independent variable and the dependent variable is simulated using the independent variable and a random normal distribution with mean equal to mu and standard deviation equal to sd as per the linear equation (See the simulations of variables and the linear equation in the coming slides).

The purpose of this presentation is to show that calculating the predicted values manually by using the regression formula by first calculating the coefficient and formulating the regression/linear equation (best-fitting line) is the same as using the built model and then directly use the predict() function in R on the model to predict values.

--- .class #id 
## Steps
1. Generate independent variable x values
2. Generate dependent variable y values
3. Generate a Linear Regression Model 
4. Formulate the Regression formula and calculate(predict) expected values
5. Run the predict function on the model and generate (predict) expected values
6. Draw a table to compare regressed y values and predict() y values

---
## Simulate the Data

```r
n   = 5; mu  = 0; var = 1
x <- runif(n)
y <- 5 + 2.7 * x + rnorm(n, mean=mu, sd=sqrt(var))
```

## Build the Model

```r
# Build/Fit the model 
regLinMod <- lm(y~x)
# Extract and store the Coefficients
coef <- coef(regLinMod)
# Use the predict() function. "Predict y"
y_predict <- predict(regLinMod)
# Use equation. "Regressed y"
y_regressed <- coef[1] + coef[2] * x
```

---
## Results

```r
# Comparison Table
final <- cbind(x, y, y_regressed, y_predict)
colnames(final) <- c("x", "y","Regressed y","Predict y")
final
```

```
##           x        y Regressed y Predict y
## 1 0.2618353 4.712583    4.922360  4.922360
## 2 0.2727752 5.968698    4.972994  4.972994
## 3 0.8745258 7.177612    7.758153  7.758153
## 4 0.9096031 8.375246    7.920505  7.920505
## 5 0.1857404 3.910033    4.570160  4.570160
```
## Conclusion

Although in this presentation/application data was simulated, this methodology can be applied to any data that has a linear relationship. As shown both the predicted values using the regession equation (best fit) and the predict() function in R are the same.
