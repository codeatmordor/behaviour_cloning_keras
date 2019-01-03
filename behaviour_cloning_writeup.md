# **Behavioral Cloning** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.

---

**Behavioral Cloning Project**

The goals / steps of this project are the following:
* Use the simulator to collect data of good driving behavior
* Build, a convolution neural network in Keras that predicts steering angles from images
* Train and validate the model with a training and validation set
* Test that the model successfully drives around track one without leaving the road
* Summarize the results with a written report


[//]: # (Image References)

[image1]: ./data/IMG/center_2016_12_01_13_30_48_287.jpg "Centre Camera Image"
[image2]: ./data/IMG/left_2016_12_01_13_30_48_287.jpg "Left Camera Image"
[image3]: ./data/IMG/right_2016_12_01_13_30_48_287.jpg "Right Camera Image"
[image4]: ./examples/figure_1.png "Loss Plot"


## Rubric Points
### Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/432/view) individually and describe how I addressed each point in my implementation.  

---
### Files Submitted & Code Quality

#### 1. Submission includes all required files and can be used to run the simulator in autonomous mode

My project includes the following files:
* model.py containing the script to create and train the model
* drive.py for driving the car in autonomous mode
* model.h5 containing a trained convolution neural network 
* writeup_report.md or writeup_report.pdf summarizing the results

#### 2. Submission includes functional code
Using the Udacity provided simulator and my drive.py file, the car can be driven autonomously around the track by executing 
```sh
python drive.py model.h5
```

#### 3. Submission code is usable and readable

The model.py file contains the code for training and saving the convolution neural network. The file shows the pipeline I used for training and validating the model, and it contains comments to explain how the code works.

### Model Architecture and Training Strategy

#### 1. An appropriate model architecture has been employed

keras high level APIs are used in creation of my model which is inspired by nVIDIA model explained in lectures. This model comprises five Convolutional layers and four Dense layers. The model also contains a Dropout layer, a Flatten layer and one Cropping2D layer. The data is normalized in the model using a Keras lambda layer. The total number of parameters in the proposed model is 348, 219.

#### 2. Attempts to reduce overfitting in the model

TThe model contains dropout layer in order to reduce overfitting(model.py:108). Dropout rate is 50% (0.5 probability). The model was trained and validated on data sets provided by Udacity. The model was tested by running it through the simulator and ensuring that the vehicle could stay on the track for most of the track length.

#### 3. Model parameter tuning

The model used an adam optimizer, so the learning rate was not tuned manually (model.py line 114).The number of epochs is set to 5 and batch_size is set to 32.

#### 4. Appropriate training data

Training data was chosen to keep the vehicle driving on the road. I used a combination of center lane driving, recovering from the left and right sides of the road.

### Model Architecture and Training Strategy

#### 1. Solution Design Approach

Data set was spilt for test and validation using split method with factor of  0.2. I used generator so that a part of training data images is operated upon at a given time. Training data set is approx 8000 images to train the model. Also, augmented all of the images in the training data.  Steering corrections are also introduced alongwith appropriate camera images i.e. left, right and center camera images. At the end of the process, the vehicle is able to drive autonomously around the track without leaving the road.
![Centre Camera Image][image1]
![Left Camera Image][image2]
![Right Camera Image][image3]

In the end, after training, when the model is saved, a plot is also depicted to show the training and validation losses.
![Losses Plot][image4]


#### 2. Final Model Architecture

The final model architecture (model.py lines 101-113) consisted of multiple layers of convolution neural network.


