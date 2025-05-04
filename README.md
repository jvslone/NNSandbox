# **If you use this code as the basis for any of the assignment questions, you must both cite it and include a text paragraph describing how it works (i.e. breakdown the process of training a neural network, be somewhat detailed). This only applies if you directly copy the code as a base, not if you just look at it to get an idea of what to do.**

The Code for the models can be found in the 'Models' folder. For a bit of a view of the datasets, look in the 'DataExploration' folder.

The exact structure of the network (i.e. the number of layers and the number of neurons in each layer, etc...) is purposely made to be suboptimal as these are for you to determine. A list of things to tune can be found below: 

* Learning Rate
* What Scheduler to use/ if you use one
* Minimum Learning Rate
* Number of Epochs
* Weight Decay strength, whether to use it
* Validation Set Percentage of Train Set
* What Optimizer to use
* What Activation Functions (both hidden and output) to use
* Number of Layers
* Number of Nodes in each layer
* Any Regularization
* Batch Size (mostly unimportant)
* What loss function to use
* etc...

Here are some useful links:

- [PyTorch Activation Functions](https://pytorch.org/docs/stable/nn.html#non-linear-activations-weighted-sum-nonlinearity)
- [PyTorch Loss Functions](https://pytorch.org/docs/stable/nn.html#loss-functions)
- [PyTorch Optimizers](https://pytorch.org/docs/stable/optim.html#algorithms)
- [PyTorch Schedulers](https://pytorch.org/docs/stable/optim.html#how-to-adjust-learning-rate)

Some things to watch for:

- Underfitting (not enough non-linearity, learnable parameters, epochs, or high enough learning rate)
- Overfitting (too many learnable parameters, epochs, or not enough regularization/weight punishment)
- Improper Loss (Loss reads low, but performance is not great, need a different loss function)
- Model Not Learning (If your loss stays high, compare it to the loss attained by random guessing; setting lr arbitrarily low is a way to accomplish this)

# **Guide For Model Optimization**

**For Underfitting, you should consider:**

- Number Of Epochs
- Learning Rate
- Model Shape/Size (i.e. how many layers and neurons per layer)
- Amount of Non-Linearity in the network (typically regarding activation functions)
  - On that note, hidden-layer activation functions can be roughly divided into two categories
  - The first is good at injecting high amounts of non-linearity at the start of a network. Example: SELU
  - The second is good for predictive power in the latter parts of the network. Example: PReLU

**For Overfitting, a lot of the same parameters are at play, albeit with some new options**

- Number Of Epochs
- Learning Rate
- Model Shape/Size
- If a Scheduler is Present
  - What Scheduler
  - What Minimum LR
- Regularization (L1, L2, or Elastic Net)
- Weight Decay (Think of it as a kind of dropout)
- Actual Dropout (Mostly used for CNNs)
- If Classification, is there a class imbalance? Has that been addressed by either
  - Shifting the balance of the data with sampling, or
  - Weighting the loss function based on the imbalance

**For an Improper Loss Function, there is pretty much just one parameter:**

- What loss function are you using? (This is a bit more of an exact science in that there are loss functions that tend to perform better at specific tasks)
  - Other than your standard BCE and MSE, Huberloss is also a good choice to look into, as it balances your L1 and L2 errors

**How to Diagnose These Issues: the long and short of it.**

This question is one of the main reasons I created the repository, as most of the networks in Hwk8 (including the ones based on the active coding) did not display sufficient information to be able to easily identify these issues.

For Overfitting:

- Take a look at your Validation vs Train Loss, and compare them. A reminder that overfitting is the model's inability to generalize to data it has not seen before.
- Look at your loss curves. Are you using an appropriate number of epochs? Is your model using all that time effectively?

For Underfitting:

- Is your model leaving performance on the table? Could you get it to learn better without changing its structure? Look at the end behavior of your loss curves to determine this.
- Have you given your model the right tools? Does it seem like no matter what you do, it won't learn? This may be because it doesn't have enough free parameters or non-linearity to learn the relationships present in your use case.

Improper Loss Function:

- Do you feel that your model's loss score is reflective of your happiness with its predictive performance? Are you penalizing and rewarding it for the right things? How is the model treating outliers? How important are these outliers to you?

Note: For all measures, tests, and conclusions regarding a model's predictive performance, you should always draw from testing or validation scores.
