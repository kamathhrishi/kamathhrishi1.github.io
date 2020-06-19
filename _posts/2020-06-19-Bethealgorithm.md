---
title:  "Deep Learning in Practice-Be the algorithm"
layout: posts
mathjax: "true"
---

<p style="text-align:justify">Deep Learning models are very powerful. Infact they are so poweful that a powerful enough network could just memorize random data without any real correlations [add reference]. This allows us to feed in input,output pairs for some task. But ,its not magic it still needs some correlated patterns.In conventional machine learning , it required the practinioner to manually look at several images/test and think of possible features that could possibly define the image. Deep learning gives us the flexibility of learning these features from raw images/text. While that definetly is some great progress , it still helps to manually reannotate every image by yourself and clearly think what the defining features of the category or class is. This not only helps remove incorrect labels but also helps understand the biases your algorithm could pick up on or even pick up on certain biases for the algorithm to make training easier. As the common deep learning phrase goes "Your algorithm is good as your data". Further it also helps you decide the type of augmentations that could help your algorithm learn from. While its true neural networks are blackboxes , on a high level there is still some way to understand what they could pick up on.</p>


<p>Let us take an example of the task of Indoor Scene recognition. A simple Alexnet model was trained on just 5000 images to recongize 67 different scenes , specifically it was trained on the MIT outdoor dataset[add reference link).</p>

<p>You notice that the definining features mostly depended little bit on scenes and mostly on objects</p>
