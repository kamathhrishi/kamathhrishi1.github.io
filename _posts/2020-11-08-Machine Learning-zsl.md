---
title:  "Machine Learning-Learning to predict classes not seen during training"
layout: posts
---

<p style="text-align:justify">In conventional machine learning we train an algorithm on data/classes pairs (supervised learning) and make 
predictions or train an algorithm only on raw data(Unsuperviseed learning).But , can we possible train an algorihtm to make the right predictions on data its never seen before.
That is can a dog/cat classifier be able to predict a tiger or a mouse? It is quite possible , the specific technique is called zero shot learning. In the blogpost I would like to 
cover what zero shot learning is , its working and limitations.
</p>

<h2>Supervised Learning</h2>
<img src="https://static.javatpoint.com/tutorial/machine-learning/images/supervised-machine-learning.png"></img>
<p>In conventional supervised learning , we have a 
