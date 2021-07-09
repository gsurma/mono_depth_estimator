<h3 align="center">
  <img src="assets/mono_depth_estimator_icon_web.png" width="300">
</h3>

# Mono Depth Estimator

Python Jupyter notebook with TensorFlow Keras implementation for the **mono image depth prediction**.

<img src="assets/result4.gif">

## Usage
 
[Kaggle Notebook](https://www.kaggle.com/greg115/pix2pix-depth-estimation)

[Local Notebook](Pix2Pix-DepthEstimation.ipynb)


# How does it work?

## 1. Stereo Depth Dataset Generation

We can achieve a depth map from a pair of stereo images with the SGBM algorithm. Let's feed [stereo\_depth\_estimator](https://github.com/gsurma/stereo_depth_estimator) with [KITTI](http://www.cvlibs.net/datasets/kitti/) dataset to achieve depth maps for stereo image pairs. Then we can generate pairs of **input -> depth** by uniformly taking left or right image from the input pair and the corresponding depth map.

Full dataset available [here](https://www.kaggle.com/greg115/pix2pix-depth). Example pair:

<img src="assets/input_depth.png">


## 2. Image-to-Image Translation with Conditional Adversarial Nets

Let's train a GAN model that learns image to image translations. We are going to use **Pix2Pix** model architecture by [Isola et al](https://phillipi.github.io/pix2pix/).

We will feed the model with **source -> destination** pairs and expect it to learn the translation between them. In our case, we are going to train the network on **input -> depth** pairs and expect it to generate depth maps for unseen inputs. 

With this approach we are going to train the network that is capable of generating a depth map for a single image.

### Training


<img src="assets/training_example.png" >

Left column shows **source inputs**, middle column **model generated outputs** and right column **destination depth maps**. 


This is how the training progress looks over time:


<img src="assets/training.gif">

We can see that over time model generated outputs are getting closer to the destination depth maps generated with stereo matching.

### Results

Inputs on the left and model generated depth maps on the right:

<img src="assets/result1.gif">
<img src="assets/result2.gif">
<img src="assets/result3.gif">
<img src="assets/result4.gif">


## Author

**Greg (Grzegorz) Surma**

[**PORTFOLIO**](https://gsurma.github.io)

[**GITHUB**](https://github.com/gsurma)

[**BLOG**](https://medium.com/@gsurma)

