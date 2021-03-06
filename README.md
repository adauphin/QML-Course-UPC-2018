# QML-Course-UPC-2018
Coding exercises for UPC QML course


# Google Colab File
For those who cannot make pytorch run on their computer, they can create a google Colab file. For this they need a google / gmail account and access their google drive.
The following [link](https://colab.research.google.com/drive/1_pmKbc_sN32TMHSXotBug-QqJAHkT9-s) provides a Colab file that helps you set up everything. You can access your data on your google drive and install python packages like pytorch.

This file will help you set up the first neural network that classifies Ising configurations according to their phases, like in this [publication](https://arxiv.org/pdf/1605.01735.pdf). The data for this can be found on https://github.com/carrasqu/data_nature_phy_paper, which is the author's GitHub page.

Don't forget to activate the GPUs/TPUs (Go to Edit and then notebook settings) when using keras or pytorch. Beware: TPUs work only with tensorflow and keras.

# Homework
- First you need to set up your programming environment. If you have a Linux or Mac computer then we recommend installing [Conda](https://www.anaconda.com/download/#macos) and install all the packages with it. Google will help you out.
In the end you will need especially [pytorch](https://pytorch.org/).

- If you have a windows computer we recommend using the Google Colab file from above. You can also use it if you don't want to set up your own programming environment on Linux and Mac.

## Homework General

The Homework have to be finished until the end of the course, before the exam. In groups of 3 people (There will be one group of 4) they can be solved and handed in as a short report that contains

- The code that is well commented, such that one can understand what you have done.
- A flux diagram or pseudocode that describes the code
- A description in your own words, what you were doing and explaining the code.
- Results such as figures or diagrams.

## Homework Fully Connected and Convolutional Neural Network (Alexandre Dauphin)

Recomendation: Use the TPUs. It will be faster than the GPUs.


**First assignment (warmup):** 

- Implement the k-means algrithm for a two dimensional dataset. Benchmark it for an example with 2 and 3 clusters. You can generate benchmark examples with [make_blobs](http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_blobs.html#sklearn.datasets.make_blobs). Show a scatter plot of the results where the color corresponds to the results of the k-means algorithm. What happens if you ask k-means to find more clusters than the real number?
- Edit the notebook of the course and the Dropout function to the fully connected neural network. Look at the Loss function and the accuracy of both training and validation sets. Describe the effect of the Dropout.
- Run the unsupervised algorithm t-SNE (an implementation is present in scikit learn) on the original MNIST data and compare with the results of PCA. Is there some interesting structure in the original data?

**Second assignment:**

- Import the cifar10 dataset (present in keras)
- Explore the different kind of images present in the dataset.
- This dataset is known to be much more difficult to classify than the MNIST dataset.
- Do a PCA analysis of the original data. Is there some visible structure in the data?
- Implement a fully connected neural network to classify the cifar10 dataset (you can use a similar architecture to the one for the MNIST with redefined dimensions, do 20 epochs). It should work poorly. 
- Do a PCA analysis on the output. 
- Implement a CNN. I propose the following structure: 7 convolutional layers with respectively 32,32,64,64,128,128,128 filters of size 3X3.  Add a maxpooling after the second layer, the fourth layer and the sixth layer.
- Train the CNN (40 epochs, batch size 128) and study the loss function/ accuracy. This could take several hours so don't forget to use the callbacks to save the weights.
- Add Batch normalization layers and dropout. Does it help to converge?
- Do a PCA analysis and k-means on the layer before the classifier. 
- Implement the data augmentation. Explore the generated images and train the model with data augmentation.
- At the end of the day, you should be able to reach more than 80% of accuracy on the test set.
- Apply the transfer learning for the cifar10 classification (10 epochs). How well is working the transfer learning?


## Homework Restricted Boltzmann Machines (Patrick Huembeli)

Homework will be the following:
- The 'RBM' folder contains a fully working restricted Boltzmann machine and a dummy dataset that only contains strings of [1,0,1,0,...] and [0,1,0,1,...] which can be used as a training set for first tests.
- Make the file `RBM_cleaned_runner.py` work on your computer and try to understand the code.
- Test if the training worked well by sampling from the trained RBM. If you sample after training on this dummy data you should only get the strings [1,0,1,...] and [0,1,0,...] because this is the only data the RBM has seen. If you get other strings, your RBM is not trained perfectly. Increse for example epochs or lower the learning rate.

**First assignment:** 
- Comment the code in `RBM_helper` and `RBM_cleaned_runner` as good as possible that other people can understand what it does. Everywhere in the code where you see the comment '#What does this code do?' you will have to add comments and put a pseudocode in your final report. Use clever names for your python functions to make references in the report that one can follow what you are referring to.
- Examples for pseudo codes can be found e.g. [here](https://en.wikibooks.org/wiki/LaTeX/Algorithms) or [here](https://tex.stackexchange.com/questions/163768/write-pseudo-code-in-latex) 

**Second assignment a):** 
- Train the RBM on the Bars and Stripes or MNIST data.
- To start I recommend Bars and Stripes, because it needs much less computational resources. In the file `Bars_and_Stripes.py` you can see how the data set is generated and saved to a `.npy` file.
- We have to convert the 4x4 pixel images into a 16 dimensional vector and put them into a RBM with the same input dimension. Find out how to do this with for example 'numpy'.
- Train the RBM the same way you did it on the dummy data set from before just with a different input dimension.
- Sample from it and see what you obtain. Document this in the final report. Describe what happens. Are the bars and stripes you sample good or are they blurry or just random noise? What happens if you increase the training epochs or the steps of the Gibbs sampling? Be aware that you have to transform the output of the RBM back to a 4x4 image. The same way you transformed the 4x4 image befor eto a 16 dimensional vector.
- Explore what happens if you change the number of hidden units. In the code so far we set the number of visible and hidden units equal. Can we still learn anything if we take e.g. 4 times less hidden units? How do the images look like?

**Second assignment more information for MNIST:**

Fell free to do the 2nd assigment with MNIST. You will be able to get full points just with Bars and Stripes, but we will for sure appreciate the extra effort and give some extrapoints for the other tasks.

Since we want to use very basic functions to load the data, I downloaded the MNIST dataset from http://yann.lecun.com/exdb/mnist/ and put it in the 'RBM/data' folder. Use the 'Load_MNIST.py' file from the 'RBM' folder to load the files and explore the data set. I put some basic functions to open and show the images.

- MNIST is a bit more challenging, but also more interesting to play with. So if you decide to train your RBM on MNIST instead of Bars and Stripes, follow these steps.
- The file `Load_MNIST.py` shows you already how to load MNIST files and how to make them from grey scale to black and white. Try to understand this file and use it or something similar to load your data.
- We have to convert the 28x28 pixel images into a 784 dimensional vector and put them into a RBM with the same input dimension. Find out how to do this with for example 'numpy'.
- What happens if you train the RBM just on one type of numbers. For example extract all the number 3 images from the data set and just train on them. To do so, the `data/` folder contains also the labels of the training set to find all images that contain e.g. a 3.


**Second assignment b):** 
- If you go to `RBM_helper.py` file and change function `draw_sample(self, sample_length)` such that the Gibbs sampling is not started with an random vector, but with an actual image from the training set. What happens then? (For this task you will have to change `RBM_helper.py`)

**Third assignment:**
- Use now the images from `Bars_and_Stripes.py` that are partially blanked, which are stored in the vraiable 'subset' and also saved as a numpy file `blanked_bars_and_stripes.npy` if you run `Bars_and_Stripes.py`. You can think of these images as partially damaged and we would like to reconstruct them with our trained RBM.
- For this you will have to make changes in the `RBM_helper.py` file. In the function `draw_sample(self, sample_length)` we so far used a random vector to start the Gibbs sampling and make `sample_length` Gibbs setps until we obtain an output. Now we would like to start the Gibbs sampling with the 'damaged' images and see if we can reconstruct them. Do that and show your results.

## Homework Reinforcement Learning (Gorka Muñoz-Gil)

**First assignment:**
- Train a policy which learns which arm of a multiarmed bandit needs to be pulled to get the highest reward. You can find the class describing the mult-armed bandit in *MBA.py*.
The policy should be based on the incremental implementation and the *e*-greedy method. For *e* = [0,0.01,0.1], plot the reward obtained at each episode (go up to 1000 episodes), averaged over 2000 runs of the algorithm. Each run consists in the training of a zero-initialized policy.

**Second assignment:**
- Train a policy to find which frequency can drive a three level system from the initial state to a target state. More details to come...
