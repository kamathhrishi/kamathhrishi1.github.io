---
title:  "Deep Learning in Practice-Be The algorithm"
layout: posts
mathjax: "true"
summary:  "Manual reannotation is the process of you going through image/text of your dataset and understanding what features exactly define this given image. Manually reannotating not only helps remove incorrect labels but also helps understand biases your algorithm could pick up on or even helps you pick up on certain data for the algorithm to make training easier."
---

<p style="text-align:justify">Conventional machine learning required the practitioner to manually look at images/text and handcraft appropriate features. Deep Learning models are powerful , powerful enough that they could just memorize random data without any real correlations <a href="#ref1">[1]</a>. This allows us to feed in input/output pairs for some tasks end to end without much preprocessing effort giving us the flexibility to learn features from raw images/text but at the expense of a lot of data.</p>
<center>
<img height="400px" width="600px" src="https://i.stack.imgur.com/bN2iA.png">
</center>
<p style="text-align:justify">Its not magic it still needs some correlated patterns to generalize and learn required features. This requires you to more or less understand your training dataset. As the common machine learning phrase goes <i>"Your algorithm is good as your data"</i>. Deep learning models help extract features relevant to given dataset, provided you have enough examples that expose right features.
 <b>Manual reannotation</b> is the process of going through every image/text of the dataset and understanding what features exactly define a given class. 
 Manually reannotating not only helps <b>remove incorrect labels</b> but also helps <b>understand biases</b> your algorithm could pick up on or even helps <b>understand neural network predictions</b> to an certain extent. Further it also helps decide the type of <b>augmentations</b> that could help your algorithm generalize or prrovides cues on what additional data could help. While its true neural networks are still blackboxes or less interpretable but on a high level there are still ways to understand what they learned from the dataset.</p>

<center>

<img height="400px" width="600px" src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/allIndoors.jpg?raw=true">
</center>
<p style="text-align:justify">I would like to take an example of manually reannotating a dataset for a computer vision classification task <b>Indoor Scene Recognition</b>. The dataset consists of around only 5000 images of 67 different classes <a href="#ref2">[2]</a>. While in this post I took an example of Computer Vision task , you can similarly analyze text/speech datasets or environments in Reinforcement Learning.</p>
  
<p style="text-align:justify">Let us annotate the class bar. Think of what features could possibly define bar: high chairs , cups with drink , bottles , low lit eenvironments , bar counters , people and some food. Ofcourse not just these individual attributes but in the context of them occuring toghether. Depending on the label, all or some features could exist for the image to satisfy requirement of the label. Let us look at a few sample images which are labelled as bar in the scene recognition dataset and decide how to eliminate or keep them based on the features we would want to define a bar.</p>
<div>
 
<p float="center">
 <img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/bar_0046.jpg?raw=true" width="200" height="150"/>
</p>

<p style="text-align:justify">
The first image meets our definition of a bar : high chairs [check], drinks [check] and bar counter[check]. Although to be able to generalize these features you would need several different variations of the image ,such as ones with a bartender , people taking a drink and different shades of furnitures. 
<p float="center">
<img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/bar_0439.jpg?raw=true" width="200" height="150"/> 
</p>
 
The second image could be at a bar , but looks more like a fancy bakery or deli with only signal being the high chairs.  

<p float="center">
<img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/bar_0004.jpg?raw=true" width="200" height="150"/>
</p>

The third image also looks more like a Deli or fancy bakery counter. 

<p float="center">
<img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/bar_0528.jpg?raw=true" width="200" height="150"/>
</p>
<p float="center">
<img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/bar_0310.jpg?raw=true" width="200" height="150"/>
</p>
<p style="text-align:justify">The fourth and fifth image strengthens the features in first image and so does the fifth image making them appropriate training images. They contain high chairs , bottles , bar counters and even people.</p>
<p float="center">
 <img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/bar_0080.jpg?raw=true" width="200" height="150" />
</p>

<p style="text-align:justify"> The last image could be bar but could possibly be in the category of gameroom or bowling.
The only strong signal being the high chair , the images of bottles are too small to be learnt.</p>
<p style="text-align:justify">While annotating the images you would notice that only if you can clearly identify why the image belongs to the category you could plausibly expect the algorithm to learn the required features. But , there are possible features that the algorithm picks on that are not visually clear. The quality of features learnt depends on the amount of images supporting the features. But with enough variations of images with supporting features it makes them less likely to overfit to other aspects of the image which will be further discussed. Below are some  things I noticed when reannotating the dataset. 
</p> 


<center>
  

<h2>Incorrect Labels</h2>
<div>
<center>

<p float="center">
  <img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/LOL3.png?raw=true" width="200" height="150" />
  <img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/LOL4.png?raw=true" width="200" height="150"/> 
  <img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/LOL5.png?raw=true" width="200" height="150"/>
</p>
  
  
<p style="text-align:justify">The dataset had some incorrect labels which could also lead to learning some incorrect feature or making it difficult to learn the right features. Above images show some incorrect labels present in the dataset. The first image above was labelled as bedroom, second as auditorium and third as bedroom.</p>

<h2>Multiclass Images</h2>

<p float="center">
 <img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/LOL2.png?raw=true" width="200" height="150" />
  <img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/int36.jpg?raw=true" width="200" height="150"/> 
  <img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/INT69.jpg?raw=true" width="200" height="150"/>
</p>


<div>
<center>
<p style="text-align:justify">Some images do have certain attributes that are labelled as a single class but could possibly attributed to several classes. In the above images , the first image is labelled as a train station but has features that make it suitable for being a part of mall or church. The second has a roof and clock that make it seem more like a trainstation but belongs to staircase class. The third has the finish , lightning and shops akin to a mall but is labelled as staircase.</p>
<h2>Relating Inference Results</h2>

<p style="text-align:justify">Some observations I made after I trained a Alexnet model<a href="#ref3">[3]</a> on the dataset. The inference was stricly performed on the test data.</p>

<h2>Color and Texture</h2>
<p float="center">
 <img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/b20.jpg?raw=true" width="200" height="150" />
<img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/LOL1.png?raw=true" width="200" height="150"/> 
</p>
<div>
<center>
<p style="text-align:justify">In the above example the bedroom was incorrectly classified as a gameroom which could be explained by the large of number of images of pool tables in gameroom category. This could be solved by the right augmentation of colored images in the dataset with several different textures or simply getting more varied data. Similarly there were instances where light bluish and green textures were classifed as hospitals rooms. This could be explained by the large number of images of paramedics with bluish green clothes in the training dataset.</p>

<h3>Brightness</h3>
<p style="text-align:justify">Ensure there are enough bright and dark images of for a given class unless being low lit or bright is a feature of a given category. Most low lit images were classified as a bar or were present in top-3 predictions as almost all bar pictures were low lit.</p>

<h3>Video and Book Store</h3>
<p float="center">
 <img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/9f63b46ad67dbc0868afa77a45d339bb.jpg?token=ABK4NELETILOBZRWATOJ6D267LUJS" width="200" height="150" />
<img src="https://github.com/kamathhrishi/kamathhrishi.github.io/blob/master/_posts/Images/LOL.png?raw=true" width="200" height="150"/> 
</p>
<p style="text-align:justify">There were two different categories called video and book store. Individually observing each of the images gave little or no information on whether racks contained books or video sets. They could instead be combined into a single category.</p>
  
<center>
<h3>Scale of objects</h3>
<p style="text-align:justify">The success of scene recognition depends upon recognizing objects associted with a given scene. When objects are of different scales it can make it harder to learnt the required patterns and also making it hard to generalize during inference. Similarly the scale of features in any classification task need to be similar or the network needs to be exposed to enough images of different scales.</p>
  
<center>
<h2>The End</h2>

<p style="text-align:justify">I first read about this in Andrej Karpathy's <a href="http://karpathy.github.io/2014/09/02/what-i-learned-from-competing-against-a-convnet-on-imagenet/">blogpost</a> on his analysis on ImageNet and thought it was a simple but powerful technique for putting deep learning into practice. Understanding your data is definitely  important but it is also important to have a powerful model architecture and practices to be able to learn from the data. Ideally learning the right features require several different images with variations , which could be possible by gathering more data or by augmentations. Visualizing your dataset would give an first insight as to what your neural network could have possibly learnt. In order to further understand what your network has learnt, you could use various methods developed for the same such as occulsion experiments or deepdream.</p>  

<p style="text-align:justify">I would like to thank my friend Kavin Kumar for reviewing and helping me improve this article</p>

<h3>References</h3>
<p id="ref1" style="text-align:justify">
1. Chiyuan Zhang, Samy Bengio, Moritz Hardt, Benjamin Recht, Oriol Vinyals ,<a href="https://www.google.com/search?client=safari&rls=en&q=1.+Chiyuan+Zhang,+Samy+Bengio,+Moritz+Hardt,+Benjamin+Recht,+Oriol+Vinyals+,+%22Understanding+deep+learning+requires+rethinking+generalization%22&ie=UTF-8&oe=UTF-8">"Understanding deep learning requires rethinking generalization"
<p id="ref2" style="text-align:justify">
2. A. Quattoni, and A.Torralba.<a href="https://ieeexplore.ieee.org/document/5206537">Recognizing Indoor Scenes</a>. IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2009
<p id="ref3" style="text-align:justify">
3. Krizhevsky, Alex; Sutskever, Ilya; Hinton, Geoffrey E. (2017-05-24).<a href="https://ieeexplore.ieee.org/document/5206537">"ImageNet classification with deep convolutional neural networks"</a>. Communications of the ACM. 60 (6): 84–90. doi:10.1145/3065386. ISSN 0001-0782.
</p>

