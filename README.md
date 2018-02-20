# Regression

1. Regression Analysis is a statistical tool used to determine the relationship between the 2 differnet types of the variables.
2. It hleps us to analysie how the changes made in one variable effects the behaviour of the another variable.
3. Here we will find the dependednt and the independent variables.

- suppose that we observe a quantitative response Y and p different predictors, X1, X2, . . . , Xp. We assume that there is some relationship between Y and X = (X1,X2,...,Xp), which can be written in the very general form
Y =f(X)+ε.
- Here f is some fixed but unknown function of X1, . . . , Xp, and ε is a random error term, which is independent of X and has mean zero. In this formula- tion, f represents the systematic information that X provides about Y .

## Why Estimate f?
-There are two main reasons that we may wish to estimate f: prediction and inference. We discuss each in turn.
### Prediction
-In many situations, a set of inputs X are readily available, but the output Y cannot be easily obtained. In this setting, since the error term averages to zero, we can predict Y using ˆY = ^f(X)
- where fˆ represents our estimate for f , and Yˆ represents the resulting pre- diction for Y . In this setting, **fˆ** is often treated as a black box, in the sense **ˆ** that one is not typically concerned with the exact form of f, provided that
it yields accurate predictions for Y .
## How Do We Estimate f?
we explore many linear and non-linear approaches for estimating f. However, these methods generally share certain charac- teristics.

Our goal is to apply a statistical learning method to the training data training data in order to estimate the unknown function f. In other words, we want to find a function ^f such thatY ≈^f(X)for any observation(X,Y).Broadly speaking, most statistical learning methods for this task can be character- ized as either **parametric** or **non-parametric**. We now briefly discuss these two types of approaches.

## Parametric Methods
- Parametric methods involve a two-step model-based approach.
1. First, we make an assumption about the functional form, or shape, of f. For example, one very simple assumption is that f is linear in X:f(X) = β0 +β1X1 +β2X2 +...+βpXp.

This is a linear model, which will be discussed extensively in Chap- ter 3. Once we have assumed that f is linear, the problem of estimat- ing f is greatly simplified. Instead of having to estimate an entirely arbitrary p-dimensional function f(X), one only needs to estimate the p + 1 coefficients β0,β1,...,βp

2. After a model has been selected, we need a procedure that uses the training data to fit or train the model. In the case of the linear model, we need to estimate the parameters β0,β1,...,βp. That is, we want to find values of these parameters such that Y ≈β0 +β1X1 +β2X2 +...+βpXp.

- The most common approach to fitting the model (2.4) is referred to as (ordinary) least squares, which we discuss in Chapter 3. How- ever, least squares is one of many possible ways way to fit the linear model. In Chapter 6, we discuss other approaches for estimating the parameters in (2.4).

The model-based approach just described is referred to as parametric; it reduces the problem of estimating f down to one of estimating a set of Parameters.

Assuming a parametric form for f simplifies the problem of estimating f because it is generally much easier to estimate a set of pa- rameters, such as β0,β1,...,βp in the linear model (2.4), than it is to fit an entirely arbitrary function f.

![alt text](https://github.com/udayallu/Regression/blob/master/pics/linear%20model%20fit%20with%20lsqure%20m.png)
- **FIGURE 2.4. A linear model fit by least squares to the Income data from Fig- ure 2.3. The observations are shown in red, and the yellow plane indicates the least squares fit to the data.


![alt text](https://github.com/udayallu/Regression/blob/master/pics/smoot%20thin-plate%20spline%20fit.png)
- **Figure 2.4 shows an example of the parametric approach applied to the Income data from Figure 2.3. We have fit a linear model of the form income ≈ β0 + β1 × education + β2 × seniority.

Since we have assumed a linear relationship between the response and the two predictors, the entire fitting problem reduces to estimating β0, β1, and β2, which we do using least squares linear regression. Comparing Figure 2.3 to Figure 2.4, we can see that the linear fit given in Figure 2.4 is not quite right: the true f has some curvature that is not captured in the linear fit. However, the linear fit still appears to do a reasonable job of capturing the positive relationship between years of education and income, as well as the slightly less positive relationship between seniority and income. It may be that with such a small number of observations, this is the best we can do.

## Non-parametric Methods

Non-parametric methods do not make explicit assumptions about the func- tional form of f . Instead they seek an estimate of f that gets as close to the data points as possible without being too rough or wiggly. Such approaches can have a major advantage over parametric approaches: by avoiding the assumption of a particular functional form for f, they have the potential to accurately fit a wider range of possible shapes for f. Any parametric approach brings with it the possibility that the functional form used to estimate f is very different from the true f, in which case the resulting model will not fit the data well. In contrast, non-parametric approaches completely avoid this danger, since essentially no assumption about the form of f is made. But non-parametric approaches do suffer from a major disadvantage: since they do not reduce the problem of estimating f to a small number of parameters, a very large number of observations (far more than is typically needed for a parametric approach) is required in order to obtain an accurate estimate for f.

An example of a non-parametric approach to fitting the Income data is shown in Figure 2.5. A thin-plate spline is used to estimate f. This ap- proach does not impose any pre-specified model on f. It instead attempts to produce an estimate for f that is as close as possible to the observed data, subject to the fit—that is, the yellow surface in Figure 2.5—being smooth.

![alt text](https://github.com/udayallu/Regression/blob/master/pics/rouh%20line%20plate.png)
- **FIGURE 2.6. A rough thin-plate spline fit to the Income data from Figure 2.3. This fit makes zero errors on the training data.


In this case, the non-parametric fit has produced a remarkably ac- curate estimate of the true f shown in Figure 2.3. In order to fit a thin-plate spline, the data analyst must select a level of smoothness. Figure 2.6 shows the same thin-plate spline fit using a lower level of smoothness, allowing for a rougher fit. The resulting estimate fits the observed data perfectly! However, the spline fit shown in Figure 2.6 is far more variable than the true function f, from Figure 2.3. This is an example of overfitting the data, which we discussed previously. It is an undesirable situation because the fit obtained will not yield accurate estimates of the response on new observations that were not part of the original training data set. We dis- cuss methods for choosing the correct amount of smoothness in Chapter 5. Splines are discussed in Chapter 7.



Assuming a parametric form for f simplifies the problem of estimating f because it is generally much easier to estimate a set of pa- rameters, such as β0,β1,...,βp in the linear model (2.4), than it is to fit an entirely arbitrary function f. The potential disadvantage of a paramet- ric approach is that the model we choose will usually not match the true unknown form of f. If the chosen model is too far from the true f, then our estimate will be poor. We can try to address this problem by choos- ing flexible models that can fit many different possible functional forms for f. But in general, fitting a more flexible model requires estimating a greater number of parameters. These more complex models can lead to a phenomenon known as overfitting the data, which essentially means they follow the errors, or noise, too closely. These issues are discussed through- out this book.



### Regression Analysis is classfied into two types 
1. Linear Regression
2. Non Linear regression 

### Linear Regression is classfied in to 2 types
1. Simple linear regression
2. Multiple Linear Regression

## Simple Linear Regression

1. Simple regression enables us to find the relationship between the continus dependednt varaiable Y and a continus independednt varaible X.
2. Mathematically, we can write this linear relationship as **Y ≈ β0 + β1X**.

You might read “≈” as “is approximately modeled as”. We will sometimes
describe (3.1) by saying that we are regressing Y on X (or Y onto X).
For example, X may represent TV advertising and Y may represent sales.
- Then we can regress sales onto TV by fitting the model **sales ≈ β0 + β1 × TV**.
- β0 and β1 are two unknown constants that represent the intercept and slope terms in the linear model. Together, β0 and β1 are intercept slope known as the model coefficients or parameters.

Once we have used our training data to produce estimates ˆ β0 and ˆβ1 for the model coefficients, we can predict future sales on the basis of a particular value of TV advertising by computing **y = ˆ β0 + ˆ β1x**

where **ˆy** indicates a prediction of Y on the basis of X = x. Here we use a hat symbol, **ˆ** , to denote the estimated value for an unknown parameter or coefficient, or to denote the predicted value of the response.

## Estimating the Coefficients
In practice, β0 and β1 are unknown. So before we can use (3.1) to make predictions, we must use data to estimate the coefficients.
-  Let (x1,y1), (x2,y2),..., (xn,yn) represent n observation pairs, each of which consists of a measurement of X and a measurement of Y .

### Example
In contrast, consider the Advertising data illustrated in Figure 2.1. One may be interested in answering questions such as:
– Which media contribute to sales?
– Which media generate the biggest boost in sales? or
– How much increase in sales is associated with a given increase in TV advertising?
This situation falls into the inference paradigm. Another example involves modeling the brand of a product that a customer might purchase based on variables such as price, store location, discount levels, competition price, and so forth. In this situation one might really be most interested in how each of the individual variables affects the probability of purchase. For instance, what effect will changing the price of a product have on sales?
