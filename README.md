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

![Cost Function Evaluation](https://github.com/kushalchaudhari21/LinearRegression/blob/master/output%20screenshots/computing%20cost%20with%20sample%20theta.png)                                                                                                                                      

**3.** Next, a gradient descent algorithm is used to minimise cost function(J) using an update to vector theta on each iteration.
```
error = (X * theta) - y;
theta = theta - ((alpha/m) * (X’)*error)
```
Gradient descent gives the values of theta that minimise the cost function(J) as follows:

![Gradient descent Theta update](https://github.com/kushalchaudhari21/LinearRegression/blob/master/output%20screenshots/minimised%20theta%20using%20gradient%20descent.png) 

Visualising the regression line:

![Regression line](https://github.com/kushalchaudhari21/LinearRegression/blob/master/output%20screenshots/visualising%20final%20regression%20line.png)

**4.** Now we can predict the outputs for given values using the trained model by simply using the basic hypothesis function.
```
predict1 = [1, 3.5] * theta;
predict1 = [1, 7] * theta;
```
![Predict](https://github.com/kushalchaudhari21/LinearRegression/blob/master/output%20screenshots/predicted%20values%20using%20trained%20model.png) 

**5.** Cost function J(θ) can be visualised using every value computed in each iteration of gradient descent.
![Visualising cost function](https://github.com/kushalchaudhari21/LinearRegression/blob/master/output%20screenshots/cost%20function%20representation.png)

Contour plot for the same gives an idea of the local minima as follows:
![Visualising cost function with contours](https://github.com/kushalchaudhari21/LinearRegression/blob/master/output%20screenshots/cost%20function%20representation%20using%20contours.png)

## Important Insights

* Always go for vectorised implementation if possible. 
* To debug vectorised implementation it is insightful to print out sizes of matrices using octave function *whos*.
* Gradient descent as a method to minimize cost function scales better to a larger dataset than normal equations method. Normal equations method becomes computationally expensive for the large dataset(say 10000+ examples).
* Feature scaling(getting all features in similiar ranges to avoid skewed functions) along with mean normalisation should be used for faster gradient descent. 
* Since we add a coulumn of ones to X for vectorised implementation, this coloumn should not be normalised:
```
mu = mean(X)
sigma = std(X)

for i = 1 : size(X,2)
    X_norm(:,i) = (X(:, i) - mu(:, i))/sigma(:, i)
endfor
```
* Check J(θ) vs NumberOfIterations graph to see if gradient descent is working correctly.
* Test different α(step size) in multiples like ...0.001,0.003,0.01,0.03,0.1,0.3,1,...
* Minimising function J(θ) using normal equations is implemented by formula:
```
theta = ((X'*X)^(-1))*X'*y;
```
* pinv function works even if (X'* X) is non invertible. 

