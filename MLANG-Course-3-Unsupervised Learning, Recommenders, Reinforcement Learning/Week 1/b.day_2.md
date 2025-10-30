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

- It turns out that the K-means algorithm that you saw in the last video is also optimizing a specific cost function. Although the optimization algorithm that it uses to optimize that is not gradient descent is actually the algorithm that you already saw in the last video.
- Let's take a look at what all this means. Let's take a look at what is the cost function for K-means, to get started as a reminder this is a notation we've been using whereas CI is the index of the cluster. So CI is some number from one to K of the index of the cluster to which training example XI is currently assigned and new K is the location of cluster centroid k.
- Let me introduce one more piece of notation, which is when lower case K equals CI. So mu subscript CI is the cluster centroid of the cluster to which example XI has been assigned.
- So for example, if I were to look at some training example C train example 10 and I were to ask What's the location of the clustering centroids to which the 10th training example has been assigned? Well, I would then look up C10. This will give me a number from one to K.
- That tells me was example 10 assigned to the red or the blue or some other cluster centroid, and then mu subscript C- 10 is the location of the cluster centroid to which extent has been assigned. So armed with this notation, let me now write out the cost function that K means turns out to be minimizing.
- The cost function J, which is a function of C1 through CM. These are all the assignments of points to clusters Androids as well as new one through mu capsule K. These are the locations of all the clusters centroid is defined as this expression on the right.
- It is the average, so one over M some from i equals to m of the squared distance between every training example XI as I goes from one through M it is a square distance between X I. And Mu subscript Ci. So this quantity up here, in other words, the cost function good for K is the average squared distance between every training example XI. And the location of the cluster centroid to which the training example Xi has been assigned.
- So for this example up here we've been measuring the distance between X10 and mu subscript C10. The cluster centroid to which X10 has been assigned and taking the square of that distance and that would be one of the terms over here that we're averaging over.
- And it turns out that what the K means algorithm is doing is trying to find assignments of points of clusters centroid as well as find locations of clusters centroid that minimizes the squared distance.

<img width="1919" height="948" alt="image" src="https://github.com/user-attachments/assets/8cb482ea-b693-4702-9268-41972976f7f8" />

- Visually, here's what you saw part way into the run of K means in the earlier video. And at this step the cost function. If you were to compute it would be to look at everyone at the blue points and measure these distances and compute square. And then also similarly look at every one of the red points and compute these distances and compute the square.
- And then the average of the squares of all of these differences for the red and the blue points is the value of the cost function J, at this particular configuration of the parameters for K-means. And what they will do on every step is try to update the cluster assignments C1 through C30 in this example

<img width="1919" height="947" alt="image" src="https://github.com/user-attachments/assets/5b068a88-66f0-4a1f-8634-d6eac8cd2b14" />

- Or update the positions of the cluster centers, Mu1 and Mu2. In order to keep on reducing this cost function J. By the way, this cost function J also has a name in the literature is called the distortion function.
- If you hear someone talk about the key news algorithm and the distortion or the distortion cost function, that's just what this formula J is computing.

<img width="1919" height="952" alt="image" src="https://github.com/user-attachments/assets/7ce84518-f562-4271-8faf-ef40deb65cd4" />

- Let's now take a deeper look at the algorithm and why the algorithm is trying to minimize this cost function J. Or why is trying to minimize the distortion here on top of copied over the cost function from the previous slide. It turns out that the first part of K means where you assign points to cluster centroid. That turns out to be trying to update C1 through CM.
- To try to minimize the cost function J as much as possible while holding mu one through mu K fix. And the second step, in contrast where you move the custom centroid, it turns out that is trying to leave C1 through CM fix. But to update new one through mu K to try to minimize the cost function or the distortion as much as possible.
- Let's take a look at why this is the case. During the first step, if you want to choose the values of C1 through CM or save a particular value of Ci to try to minimize this. Well, what would make Xi minus mu CI as small as possible? This is the distance or the square distance between a training example XI. And the location of the class is central to which has been assigned.
- So if you want to minimize this distance or the square distance, what you should do is assign XI to the closest cluster centroid. So to take a simplified example, if you have two clusters centroid say close to central is one and two and just a single training example, XI.
- If you were to sign it to cluster centroid one, this square distance here would be this large distance, well squared. And if you were to assign it to cluster centroid 2 then this square distance would be the square of this much smaller distance. So if you want to minimize this term, you will take X I and assign it to the closer centroid, which is exactly what the algorithm is doing up here.
- So that's why the step where you assign points to a cluster centroid is choosing the values for CI to try to minimize J. Without changing, we went through the mu K for now, but just choosing the values of C1 through CM to try to make these terms as small as possible. How about the second step of the K-means algorithm that is to move to clusters centroids? It turns out that choosing mu K to be average and the mean of the points assigned is the choice of these terms mu that will minimize this expression.

<img width="1919" height="950" alt="image" src="https://github.com/user-attachments/assets/1c79ccf9-8b1d-4067-bae7-d46496dbcb12" />

- To take a simplified example, say you have a cluster with just two points assigned to it shown as follows. And so with the cluster centroid here, the average of the square distances would be a distance of one here squared plus this distance here, which is 9 squared.
- And then you take the average of these two numbers. And so that turns out to be one half of 1 plus 81, which turns out to be 41.
- But if you were to take the average of these two points, so 1+ 11/2, that's equal to 6. And if you were to move the cluster centroid over here to middle than the average of these two square distances, turns out to be a distance of five and five here. So you end up with one half of 5 squared plus 5 squared, which is equal to 25.
- And this is a much smaller average squared distance than 41. And in fact, you can play around with the location of this cluster centroid and maybe convince yourself that taking this mean location. This average location in the middle of these two training examples, that is really the value that minimizes the square distance. So the fact that the K-means algorithm is optimizing a cost function J means that it is guaranteed to converge, that is on every single iteration.

<img width="1919" height="942" alt="image" src="https://github.com/user-attachments/assets/3154207c-2620-47b7-917e-3886d9984415" />

- The distortion cost function should go down or stay the same, but if it ever fails to go down or stay the same, in the worst case, if it ever goes up. That means there's a bug in the code, it should never go up because every single step of K means is setting the value CI and mu K to try to reduce the cost function. Also, if the cost function ever stops going down, that also gives you one way to test if K means has converged.
- Once there's a single iteration where it stays the same. That usually means K means has converged and you should just stop running the algorithm even further or in some rare cases you will run K means for a long time. And the cost function of the distortion is just going down very, very slowly, and that's a bit like gradient descent where maybe running even longer might help a bit
- But if the rate at which the cost function is going down has become very, very slow. You might also just say this is good enough. I'm just going to say it's close enough to convergence and not spend even more compute cycles running the algorithm for even longer. So these are some of the ways that computing the cost function is helpful helps you figure out if the algorithm has converged.
- It turns out that there's one other very useful way to take advantage of the cost function, which is to use multiple different random initialization of the cluster centroid. It turns out if you do this, you can often find much better clusters using K means

---

- The very first step of the K means clustering algorithm, was to choose random locations as the initial guesses for the cluster centroids mu one through mu K. But how do you actually take that random guess.
- Let's take a look at that in this video, as well as how you can take multiple attempts at the initial guesses with mu one through mu K. That will result in your finding a better set of clusters. Let's take a look, here again is the K means algorithm and in this video let's take a look at how you can implement this first step.
- When running K means you should pretty much always choose the number of cluster centroids K to be lessened to training examples m. It doesn't really make sense to have K greater than m because then there won't even be enough training examples to have at least one training example per cluster centroids.
- So in our earlier example we had K equals two and m equals 30. In order to choose the cluster centroids, the most common way is to randomly pick K training examples. So here is a training set where if I were to randomly pick two training examples, maybe I end up picking this one and this one.
- And then we would set new one through mu K equal to these K training examples. So I might initialize my red cluster centroid here, and initialize my blue cluster centroids over here, in the example where K was equal to two. And it turns out that if this was your random initialization and you were to run K means you pray end up with K means deciding that these are the two classes in the data set
- Notes that this method of initializing the cost of central is a little bit different than what I had used in the illustration in the earlier videos.
- Where I was initializing the cluster centroids mu one and mu two to be just random points rather than sitting on top of specific training examples. I've done that to make the illustrations clearer in the earlier videos. But what I'm showing in this slide is actually a much more commonly used way of initializing the clusters centroids.
- Now with this method there is a chance that you end up with an initialization of the cluster centroids where the red cross is here and maybe the blue cross is here. And depending on how you choose the random initial central centroids K-means will end up picking a difference set of causes for your data set.

<img width="1919" height="940" alt="image" src="https://github.com/user-attachments/assets/7877bde4-ca31-45d2-b7c4-e43422594e48" />

- Let's look at a slightly more complex example, where we're going to look at this data set and try to find three clusters so k equals three in this data. If you were to run K means with one random initialization of the cluster centroid, you may get this result up here and this looks like a pretty good choice.
- Pretty good clustering of the data into three different clusters. But with a different initialization, say you had happened to initialize two of the cluster centroids within this group of points. And one within this group of points, after running k means you might end up with this clustering, which doesn't look as good. And this turns out to be a local optima, in which K-means is trying to minimize the distortion cost function, that cost function J of C one through CM and mu one through mu K that you saw in the last video.
- But with this less fortunate choice of random initialization, it had just happened to get stuck in a local minimum. And here's another example of a local minimum, where a different random initialization course came in to find this clustering of the data into three clusters, which again doesn't seem as good as the one that you saw up here on top.
- So if you want to give k means multiple shots at finding the best local optimum. If you want to try multiple random initialization, so give it a better chance of finding this good clustering up on top. One other thing you could do with the K-means algorithm is to run it multiple times and then to try to find the best local optima. And it turns out that if you were to run k means three times say, and end up with these three distinct clusterings.
- Then one way to choose between these three solutions, is to compute the cost function J for all three of these solutions, all three of these choices of clusters found by k means. And then to pick one of these three according to which one of them gives you the lowest value for the cost function J.
- And in fact, if you look at this grouping of clusters up here, this green cross has relatively small square distances, all the green dots. The red cross is relatively small distance and red dots and similarly the blue cross.
- And so the cost function J will be relatively small for this example on top. But here, the blue cross has larger distances to all of the blue dots. And here the red cross has larger distances to all of the red dots, which is why the cost function J, for these examples down below would be larger. Which is why if you pick from these three options, the one with the smallest distortion of the smallest cost function J
- You end up selecting this choice of the cluster centroids. So let me write this out more formally into an algorithm, and wish you would run K-means multiple times using different random initialization. 

<img width="1919" height="932" alt="image" src="https://github.com/user-attachments/assets/a4fbb941-8b42-4170-ad6b-d71d0cb99fd6" />

- Here's the algorithm, if you want to use 100 random initialization for K-means, then you would run 100 times randomly initialized K-means using the method that you saw earlier in this video.
- Pick K training examples and let the cluster centroids initially be the locations of those K training examples. Using that random initialization, run the K-means algorithm to convergence. And that will give you a choice of cluster assignments and cluster centroids. And then finally, you would compute the distortion compute the cost function as follows. 
- After doing this, say 100 times, you would finally pick the set of clusters, that gave the lowest cost. And it turns out that if you do this will often give you a much better set of clusters, with a much lower distortion function than if you were to run K means only a single time. I plugged in the number up here as 100. 
- When I'm using this method, doing this somewhere between say 50 to 1000 times would be pretty common. Where, if you run this procedure a lot more than 1000 times, it tends to get computational expensive.
- And you tend to have diminishing returns when you run it a lot of times. Whereas trying at least maybe 50 or 100 random initializations, will often give you a much better result than if you only had one shot at picking a good random initialization.
- But with this technique you are much more likely to end up with this good choice of clusters on top. And these less superior local minima down at the bottom. So that's it, when I'm using the K means algorithm myself, I will almost always use more than one random initialization.

<img width="1919" height="944" alt="image" src="https://github.com/user-attachments/assets/f314259c-9c1e-494a-baf5-7f9bf82a2948" />

- Because it just causes K means to do a much better job minimizing the distortion cost function and finding a much better choice for the cluster centroids. Before we wrap up our discussion of K means, there's just one more video in which I hope to discuss with you. The question of how do you choose the number of clusters centroids? How do you choose the value of K?

---

## Choosing the Number of Clusters

- The k-means algorithm requires as one of its inputs, k, the number of clusters you want it to find, but how do you decide how many clusters to used. Do you want two clusters or three clusters of five clusters or 10 clusters? Let's take a look.
- For a lot of clustering problems, the right value of K is truly ambiguous. If I were to show different people the same data set and ask, how many clusters do you see? There will definitely be people that will say, it looks like there are two distinct clusters and they will be right. There would also be others that will see actually four distinct clusters.
- They would also be right. Because clustering is unsupervised learning algorithm you're not given the quote right answers in the form of specific labels to try to replicate. There are lots of applications where the data itself does not give a clear indicator for how many clusters there are in it.

<img width="1919" height="936" alt="image" src="https://github.com/user-attachments/assets/8143b004-ec98-453e-9d91-f0f95c042eb0" />

- If you look at the academic literature on K-means, there are a few techniques to try to automatically choose the number of clusters to use for a certain application. I'll briefly mention one here that you may see others refer to.
- But one way to try to choose the value of K is called the elbow method and what that does is you would run K-means with a variety of values of K and plot the cost function or the distortion function J as a function of the number of clusters.
- What you find is that when you have very few clusters, say one cluster, the distortion function or the cost function J will be high and as you increase the number of clusters, it will go down, maybe as follows. and if the curve looks like this, you say, well, it looks like the cost function is decreasing rapidly until we get to three clusters but the decrease is more slowly after that.
- Let's choose K equals 3 and this is called an elbow, by the way, because think of it as analogous to that's your hand and that's your elbow over here. Plotting the cost function as a function of K could help, it could help you gain some insight. I personally hardly ever use the the elbow method myself to choose the right number of clusters because I think for a lot of applications, the right number of clusters is truly ambiguous and you find that a lot of cost functions look like this with just decreases smoothly and it doesn't have a clear elbow by wish you could use to pick the value of K.
- One technique that does not work is to choose K so as to minimize the cost function J because doing so would cause you to almost always just choose the largest possible value of K because having more clusters will pretty much always reduce the cost function J. Choosing K to minimize the cost function J is not a good technique.

<img width="1919" height="942" alt="image" src="https://github.com/user-attachments/assets/fecc7c56-548c-40b5-acd3-89479b9475d4" />

- How do you choose the value of K and practice? Often you're running K-means in order to get clusters to use for some later or some downstream purpose. That is, you're going to take the clusters and do something with those clusters. What I usually do and what I recommend you do is to evaluate K-means based on how well it performs for that later downstream purpose.
- Let me illustrate to the example of t-shirt sizing. One thing you could do is run K-means on this data set to find the clusters, in which case you may find clusters like that and this would be how you size your small, medium, and large t-shirts, but how many t-shirt sizes should there be? Well, it's ambiguous.
- If you were to also run K-means with five clusters, you might get clusters that look like this. This will let shoe size t-shirts according to extra small, small, medium, large, and extra large. Both of these are completely valid and completely fine groupings of the data into clusters, but whether you want to use three clusters or five clusters can now be decided based on what makes sense for your t-shirt business.
- Does a trade-off between how well the t-shirts will fit, depending on whether you have three sizes or five sizes, but there will be extra costs as well associated with manufacturing and shipping five types of t-shirts instead of three different types of t-shirts. What I would do in this case is to run K-means with K equals 3 and K equals 5 and then look at these two solutions to see based on the trade-off between fits of t-shirts with more sizes, results in better fit versus the extra cost of making more t-shirts where making fewer t-shirts is simpler and less expensive to try to decide what makes sense for the t-shirt business.
- When you get to the programming exercise, you also see there an application of K-means to image compression. This is actually one of the most fun visual examples of K-means and there you see that there'll be a trade-off between the quality of the compressed image, that is, how good the image looks versus how much you can compress the image to save the space.
- In that program exercise, you see that you can use that trade-off to maybe manually decide what's the best value of K based on how good do you want the image to look versus how large you want the compress image size to be. That's it for the K-means clustering algorithm.

<img width="1919" height="946" alt="image" src="https://github.com/user-attachments/assets/e4791572-c9fb-453a-b91b-0bbd3a0a701f" />

With that, we're ready to move on to our second unsupervised learning algorithm, which is anomaly detection. How do you look at the data set and find unusual or anomalous things in it. 
This turns out to be another, one of the most commercially important applications of unsupervised learning. I've used this myself many times in many different applications.

---

