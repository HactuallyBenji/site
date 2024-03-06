Softmax regression (also called multinomial logistic regression) is a generalization of logistic regression that we can use for multi-class classification problems. In problems where you want to classify an instance into one of multiple possible classes, softmax regression is a commonly used method.

Here's a step-by-step explanation:

1. **Linear Function**: This is the first step in softmax regression. For each class, a separate linear function is learned. If you have `n` features and `m` classes, you will learn `m*(n+1)` parameters (weights and biases). The linear function is given by `y = Wx + b`, where `W` is the weight matrix, `x` is the input feature vector, and `b` is the bias vector. Each class has its own `W` and `b`.
    
2. **Softmax Function**: The softmax function is used to convert the output of the linear functions into probabilities. The softmax function's output vector will have the same dimension as the input vector, with each value between 0 and 1, and the total sum of the values will be 1. The softmax function `S` for a vector `Z` is defined as `S(Z)_j = e^(Z_j) / Σ e^(Z_k)` for `j = 1, ..., K` and `k = 1, ..., K`.
    
3. **Probability Distribution**: The output of the softmax function is a probability distribution over `K` different possible outcomes. Each element of the output vector represents the probability that the input vector belongs to a specific class.
    
4. **Prediction**: The prediction is simply the class with the highest estimated probability. This is computed with `argmax(i)`, where `i` ranges over the classes.
    
5. **Cross-Entropy Loss**: The cross-entropy loss function is used to measure the dissimilarity between the predicted and true distributions. It's defined as `L = - Σ y_i * log(y'_i)`, where `y` is the true distribution and `y'` is the predicted distribution. The goal during training is to minimize this loss.
    
6. **Gradient Descent**: Gradient descent is an optimization algorithm used to minimize the loss function. It iteratively adjusts the parameters (weights and biases) in the direction that most decreases the cost function. The parameters are updated using the rule `θ = θ - η * ∇J(θ)`, where `θ` represents the parameters, `η` is the learning rate, and `∇J(θ)` is the gradient of the loss function.
    

By iterating through these steps, softmax regression learns a model that can classify instances into one of multiple possible classes.

In [1]:

import numpy as np

# Define the softmax function
def softmax(x):
    # Subtracting the maximum value for numerical stability
    exps = np.exp(x - np.max(x))
    return exps / np.sum(exps)

# Define the cross-entropy loss function
def cross_entropy_loss(y_pred, y_true):
    # Avoiding numerical instability by adding a small epsilon
    epsilon = 1e-9
    return -np.sum(y_true * np.log(y_pred + epsilon))

# Generate some sample data
num_samples = 100
num_features = 3
num_classes = 2

np.random.seed(0)
X = np.random.randn(num_samples, num_features)
y = np.random.randint(num_classes, size=num_samples)

# Initialize the weights and biases
W = np.random.randn(num_features, num_classes)
b = np.random.randn(num_classes)

# Training loop
learning_rate = 0.1
num_epochs = 100

for epoch in range(num_epochs):
    # Forward pass
    logits = np.dot(X, W) + b
    y_pred = softmax(logits)

    # Compute the loss
    loss = cross_entropy_loss(y_pred, np.eye(num_classes)[y])

    # Backward pass
    grad_logits = y_pred - np.eye(num_classes)[y]
    grad_W = np.dot(X.T, grad_logits)
    grad_b = np.sum(grad_logits, axis=0)

    # Update the weights and biases
    W -= learning_rate * grad_W
    b -= learning_rate * grad_b

    # Print the loss every 10 epochs
    if (epoch + 1) % 10 == 0:
        print(f"Epoch {epoch + 1}: Loss = {loss}")

# Print the final weights and biases
print("Final weights:")
print(W)
print("Final biases:")
print(b)

Epoch 10: Loss = 1962.1213523984934
Epoch 20: Loss = 2048.153984716841
Epoch 30: Loss = 2059.505031700428
Epoch 40: Loss = 2064.957678188899
Epoch 50: Loss = 2068.417087881193
Epoch 60: Loss = 2071.390218063033
Epoch 70: Loss = 2072.2785484566075
Epoch 80: Loss = 2072.3250234233046
Epoch 90: Loss = 2072.3265341456513
Epoch 100: Loss = 2072.3265821222817
Final weights:
[[  24.9121626    54.46180505]
 [  51.00844995   37.73787157]
 [  -2.332342   -113.93102528]]
Final biases:
[499.52812614 489.75059573]

In [2]:

def predict_sample(sample):
    logits = np.dot(sample, W) + b
    probabilities = softmax(logits)
    predicted_class = np.argmax(probabilities)
    return predicted_class

In [3]:

# Define a new sample
new_sample = np.array([1.2, 0.5, -0.8])

# Use the predict_sample method with the new sample
predicted_class = predict_sample(new_sample)

# Print the predicted class
print("Predicted class:", predicted_class)

Predicted class: 1