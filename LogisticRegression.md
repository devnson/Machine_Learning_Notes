# Logistic Regression



## What is wrong with Linear Regression for Classification?

The linear regression model can work well for regression, but fails for classification. Why is that? In case of two classes, you could label one of the classes with 0 and the other with 1 and use linear regression. Technically it works and most linear model programs will spit out weights for you. But there are few problems with this approach:

A linear model does not output probabilities, but it treates the classes as numbers (0 and 1) and fits the best hyperplane (for a single feature, it is a line) that minimizes the distances between the points and the hyperplane. So it simply interpolates between the points, and you cannot interpret it as probabilities. 

A linear model also extrapolates and gives you values below zero and above one. This is a good sign that there might be a smarter approach to classification.

Since the predicted outcome is not a probability, but a linear interpolation between points, there is not meaningful threshold at which you can distinguish one class from the other. 

It is important to clarify the distinction between regression and classification models. Regression models predict a continous variable, such as rainfall amount or sunlight intensity. They can also predict probabilities, such as the probability that an image contains a cat. A probability-predicting regression model can be used as part of classifier by imposing a decision rule - for example, if the probability is 50% or more, decide it's a cat.

Logistic regression predicts probabilities, and is therefore a regression algorithm. However, it is commonly described as a classification method in the machine learning literature, because it can be (and is often) used to make classifiers. There are also "true" classification algorithms, such as SVM, which only predict an outcome and do not provide a probability. We won't discuss this kind of algorithm here.

<b> Linear vs. Logistic Regression on Classification Problems </b>

As Andrew Ng explains it, with linear regression you fit a polynomial through the data - say like on the example below we're fitting a straight line through {tumor size, tumor type} sample set:



Above, malignant tumors get 1 and non-malignant ones get 0, and the green line is our hypothesis h(x). To make predictions we may say that for any give tumor size x, if h(x) gets bigger than 0.5 we predict malignant tumor, otherwise we predict benign.

Looks like this way we could correctly predict every single training set sample, but now let's change the task a bit.

Intuitively it's clear that all tumors larger certain threshold are malignant. So let's add another sample with huge tumor size, and run linear regression again:

https://i.stack.imgur.com/nEC4H.png

Now our h(x) > 0.5 ---> malignant doesn't work anymore. To keep making correct predictions we need to change it to h(x) > 0.2 or something - but that not how the algorithm should work.

We cannot change the hypothesis each time a new sample arrives. Instead, we should learn it off the training set data, and then (using the hypothesis we've learned) make correct predictions for the data we haven't seen before.



# Logistic Regression Maths

Logistic Regression is an omnipresent and extensively used alogrithm for classification. It is a classification model, very easy to use and its performance is superlative in linearly separable class. This is based on the probability for a sample to belong to a class. Here probabilities must be continous and bounded between (0,1). It is dependent on a threshold function to make a decision that is called Sigmoid or Logistic function.
