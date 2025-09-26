- This week we are going to look at the following topics
  - Unsupervised Learning
    - Clustering
    - Anomaly Detection
  - Recommender Systems
  - Reinforcement Learning (Great at playing video games, even outperforming humans)
 
---

### What is Clustering?

- A clustering algorithm looks at a number of data points and automatically finds data points that are related or similar to each other.
- Let me contrast clustering, which is an unsupervised learning algorithm, with what you had previously seen with supervised learning for binary classification. Given a dataset like this with features x_1 and x_2. With supervised learning, we had a training set with both the input features x as well as the labels y. We could plot a dataset like this and fit, say, a logistic regression algorithm or a neural network to learn a decision boundary like that.
- In supervised learning, the dataset included both the inputs x as well as the target outputs y

<img width="1913" height="942" alt="image" src="https://github.com/user-attachments/assets/2b82a5c1-8ea4-4665-b405-ac8ae53cf5dc" />

- In contrast, in unsupervised learning, you are given a dataset like this with just x, but not the labels or the target labels y. That's why when I plot a dataset, it looks like this, with just dots rather than two classes denoted by the x's and the o's
- Because we don't have target labels y, we're not able to tell the algorithm what is the "right answer, y" that we wanted to predict. Instead, we're going to ask the algorithm to find something interesting about the data, that is to find some interesting structure about this data.
- But the first unsupervised learning algorithm that you learn about is called a clustering algorithm, which looks for one particular type of structure in the data. Namely, look at the dataset like this and try to see if it can be grouped into clusters, meaning groups of points that are similar to each other.

<img width="1916" height="941" alt="image" src="https://github.com/user-attachments/assets/371aa6eb-2972-4de2-a967-9d0983b49b36" />

- One of the applications I found fascinating was astronomers using clustering to group bodies together to figure out which ones form one galaxy or which one form coherent structures in space. Clustering today is used for all of these applications and many more. In the next video, let's take a look at the most commonly used clustering algorithm called the k-means algorithm, and let's take a look at how it works. 
- Some more examples of the Clustering example

<img width="1915" height="953" alt="image" src="https://github.com/user-attachments/assets/dbc1761b-0fd0-4020-b23a-aec3ba2a052b" />

---

### K-means intuition

- Here I've plotted a data set with 30 unlabeled training examples. So there are 30 points. And what we like to do is run K-means on this data set. The first thing that the K-means algorithm does is it will take a random guess at where might be the centers of the two clusters that you might ask it to find. In this example I'm going to ask it to try to find two clusters.
- Later in this week we'll talk about how you might decide how many clusters to find. But the very first step is it will randomly pick two points, which I've shown here as a red cross and the blue cross, at where might be the centers of two different clusters. This is just a random initial guess and they're not particularly good guesses.

<img width="1810" height="950" alt="image" src="https://github.com/user-attachments/assets/7947f967-8afc-49e1-8c4e-5586afdf3012" />

- But it's a start. One thing I hope you take away from this video is that K-means will repeatedly do two different things. The first is assign points to cluster centroids and the second is move cluster centroids. Let's take a look at what this means.
- The first of the two steps is it will go through each of these points and look at whether it is closer to the red cross or to the blue cross. The very first thing that K-means does is it will take a random guess at where are the centers of the cluster? And the centers of the cluster are called cluster centroids.
- After it's made an initial guess at where the cluster centroid is, it will go through all of these examples, x(1) through x(30), my 30 data points. And for each of them it will check if it is closer to the red cluster centroid, shown by the red cross, or if it's closer to the blue cluster centroid, shown by the blue cross.
- And it will assign each of these points to whichever of the cluster centroids It is closer to. I'm going to illustrate that by painting each of these examples, each of these little round dots, either red or blue, depending on whether that example is closer to the red or to the blue cluster centroid.
- So this point up here is closer to the red centroid, which is why it's painted red. Whereas this point down there is closer to the blue cluster centroid, which is why I've now painted it blue. So that was the first of the two things that K-means does over and over. Which is a sign points to clusters centroids.
<img width="1908" height="934" alt="image" src="https://github.com/user-attachments/assets/25c6f04e-7ab2-42ba-8a78-5cd058d96635" />

---

<img width="1893" height="935" alt="image" src="https://github.com/user-attachments/assets/e4b8f972-2732-4010-82c7-8cbf259770c5" />

- The second of the two steps that K-means does is, it'll look at all of the red points and take an average of them. And it will move the red cross to whatever is the average location of the red dots, which turns out to be here. And so the red cross, that is the red cluster centroid will move here. And then we do the same thing for all the blue dots. Look at all the blue dots, and take an average of them, and move the blue cross over there.
- So you now have a new location for the blue cluster centroid as well. In the next video we'll look at the mathematical formulas for how to do both of these steps. But now that you have these new and hopefully slightly improved guesses for the locations of the to cluster centroids, we'll look through all of the 30 training examples again.

<img width="1915" height="932" alt="image" src="https://github.com/user-attachments/assets/ac375427-1875-4a83-8f57-8dae99e76f42" />

- And check for every one of them, whether it's closer to the red or the blue cluster centroid for the new locations. And then we will associate them which are indicated by the color again, every point to the closer cluster centroid. And if you do that, you see that the field points change color.
- So for example, this point is colored red, because it was closer to the red cluster centroid previously. But if we now look again, it's now actually closer to the blue cluster centroid, because the blue and red cluster centroids have moved.So if we go through and associate each point with the closer cluster centroids, you end up with this. And then we just repeat the second part of K-means again. Which is look at all of the red dots and compute the average. 
- And also look at all of the blue dots and compute the average location of all of the blue dots. And it turns out that you end up moving the red cross over there and the blue cross over here. And we repeat.
- Let's look at all of the points again and we color them, either red or blue, depending on which cluster centroid that is closer to. So you end up with this. And then again, look at all of the red dots and take their average location, and look at all the blue dots and take the average location, and move the clusters to the new locations.
- And it turns out that if you were to keep on repeating these two steps, that is look at each point and assign it to the nearest cluster centroid and then also move each cluster centroid to the mean of all the points with the same color.
- If you keep on doing those two steps, you find that there are no more changes to the colors of the points or to the locations of the clusters centroids. And so this means that at this point the K-means clustering algorithm has converged.

<img width="1909" height="947" alt="image" src="https://github.com/user-attachments/assets/d4cec64e-95bd-4c6a-8c74-0c01edc1ac93" />

- Because applying those two steps over and over, results in no further changes to either the assignment to point to the centroids or the location of the cluster centroids. In this example, it looks like K-means has done a pretty good job. It has found that these points up here correspond to one cluster, and these points down here correspond to a second cluster.
- So now you've seen an illustration of how K-means works. The two key steps are, assign every point to the cluster centroid, depending on what cluster centroid is nearest to.
- And second move each cluster centroid to the average or the mean of all the points that were assigned to it. In the next video, we'll look at how to formalize this and write out the algorithm that does what you just saw in this video.

--- 

