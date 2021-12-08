The Code of Emotion Recognition
Author: Lanqing Zhao, Chieh-En Li


1. Introduction of the algorithm
The algorithm of this project takes a input image that contains human facial expression (typically only one human facial expression) and outputs a label of emotion from 
 
happy,sad,netural,surprise,disgust,angry,and fear
 
The image can appear to be either color or gray but must be in RGB color space. The algorithm requires image to be resized to 224*224*3 format
and to be standardized by subtracting the mean and being divided by standard deviation. The  trained model is fine-tuned from VGG_16 model and gives the result based on
 the maximum probability from the softmax classifier. The accuracy of the training is around 95%. This model is trained by images in lab conditions.

2. File structure and functions
The files are in python notebook and python. We pefer the users to use notebook version

This set of files should be run on google colab


It contains mounting of google drive, training,image augmentation, randomization, and, relabel the image , and test parts
a)Training part
It will first load the VGG_16 model and modify it to meet the requirement of project. Then it will perform data pre-processing and generate the data batches. After that, it finally
gives the plot of accuracy and loss vs epochs.
For the training part, the requirement is that the data must be preprocessed in its corresponding directories of labels. Random data is not acceptable.

b)Image Augmentation
It will augment the dataset by adding random noise, rotation, and flip. It saves all images in png format. The image will be saved based on labels in its labeled directory.

c)Randomization
It will randomly select similar amount of images to form training and validation dataset for each class. The user must adjust the parameter based on the amount of images they have.
d) Relabel the image:
This part is for the purpose to relabel the images in the random order. It can be used to relabel the images from 7 label directories for the purpose of making confusion martix.
The requirement is that the filename must contain the label of image.
e)Test 
The test has 3 modes: number, confused matrix,and unlabel
The number mode only evaluates the model against dataset to give a numerical accuracy and loss (the data must be stored in its corresponding directories of label)
The confused matrix mode gives the confusion matrix in normalized and unnormalized format(the data must be preprocessed by d)
The unlabeled mode only predicts the label without checking the accuracy

The users are expected to mount their their google drive and rewrite the directory name before these codes is run.

3. Other specifications
The weights of model will be provided.(the file is too large to be attanched). The link is below:
https://drive.google.com/file/d/1K-YyrgKxylmrretnAAE7tvMOEQyP-y8Q/view?usp=sharing
The dataset is CK+ and JAFFE(not provided). The conversion of CK+ in jaffe format is referred to HappyNet source code.
We provide 2 images per class sample test data with labels.
The time we used is about 3 minutes per epoch after the first one.

4. some source code credits
Some of the source codes are from: 
Keras Documentation
HappyNet by Dan Duncan , Gautam Shine and Chris English
"Deep Learning with Python" by François Chollet
Scikit learn