## Description

This is an octave prototype to train a linear regression model for given dataset.

The prototype implements linear regression with one variable. It also gives insights into its supplementary algorithms like gradient descent which minimises the cost function and the algorithm to calculate value of cost function using theta matrix.

This prototype also includes some files whose names end with *…multi.m* that perform linear regression with multiple variables(multiple features). The complete details for the implementation and procedure can be found in [ex1](https://github.com/kushalchaudhari21/LinearRegression/blob/master/ex1.pdf).

## Sample Invocation

After running Octave cli, in the project directory input the following to execute the algorithm
```
ex1
```

## General Procedure

**1.**  It is better to visualise the data first before execution so a plotting function is used. 
![Visualising data](https://github.com/kushalchaudhari21/LinearRegression/blob/master/output%20screenshots/visualising%20the%20data.png)                                                                                                                                
**2.** Formulation for computing cost(J) is as follows:
```
h = X * theta                           
MeanSquaredError = sum((h - y).^2)
J = MeanSquaredError/(2 * m)
```
Cost function computed using vector theta = [0 ; 0] is:
![Cost Function Evaluation](https://github.com/kushalchaudhari21/LinearRegression/blob/master/output%20screenshots/computing%20cost%20with%20sample%20theta.png)                                                                                                                                      **3.** Next, a gradient descent algorithm is used to minimise cost function(J) using an update to vector theta on each iteration.
```
error = (X * theta) - y;
theta = theta - ((alpha/m) * (X’)*error)
```
Gradient descent gives the values of theta that minimise the cost function(J) as follows:
![Gradient descent Theta update](https://github.com/kushalchaudhari21/LinearRegression/blob/master/output%20screenshots/minimised%20theta%20using%20gradient%20descent.png) 
Visualising the regression line:
![Regression line](https://github.com/kushalchaudhari21/LinearRegression/blob/master/output%20screenshots/visualising%20final%20regression%20line.png)




## Important Insights



