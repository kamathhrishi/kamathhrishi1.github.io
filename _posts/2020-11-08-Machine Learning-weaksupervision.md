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

<p style="text-align:justify">In this blogpost I would like to introduce weak supervised learning and provide examples of how its done for object detection and instance segmentation tasks</p>
