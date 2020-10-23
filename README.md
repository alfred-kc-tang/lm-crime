# [Linear Regression on Crime Rates](https://alfred-kctang.github.io/lm-crime/)

## Table of Contents

* [Introduction](#introduction)
* [Data Source](#data-source)
* [Assumptions](#assumptions)
* [Conclusion](#conclusion)
* [Keywords](#keywords)
* [Coding Style](#coding-style)
* [License](#license)

## Introduction

Linear Regression is one of the traditional techniques that are still in common use. Its simplicity and understandability display its great elegance. Yet it would tell a fairy tale if we accept its conclusion without its assumptions in mind. If its assumptions turn out to be flawed, we would have false premises to reach the conclusion that appears to be justified by the mathematics behind it. What's worse, we would be unaware of this mistake without checking the assumptions. Instead of solely constructing linear models, the project brings these assumptions of linear regression into sharp focus, in addition to other important topics on variable selection as well as model comparison.

## Data Source

The data set is obtained from the [StatSci.org](http://www.statsci.org/data/general/uscrime.html).

## Assumptions

### 1. Linearity and Homoscedasticity

What linearity means concisely is that the function is *linear in the parameters*, instead of linear in explanatory variables. Explanatory variables are allowed to have non-linear patterns in the models, for linear models can model non-linear patterns in the data by the use of non-linear variables, e.g. using the cubic version of an explanatory variable, or by the log-transformation on the variables, for example. Thus, to put it precisely, *the function is linear in the sense that it is a sum of terms, each of which is of the product form as a parameter multiplied by a function of a given explanatory variable (which can simply be the variable itself without any transformation)*. Therefore, the linearity assumption does NOT mean that the relationship between the response variable and each of the explanatory variables are assumed to be linear, which is a much stronger assumption.

On the other hand, it is the linearity assumption that leads to the assumption of homoscedasticity, which says that different values of the response variable are assumed to have the same variance in their residuals, regardless of the values of the explanatory variables. In fact, professor Nau points out the connection between the two assumptions: "Heteroscedasticity [i.e. violation of the homoscedasticity assumption] can also be a byproduct of a significant violation of the linearity and/or independence assumptions, in which case it may also be fixed as a byproduct of fixing those problem". After all, when heteroscedasticity is discovered, it is a sign of some patterns left unexplained by the linear model, and these patterns are most likely non-linear.

### 2. Additivity and Non-Multicollinearity

If there is an assumption about the explanatory variable themselves in the light of the above form of linear model, it is the additivity assumption that the response variable can be modelled by adding the explanatory variables on top of each other, as Professor Robert Nau at Duke University articulated well on [his website](http://people.duke.edu/~rnau/testing.htm). In his own words, "the effects of different independent variables on the expected value of the dependent variable is additive." Its implication is that *the coefficient of an explanatory variable does not depend on the values of other explanatory variables*. So what this assumption means to users is, concisely speaking, that *the marginal effect of an explanatory variable is independent from any changes in other explanatory variables*. Thus, the assumption of no multicollinearity that there is no correlation between the explanatory variables comes into play, so that the variables are assumed to be independent.

### 3. Independently and Identically Normally Distributed Errors

This assumption is that the error terms are independently and identically normally distributed; to put it simply, the errors are uncorrelated with each other and has a normal distribution shape. As a result, both the mean and the zero are nearly zero. This assumption, especially the independence of errors, is obviously connected to the above assumptions. It should be clearly stated that it is the prediction errors that are required to be normally distributed, while the explanatory and response variables themselves are NOT required to be normally distributed. Therefore, looking at the histograms of all the variables before model building in EDA does NOT ensure that this assumption is held.

Nonetheless, this assumption is loosen as the sample size grows; that is, this assumption is no longer held given a large sample size. If you only aim at estimating the coefficients and predictions in the manner of minimizing mean squared error (MSE) and are confident that the model specification is correct, the assumption is not necessary, technically speaking. That is the reason why some references on regression analysis do not list normally distributed errors among the key assumptions, according to Professor Nau. However, we are generally interested in making inferences about the model and/or estimating the probability that a given prediction error will exceed a given threshold, in which case the distribution assumption is important.

### Further Details

For the rationale behind the assumptions, how to check whether the assumptions are held in the data, and how to deal with violations of the assumptions, please refer to the [Markdown webpage](https://alfred-kctang.github.io/lm-crime/).

## Conclusion

In this project, it is found that only a subset of the explanatory variables are useful, namely M, Ed, Po1, U2, Ineq and Prob. We are able to determine that the selective model using only the above variables is a better alternative to the full model by using adjusted R-squared, which is a better model performance measure than R-squared. It is because the adjusted version takes both the percentage and explained variance and the number of explanatory variables into account. Then, I went on to elaborate on the assumptions of linear regression that are often neglected by users. It is discovered that the best model faces no violations of the first two assumptions: (1) linearity and homoscedasticity as well as (2) additivity and non-multicollinearity. However, there are arguably outliers that lead to the violation of (3) the error distribution assumption in the best model. The model after the removal of the outlier candidates, however, has a lower adjusted R-squared than the model without the removal. Therefore, I would not consider the candidates as outlier, not only because the significance level of the outlier test is still higher than 0.05, but also because it plays a role in improving the model prediction accuracy.

All in all, we should be aware of the assumptions of the linear regression. It is easy to throw the data into the model, but the mathematics and the software do not make the predictions accurate and the explanations convincing if you are not critical of the assumptions. It is this project's hope that the awareness of checking the assumptions when building regression models be fostered.

## Keywords

additivity, adjusted R-squared, assumption diagnostics, backward elimination, heteroscedasticity, homoscedasticity, linearity, linear regression, model comparison, multicollinearity, non-linearity, normality, outliers, regression, R-squared, variable selection

## Coding Style

This projects follows [Google's R Style Guide](https://google.github.io/styleguide/Rguide.html), which is a fork of the [Tidyverse Style Guide](https://style.tidyverse.org/) by Hadley Wickham.

## License

This repository is covered under the [MIT License](https://github.com/alfred-kctang/crime-rates/blob/master/LICENSE).
