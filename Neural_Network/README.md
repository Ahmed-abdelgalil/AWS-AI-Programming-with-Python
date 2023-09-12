# Neural Network 

### Gradient Descent

**Gradient descent** is an optimization algorithm commonly used to minimize the cost or loss function associated with a model. 
Its primary purpose is to adjust the parameters (weights and biases) of a model in order to find the optimal set of parameters that minimize the cost function and make the model perform better.

Here's how gradient descent works:

1. **Initialization**: You start with an initial set of parameters for your model. These parameters can be random or based on some prior knowledge.

2. **Compute the Gradient**: You calculate the gradient (a vector of partial derivatives) of the cost function with respect to each parameter. This gradient tells you the direction and magnitude of the steepest increase in the cost function.

3. **Update Parameters**: You adjust the parameters in the opposite direction of the gradient to minimize the cost function. This adjustment is done using a learning rate, which determines the step size for each update. The learning rate is a hyperparameter and controls how quickly or slowly the algorithm converges.

4. **Repeat**: Steps 2 and 3 are repeated iteratively until a stopping criterion is met. Common stopping criteria include a maximum number of iterations or reaching a predefined threshold for the cost function.

The idea behind gradient descent is to find the minimum of the cost function by iteratively moving towards the minimum in small steps. The algorithm relies on the fact that the gradient points in the direction of the steepest increase in the cost function, so by moving in the opposite direction, you gradually descend towards the minimum.

There are different variations of gradient descent, including:

| **Gradient Descent Variant**      | **Description**                                                                                                                                                         |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Batch Gradient Descent           | Computes the gradient using the entire dataset in each iteration. Can be computationally expensive for large datasets but tends to have more stable convergence.   |
| Stochastic Gradient Descent (SGD)| Computes the gradient using a single randomly selected data point in each iteration. Faster but can have more oscillations in the convergence path.             |
| Mini-Batch Gradient Descent      | A compromise between batch and stochastic gradient descent. Uses a small random subset (mini-batch) of the data in each iteration, balancing efficiency and stability. |
| Momentum                         | An enhancement to gradient descent that accelerates convergence by adding a momentum term that accounts for past gradient updates.                                       |
| Adaptive Learning Rate Methods   | Algorithms like Adagrad, RMSprop, and Adam adapt the learning rate for each parameter during training to improve convergence.                                          |

This table summarizes the key characteristics of these gradient descent variants used in optimization algorithms for machine learning and deep learning.
