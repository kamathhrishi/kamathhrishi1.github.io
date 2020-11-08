---
title:  "Machine Learning-Learning to predict classes not seen during training"
layout: posts
---

<p style="text-align:justify">In conventional machine learning we train an algorithm on data/classes pairs (supervised learning) and make 
predictions or train an algorithm only on raw data(Unsupervised learning).But , can we possible train an algorihtm to make the right predictions on data its never seen before.
That is can a dog/cat classifier be able to predict a tiger or a mouse? It is quite possible , the specific technique is called zero shot learning. In the blogpost I would like to 
cover what zero shot learning is , its working and limitations.
</p>

<img src="https://csdl-images.computer.org/trans/tp/2016/07/figures/akata1-2487986.gif"></img>

<p style="text-align:justify">In Zero shot learning (ZSL) cannot be done directly on just image/label pairs , they require an intermediate that helps algorithms relate images to classes. Lets call these intermediates as attributes. These attributes could be word vectors of the class , a sentance description of the class or a vector with description of the class. So in ZSL we learn to go from image to attributes and then attributes to classes. We learn the relationship from a given set of classes for which we have the relevant image-attribute pairs. In this blogpost I would like to focus on ZSL that uses a vector description of a given class. A vector describing a given class consists of each point in the vector describing a particular feature. A binary number of 1 on the 1st position might describe that its a brown animal , 2nd position describing if its associated with water with as many attributes as possible describing a class. The more attributes , the finer detail it could learn about a given class but also requires more data to learn the relevant relationships.</p>

<p>Zero shot learning requires a large number of classes that represent the attributes.Attributes are a finer description of each classes and are expensive in terms of annotation as it requires each data labeller to decide for each datapoint on around 50-100 attributes.</p>
