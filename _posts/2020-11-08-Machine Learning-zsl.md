---
title:  "Machine Learning-Learning to predict classes not seen during training"
layout: posts
---

<p style="text-align:justify">In conventional machine learning we train an algorithm on data/classes pairs (supervised learning) or train an algorithm only on raw data(Unsupervised learning) and make predictions. But , can we possible train an algorihtm to make the right predictions on class of data its never seen before?
Quite possible , the specific technique is called zero shot learning.</p>

<p>In this blogpost I would like to cover what zero shot learning (ZSL) is , its working and limitations.</p>

<br />

<img src="https://csdl-images.computer.org/trans/tp/2016/07/figures/akata1-2487986.gif">

<br />

<p style="text-align:justify">ZSL is a type of learning method that allows to predict classes the algorithm has not seen during training time. ZSL cannot be done directly on just image/label pairs , they require an intermediate that helps algorithms relate images to classes. Lets call these intermediates as attributes. These attributes could be word vectors of the class , a sentance description of the class or a vector with description of the class. So in ZSL we learn to go from image to attributes and then attributes to classes. We learn the relationship from a given set of classes for which we have the relevant image-attribute pairs. In this blogpost I would like to focus on ZSL that uses a vector description of a given class. 
  
<br />
<img src="https://www.ecse.rpi.edu/~cvrl/database/Attribute_Dataset_Files/apascal.png">
<br />

<p style="text-align:justify">A vector describing a given class consists of each point in the vector describing a particular feature. A binary number of 1 on the 1st position might describe that its a brown animal , 2nd position describing if its associated with water with as many attributes as possible describing a class. Attributes could be binary or continious with value denoting the strength of each given attribute.The more attributes , the finer detail it could learn about a given class but also requires more data to learn the relevant relationships.The network uses the seen classes to learn relation between images and attributes or other information such as human gaze , word embeddings or whatever information that could be related between classes and images. Based on what the network learns it could be further mapped to the objects and attributes.</p>

<p style="text-align:justify">Say your classifier has pig , dogs , horses and cats images and its attributes during training time and has to classify a zebra during test time. During training time it learns the relation between image pixels and attribute such as 'stripes,tail,black,white...'. So during test time given an image you predict its attributes and find the class the attributes correspond to. ZSL is very much like how humans learn , we learn concepts and relate them to new instances we haven't seen before.</p>

<p style="text-align:justify">Zero shot learning requires images that represent all the attributes in the training set.Attributes are a finer description of each classes and can even be used to augment supervised learning in some cases. But , attributes are expensive in terms of annotation as it requires data labeller to provide values for every attribute for every datapoint which increases the labelling cost by atleast x(Number of attributes) as compared to labelling data for supervised learning. Attributes can also be a little subjective to data labeller. There are also other intermediate alternatives such as word embeddings that could be used to learn an intermediate representation but might be a little a noisy and might not have a direct relationship between various features/cues of images but are much easier to obtain.</p>
