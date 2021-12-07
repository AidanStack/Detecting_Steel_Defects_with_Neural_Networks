#  Detecting Defects in Steel with Neural Networks 
Aidan Stack - 2021

# Business Context

  Terms like ‘AI’, ‘Machine Learning’ and ‘Neural Networks’, usually inundate the mind with images of IBM’s [Watson](https://www.ibm.com/watson) crushing some of human kind’s most knowledgeable representatives in Jeopardy, or Google’s [AlphaGo](https://deepmind.com/research/case-studies/alphago-the-story-so-far) beating the world’s top ranked player in Go, a game widely respected as one of the most complex strategy games of all time. What probably doesn’t spring to mind is the deployment of these technologies in an industry like steel manufacturing. However, in much the same way that computers have become ubiquitous in all businesses over the last 70 years, organizations of all kinds are realizing the power of utilizing machine learning solutions. Sometimes called [‘Industry 4.0’](https://www.n-ix.com/computer-vision-manufacturing/), manufacturers are adopting AI, deep learning, and computer vision to improve product quality, reduce costs, and increase efficiency. AI has made its way into every step of the manufacturing process, from supply chain to inventory management, however the focus of this project is computer vision for defect detection.

  The dataset for this project comes from a [kaggle competition](https://www.kaggle.com/c/severstal-steel-defect-detection) put out by Russian steel production company [Severstal](https://www.severstal.com/eng/about/), who are looking to utilize machine learning to ‘improve automation, increase efficiency, and maintain quality’ throughout their production process. They are part of the global movement of manufacturing companies towards increased use of AI, and understand the value unlocked by applied machine learning. The specific AI application they are looking to improve with this kaggle competition is the detection of defects in steel using images of sheet steel from their production process. Detection of defects using computer vision could be integrated into the manufacturing pipeline and help reduce costs, and material waste. 

  Steel is the worlds [second largest commodity item](https://secure.fia.org/files/css/magazineArticles/article-1410.pdf) behind crude oil, with [1.8 billion](https://www.weforum.org/agenda/2021/06/global-steel-production/#:~:text=Consumption%20and%20Production-,Steel%20is%20the%20foundation%20of%20our%20buildings%2C%20vehicles%2C%20and%20industries,scaling%20down%20their%20domestic%20production.) metric tons of crude steel produced in 2020 alone. The titanic size of this industry means that any improvements to efficiency that AI could afford would be well worth the investment. Additionally, [how appropriate AI is for various real world applications](https://www.ml.cmu.edu/research/joint_phd_dissertations/dissertation_dearteaga.pdf) is often judged in the context of low volume, high stakes vs high volume, low stakes. For example looking at an X-ray and determining whether a patient has pneumonia is a classic low volume, high stakes image classification task, here the accountability and expert eye of human labor often makes the most sense. AI is often a better fit for high volume, low stakes contexts where an error is much more tolerable, but the volume is too high for human labor to make sense. The business context of this task supplied by severstal is a perfect example of this high volume, low stakes paradigm. Computer vision is a highly appropriate choice, and could be leveraged to improve the production of a commodity item with huge annual volume, and a relatively high tolerance for errors. The dataset is a perfect fit for the business problem at hand, because it comes directly from a steel manufacturer, so the results of this project will be generalizable to similar tasks within the steel industry. 

# Data Understanding 

The dataset includes 18,074 total images, 12,568 in the training set, and 5,506 in the test set. All the images are grayscale and come in a resolution of 1600 pixels wide, by 256 pixels tall. Included with the images is a csv, which lists all the images that contain defects, where each row is indexed by the name of .jpg file, and say what class of defect is in the image, as well as data on which pixels in the image make up that defect. Images that are listed more than once in this csv contain more than one class of defect, and images from the training set not listed in this csv at all are images where no defect is present.

# Data Preparation 

In order for the neural networks to be able to interpret the training images, the images must first undergo several transformations. The first is to convert the .jpg files into raw arrays. Since all the work for this project was done on AWS, the images are stored in a bucket on Amazon S3 then imported into Amazon Sagemaker where they are converted into arrays.

# Modeling Process

  ## Basic Artifical Neural Networks

  ## Convolutional Neural Networks 

# Model Evaluation 

# Conclusions
