---
title:  "Deep Learning in Practice-Be the algorithm"
layout: posts
mathjax: "true"
---

<p style="text-align:justify">Deep Learning models are very powerful.Powerful enough network that they could just memorize random data without any real correlations [add reference]. This allows us to feed in input/output pairs for some tasks end to end without much preprocessing effort. But ,its not magic it still needs some correlated patterns.In conventional machine learning , it required the practinioner to manually look at images/test and think of possible features that could possibly define the image. Deep learning gives us the flexibility to learn these features from raw images/text but at the expensive of a lot of data. This still requires you to more or less necessary to understand your training dataset. Also the common deep learning phrase goes "Your algorithm is good as your data". Deep learning architectures help extract the required features , these features are still highly dependent on how your input data is presented and the amount of data which expose the features in the right manner. 
Manually reannotating not only helps remove incorrect labels but also helps understand the biases your algorithm could pick up on or even pick up on certain biases for the algorithm to make training easier. Further it also helps you decide the type of augmentations that could help your algorithm learn from. While its true neural networks are still blackboxes or less interpretable , on a high level there is still some way to understand what they could pick up on or what they are picking up on.</p>

<p style="text-align:justify">Let us take an example of the task of Indoor Scene recognition<add reference>. A simple <add reference>Alexnet model was trained on just 5000 images to recognize 67 different scenes , specifically it was trained on the MIT outdoor dataset[add reference link).</p>

<h2>Incorrect Annotations</h2>

<p>Add staircase example</p>
<p>Add train station example</p>
<p>While annotators do try their best to add relevant scenes in the dataset at times it does get confusing for neural networks for learning the right features.</p>

<h2>Confusing Images</h2>

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

