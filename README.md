#  Detecting Defects in Steel with Neural Networks 
Aidan Stack - 2021

# Business Context

  Terms like ‘AI’, ‘Machine Learning’ and ‘Neural Networks’, usually inundate the mind with images of IBM’s [Watson](https://www.ibm.com/watson) crushing some of human kind’s most knowledgeable representatives in Jeopardy, or Google’s [AlphaGo](https://deepmind.com/research/case-studies/alphago-the-story-so-far) beating the world’s top ranked player in Go, a game widely respected as one of the most complex strategy games of all time. What probably doesn’t spring to mind is the deployment of these technologies in an industry like steel manufacturing. However, in much the same way that computers have become ubiquitous in all businesses over the last 70 years, organizations of all kinds are realizing the power of utilizing machine learning solutions. Sometimes called [‘Industry 4.0’](https://www.n-ix.com/computer-vision-manufacturing/), manufacturers are adopting AI, deep learning, and computer vision to improve product quality, reduce costs, and increase efficiency. AI has made its way into every step of the manufacturing process, from supply chain to inventory management, however the focus of this project is computer vision for defect detection.

  The dataset for this project comes from a [kaggle competition](https://www.kaggle.com/c/severstal-steel-defect-detection) put out by Russian steel production company [Severstal](https://www.severstal.com/eng/about/), who are looking to utilize machine learning to ‘improve automation, increase efficiency, and maintain quality’ throughout their production process. They are part of the global movement of manufacturing companies towards increased use of AI, and understand the value unlocked by applied machine learning. The specific AI application they are looking to improve with this kaggle competition is the detection of defects in steel using images of sheet steel from their production process. Detection of defects using computer vision could be integrated into the manufacturing pipeline and help reduce costs, and material waste. 

# Data Understanding 

The dataset includes 18,074 total images, 12,568 in the training set, and 5,506 in the test set. All the images are grayscale and come in a resolution of 1600 pixels wide, by 256 pixels tall. Included with the images is a csv, which lists all the images that contain defects, where each row is indexed by the name of .jpg file, and say what class of defect is in the image, as well as data on which pixels in the image make up that defect. Images that are listed more than once in this csv contain more than one class of defect, and images from the training set not listed in this csv at all are images where no defect is present.

# Reproducability and Environment Set-up

The number of images in the dataset and their relatively high resolution meant that this project was going to be computationally intensive, so all steps were performed on the cloud, using AWS. The images and CSVs were downloaded locally from kaggle, then uploaded to an Amazon S3 bucket. Using Amazon Sagemaker, an ml.m5.2xlarge notebook instance was created, with a volume size of 100GB. Multiple separate notebooks were created inside this instance, all with AWS' built in conda_tensorflow2_p36 environment. 

# Data Preparation

In order for the neural networks to be able to interpret the training images, the images must first undergo several transformations. The first is to convert the .jpg files into raw arrays. The dataset was fairly clean; all of the images have the same format of 256 by 1600, and have only 1 color channel, meaning they are grayscale. To reduce compute time, the images were reformatted to 256 by 256 upon import. The image arrays were then scaled from a range of 0 to 255, to a range of 0 to 1. The arrays were also flattened to be 1-Dimensional for use in the artificial neural networks, in the convolutional networks notebook, the arrays are again reshaped to a format of 256 x 256 x 1. 
first 3 images
<br>
<h3><center> First three images, all class 0 (no defect) </center></h3>

![nodefect.jpg](attachment:nodefect.jpg)

Only looking at these first images the difficulty of the task becomes clear, as these three images all belong to the same class yet vary widely in their content. 
<br>

# Binary Classification 

# Multiclass Classification 

# Conclusions
