# NN

## cost function

- $L$ = total number of layers in the network

- $s_l$ = number of units (not counting bias unit) in layer l

- $K$ = number of output units/classes

  ​

$J(\Theta) = - \frac{1}{m} \sum_{i=1}^m \sum_{k=1}^K \left[y^{(i)}_k \log ((h_\Theta (x^{(i)}))_k) + (1 - y^{(i)}_k)\log (1 - (h_\Theta(x^{(i)}))_k)\right] + \frac{\lambda}{2m}\sum_{l=1}^{L-1} \sum_{i=1}^{s_l} \sum_{j=1}^{s_{l+1}} ( \Theta_{j,i}^{(l)})^2$



## BP Algorithm

- Given training set $\lbrace (x^{(1)}, y^{(1)}) \cdots (x^{(m)}, y^{(m)})\rbrace$

- For training example $t =1$ to $m$:

  1. Set $a^{(1)} := x^{(t)}$

  2. Perform forward propagation to compute $a^{(l)}$ for $l=2,3,…,L$

  3. Using $y^{(t)}$, compute $\delta^{(L)} = a^{(L)} - y^{(t)}$

  4. Compute  $δ^{(L−1)},δ^{(L−2)},…,δ^{(2)}$ using $δ^{(l)}=((Θ(l))^Tδ^{(l+1)}) .∗ a^{(l)} .∗ (1−a^{(l)})$

     p.s. $g′(z^{(l)})=a^{(l)} .∗ (1−a^{(l)})$

  5. $\Delta^{(l)}_{i,j} := \Delta^{(l)}_{i,j} + a_j^{(l)}$,  or with vectorization, $Δ^{(l)}:=Δ^{(l)}+δ^{(l+1)}(a^{(l)})^T$

     Hence we update our new $\Delta$ matrix.

     - $D_{i,j}^{(l)}:=\frac{1}{m}(Δ_{i,j}^{(l)}+λ\Theta_{i,j}^{(l)})$, if $j≠0$

     - $D_{i,j}^{(l)}:=\frac{1}{m}Δ_{i,j}^{(l)}$, if $j=0$

     The capital-delta matrix D is used as an "accumulator" to add up our values as we go along and eventually compute our partial derivative. Thus we get $\frac \partial {\partial \Theta_{ij}^{(l)}} J(\Theta)= D_{ij}^{(l)}$

## Gradient Checking

$ \frac \partial {\partial \Theta_j} J(\Theta) ≈ \frac{J(\Theta_1, ... , \Theta_{j+ϵ}, ..., \Theta_n)-J(\Theta_1, ... , \Theta_{j-ϵ}, ..., \Theta_n)}{2ϵ}$

A small value for ${\epsilon}$ (epsilon) such as ${\epsilon = 10^{-4}}$, guarantees that the math works out properly



## Random Initialization

$(-\epsilon,\epsilon)$



## Training a Neural Network

1. Randomly initialize the weights
2. Implement forward propagation to get $h_\Theta(x^{(i)})$ for any $x^{(i)}$
3. Implement the cost function
4. Implement backpropagation to compute partial derivatives
5. Use gradient checking to confirm that your backpropagation works. Then disable gradient checking.
6. Use gradient descent or a built-in optimization function to minimize the cost function with the weights in theta.