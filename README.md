# **A.I. Opening Approach to Diabetic Retinopathy**

**Author:** _Hoang Nguyen_


<img src="images\phone_screening.jpg" width=80%>


## Overview

The World Health Organization estiamtes that over 420 million people worldwide have diaebetes with the number of cases and prevalance of disease increasing worldwide each year. The majority of these cases occur in low to middle income countries where resources are low. Early detection of this disease and it's complications can reduce health burdens worlwide.

<img src="images\diabetes.jpeg" width=80%>

One major complication of Diabetes, and that can readily be screened, is Diabetic Retinopathy, one of the leading causes of blindness around the world. 

<img src="images\dretina.png" width=50%>

Currently, detecting Diabetic Retinoapthy is a time-consuming and manual process that requires bulky devices to take pictures for trained clinicians to examine and evaluate digital color fundus photographs of the retina. By the time human readers submit their reviews, often a day or two later, the delayed results lead to lost follow up, miscommunication, and delayed treatment. While this approach is effective, its resource demands are high. The expertise and equipment required are often lacking in areas where the rate of diabetes in local populations is high and DR detection is most needed.

One promising technique that has shown promising results in the literature is smartphone fundus photography. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5609317/

<img src="images\phone_exam.jpg">
<img src="images\eye.jpg" width=50%>

Using powerful smartphone imaging equipped with a portable lens partnered up with machine learning to detect DR can make health screening more accessible and get help to those who needs it the most.

## Data
The data set comes a kaggle competition that can be found here: https://www.kaggle.com/competitions/diabetic-retinopathy-detection/overview

The file contains 90 gigabites of images seperated into train set with labels and a test set without the labels. The labels are categorized as 0 (No DR) to 4 (Different severity of DR). Since this is not for the competition, the test set with no labels will be excluded. The training set will then be split to our own test, train, and validation set. Additionally, the problem will be set to a binary classification problem0 (No DR), 1 (DR present) for our purposes of a positive or negative detetction. The sample is very robust with a lot of noise and class imbalances were accounted for with weights.

## Methods
This project took an iterative approach training different types of neural networks while tuning the hyperparameters. There are multiple iterations of each model, but only the best performance will be shown.

## Results

Below are the models with the best hyperparemeters with the baseline being a standard convolution neural network. The model with the highest accuracy was the Ensemble Model where we averaged the predictions of our best 3 models.

<img src="images\accuracy.png">

Below is a diagram of how the models were ensembled that gave us the best results. We pass an image through our models to get 3 different predictions. We then averaged the first two predictions from the Densenet and Xception network. We then use this averaged results and then average that with prediction 3 from the InceptionResNetV2. The new averaged prediction is then use to predict if the image is normal or has the disease based on a threshold we set. What ensembling does to our modeling is that it can help capture certain things that each network architecture does well on. 

<img src="images\ensemble_flow_chart.png">

What may be more important than accuracy is our recall score. Diagnosing a patient normal when they actually have the disease is very costly. But as you can see in the confusion matrix, our model did not perform very well on this metric at a .5 threshold. We can adjust the threshold  to reduce the false negatives so we can capture more patients with the disease. And having a low threshold might be okay for a situation like this where communities don’t have access to care to begin with. However, determining the right threshold could require some consultation with a medical expert. What we think may be more useful is if our model just gives us a probability score . That can be paired with the patient’s medical history to make a better prediction. 


<img src="images\False_Positives.png">


## Conclusion 
In many underserved areas, the nearest healthcare facilities are often hours away. This often leads to patients not seeking care until symptoms are severe, but by then it might be too late.  But what if we can catch it earlier.  With accessible high quality imaging tools, we can train community health workers to use this technology and use machine learning model to give us a predictions. Using this prediction ensembled with patient’s medical history, we can get them taken care of sooner before its too late.

<img src="images\qr_code.png" width = 30%>


## Next Steps

- <u> Tabular Data </u>
    - We can combine our model with tabular data.  Knowing if the patient has a family history of a disease goes a long way.
<br><br>
- <u> Other Illnesses </u>
    - Expand our prediction to other eye related illnesses since we have a picture already..
<br><br>
- <u>Web Application</u>
    - Improve on the web application to add in new features such as step by step instruction on how to take these images or trouble shooting features.


## For More Information
Please review our full analysis in our [Jupyter Notebook](./Main.ipynb) or our [presentation]().

For any additional questions, please contact

<img src="images\Hoang.png" width=10%> Hoang Nguyen: hvnguyen90@gmail.com <br />


## Repository Structure

```
├── README.md                           
├── Main.ipynb   
├── Presentation.pdf 
├── notebooks  
├── data                                
└── images 
```