# Customer-Churn-Analysis
**Introduction: What is Logistic Regression?**
Logistic regression is a classification algorithm that predicts the probability of an outcome that can only have two values (i.e. a dichotomy). A logistic regression produces a logistic curve, which is limited to values between 0 and 1. Logistic regression models the probability that each input belongs to a particular category.
Logistic regression is an excellent tool to know for classification problems, which are problems where the output value that we wish to predict only takes on only a small number of discrete values. Here we'll focus on the binary classification problem, where the output can take on only two distinct classes.
In Logistic Regression, the log-odds of a categorical response being "true" (1) is modeled as a linear combination of the features:
log(p1−p)=w0+w1x1,...,wjxj=wTx 
where:
w0  is the intercept term, and  w1  to  wj  represents the parameters for all the other features (a total of j features).
By convention of we can assume that  x0=1 , so that we can re-write the whole thing using the matrix notation  wTx .
This is called the logit function. The equation can be re-arranged into the logistic function:
p=ewTx1+ewTx 
Or in the more commonly seen form:
hw(x)=11+e−wTx
![image](https://github.com/Alisyed098/Customer-Churn-Anallysis/assets/134094832/13727cfc-4ebd-46f0-9b01-1d49942876c5)
The logistic function has some nice properties. The y-value represents the probability and it is always bounded between 0 and 1, which is want we wanted for probabilities. For an x value of 0 you get a 0.5 probability. Also as you get more positive x value you get a higher probability, on the other hand, a more negative x value results in a lower probability.
