## K-means algorithm

- Here's the K-means algorithm. The first step is to randomly initialize K cluster centroids, Mu 1 Mu 2, through Mu k. In the example that we had, this corresponded to when we randomly chose a location for the red cross and for the blue cross corresponding to the two cluster centroids. In our example, K was equal to two. If the red cross was cluster centroid one and the blue cross was cluster centroid two.

<img width="1832" height="809" alt="image" src="https://github.com/user-attachments/assets/c204414a-5410-4b98-be0c-7c0877f2d3c3" />

- These are just two indices to denote the first and the second cluster. Then the red cross would be the location of Mu 1 and the blue cross would be the location of Mu 2. Just to be clear, Mu 1 and Mu 2 are vectors which have the same dimension as your training examples, X1 through say X30, in our example.
- All of these are lists of two numbers or they're two-dimensional vectors or whatever dimension the training data had. We had n equals two features for each of the training examples then Mu 1 and Mu 2 will also be two-dimensional vectors, meaning vectors with two numbers in them.
- Having randomly initialized the K cluster centroids, K-means will then repeatedly carry out the two steps that you saw in the last video. The first step is to assign points to clusters, centroids, meaning color, each of the points, either red or blue, corresponding to assigning them to cluster centroids one or two when K is equal to two.
- That means that we're going to, for I equals one through m for all m training examples, we're going to set c^i to be equal to the index, which can be anything from one to K of the cluster centroid closest to the training example x^i
- Mathematically you can write this out as computing the distance between x^i and Mu k. In math, the distance between two points is often written like this. It is also called the L2 norm.

<img width="1919" height="938" alt="image" src="https://github.com/user-attachments/assets/73fb19d9-57f1-43c8-a21f-ecf36f461de7" />

- What you want to find is the value of k that minimizes this, because that corresponds to the cluster centroid Mu k that is closest to the training example x^i. Then the value of k that minimizes this is what gets set to c^i.
- When you implement this algorithm, you find that it's actually a little bit more convenient to minimize the squared distance because the cluster centroid with the smallest square distance should be the same as the cluster centroid with the smallest distance.
- When you look at this week's optional labs and practice labs, you see how to implement this in code for yourself. As a concrete example, this point up here is closer to the red or two cluster centroids 1. If this was training example x^1, we will set c^1 to be equal to 1.
- Whereas this point over here, if this was the 12th training example, this is closer to the second cluster centroids the blue one. We will set this, the corresponding cluster assignment variable to two because it's closer to cluster centroid 2. That's the first step of the K-means algorithm, assign points to cluster centroids.

<img width="1919" height="925" alt="image" src="https://github.com/user-attachments/assets/fce987d4-94c8-4061-85fa-295ccc45246d" />

---

- The second step is to move the cluster centroids. What that means is for lowercase k equals 1 to capital K, the number of clusters. We're going to set the cluster centroid location to be updated to be the average or the mean of the points assigned to that cluster k.
- what that means is, we'll look at all of these red points, say, and look at their position on the horizontal axis and look at the value of the first feature x^1, and average that out. Compute the average value on the vertical axis as well. After computing those two averages, you find that the mean is here, which is why Mu 1, that is the location that the red cluster centroid gets updated as follows.
- Similarly, we will look at all of the points that were colored blue, that is, with c^i equals 2 and computes the average of the value on the horizontal axis, the average of their feature x1. Compute the average of the feature x2. Those two averages give you the new location of the blue cluster centroid, which therefore moves over here. 

<img width="1919" height="936" alt="image" src="https://github.com/user-attachments/assets/3b6a7033-bd29-4272-90dd-0aa8a3685759" />

- Just to write those out in math. If the first cluster has assigned to it training examples 1,5,6,10. Just as an example. Then what that means is you will compute the average this way. Notice that x^1, x^5, x^6, and x^10 are training examples.
- Four training examples, so we divide by 4 and this gives you the new location of Mu1, the new cluster centroid for cluster 1. To be clear, each of these x values are vectors with two numbers in them, or n numbers in them if you have n features, and so Mu will also have two numbers in it or n numbers in it if you have n features instead of two

<img width="1919" height="949" alt="image" src="https://github.com/user-attachments/assets/832811c9-96da-4552-bd18-0bb409b004d1" />

- Now, there is one corner case of this algorithm, which is what happens if a cluster has zero training examples assigned to it. In that case, the second step, Mu k, would be trying to compute the average of zero points. That's not well-defined. If that ever happens, the most common thing to do is to just eliminate that cluster. You end up with K minus 1 clusters.

<img width="1919" height="925" alt="image" src="https://github.com/user-attachments/assets/ca3d1412-d503-4832-81d1-a1ce72740604" />

- Or if you really, really need K clusters an alternative would be to just randomly reinitialize that cluster centroid and hope that it gets assigned at least some points next time round. But it's actually more common when running K-means to just eliminate a cluster if no points are assigned to it.
- Even though I've mainly been describing K-means for clusters that are well separated. Clusters that may look like this. Where if you asked her to find three clusters, hopefully they will find these three distinct clusters.
- It turns out that K-means is also frequently applied to data sets where the clusters are not that well separated. For example, if you are a designer and manufacturer of cool t-shirts, and you want to decide, how do I size my small, medium, and large t-shirts.

<img width="1919" height="940" alt="image" src="https://github.com/user-attachments/assets/597b96d7-d023-4360-955b-7a131b1ede16" />

- How small should a small be, how large should a large be, and what should a medium-size t-shirt really be? One thing you might do is collect data of people likely to buy your t-shirts based on their heights and weights. You find that the height and weight of people tend to vary continuously on the spectrum without some very clear clusters.
- Nonetheless, if you were to run K-means with say, three clusters centroids, you might find that K-means would group these points into one cluster, these points into a second cluster, and these points into a third cluster. If you're trying to decide exactly how to size your small, medium, and large t-shirts, you might then choose the dimensions of your small t-shirt to try to make it fit these individuals well.
- The medium-size t-shirt to try to fit these individuals well, and the large t-shirt to try to fit these individuals well with potentially the cluster centroids giving you a sense of what is the most representative height and weight that you will want your three t-shirt sizes to fit
- This is an example of K-means working just fine and giving a useful results even if the data does not lie in well-separated groups or clusters.

<img width="1919" height="931" alt="image" src="https://github.com/user-attachments/assets/1142d6f5-4067-4ed5-993c-aa0c359240b8" />

- That was the K-means clustering algorithm. Assign cluster centroids randomly and then repeatedly assign points to cluster centroids and move the cluster centroids. But what this algorithm really doing and do we think this algorithm will converge or they just keep on running forever and never converge.

---

## Optimization Objective

