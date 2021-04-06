# Logistic Regression

Logistic regression is the appropriate regression analysis to conduct when the dependent variabel is dichotomous (binary). Like all regression analysis, the logistic regression is a predictive analysis. Logistic regression is used to describe data and to explain the relationship between one dependent binary variable and one or more nominal, ordianl, interval or ratio-level independent variables.

Here are just a few of the attributes of logistic regression that make it incredibly popular: it's fast, it's highly interpretable, it doesn't require input features to be scaled, it doesn't require any tuning, it's easy to regularize, and it outputs well-calibrated predicted probabilities.

But despite its popularity, it is often misunderstood. Here are a few common questions about logistic regression:

- Why is it called "logistic regression" if it's used for classification?
- Why is it considered a linear model?
- How do you interpret the model coefficients?

![unnamed](https://user-images.githubusercontent.com/23405520/113658206-3eb58180-96bd-11eb-9cf7-8b1fee9faca1.png)



## What is wrong with Linear Regression for Classification?

The linear regression model can work well for regression, but fails for classification. Why is that? In case of two classes, you could label one of the classes with 0 and the other with 1 and use linear regression. Technically it works and most linear model programs will spit out weights for you. But there are few problems with this approach:

A linear model does not output probabilities, but it treates the classes as numbers (0 and 1) and fits the best hyperplane (for a single feature, it is a line) that minimizes the distances between the points and the hyperplane. So it simply interpolates between the points, and you cannot interpret it as probabilities. 

A linear model also extrapolates and gives you values below zero and above one. This is a good sign that there might be a smarter approach to classification.

Since the predicted outcome is not a probability, but a linear interpolation between points, there is not meaningful threshold at which you can distinguish one class from the other. 

It is important to clarify the distinction between regression and classification models. Regression models predict a continous variable, such as rainfall amount or sunlight intensity. They can also predict probabilities, such as the probability that an image contains a cat. A probability-predicting regression model can be used as part of classifier by imposing a decision rule - for example, if the probability is 50% or more, decide it's a cat.

Logistic regression predicts probabilities, and is therefore a regression algorithm. However, it is commonly described as a classification method in the machine learning literature, because it can be (and is often) used to make classifiers. There are also "true" classification algorithms, such as SVM, which only predict an outcome and do not provide a probability. We won't discuss this kind of algorithm here.

<b> Linear vs. Logistic Regression on Classification Problems </b>

As Andrew Ng explains it, with linear regression you fit a polynomial through the data - say like on the example below we're fitting a straight line through {tumor size, tumor type} sample set:

![VVtRW](https://user-images.githubusercontent.com/23405520/113657782-4e809600-96bc-11eb-812f-c4c518a9b419.png)


Above, malignant tumors get 1 and non-malignant ones get 0, and the green line is our hypothesis h(x). To make predictions we may say that for any give tumor size x, if h(x) gets bigger than 0.5 we predict malignant tumor, otherwise we predict benign.

Looks like this way we could correctly predict every single training set sample, but now let's change the task a bit.

Intuitively it's clear that all tumors larger certain threshold are malignant. So let's add another sample with huge tumor size, and run linear regression again:

![nEC4H](https://user-images.githubusercontent.com/23405520/113657808-57716780-96bc-11eb-8533-179be1e53b29.png)


Now our h(x) > 0.5 ---> malignant doesn't work anymore. To keep making correct predictions we need to change it to h(x) > 0.2 or something - but that not how the algorithm should work.

We cannot change the hypothesis each time a new sample arrives. Instead, we should learn it off the training set data, and then (using the hypothesis we've learned) make correct predictions for the data we haven't seen before.



# Logistic Regression Maths

Logistic Regression is an omnipresent and extensively used alogrithm for classification. It is a classification model, very easy to use and its performance is superlative in linearly separable class. This is based on the probability for a sample to belong to a class. Here probabilities must be continous and bounded between (0,1). It is dependent on a threshold function to make a decision that is called Sigmoid or Logistic function.

To understand the concept of Logistic Regression, it is important to understand the concept of <b> Odd Ration (OR) </b>, <b> Logit functions </b>, <b> Sigmoid function </b> , or <b> Logistic function </b> and <b> Cross entropy </b> or <b> Log Loss </b>.

![unnamed](https://user-images.githubusercontent.com/23405520/113658369-8e944880-96bd-11eb-9a3d-04d150c2fda2.png)

- Odd ratio
- Logit function
- Sigmoid function
- Logistic function
- Cross entropy or Log loss

### Odd Ratio (OR)

Odd Ratio (OR) is the odds in favor of a particular event. It is a measure of association between exposure and outcome.

        Odds Ratio =  Odds(success) / Odds(failure)
        

Let's take the probability range between 0 and 1. Let's say:

  - Probability of Success (P) = 0.8
  - Probability of Not Success (!P) or (Q) = 1 - P = 1 - 0.8 = 0.2

Odds are the ratio of the probability of success and the probability of not success.

  Odds(success) = P / Q = 0.8 / 0.2  = 4
  Odds(failure) = !P / Q = 0.2 / 0.8 = 0.25
  
  
<b> Problem Statement </b> : Suppose that 7 out of 10 boys are admitted to Data Science while 3 of 10 girls are admitted. Find the probability of boys getting admitted to Data Science? 

Soln:
 ` 
  Total boys = 10
  Total girls = 10
  
    Probability of boys (Pb) = 7 / 10 = 0.7
    Probability of boys not getting admitted (!Pb) = 1 - P = 1 - 0.7 = 0.3
    &
    Probability of girls (Pg) = 3 / 10 = 0.3
    Probability of girls not getting admitted (!Pg) = 1 - P = 1 - 0.3 = 0.7
    
    Now, 
         Odds of getting admitted in Data Science by boys = Pb/ Qb = 0.7/ 0.3 = 2.33
         
        Odds of girls getting admission in Data Science  = Pg / Qg = 0.3 / 0.7 = 0.42
        
   Hence, 
   
        Odds Ratio = Odds(boys) / Odds (girls) = 2.33 / 0.42 = 5.44
        
`

### Logit Function

Logit function is the algorithm of the odd ratio (log - odds). It takes the input values in the range 0 to 1 and the transforms them to value over the entire real number range. Let's take P as Probability, then <b> P / (1 - P) </b> is the corresponding odds, the logit of the probability is the logarithm of the odd given below:

  `Logit (P) = log ( P / 1- P) = log (odds) `
  
  <b> Example: </b>
          
          If the car sold, then Sold = 1
          If the car did not sell, then sold = 0
          
          price = Sale Price of the car
        So, 
            Pi = B0 + B1 * (Pricei) + E
            
        So, 
            Pi / (1 - Pi) = B0 + B1 * (Pricei) * E
        
        And finally with logit function,
        
          log (Pi / (1 - Pi)) = B0 + B1 * (pricei) + E
          

<b> Problem Statement </b>

Let's thre is a car and its price is $45,000 with an additional feature called a pink slip. Find the probability of sell for this car?


### Logistic function or Sigmoid function

The inverse of the logit function is called the logistic function or Sigmoid function. It is named as Sigmoid function.

  The equation: 
          
![0_WEVwKfBLUPOKBQ7a](https://user-images.githubusercontent.com/23405520/113659801-71ad4480-96c0-11eb-8e90-a5c0cbf49bd7.gif)
           
### Cross entropy or Log loss

Cross entropy loss or log loss, measure the performance of a classification model where output is a probability value between 0 and 1. Cross entropy loss increases as the predicted probability diverges from the actual label. As the predicted probability approaches 1, log loss slowly decreases.

Each predicted class probability is compared to the actual class desired output 0 or 1 and a score / loss is calculated that penalizes the probability based on how far it is from the actual expected value.

` Cost = - ( Yactual ) * log( Y predicted) - ( 1 - Y actual ) * log ( 1 - Ypredicted) `



![1_wilGXrItaMAJmZNl6RJq9Q](https://user-images.githubusercontent.com/23405520/113660058-f1d3aa00-96c0-11eb-897f-dbd5c105913c.png)

# Logistic Regression Steps

- How to calculate the logistic function.
- Learn the coefficients for a Logistic regression model using Stochastic Gradient Descent.
- Make predictions using the Model


![Logistic1](https://user-images.githubusercontent.com/23405520/113660928-bcc85700-96c2-11eb-9ea3-122f4c947c4b.jpg)

![Logistic2](https://user-images.githubusercontent.com/23405520/113660935-c0f47480-96c2-11eb-8935-8090870347f1.jpg)


![Logistic3](https://user-images.githubusercontent.com/23405520/113660946-c782ec00-96c2-11eb-8d58-bf40f619b32f.jpg)

![Logistic4](https://user-images.githubusercontent.com/23405520/113660961-cd78cd00-96c2-11eb-9ee4-256a67eb0ed5.jpg)

