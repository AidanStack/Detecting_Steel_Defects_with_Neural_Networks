#  Detecting Defects in Steel with Neural Networks 
Aidan Stack - 2021

# Business Context

  Terms like ‘AI’, ‘Machine Learning’ and ‘Neural Networks’, usually bring to mind with images of IBM’s [Watson](https://www.ibm.com/watson) crushing some of human kind’s most knowledgeable representatives in Jeopardy, or Google’s [AlphaGo](https://deepmind.com/research/case-studies/alphago-the-story-so-far) beating the world’s top ranked player in Go, a game widely respected as one of the most complex strategy games of all time. What probably doesn’t spring to mind is the deployment of these technologies in an industry like steel manufacturing. However, in much the same way that computers have become ubiquitous in all businesses over the last 70 years, organizations of all kinds are realizing the power of utilizing machine learning solutions. Sometimes called [‘Industry 4.0’](https://www.n-ix.com/computer-vision-manufacturing/), manufacturers are adopting AI, deep learning, and computer vision to improve product quality, reduce costs, and increase efficiency. AI has made its way into every step of the manufacturing process, from supply chain to inventory management, however the focus of this project is computer vision for defect detection.

  The dataset for this project comes from a [kaggle competition](https://www.kaggle.com/c/severstal-steel-defect-detection) put out by Russian steel production company [Severstal](https://www.severstal.com/eng/about/), who are looking to utilize machine learning to ‘improve automation, increase efficiency, and maintain quality’ throughout their production process. They are part of the global movement of manufacturing companies towards increased use of AI, and understand the value unlocked by applied machine learning. The specific AI application they are looking to improve with this kaggle competition is the detection of defects in steel using images of sheet steel from their production process. Detection of defects using computer vision could be integrated into the manufacturing pipeline and help reduce costs, and material waste. 
  
  The goal of this project is to train neural networks to classify these steel images in two modes: binary classification, and multiclass classification. In the binary context, the networks were trained to recognize each image as either containing a defect, or not containing a defect. In this use case, manufacturing engineers could separate the steel by class as it flowed through the production line, removing pieces exhibiting defects. Multiclass classification provides a similar yet more flexible mode of deployment, where engineers at the site could determine which classes of defects were more tolerable, and allow those pieces through, or simply separate each class of defect into its own production stream. 

# Data Understanding 

* The training set is comprised of 12,568 grayscale images of steel,
* Included with the images is a csv, which lists all the images that contain defects. 
  * This csv serves as the ground truth labels for the networks, and images not listed in this csv are of class 0, meaning no defects are present
* In the training set, 53% have no defects, while 47% exhibiting one or more class of defect
* 97% percent of the images contain either no defects, or only one class of defect, with only 3% containing more than one class simultaneously

# Reproducability and Environment Set-up

The number of images in the dataset and their relatively high resolution meant that this project was going to be computationally intensive, so all steps were performed on the cloud, using AWS. The images and CSVs were downloaded locally from kaggle, then uploaded to an Amazon S3 bucket. Using Amazon Sagemaker, an ml.m5.2xlarge notebook instance was created, with a volume size of 100GB. Multiple separate notebooks were created inside this instance, all with AWS' built in conda_tensorflow2_p36 environment. 

# Data Preparation

The images underwent several transformations before they were correctly formatted as inputs to neural networks. 
* The jpg image files were converted into numpy arrays.
* To reduce the number of trainable parameters, the images were resized from 1600 x 256 x 1, to 256 x 256. 
* The values in the arrays were scaled so that instead of ranging from 0 to 255, they ranged from 0 to 1 
* The arrays were flattened to be 1-Dimensional for use in the artificial neural networks
  * In the convolutional network notebook, the arrays were reshaped to 256 x 256 x 1

# Binary Classification 

For binary classification, the goal was simply to train the networks to correctly classify an image based on defects present vs no defects present. In addition to the preprocessing already done on the images, the csv included with the original dataset required modification. The list of jpg file names, in conjunction with the provided csv were transformed into one hot encoded labels, the format required by keras. These labels recorded whether each image was a '0' (no defects present) or a '1' (defects present). 

The first metric to beat was the modeless baseline of 53%, the accuracy you would achieve by guessing the majority class (no defects). The performance of different network architectures was explored by first training artificial neural networks, and then moving on to convolutional networks. The final iteration of the artificial networks achieved a 77% accuracy in this binary context. The final convolutional network managed 85% accuracy, due to the specialization of convolutional networks for image classification. Since the C.N.N.s proved the most appropriate for this task, they were used exclusivley in the multiclass classification section. 


# Multiclass Classification 

In this context images were labelled as one of five classes, '0', meaning no defects present, and '1' through '4' representing each class of defect respectively. The training labels from the binary classification process wouldn't work for this task, so new training labels were created. 

# Conclusions

With 1.8 billion tons of crude steel produced in 2020 alone, the enormous scale of the global steel industry means that even small improvements to efficiency would be enough to move the needle, and have real economic and environmental impacts. The global demand for steel is increasing, and that trend is expected to continue, especially as developing nations mature economically, and begin to demand more steel for construction and industry. This means that the earlier the steel industry invests in machine learning solutions, the more time the cost and carbon benefits will have to compound. Steel is a commodity item, which means it often competes solely on the basis of cost. This means computer vision tasks like the one explored in this project are high volume, low cost of error, meaning machine learning is an appropriate approach.

These reasons "Why", combined with the "How" explored throughout this project, prove that a computer vision solution using deep learning, and more specifically convolutional neural networks, is not only appropriate, but viable in this business context.

# Navigating This Repository

  Notebooks
    EDA Notebook - All data exploration steps 
    Artificial Neural Network - Binary classification using simple networks
    Convolutional Neural Network - Binary and multiclass classificiation using convolutional networks

  Main Report Notebook - Technical summary covering the entire project from business problem to final conclusions
  
  README - You are here 
  
# Resources 

[Kaggle Competition (original dataset)](https://www.kaggle.com/c/severstal-steel-defect-detection)

[Severstal](https://www.severstal.com/eng/about/)

[Computer Vision in Manufacturing/ ‘Industry 4.0’](https://www.n-ix.com/computer-vision-manufacturing/)

[Defect Mask Visualization Reference](https://www.kaggle.com/go1dfish/clear-mask-visualization-and-simple-eda)









