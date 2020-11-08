---
title:  "Introduction to Weakly Supervised Learning"
layout: posts
---

<p style="text-align:justify">Supervised Machine Learning relies on labelled data that consists of data and pairs of expected outputs , for example an image of dog that is labelled a dog.
They are essentially mathematical models with parameters optimized according to a given criterion or what you would call a loss/error function 
that measures how the of a given model differs from an expected output. Curating the dataset on which the model is trained/tested requires manual effort of
data labellers labelling every image for a given task. Some tasks are expensive to annotate and some are easier or we might have large well curated datasets for tasks that are easy to
annotate. Weakly supervised learning allows us to use the datasets which are easy to annotate to perform tasks that are more expensive to annotate. 
For , example from a dataset consisting of labelled pairs of image/label pairs we could curate a dataset for object localization and semantic segmentation and train a model for the same.</p> 

<h1>General Weakly Supervised Pipeline</h1>

<p style="text-align:justify">In this blogpost I would like to introduce weak supervised learning and provide examples of how its done for object detection.</p>

<h1>Object Detection</h1>

<img src="https://www.arunponnusamy.com/images/yolo-object-detection-opencv-python/yolo-object-detection.jpg">

<p style="text-align:justify">Object detection is the task of not only classifiying instances of given class but also specifying its bounding box location (task called localization). Annotating 
images with bounding boxes are more expensive as compared to anotating a single label for a image as in case for object classification. So instead we use a dataset consisting a pair of image/labels and train a classifier on it and use it to annotate bounding boxes for object detection. </p>

