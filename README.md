# Math-Project
This is a document written in the objective of answering certain questions in relation to a linear regression model, a forecasting model, general questions about equation and at last monetary policy of FED. The document is subdivided in four sections. Each section is attempting to elucidate my answers to all the questions, except the third section in which I will only present the solutions to the equations. As to the solution of the equations, they will be presented on a fraction format. This paper has been written in a Markdown format, because I want to use LaTex so the equation can be readable and look attractive to the eyes. It is simply a personal choice. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. 

# Question - Analysis of the Linear Regression Model

In fact before going further, in a general way, one of the purposes of having a model is to predict the outcome of a situation when a independent variable changes. They can allow people to simulate scenarios. 
We will analyze the predictors underscored here  in order to determine if the predictors are significant enough to predict the family income. Income of house can be a function of these independent variables. \(f(income)=({value,education, mortgage, age, gender})\), the best way to outline the function: \(family-income =28.37 + 28*Value + 0.652*Education - 0.050*Age - 0.001*Mortgage + 0.751*Gender)\). The purpose in the homework is not to interpret the model, but I can give some examples to interpret the model. I would simulate the model randomly by attributing the variables. For each additional value of home of \($1000\), the family income will increase by \($28\) on an average. Family income will increase on average by \($.652\) for each additional year getting education. An increase of a year of age after the means of age, \(37\), will decrease the family income on average by \($.050\). On average, the family income will increase \(0.751\)times greater when the head of the household is male than when it is a female. On average, the family income will decrease by \($ 0.001\) when the monthly mortgage payment increases by a one dollar. 

## Effectiveness of the predictors of the model
Given the fact that F-statistic/test shows a P-value less than 0.05, it is conclusive to accept that the overall association of all independent variables in the regression model, otherwise it could have been rejected. The overall significance of the model is based on the F-test. The model is effective in this particular situation. But when we consider the T-test which presents the significance of individual variables, the predictors value of the house, years of education and gender are significant with their respective P-value less than 0.05. It implies that these variables are effective predictors individually, however the regressors age and monthly mortgage payment are not significant to predict the family income. They have a P-value higher than 0.05. Therefore, they are not effective predictors to the model.
It is a good thing that the R-square is 74.8%. It means that 74.8% of the variation of the  family income is related to the variation of the regressors such as value, education, gender, more or less mortgage payment and age.

## Recommendation to improve the predictability of the Model

First of all, for such a regression model, there needs to be a larger sample size than an observation of 25.
The formulation of the model has not shown a priori any sign of multicolinearity, which is the occurrence of high intercorrelation among two or more independent variables (Rhodd, 2020). This assumption has not been proved by a statistical test here since it is not the objective but it is still valid when considering the variables.

I strongly recommend that the variable “income tax declared by the households” be incorporated in the model to predict family income.
Some explicit information has not be given about the regressand “family income”. Is  it the objective of model to determine the family income on a yearly, quarterly, monthly basis? This specificity that is left out makes our interpretation less accurate and precise.

I made the assumption that the bank needs the model for giving loans or financing projects for its customers. In regard to this assumption, the bank fails to conduct the appropriate model for its benefit in terms of a bigger picture. Why would the bank try to determine the income of a family whereas it can ask the households to submit all documents that can weigh in their favor? I would recommend the bank to conduct a logistic regression that can predict loan defaults.Thus, the bank can know in advance the customer who will be likely to default.

Some explicit information has not been given about the depend variable. This lack of information makes difficult to interpret the dependent variable with the precision but not the regression model. the question we ask ourselves, is the income of households that the bank is trying to determine yearly, quartely or monthly?
I would incorporate income tax as a valuable independent variable.  But we have to agree that it would increase the \(r^2\), the r-squared.According to Woolridge (2016), "an important fact about \(r^2\) is that it never decreases. it usually increases when independent variables variable is added to a regression". That is to say, by incorporating the income tax as a regressand, it will increase the r squared. Instead of having R-square of 0.748, the regression statistic will display a higher one. 


# Question 2 - Choice of the Best Forecasting Model

## Growth Rate and Average Growth Rate 

The monthly growth rate will be presented in a table. Since it is an academic homework, I find it appropriate to present the steps even though it doesn't really matter. It is done in case someone would like to know how I come down to the results

```{r pressure, echo=TRUE,comment=TRUE, cache=TRUE, include=TRUE}
##Since it is a homework, I let the codes appear.
library(dplyr)
library(tidyr)
Period=c("Month 1", "Month 2", "Month 3", "Month 4", 
         "Month 5", "Month 6", "Month 7", "Month 8", 
         "Month 9", "Month 10", "Month 11", "Month 12")
Actual_Value = c(10, 12, 16, 13, 17, 19, 15,  20, 22, 19, 21, 19)
data=data.frame(Period,Actual_Value)
growth_data=data%>%
  mutate(Growth_rate=(Actual_Value-lag(Actual_Value))/lag(Actual_Value)*100,
         rounded=round(Growth_rate,2))
average_growth=mean(growth_data$rounded, na.rm = TRUE)
```
The table for the growth rate can be seen in the pdf or rmarkdown format.


``` {r}
growth_data
```
 
 
 **The average month growth rate is \(7.8872\)**.
``` {r echo=FALSE, include=TRUE}
average_growth=mean(growth_data$rounded, na.rm = TRUE)
print(average_growth)
```

## The best fit Model

To decide the Model that is the best fit, we have to look at the Mean Absolute Percent Error (MAPE) and choose the smaller MAPE. In this case, based on the three techniques used, We would choose the **three period moving average** to predict the next period's growth rate because it presents the lowest MAPE or it has the smallest deviation. 


# Question - Understanding some concepts about Federal reserve

This section will attempt to explain the reasons why the Federal Reserve used open market operations,the discount rate, and the reserve requirement to reduce inflation. Afterward, I will present shortly the three policies and in the way mention the reasons among the three why a policy matters most and best than the two others.

## How the FED reduces inflation

Before going straight to the question, it is important that each of the economic goals of the FED is well defined. Once we understand each economic goals of FED, subsequently, we will be able to relate it to how the FED reduces inflation. The goals of monetary policy are to promote maximum employment, stable prices and moderate long-term interest rates.
The **discount rate** is the interest rate Reserve Banks charge commercial banks for short-term loans. Federal Reserve lending at the discount rate complements open market operations in achieving the target federal funds rate and serves as a backup source of liquidity for commercial banks. Lowering the discount rate is expansionary because the discount rate influences other interest rates. Lower rates encourage lending and spending by consumers and businesses. Likewise, raising the discount rate is contractionary because the discount rate influences other interest rates. Higher rates discourage lending and spending by consumers and businesses. 
**Reserve requirements** are the portions of deposits that banks must hold in cash, either in their vaults or on deposit at a Reserve Bank. A decrease in reserve requirements is expansionary because it increases the funds available in the banking system to lend to consumers and businesses. An increase in reserve requirements is contractionary because it reduces the funds available in the banking system to lend to consumers and businesses.
**Open market operations** are when central banks buy or sell securities. These are bought from or sold to the country's private banks. When the central bank buys securities, it adds cash to the banks' reserves. That gives them more money to lend. When the central bank sells the securities, it places them on the banks' balance sheets and reduces its cash holdings.

To get to the bottom of the question, The Federal Reserve works to promote a strong U.S. economy. The FED’s goals of maximum employment, stable prices, and moderate long-term interest rates. When prices are stable, long-term interest rates remain at moderate levels, so the goals of price stability and moderate long-term interest rates go together. As a result, it influences employment and inflation primarily through using its policy tools to influence the availability and cost of credit in the economy.
When interest rates go down, it becomes cheaper to borrow, so households are more willing to buy goods and services, and businesses are in a better position to purchase items to expand their businesses, such as property and equipment. Businesses can also hire more workers, influencing employment. And the stronger demand for goods and services may push wages and other costs higher. Thus it will influence inflation.

**The conclusion that we come to, as interest rates are reduced, more people are able to borrow more money. The result is that consumers have more money to spend. This causes the economy to grow and inflation to increase. By the same token, When the FED wants to reduce the inflation, the FED increases interest rate**.

## The most effective policy of all three policies
From my standpoint and in the light of everything aformentioned, the FED's policy related to interest rate is the most effective one. because it is the primary tool to influence employment and inflation. 

# Bibliography

Federal Reserve.(2020).Federal Reserve Board - Monetary Policy. Retrieved from https://www.federalreserve.gov/monetarypolicy.htm.

Federal Reserve Edication.org. (n.d). Monetary Policy Basics. Retrieved from: https://www.federalreserveeducation.org/about-the-fed/structure-and-functions/monetary-policy.

Rhodd.(2020). Correlation Regression Analysis and Forecasting. Florida Atlantic University.Retrieved from: https://canvas.fau.edu/courses/92000/files/20268406?module_item_id=2296074.
