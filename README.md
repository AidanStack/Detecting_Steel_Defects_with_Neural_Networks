#  Detecting Defects in Steel with Neural Networks 
Aidan Stack - 2021

# Navigating this Repository


# Business Overview 

The dataset for this project comes from a kaggle competition put out by Russian steel production company Severstal, who are looking to utilize machine learning to ‘improve automation, increase efficiency, and maintain quality’ throughout their production process. They are part of a global movement of manufacturing companies increasing their use of AI, and understand the value unlock that is machine learning. The specific AI application they are looking to improve with this kaggle competition is the detection of defects in steel using images of sheet steel from their production process.

# Data Understanding 

The dataset includes 18,074 total images, 12,568 in the training set, and 5,506 in the test set. All the images are grayscale and come in a resolution of 1600 pixels wide, by 256 pixels tall. Included with the images is a csv, which lists all the images that contain defects, where each row is indexed by the name of .jpg file, and say what class of defect is in the image, as well as data on which pixels in the image make up that defect. Images that are listed more than once in this csv contain more than one class of defect, and images from the training set not listed in this csv at all are images where no defect is present.

# Data Preparation 

In order for the neural networks to be able to interpret the training images, the images must first undergo several transformations. The first is to convert the .jpg files into raw arrays. Since all the work for this project was done on AWS, the images are stored in a bucket on Amazon S3 then imported into Amazon Sagemaker where they are converted into arrays.

# Modeling Process

  ## Basic Artifical Neural Networks

  ## Convolutional Neural Networks 

# Model Evaluation 

# Conclusions
