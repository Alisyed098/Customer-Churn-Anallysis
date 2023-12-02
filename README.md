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

**Defining the cost function for Logistic Regression**

When utilizing logistic regression, we are trying to learn the w values in order to maximize the probability of correctly classifying our glasses. Let's say someone did give us some w values of the logistic regression model, how would we determine if they were good values or not? What we would hope is that for the household of class 1, the probability values are close to 1 and for the household of class 0 the probability is close to 0.
But we don't care about getting the correct probability for just one observation, we want to correctly classify all our observations. If we assume our data are independent and identically distributed (think of it as all of them are treated equally), we can just take the product of all our individually calculated probabilities and that becomes the objective function we want to maximize. So in math:
∏class1hw(x)∏class01−hw(x)

The ∏ symbol means take the product of the hw(x) for the observations that are classified as that class. You will notice that for observations that are labeled as class 0, we are taking 1 minus the logistic function. That is because we are trying to find a value to maximize, and since observations that are labeled as class 0 should have a probability close to zero, 1 minus the probability should be close to 1. This procedure is also known as the maximum likelihood estimation.
Next we will re-write the original cost function as:
ℓ(w)=∑i=1Nyilog(hw(xi))+(1−yi)log(1−hw(xi))
where:
We define yi to be 1 when the ith observation is labeled class 1 and 0 when labeled as class 0, then we only compute hw(xi) for observations that are labeled class 1 and 1−hw(xi) for observations that are labeled class 0, which is still the same idea as the original function.
Next we'll transform the original hw(xi) by taking the log. As we'll later see this logarithm transformation will make our cost function more convenient to work with, and because the logarithm is a monotonically increasing function, the logarithm of a function achieves its maximum value at the same points as the function itself. When we take the log, our product across all data points, it becomes a sum.
The N simply represents the total number of the data.
Often times you'll also see the notation above be simplified in the form of a maximum likelihood estimator:
ℓ(w)=∑i=1Nlog(P(yi∣xi,w))
The equation above simply denotes the idea that , w represents the parameters we would like to estimate the parameters w by maximizing conditional probability of yi given xi.
Now by definition of probability in the logistic regression model:
hw(xi)=11+e−wTxi and 1−hw(xi)=e−wTxi1+e−wTxi.
By substituting these expressions into our ℓ(w) equation and simplifying it further we can obtain a simpler expression.
ℓ(w)=∑i=1Nyilog(hw(xi))+(1−yi)log(1−hw(xi))=∑i=1Nyilog(11+e−wTxi)+(1−yi)log(e−wTxi1+e−wTxi)=∑i=1N−yilog(1+e−wTxi)+(1−yi)(−wTxi−log(1+e−wTxi))=∑i=1N(yi−1)(wTxi)−log(1+e−wTxi)

**What is Churn Prediction?**

Churn prediction is analytical studies on the possibility of a customer abandoning a product or service. The goal is to understand and take steps to change it before the costumer gives up the product or service.

**About Data**

customerID : Customer ID

gender : Whether the customer is a male or a female

SeniorCitizen : Whether the customer is a senior citizen or not (1, 0)

Partner : Whether the customer has a partner or not (Yes, No)

Dependents : Whether the customer has dependents or not (Yes, No)

tenure : Number of months the customer has stayed with the company

PhoneService : Whether the customer has a phone service or not (Yes, No)

MultipleLines : Whether the customer has multiple lines or not (Yes, No, No phone service)


InternetService : Customer’s internet service provider (DSL, Fiber optic, No)

OnlineSecurity : Whether the customer has online security or not (Yes, No, No internet service)

OnlineBackup : Whether the customer has online backup or not (Yes, No, No internet service)

DeviceProtection : Whether the customer has device protection or not (Yes, No, No internet service)

TechSupport : Whether the customer has tech support or not (Yes, No, No internet service)

StreamingTV : Whether the customer has streaming TV or not (Yes, No, No internet service)

StreamingMovies : Whether the customer has streaming movies or not (Yes, No, No internet service)

Contract : The contract term of the customer (Month-to-month, One year, Two year)

PaperlessBilling : Whether the customer has paperless billing or not (Yes, No)

PaymentMethod : The customer’s payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))
MonthlyCharges : The amount charged to the customer monthly
TotalCharges : The total amount charged to the customer
Churn : Whether the customer churned or not (Yes or No)
