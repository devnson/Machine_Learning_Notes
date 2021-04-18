# Decision Trees

The decision tree is an efficient algorithm for describing a way to traverse a dataset while also defining a tree like path to the expected outcomes. This branching in a tree is based on control statements or values, and the data points lie on either side of the splitting node, depending on the value of a specific feature.

The structure of a decision tree can be defined by a root node, which is the most important splitting feature. The internal nodes are tests on an attribute. For example, if an internal node has a control statement (age<40), then the data points satisfying this condition are on one side, and the rest on the other. The leaf nodes belong to the available classes that the dataset represents.

A Random Forest 🌲🌲🌲 is actually just a bunch of Decision Trees 🌲 bundled together (ohhhhh that’s why it’s called a forest). We need to talk about trees before we can get into forests.

Look at the following dataset:

![dataset](https://user-images.githubusercontent.com/23405520/113811475-e1d3cd00-9789-11eb-8b58-fda7bc4fda04.png)

If I told you that there was a new point with an xx coordinate of 11, what color do you think it’d be?

Blue, right? 

You just evaluated a decision tree in your head:


![decision-tree](https://user-images.githubusercontent.com/23405520/113811519-f3b57000-9789-11eb-8601-b7f9fc7d37e2.png)

That’s a simple decision tree with one decision node that tests x < 2 . If the test passes (x < 2), we take the left branch and pick Blue. If the test fails (x≥2), we take the right branch and pick Green.

![dataset-split](https://user-images.githubusercontent.com/23405520/113811538-016af580-978a-11eb-8d0d-b7e841fa3270.png)

Decision Trees are often used to answer that kind of question: given a labelled dataset, how should we classify new samples?

Labelled: Our dataset is labelled because each point has a class (color): blue or green.

Classify: To classify a new datapoint is to assign a class (color) to it.

Here’s a dataset that has 3 classes now instead of 2:

![dataset2](https://user-images.githubusercontent.com/23405520/113811571-16478900-978a-11eb-99fb-3dc2158ef619.png)

Our old decision tree doesn’t work so well anymore. Given a new point (x, y)(x,y),

If x ≥ 2, we can still confidently classify it as green. 
If x <= 2, we can’t immediately classify it as blue - it could be red, too.  
We need to add another decision node to our decision tree:



![decision-tree2](https://user-images.githubusercontent.com/23405520/113811647-3bd49280-978a-11eb-9744-19e400efd4a6.png)

![dataset2-split](https://user-images.githubusercontent.com/23405520/113811671-455dfa80-978a-11eb-999d-bd9f0e3e419a.png)

Pretty simple, right? That’s the basic idea behind decision trees.

<b>2. Training a Decision Tree </b>

Our first task is to determine the root decision node in our tree. Which feature (x or y) will it test on, and what will the test threshold be? For example, the root node in our tree from earlier used the x feature with a test threshold of 2:

![decision-tree2-root](https://user-images.githubusercontent.com/23405520/113811775-71797b80-978a-11eb-8254-284219e713bf.png)

Intuitively, we want a decision node that makes a “good” split, where “good” can be loosely defined as separating different classes as much as possible. The root node above makes a “good” split: all the greens are on the right, and no greens are on the left.

Thus, our goal is now to pick a root node that gives us the “best” split possible. But how do we quantify how good a split is?

Back to the problem of determining our root decision node. Now that we have a way to evaluate splits, all we have to do to is find the best split possible! For the sake of simplicity, we’re just going to try every possible split and use the best one (the one with the highest Gini Gain). This is not the fastest way to find the best split, but it is the easiest to understand.

Trying every split means trying

- Every feature (x or y).
- All “unique” thresholds. We only need to try thresholds that produce different splits.

For example, here are the thresholds we might select if we wanted to use the x coordinate:


![dataset2-thresholds-x](https://user-images.githubusercontent.com/23405520/113811887-aede0900-978a-11eb-9ba5-903077e826b4.png)


Let’s do an example Gini Gain calculation for the x = 0.4 split.

![image](https://user-images.githubusercontent.com/23405520/113811926-c1f0d900-978a-11eb-82e5-0910b134a67d.png)

First, we calculate the Gini Impurity of the whole dataset:

![image](https://user-images.githubusercontent.com/23405520/113811967-d59c3f80-978a-11eb-8fbf-61451e2a77ea.png)

Then, we calculate the Gini Impurities of the two branches:

![image](https://user-images.githubusercontent.com/23405520/113811982-de8d1100-978a-11eb-91c9-fc173d771b08.png)

Finally, we calculate Gini Gain by subtracting the weighted branch impurities from the original impurity:

![image](https://user-images.githubusercontent.com/23405520/113812001-e64cb580-978a-11eb-832e-4e8d100fc11d.png)

We can calculate Gini Gain for every possible split in the same way:

![image](https://user-images.githubusercontent.com/23405520/113812019-f1074a80-978a-11eb-8e85-b2808e6a9819.png)

![image](https://user-images.githubusercontent.com/23405520/113812031-f82e5880-978a-11eb-909a-32208f3bea89.png)


After trying all thresholds for both x and y, we’ve found that the x=2 split has the highest Gini Gain, so we’ll make our root decision node use the x feature with a threshold of 2. Here’s what we’ve got so far:

![image](https://user-images.githubusercontent.com/23405520/113812082-11370980-978b-11eb-913b-f56389543f96.png)

<b> 2.2: Training a Decision Tree: The Second Node </b>

Time to make our second decision node. Let’s (arbitrarily) go to the left branch. We’re now only using the datapoints that would take the left branch (i.e. the datapoints satisfying x<2), specifically the 3 blues and 3 reds.      

To build our second decision node, we just do the same thing! We try every possible split for the 6 datapoints we have and realize that y=2 is the best split. We make that into a decision node and now have this:

![image](https://user-images.githubusercontent.com/23405520/113812137-2ca21480-978b-11eb-8811-248d9b3889fe.png)

Our decision tree is almost done…

<b> 2.3 Training a Decision Tree: When to Stop? </b>

Let’s keep it going and try to make a third decision node. We’ll use the right branch from the root node this time. The only datapoints in that branch are the 3 greens.   

Again, we try all the possible splits, but they all

- Are equally good.
- Have a Gini Gain of 0 (the Gini Impurity was already 0 and can’t go any lower).


It doesn’t makes sense to add a decision node here because doing so wouldn’t improve our decision tree. Thus, we’ll make this node a leaf node and slap the Green label on it. This means that we’ll classify any datapoint that reaches this node as Green.

If we continue to the 2 remaining nodes, the same thing will happen: we’ll make the bottom left node our Blue leaf node, and we’ll make the bottom right node our Red leaf node. That brings us to the final result:

![image](https://user-images.githubusercontent.com/23405520/113812208-51968780-978b-11eb-883d-1a6e23d5db04.png)



## Information Gain and Entropy

Information Gain, like Gini Impurity, is a metric used to train Decision Trees. Specifically, these metrics measure the quality of a split. For example, say we have the following data:


![dataset](https://user-images.githubusercontent.com/23405520/113811288-8c97bb80-9789-11eb-9970-9736a8d42370.png)

What if we made a split at x = 1.5 ?

![dataset-imperfect-split](https://user-images.githubusercontent.com/23405520/113811354-b3ee8880-9789-11eb-8224-acd4402cc587.png)

This imperfect split breaks our dataset into these branches:

Left branch, with 4 blues.    
Right branch, with 1 blue and 5 greens.      
It’s clear this split isn’t optimal, but how good is it? How can we quantify the quality of a split?

That’s where Information Gain comes in.

<b> Information Entropy </b>

Before we get to Information Gain, we have to first talk about Information Entropy. In the context of training Decision Trees, Entropy can be roughly thought of as how much variance the data has. For example:

A dataset of only blues  would have very low (in fact, zero) entropy.
A dataset of mixed blues, greens, and reds  would have relatively high entropy.
Here’s how we calculate Information Entropy for a dataset with C classes:

![image](https://user-images.githubusercontent.com/23405520/113812299-7c80db80-978b-11eb-93e3-a3181c527dd6.png)

where, pi is the probability of randomly picking an element of class i (i.e. the proportion of the dataset made up of class i).

The easiest way to understand this is with an example. Consider a dataset with 1 blue, 2 greens, and 3 reds: Then

![image](https://user-images.githubusercontent.com/23405520/113812373-a20de500-978b-11eb-8893-aabf5ad1f497.png)



<b> Information Gain </b>

It’s finally time to answer the question we posed earlier: how can we quantify the quality of a split?

Let’s consider this split again:

![image](https://user-images.githubusercontent.com/23405520/113812431-b94cd280-978b-11eb-8431-c401bcf0baa2.png)

Before the split, we had 5 blues and 5 greens, so the entropy was

![image](https://user-images.githubusercontent.com/23405520/113812455-c23da400-978b-11eb-9fa4-f3283438bf01.png)

After the split, we have two branches.

![image](https://user-images.githubusercontent.com/23405520/113812548-ebf6cb00-978b-11eb-9d33-25dad7816756.png)

![image](https://user-images.githubusercontent.com/23405520/113812578-f7e28d00-978b-11eb-9d51-ed063ff796ec.png)

![image](https://user-images.githubusercontent.com/23405520/113812603-04ff7c00-978c-11eb-953f-3ef6b08809c9.png)


### Gini Impurity

![image](https://user-images.githubusercontent.com/23405520/113812690-252f3b00-978c-11eb-8bfc-83d15ab9cfda.png)

![image](https://user-images.githubusercontent.com/23405520/113812732-35471a80-978c-11eb-9c90-0ea6d6e0eff6.png)

![image](https://user-images.githubusercontent.com/23405520/113812760-4728bd80-978c-11eb-9884-603976b9ec00.png)

![image](https://user-images.githubusercontent.com/23405520/113812795-51e35280-978c-11eb-85de-fe62fe86cf6b.png)

![image](https://user-images.githubusercontent.com/23405520/113812815-5a3b8d80-978c-11eb-8e88-4a63f691b555.png)


![image](https://user-images.githubusercontent.com/23405520/113812844-67f11300-978c-11eb-953d-a7e588b1db4f.png)
![image](https://user-images.githubusercontent.com/23405520/113812867-73443e80-978c-11eb-93e8-e1895fe4b748.png)

![image](https://user-images.githubusercontent.com/23405520/113812890-7b9c7980-978c-11eb-9f29-df0465c0cfb2.png)

![image](https://user-images.githubusercontent.com/23405520/113812908-85be7800-978c-11eb-9a5d-92ac1a91997d.png)
![image](https://user-images.githubusercontent.com/23405520/113812939-940c9400-978c-11eb-878a-ca5548702b84.png)
![image](https://user-images.githubusercontent.com/23405520/113812971-a4bd0a00-978c-11eb-8a3c-57cc7597064c.png)
![image](https://user-images.githubusercontent.com/23405520/113813006-af779f00-978c-11eb-9260-e52c1b26e325.png)
![image](https://user-images.githubusercontent.com/23405520/113813027-b9999d80-978c-11eb-8fdd-7c68b6109f91.png)

![image](https://user-images.githubusercontent.com/23405520/113813038-c3230580-978c-11eb-9239-09463fe699b0.png)



## Example

![image](https://user-images.githubusercontent.com/23405520/113813260-2dd44100-978d-11eb-9155-ecce22c22706.png)


