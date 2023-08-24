# Deep_Learning_TAU course

# HW1: Lenet5 network over the FashionMNIST data set
The primary goal is to evaluate the impact of three specific techniques when applied to Lenet5:

Dropout: This involves adding dropout layers to the hidden layers of the Lenet5 network to reduce overfitting.

Weight Decay (L2 Loss): Weight decay, also known as L2 regularization, is employed to control overfitting by adding a regularization term to the network's loss function.

Batch Normalization: Batch normalization is introduced to normalize the activations within each layer, which can accelerate training and improve the network's generalization.

# HW2: Recurrent NeuralNetwork Regularization
The task involves conducting experiments on the Penn Tree Bank dataset, which is used for predicting the next word in a sequence. Instead of measuring performance with accuracy, the metric used is perplexity, which is similar to cross-entropy loss in classification-based neural networks.

Key points for the task are as follows:

Dataset: The Penn Tree Bank dataset was downloaded from the course Moodle to ensure the correct and updated version.

Architecture: Based on the "small" model described in "Recurrent Neural Network Regularization" by Zaremba et al. This model has 200 hidden units, differing from the "medium" and "large" models which have 650 and 1500 hidden units respectively.

Experiments: We had to Conduct four sets of experiments, each with two variations, and present convergence graphs for both training and test perplexity. Specify the learning rate and dropout keep_prob for each experiment:

a. LSTM-based network without dropout.

b. LSTM-based network with dropout.

c. GRU-based network without dropout.

d. GRU-based network with dropout.

The goal of these experiments is to observe how different configurations of LSTM and GRU-based networks, with or without dropout, affect the perplexity of the Penn Tree Bank dataset.

# HW3 VAE, GAN, WGAN:
The task involves implementing a part of the paper "Semi-supervised Learning with Deep Generative Models" by Kingsma et al. Specifically, we had to implement the M1 scheme described in Algorithm 1 and detailed throughout the paper. This scheme is based on a Variational Autoencoder (VAE) for feature extraction, followed by a transductive Support Vector Machine (SVM) for classification.

Here are the key points for the task:


Implementation: We Implemented the network architecture suggested for MNIST as described in the paper. This architecture should consist of a VAE for feature extraction followed by an SVM for classification.

Dataset: We Applied this implemented model based on the Fashion MNIST dataset.

Experimentation: We  presented the results for different labeled data scenarios: 100, 600, 1000, and 3000 labeled examples. The results were reported in a format similar to Table 1 in the paper.

In summary, the task involves implementing the M1 scheme, adapting it to the Fashion MNIST dataset, and conducting experiments with varying numbers of labeled examples to evaluate its performance.
