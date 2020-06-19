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
  Further it also helps you decide the type of augmentations that could help your algorithm learn from. While its true neural networks are still blackboxes or less interpretable , on a high level there is still some way to understand what they could pick up on or what they are picking up on.
 
<center>
<img height="400px" width="600px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/allIndoors.jpg?token=ABK4NEIT4QMOYRPWLNPZNXK66XJEM">
</center>
<p style="text-align:justify">Let us take an example of the task of Indoor Scene recognition<add reference>. A simple <add reference>Alexnet model was trained on just 5000 images to recognize 67 different scenes , specifically it was trained on the MIT outdoor dataset[add reference link).
  
<p style="text-align:justify">Let us annotate the class bar.Think of what features could possibly define bar:bar stoll ,drinks,low lit,wooden furniture,people and some food. Offcourse not just these individual attributes but in the context and depending on the class all or possible some features could exist. Let us collect some images or ensure we have a dataset with these features on which a model could be trained on. Here are some examples which agree upon the definition.

<center>
<div>
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0046.jpg?token=ABK4NEI7XT4UMWWODSI4U6K66XMFA">
<img height="200px" width="200px" 
 src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0528.jpg?token=ABK4NEJYCGTFTOOBLCBC2US66XOXK">
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0310.jpg?token=ABK4NEKCBUANVMJPXH57MOS66XO34">
<div>
<p style="text-align:justify">Here are some images that are present in the category bar but would'nt make good images for classifying bars. Although they might have certain features and are images taken in bars they seem more like a restaurant or a deli.The dataset also has classes called restaurant and deli making it harder to learn both the classes. 
<center>
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0194.jpg?token=ABK4NEOUW4RWTT5BCGFZFRC66XQTI">
 <img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0439.jpg?token=ABK4NEMGDL3UVKZBOUM65Q266XQTA">
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/bar_0004.jpg?token=ABK4NEMWLYZLVD2I6W7QKVS66XUR2">

<h2>Incorrect Annotations</h2>
<div>
<center>
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/homeoff005.jpg?token=ABK4NEOKRBNEJXCLLSXD7S266XVM6">
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/serre43_173.jpg?token=ABK4NEOHIOBNNKKGRFXOXAC66XVNE">
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/dsc04183.jpg?token=ABK4NEIUUSOXHTYFFHAXTGS66XVPE">
  
<p style="text-align:justify">The datase had some incorrect classes which could also lead to learning some incorrect feature or making it difficult to learn the right features.Above images show some incorrect labels present in the dataset.The first image above was labelled as bedroom, second as auditorium and third as bedroom.</p>

<h2>Multiclass Images</h2>

<div>
<center>
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/train_station_34_15_altavista.jpg?token=ABK4NEJSDFUIXKZPKCIEPUK66X5SO">
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/int36.jpg?token=ABK4NEO23YIJXDMW7Y7SWHK66X6OS">
<img height="200px" width="200px" src="https://raw.githubusercontent.com/kamathhrishi/kamathhrishi.github.io/master/_posts/Images/INT69.jpg?token=ABK4NEKJW3DMDWEXZ57ZL3C66X5X2">

<p style="text-align:justify">Some images do have certain attributes that are labelled as a single class but could possibly attributed to several classes. In the above image , the first image could possibly be a part of a church , airport , train station or a mall. The second could classified as a staircase , mall or airport. The second being staircase and a train station.</p>

<h2>Brightness</h2>
<p>Bar and other images</p>
<h2>Scale of objects</h2>

<h2>Color</h2>
<p>Casino and bed</p>
<p>Hospital and bed</p>

<p>Note that I take no credit for this idea. Its something I came across Andrej Karpathy's blogpost a few years back and was reminded when I read this tweet</p>


