---
title:  "Deep Learning in Practice-Be the algorithm"
layout: posts
mathjax: "true"
---

<center>
<img src="https://i.stack.imgur.com/bN2iA.png"/>
</center>

<p style="text-align:justify">In conventional machine learning , it required the practinioner to manually look at images/text and decide appropriate features. Deep Learning models are powerful. Powerful enough network that they could just memorize random data without any real correlations [add reference]. This allows us to feed in input/output pairs for some tasks end to end without much preprocessing effort.While , Deep learning gives us the flexibility to learn these features from raw images/text but at the expense of a lot of data. Its not magic it still requires some correlated patterns.This requires you to more or less necessary to understand your training dataset.As the common deep learning phrase goes "Your algorithm is good as your data". Deep learning architectures help extract features relevant to given dataset, part rovided you have enough examples that expose right features.
Manual reannotation is the process of you going through image/text of your dataset and understanding what features exactly define this given image. I din't know what a cloister was until I manually began reannotating my dataset. It just seemed like walls of Stanford University I admired. 
Manually reannotating not only helps remove incorrect labels but also helps understand the biases your algorithm could pick up on or even pick up on certain biases for the algorithm to make training easier. 
  Further it also helps you decide the type of augmentations that could help your algorithm learn from. While its true neural networks are still blackboxes or less interpretable , on a high level there is still some way to understand what they could pick up on or what they are picking up on.</p>
 
<center>
<img height="400px" width="600px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/allIndoors.jpg?token=ABK4NEIT4QMOYRPWLNPZNXK66XJEM">
</center>
<p style="text-align:justify">Let us take an example of the task of Indoor Scene recognition<add reference>. A simple <add reference>Alexnet model was trained on just 5000 images to recognize 67 different scenes , specifically it was trained on the MIT outdoor dataset[add reference link).</p>
  
<p style="text-align:justify">Let us annotate the class bar.Think of what features could possibly define a bar> a bar stoll ,drinks,low lit,wooden furniture,people and some food. Offcourse not just these individual attributes but in the context and depending on the class all or possible some features could exist. Let us collect some images or ensure we have a dataset with these features on which a model could be trained on. Here are some examples which agree upon the definition. </p>

<center>
<div>
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0046.jpg?token=ABK4NEI7XT4UMWWODSI4U6K66XMFA">
<img height="200px" width="200px" 
 src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0528.jpg?token=ABK4NEJYCGTFTOOBLCBC2US66XOXK">
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0310.jpg?token=ABK4NEKCBUANVMJPXH57MOS66XO34">
  </div>
</center>
<div>
<p>Here are some images that are present in the category bar but would'nt make good images for classifying bars. Although they might have certain features and are images taken in bars they seem more like a restaurant. There is also a class called restaurant where these images would instead go. 
<center>
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0194.jpg?token=ABK4NEOUW4RWTT5BCGFZFRC66XQTI">
 <img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0439.jpg?token=ABK4NEMGDL3UVKZBOUM65Q266XQTA">
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0004.jpg?token=ABK4NEMWLYZLVD2I6W7QKVS66XUR2">
</center>
</div>

<h2>Incorrect Annotations</h2>
<p>The above image was labelled as bedroom while the label kitchen or dining room seemed more appropriate. 
<p>The above image was labelled as auditorium while it could belong to category "office".
<p>The above image was labelled as office. I can clearly imagine my perfect neural network just memorizing this image. 
<h2>Confusing Images</h2>
<p>While annotators do try their best to add relevant scenes in the dataset at times it does get confusing for neural networks for learning the right features.</p>
<p>Add staircase example</p>
<p>Add train station example</p>
<p>Computer room and office room</p>
<p>Libing room and bedroom</p>
<p>Corridor and prison</p>
<p>Church inside and bed</p>

<h2>Brightness</h2>
<p>Bar and other images</p>
<h2>Scale of objects</h2>

<h2>Color</h2>
<p>Casino and bed</p>
<p>Hospital and bed</p>

<p>Note that I take no credit for this idea. Its something I came across Andrej Karpathy's blogpost a few years back and was reminded when I read this tweet</p>


