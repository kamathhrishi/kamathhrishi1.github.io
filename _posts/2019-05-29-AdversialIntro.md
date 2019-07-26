---
title:  "Introduction to Adversial Examples"
layout: posts
---

<p style="text-align:justify">Look at these two images</p>
<center>
<img src="https://pbs.twimg.com/media/DzIyOyEWwAAOxWv.jpg">
<img height="224" width="224" src="http://williamcalvin.com/portraits/gibbon/Lar%20Gibbon%20female%20Jane%20Twycross%20012s.jpg">
</center>
<p style="text-align:justify"> You can clearly distinguish what a Gibbon and a panda are. Even Convolution Neural Networks (CNN) can :) . There seems like no problem except we would like it to make the neural network prediction as confident as possible. Now look at these two images do you notice any difference?  </p>
<center>
<img src="https://pbs.twimg.com/media/DzIyOyEWwAAOxWv.jpg">
<img src="https://pbs.twimg.com/media/DzIyOyEWwAAOxWv.jpg">
</center>
<p style="text-align:justify">Now it gets scary when your model predicts this slightly perturbated image of a panda as a gibbon with 99.3% confidence and predicts the original image as a panda with just 55% confidence. We term these as adversial examples , which has questioned the fundamental aspects of what neural networks actually learn and their capabilities. This can be especially dangerous considering how widespread neural networks are. </p>
<p style="text-align:justify">This was first discovered by Christian Szegedy in 2014</p>
<p><a href=""></a>
<p style="text-align:justify">The upside of adversial examples are they can be used as training data making your neural networks generalize better.</p>
<p>I will show you a pytorch implementating of adversial examples and other possible adversial attacks in another tutorial</p>
