# Decision Trees

The decision tree is an efficient algorithm for describing a way to traverse a dataset while also defining a tree like path to the expected outcomes. This branching in a tree is based on control statements or values, and the data points lie on either side of the splitting node, depending on the value of a specific feature.

The structure of a decision tree can be defined by a root node, which is the most important splitting feature. The internal nodes are tests on an attribute. For example, if an internal node has a control statement (age<40), then the data points satisfying this condition are on one side, and the rest on the other. The leaf nodes belong to the available classes that the dataset represents.

### Example of decision tree induction
Applying the above algorithm for the problem of deciding whether to walk or take a bus, we can develop a decision tree by selecting a root node, internal nodes, leaf nodes, and then by defining step-by-step the splitting criteria for the class. We select the most important node as root node, which is weather. Depending on the weather and other conditions like time and hunger, we can build our tree as follows:
![1_WYo9_o95ApwRR-zH-JBSzw](https://user-images.githubusercontent.com/23405520/113809904-be5b5300-9786-11eb-9599-a3101d52992a.png)


### How do we know where to split?

An attriubte selection measure is a heuristic for selecting the splitting criterion that's most capable of deciding how to partition data in such a way that would result in individual classes. Attribute selection measures are know as splitting rules because they define how the data points are to be split on a certain level in a decision tree. The attribute that has  the best score for the measure is choosen as the splitting attribute for the given data points.

<b> Here are some major attribute selection measures: </b>

1. <b> Information Gain </b>

![1_3C0u8k-FDnkD900ZZOmttw](https://user-images.githubusercontent.com/23405520/113810146-3aee3180-9787-11eb-96e2-7fb0979a90f9.png)

2. <b> Gini Ratio </b>

## Information Gain and Entropy

Information Gain, like Gini Impurity, is a metric used to train Decision Trees. Specifically, these metrics measure the quality of a split. For example, say we have the following data:

[svgtopng.zip](https://github.com/xdevson/machine_learning_notes/files/6269025/svgtopng.zip)





3. <b> Gini Ratio </b>
