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
- Model Not Learning (If your loss stays high, compare it to the loss attained by random guessing, setting lr arbitrarily low is a way to accomplish this)
