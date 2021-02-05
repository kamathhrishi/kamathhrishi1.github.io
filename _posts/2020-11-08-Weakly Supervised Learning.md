---
title:  "Introduction to Weakly Supervised Learning (In Progress , putting it in public is a promise :) )"
layout: posts
---

<p style="text-align:justify">Supervised Machine Learning relies on labelled data that consists of data and pairs of expected outputs. For example an image of dog that is labelled a dog.
Supervised Machine Learning models are essentially mathematical models with parameters optimised according to a given criterion or what you would call a loss/error function 
that measures how the of a given model differs from an expected output. Curating the dataset on which the model is trained/tested requires manual effort of
data labellers labelling every image for a given task. Some tasks are expensive to annotate and some are easier or we might have large well curated datasets for tasks that are easy to
annotate. </p>
<p style="text-align:justify">
Weakly supervised learning allows us to use the datasets which are easy to annotate to perform tasks that are more expensive to annotate. It could use another classifier to label the data or handcrafted domain knowledge. 
For , example from a dataset consisting of labelled pairs of image/label pairs  is good for a classification task we could curate a dataset for object localisation and semantic segmentation and train a model for the same. Another example extending to text for sentimental analysis.
We could take several rows of text and use if else statements to check if words that correspond to negative/positive sentiment are present and label the dataset accordingly. 
This leads to a dataset with noisy labels with which can learn a sentimental classifier. The intuition why this works is that most noisy labels have some learnable patterns. 
We must also ensure that the algorithm does not overfit to the noisy patterns. This can be done by curating a small dataset with correct labels which can be used as test set. 
</p> 

<h1>General Weakly Supervised Pipeline</h1>

1. Label Dataset
2. Use Noise labelled dataset to train classifier
3. Relabel dataset
4. Retrain classifier until convergence

<p style="text-align:justify">In this blogpost I would like to introduce weak supervised learning and provide examples of how its done for object detection.</p>

<h1>Object Detection</h1>

<img src="https://www.arunponnusamy.com/images/yolo-object-detection-opencv-python/yolo-object-detection.jpg">

<p style="text-align:justify">Object detection is the task of not only classifiying instances of given class but also specifying its bounding box location (task called localization). Annotating 
images with bounding boxes are more expensive as compared to anotating a single label for a image as in case for object classification. So instead we use a dataset consisting a pair of image/labels and train a classifier on it and use it to annotate bounding boxes for object detection. </p>

<p>Visual Cues for Segmentation and Localisation</p>
<p>Segmentation</p>

<p>Localisation</p>

<p style="text-align:justify">There are several ways of leveraging weakly supervised learning to label datasets for segmentation and detection using an existing classifier. Annotating dataset for object 
detection has these steps 
1. Region Proposal 
2. Label regions 
3. Region Selection 
4. Label dataset 
5. Train Localization network 
6. Back to step 2

I would explain these individual components in some detail

Region selection is done using selective max , sliding windows or edgebox. These regions are labelled by an classifier trained on classification task on classes contained in the image.
The classifier is leveraged to label the regions. There are several stratergies to leverage to 

, but there are some approaches that perform 2-5 end to end which I will save for another blogpost. 

Having motivated weakly supervised learning as a way of labelling data with less difficulty , its still far from use in production system and still an active research area. 
But , it seems like a promising method for future use. </p>
