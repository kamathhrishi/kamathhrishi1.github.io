---
title:  "Deep Learning in Practice-Be the algorithm"
layout: posts
mathjax: "true"
summary:  "Manual reannotation is the process of you going through image/text of your dataset and understanding what features exactly define this given image. Manually reannotating not only helps remove incorrect labels but also helps understand biases your algorithm could pick up on or even helps you pick up on certain data for the algorithm to make training easier."
---

<p style="text-align:justify">Conventional machine learning required the practinioner to manually look at images/text and handcraft appropriate features. Deep Learning models are powerful. Powerful enough that they could just memorize random data without any real correlations [1]. This allows us to feed in input/output pairs for some tasks end to end without much preprocessing effort giving us the flexibility to learn features from raw images/text but at the expense of a lot of data.</p>
<img height="400px" width="600px" src="https://i.stack.imgur.com/bN2iA.png">
<p style="text-align:justify">Its not magic it still needs some correlated patterns to generalize and learn required features. This requires you to more or less understand your training dataset. As the common machine learning phrase goes "Your algorithm is good as your data". Deep learning models help extract features relevant to given dataset, provided you have enough examples that expose right features.
 <b>Manual reannotation</b> is the process of you going through image/text of your dataset and understanding what features exactly define this given image. 
 Manually reannotating not only helps <b>remove incorrect labels</b> but also helps <b>understand biases</b> your algorithm could pick up on or even helps you <b>understand neural network predictions</b> to an certain extent. Further it also helps you decide the type of <b>augmentations</b> that could help your algorithm generalize or help you pick up on certain data for the algorithm to make training easier. While its true neural networks are still blackboxes or less interpretable but on a high level there are still ways to understand what they learned from the dataset.</p>

<center>

<img height="400px" width="600px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/allIndoors.jpg?token=ABK4NEIT4QMOYRPWLNPZNXK66XJEM">
</center>
<p style="text-align:justify">I would like to take an example of manually reannotating a dataset for a computer vision classification task <b>Indoor Scene Recognition</b>. The dataset consists of around only 5000 images of 67 different classes [2].</p>
  
<p style="text-align:justify">Let us annotate the class bar. Think of what features could possibly define bar: high chairs , drinks , bottles , low lit , bar counters , people and some food. Offcourse not just these individual attributes but in the context. Depending on the class all or some features could exist for the image to satisfy requirement of the label. Let us look at a few sample images which are labelled as bar in the scene recognition dataset and decide how to eliminate or keep them based on the features we would want to define a bar.
<div>

<img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0310.jpg?token=ABK4NEKCBUANVMJPXH57MOS66XO34" width="200" height="150"/>

<p style="text-align:justify">
The first image meets our definition of a bar : high chairs [check], drinks [check] and bar counter[check]. Although to be able to generalize these features you would need several different variations of the image , to name a few images with bartender , people taking a drink and different shades of furnitures. 
<p float="center">
<img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0439.jpg?token=ABK4NEMGDL3UVKZBOUM65Q266XQTA" width="200" height="150"/> 
</p>
 
The second image could be at a bar , but looks more like a fancy bakery or deli with only signal being the high chairs.  

<p float="center">
<img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0004.jpg?token=ABK4NEMWLYZLVD2I6W7QKVS66XUR2" width="200" height="150"/>
</p>

The third image also looks more like a Deli or fancy bakery counter. 

<p float="center">
<img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0528.jpg?token=ABK4NEJYCGTFTOOBLCBC2US66XOXK" width="200" height="150"/>
</p>

The fourth image strengthens the features in first image and so does the fifth image making them appropriate training images. 

<p float="center">
 <img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0080.jpg?token=ABK4NEJ4AHCGDLM5HHDYGYC6652QE" width="200" height="150" />
</p>

<p style="text-align:justify"> The last image could be bar but could possibly be in the category of gameroom or bowling.
The only strong signal being the high chair , the images of bottles are too small to be learnt.</p>
<p style="text-align:justify">While annotating the images you would notice that only if you can clearly identify why the image belongs to the category you could plausibly expect the algorithm to learn the required features. But , its not necessary at times there would be features that aren't very clear at the first look. The quality of features learnt depends on the amount of images supporting the features with enough variations that don't make them overfit to other aspects of the image which will be further discussed. Below are some  things I noticed when reannotating the dataset. 
</p> 


<center>
  

<h2>Incorrect Labels</h2>
<div>
<center>

<p float="center">
  <img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/homeoff005.jpg?token=ABK4NEOKRBNEJXCLLSXD7S266XVM6" width="200" height="150" />
  <img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/serre43_173.jpg?token=ABK4NEOHIOBNNKKGRFXOXAC66XVNE" width="200" height="150"/> 
  <img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/dsc04183.jpg?token=ABK4NEIUUSOXHTYFFHAXTGS66XVPE" width="200" height="150"/>
</p>
  
  
<p style="text-align:justify">The dataset had some incorrect labels which could also lead to learning some incorrect feature or making it difficult to learn the right features. Above images show some incorrect labels present in the dataset. The first image above was labelled as bedroom, second as auditorium and third as bedroom.</p>

<h2>Multiclass Images</h2>

<p float="center">
 <img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/train_station_34_15_altavista.jpg?token=ABK4NEJSDFUIXKZPKCIEPUK66X5SO" width="200" height="150" />
  <img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/int36.jpg?token=ABK4NEIAD4UCOLTKPTHSPYC665OGQ" width="200" height="150"/> 
  <img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/INT69.jpg?token=ABK4NEKJW3DMDWEXZ57ZL3C66X5X2" width="200" height="150"/>
</p>


<div>
<center>
<p style="text-align:justify">Some images do have certain attributes that are labelled as a single class but could possibly attributed to several classes. In the above images , the first image is labelled as a train station but has features that it suitable for being a part of mall or church. The second has a roof and clock that make it seem more like a trainstation but belongs to staircase class. The third has the finish , lightning and shops akin to a mall but is labelled as staircase.</p>
<h2>Relating Inference Results</h2>

<p style="text-align:justify">Some observations I made after I trained a Alexnet model[3] on the dataset. The inference was stricly performed on the test data.</p>

<h2>Color and Texture</h2>
<p float="center">
 <img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/b20.jpg?token=ABK4NEOIFJ4KJJGWFUD23PK66YL7W" width="200" height="100" />
<img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/sala_de_juegos_13_14_altavista.jpg?token=ABK4NEI5FKUX343SLSCH5NS66YMZK2" width="200" height="150"/> 
</p>
<div>
<center>
<p style="text-align:justify">In the above example the bedroom was incorrectly classified as a gameroom which could be explained by the large of number of images of pool tables in gameroom category. This could be solved by the right augmentation of colored images in the dataset with several different textures or simply getting more varied data. Similarly there were insatnces where textures light bluish green textures were classifed as hospitals rooms as there were images of paramedics with bluish green clothes.</p>
 

<h3>Brightness</h3>
<p style="text-align:justify">Ensure there are enough bright and dark images of for a given class unless being low lit or bright is a feature of a given category. Most low lit images were classified as a bar or were present in top-3 predictions as almost all bar pictures were low lit.</p>

<h3>Video and Book Store</h3>
<p float="center">
 <img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bookstore_02_03_flickr.jpg?token=ABK4NENJN5PU36BUDWWHJRS666F2O" width="200" height="150" />
<img src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/blockbuster_24_07_altavista.jpg?token=ABK4NEIJBWZ65QC5DD6Y252666F4A" width="200" height="150"/> 
</p>
<p style="text-align:justify">There were two different categories called video and book store. Individually observing each of the images gave little or no information on whether racks contained books or video sets. They could instead be combined into a single category.</p>
  
<center>
<h3>Scale of objects</h3>
<p style="text-align:justify">The sucess of scene recognition depends upon recognizing objects associted with a given scene. When objects are of different scales it can make it harder to learnt the required patterns and also making it hard to generalize during inference. Similarly the scale of features in any classification task need to be similar or the network needs to be exposed to enough images of different scales.</p>
  

<p style="text-align:justify">I first read about this in Andrej Karpathy's blogpost on his analysis on ImageNet and thought it was a simple but powerful technique for putting deep learning into practice.</p>  


<h3>References</h3>
<p style="text-align:justify">
1. Chiyuan Zhang, Samy Bengio, Moritz Hardt, Benjamin Recht, Oriol Vinyals , "Understanding deep learning requires rethinking generalization" 
</p>
<p style="text-align:justify">
2. A. Quattoni, and A.Torralba. Recognizing Indoor Scenes. IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2009
</p>
<p style="text-align:justify">
3. Krizhevsky, Alex; Sutskever, Ilya; Hinton, Geoffrey E. (2017-05-24). "ImageNet classification with deep convolutional neural networks". Communications of the ACM. 60 (6): 84–90. doi:10.1145/3065386. ISSN 0001-0782.
</p>

