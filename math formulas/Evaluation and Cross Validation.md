# Evaluation

- Training set: 60%
- Cross validation set: 20%
- Test set: 20%



# Bias and Variance

- High bias -> underfitting (训练结果不好)
- High Variance -> overfitting (训练好，测试差)



**High bias (underfitting)**: both $J_{train}(\Theta)$ and $J_{CV}(\Theta)$ will be high. Also, $J_{CV}(\Theta) \approx J_{train}(\Theta)$.

**High variance (overfitting)**: $J_{train}(\Theta)$ will be low and $J_{CV}(\Theta)$ will be much greater than $J_{train}(\Theta)$.

![1](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/I4dRkz_pEeeHpAqQsW8qwg_bed7efdd48c13e8f75624c817fb39684_fixed.png?expiry=1653782400000&hmac=jukwIrvhBFPlDr3--IdIhbpKoSC6f_O5l5sP0I8iFZQ)

p.s. polynome 多项式

![2](https://www.likecs.com/default/index/img?u=aHR0cHM6Ly9waWFuc2hlbi5jb20vaW1hZ2VzLzQyLzU5MmY3N2ExNzI0YzQxZWI5YTU3MjdlZjc3ZWY1YmIyLnBuZw==)



# Learning Curves

Training an algorithm on a very few number of data points (such as 1, 2 or 3) will easily have 0 errors because we can always find a quadratic curve that touches exactly those number of points. Hence:

- As the training set gets larger, the error for a quadratic function increases.
- The error value will plateau out after a certain $m$, or training set size.

## experiencing high bias

![3](https://www.likecs.com/default/index/img?u=aHR0cHM6Ly9waWFuc2hlbi5jb20vaW1hZ2VzLzQ5OC8wMTE4NWNiYzM3MDk5Y2UyNjQ3OTEwYTIxNTczNTIwYS5wbmc=)



## experiencing high variance 

![4](https://www.likecs.com/default/index/img?u=aHR0cHM6Ly9waWFuc2hlbi5jb20vaW1hZ2VzLzE4Ny9hMDc2MDZlZmMzNjE3YTEwNDYyNDlmY2JmNjQ4Mzc3Yi5wbmc=)



# Deciding what to do next

Our decision process can be broken down as follows:

- **Getting more training examples:** Fixes high variance


- **Trying smaller sets of features:** Fixes high variance


- **Adding features:** Fixes high bias


- **Adding polynomial features:** Fixes high bias


- **Decreasing λ:** Fixes high bias


- **Increasing λ:** Fixes high variance.

### **Diagnosing Neural Networks**

- A neural network with fewer parameters is **prone to underfitting**. It is also **computationally cheaper**.
- A large neural network with more parameters is **prone to overfitting**. It is also **computationally expensive**. In this case you can use regularization (increase λ) to address the overfitting.

Using a single hidden layer is a good starting default. You can train your neural network on a number of hidden layers using your cross validation set. You can then select the one that performs best. 

**Model Complexity Effects:**

- Lower-order polynomials (low model complexity) have high bias and low variance. In this case, the model fits poorly consistently.
- Higher-order polynomials (high model complexity) fit the training data extremely well and the test data extremely poorly. These have low bias on the training data, but very high variance.
- In reality, we would want to choose a model somewhere in between, that can generalize well but also fits the data reasonably well.