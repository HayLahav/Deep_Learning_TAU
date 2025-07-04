# Abstract
In this project, we address the problem of creating a deep-learning generative diffusion model capable of discerning and generating optimal meta-surface configurations based on observed light-scattering behaviors.
The training of our model relies on a dataset that encompasses meta-surface samples and their corresponding light-scattering behaviors.
Our approach involves using a conditioned diffusion model based on a 2D UNet architecture from Hugging Face, which we adjust according to our data.
In addition, we had to modify and enhance the model architecture to optimize its performance. Using a dataset of 25,000 meta-surface patterns and their corresponding light-scattering data, we trained our model to predict the meta-surface pattern configuration that corresponds to a given matrix of light properties.

![metasurfaces](https://github.com/user-attachments/assets/44bbf242-509f-43eb-86eb-4e367b5f0fe0)


# Introduction
This project addresses the challenge of utilizing diffusion models to navigate the complex landscape of meta-surface design.
Our goal is to fit each light's properties matrix into a suitable meta-surface pattern using a diffusion model. 
In the modern era, metasurfaces enable the precise manipulation of light properties, including phase, amplitude, and wavefront.
Given a dataset comprising meta-surfaces and their interactions with light, our objective is to train a diffusion model capable of identifying the most suitable meta-surface for a given measurement of light.

# Related Work
There are no existing implementations for our exact project, which involves fitting a meta-surface pattern based on its corresponding light-scattering behaviors using diffusion models.
We had to develop a custom solution for this specific classification/fitting problem. Our search of relevant papers revealed that diffusion models are commonly used for segmentation and text-to-image generation tasks, such as the Stable Diffusion model.
However, we did not find any diffusion model papers or projects that use light properties and patterns for image-to-image fitting tasks.

# Data
The data used in this project consists of light scattering from silicon surfaces. The material under study is silicone, and the wavelength used is 1550nm.
The dataset, provided by Prof. Scheuer's nanophotonics lab at Tel Aviv University, contains twenty-five thousand samples.

Each sample includes the following data:

xx_data: The material template is represented as a binary vector with a size of 100, arranged in a 10 x 10 matrix.
h: The height of the template, which varies for each sample.
Rm and Tm: Matrices representing the transmission and reflection of light, with vector lengths of 529, arranged in a 23 x 23 matrix.

The data was initially received in the form of MATLAB files. We loaded this dataset and converted it into a DataFrame, ensuring that each column contained the following information for each sample: xx_data, h, Rm, and Tm. To match the UNet model architecture, we created two 32 x 32 matrices for each sample:

The pattern matrix is a binary matrix with one channel, padded with zeros to achieve a consistent 32 x 32 size.
The light matrix is a matrix with three channels:
Channel 1: Rm Matrix.
Channel 2: Tm matrix.
Channel 3: The height of the pattern was normalized, and we padded the matrices with zeros to achieve a consistent size of 32 x 32.

# Method
Diffusion models are a type of latent variable model, parametrized as p_θ(y₀), defined through the integral of p_θ(y_(0:T)) over y₁, ..., y_T, the latent variables of the same dimensionality as the data y_0~p(y_0).
What sets diffusion models apart from other latent variable models is that the approximate posterior p(y_(1:T)|y_0), known as the 'forward process,' is constrained to a Markov chain that gradually introduces Gaussian noise to the data following a predefined variance schedule β₁, ..., β₋T.
The training process involves optimizing the standard variational bound on the negative log-likelihood. Our method has advantages over generative adversarial networks (GANs), an alternative method. Some of the advantages are better diversity of the outputs, more stable training and less prone to mode collapse.
Since there is no other implementation of our project,s we could not compare our results with other projects' results.

# Experiments
##  Validation of Problem-Solving Approaches
In our experiments, we explored different approaches and inputs to solve the problem of fitting a light matrix to its corresponding meta-surface pattern.
After a thorough evaluation, we selected the best approach based on accuracy and loss. We also conducted experiments with different batch sizes and loss functions to optimize the model's performance.

##  Results Visualization
We employed a diverse range of visual aids, such as graphs, tables, and visualizations, to effectively convey our experimental findings. Our analysis involved a comprehensive examination of the model's performance across various batch sizes, loss functions, and learning rates. 
Notably, we observed that specific configurations consistently outperformed others, and our conclusions have been thoughtfully presented.

##  Addressing Failure Modes in Our Model
Throughout our experiments, we encountered challenges such as overfitting, limited denoising performance under heavy noise, and inadequate data preparation.
We discussed how we addressed these issues and improved the model's performance.

# Conclusions
After extensive experimentation, we identified the optimal model parameters, including a learning rate of 3e^(-04) and a batch size of 20, which, when combined with the Mean Squared Error (MSE) Loss function, yielded predictions of the required meta-surface pattern after approximately 50 training epochs.
The reliability of the generated patterns for a matrix outside the training dataset can be verified solely by examination in the laboratory. 

# Future Extensions
Our project provides a solid foundation for future extensions and new applications:
Hardware Acceleration: Deploy the model on hardware accelerators to ensure fast and efficient predictions.
Interactive User Interface: Develop an interactive user interface, such as a smartphone application, that allows users to input different parameters and visualize predicted meta-surface patterns in real time.
Fine-Tuning: Continue to fine-tune the model parameters to achieve even greater optimization and identify a more efficient optimizer, aiming to accelerate the training process significantly and improve the accuracy of meta-surface pattern prediction.
Multi-Modal Learning: Explore the integration of multiple modalities into the diffusion model. For example, incorporate additional types of data such as thermal or infrared imaging to enhance the model's ability to predict meta-surface patterns under various conditions.


