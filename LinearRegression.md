# LinearRegression

Linear regression strives to show the relationship between two variables by applying a linear equation to observed data. One variable is supposed to be an independent variable,
and the other is to be a dependent variable.

For example: the weight of the person is linearly related to his height. Hence this shows a linear relationship between the height and weight of a person As height increases, the
weight of the person also get increased. 

It is not necessary that here once variable is dependent on others, or one causes the other, but there is some critical relationship between the two variables. In such cases, we
use a scatter plot to imply the strength of the relationship between the variables. If there is no relation or linking between the variables, the scatter plot does not indicate 
any increasing or decreasing pattern. For such cases, the LR is not beneficial to the given data.

<b> Linear Regression Equation </b>

The measure of the extent of the relationship between two variables is shown by the correlation coefficient. The range of this coefficient lies betweene -1 to 1.

A linear equation is written in the form of :

y = a+bx

where, X is the independent variables and plotted along the x-axis
       y is the dependent variables
       The slope of the line is b, and a is the intercept. 
      
or, it can be written as:

y = mx + c 

y = ax + b


## Linear Regression Formula

Linear regression shows the linear relationship between two variables. The eqn of linear relationship is similar to slope formula.
- y = a + bx or,
- y = mx + c,
- y = ax + b

Here, 
     

![how-to-create-a-simple-linear-regression-equation](https://user-images.githubusercontent.com/23405520/113529783-07be6d80-95e2-11eb-99cf-4bb9c89ea7cf.png)



## Simple Linear Regression

They very most straightforward case of a single scalar predictor variable x and a single scalar response variable y is known as simple linear regression. The equation of this regression is represented by:

y = a + bx

The expansion to multiple and vector valued predictor variable is known as multiple linear regression, also known as multivariable linear regression. The eqn of this regression is represented by 

y = a + bx

Almost all real world regression patterns include multiple predictors and basic explanations of linear regression are often explained in terms of the multiple regression form. Note that though, in these cases the dependent variable y in yet a scaler.


## Least Square Regression Line or Linear Regression Line.

The most popular method to fit a regression line in the XY plot is the method of least squares. This process determines the best fitting line for the noted data by reducing the sum of the squares of the vertical deviations from each data point to the line. If a point rests on the fitted data accurately, then its perpendicular deviation is 0. Because the variations are first squared, then added, their positive and negative values will not be cancelled.

Linear regression determines the straight line, called the least squares regression line or LSRL, that best expresses observations in a bivariate analysis of dataset. Suppose Y is a dependent variable, and X is an independent variable, then the population regression line is given by:

![18d7e-1eieyrsqib85cpa32zapqwq](https://user-images.githubusercontent.com/23405520/113530306-4d2f6a80-95e3-11eb-8a3f-abc073a20e25.png)

where, !B is a constant
       B1 is the regression coefficient
       
       
If a random sample of observations is given, then the regression line is expressed by:

![image](https://user-images.githubusercontent.com/23405520/113530531-e494bd80-95e3-11eb-8ff3-4f9527a45cdd.png)


where, !b is constant
       b1 is the regression coefficent.
       X is the independent variable.
       y hat is the predicted value.

### Regression Coefficient

![BIO-311-Eq22](https://user-images.githubusercontent.com/23405520/113530864-c5e2f680-95e4-11eb-8c69-5f2ab98cb5ad.gif)

xi and yi are observed datasets.
x and y are mean.



### R Squared Formula


![Capture](https://user-images.githubusercontent.com/23405520/113534619-d9935a80-95ee-11eb-8e50-ed1c869d8dee.PNG)

