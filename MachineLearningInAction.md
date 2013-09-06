# Machine Learning in Action

## Part 1:  Classification

### Chapter 1: Machine Learning Basics

Supervised Learning Tasks: kNN, Naive Bayes, SVMs, Decision Trees, Linear, Locally Weight Linear, Ridge, Lasso

Unsupervised Learning Tasks: kMeans, DBSCAN, EM, Parzen Window

### Chapter 2: kNN

* Pros: high accuracy, insensitive to outliers, no assumptions about data
* Cons: Computationally expensive, lots of memory, Needs to be normalized
* Works with: Numeric, Nominal

```
For every point in our dataset:
```
Examples: Dating preferences, handwriting recognition

Summary
* kNN is example of instance-based learning (need instances of data to perform classification). 
* Large storage
* Need to scan all data to find distances, so slow. 
* Can't understand representation.

### Chapter 3: Decision Trees

* Pros: computationally cheap, knowledge representation is easy to understand, missing values are OK, can deal with irrelevant features
* Cons: Prone to overfitting
* Works with: Numeric, Nominal

Decision trees are often used in expert systems, comparable to human output.


Information Gain, Entropy, Gini impurity
Info(xi) = equation here

Tree Algorithms: 

* CART
* C4.5
* ID3 - Can't handle numeric values, not good if many splits.

Create Branch:

```
Check if every item in the dataset is in the same class: 
	If so return the class label
```

Example: predict contact lens type, predict spam, is fish?

### Chapter 4: Naive Bayes
* Pros: works well with small amount of data, handles multiple classes
* Cons: sensitive to how the input data is prepared
* Works with: Nominal 

Assumptions: each feature has same probability, each feature is independent


```
Count the number of documents in each class for every training document:
	return conditional probabilities for each class



Example: documentation classification, spam, guess location by text

### Chapter 5: Logistic Regression
* Pros: Computationally inexpensive, easy to implement, knowledge representation is interpretable
* Cons: Prove to underfitting, may have low accuracy
* Works with: Numeric, Nominal

Optimations are used to find regression coefficients: [stochastic] gradient ascent

Options to dealing with missing values in data:

* Use feature's mean value from all the available data
* Fill unknowns with special value like -1
* Ignore the instance
* Use mean value from similar items
* Use another ML algorithm to predict the value

Gradient Ascent Pseudo Code:

```
Start with the weights all set to 1 
For each piece of data in the dataset:
```
Examples: horse fatalities from colic

Logistic regression is finding best-fit parameters to a nonlinear function called the sigmoid.

### Chapter 6: Support Vector Machines (SVM)
* Pros: Low generalization error, computationally inexpensive, easy to interpret results
* Cons: Sensitive to tuning parameters and kernel choice; natively only handles binary classification
* Works with: Numeric, Nominal

Concerns with SVMs:

* Need to find the maximum margin by solving a quadratic optimization problem
* Optimization can use SMO, or Platt's SMO
* Kernels: transform data onto another space. Examples: RBF (radial bias function). Used because of inner products
* Kernels are sensitive of parameters

SVMs generate a binary decision (but can be changed to support more). Good generatialization error. 

Terms:

* Linearly Separable
* Separating Hyperplane: line used to separate the dataset.
* Hyperplane:
* Support vectors: points closest to separating hyperplane, which are used for classification
* Margin: 
* Slack Variables: 

SMO:

* takes large optimization problem and breaks it into many small problems
* problems can be solved sequentially, but faster
* chooses two alphas to optimize on each cycle. once a suitable pair of alphas is found, one is increased, other is decreated.
* Two criterias for alphas:
	* both alphas have to be outside margin boundary
	* alphas aren't clamped or bounded

SMO Pseudo Code:

```
Create an alphas vector filled with 0s
		If the data vector can be optimized:
```
Examples: handwriting classification (so don't need to package data with model)

SVMs are a type of classifier, generate a binary decision. Considered to be the best stock algorithm in unsupervised learning.

SVMs try to maxmimize margin by solving quadratic optimization problem. 

### Chapter 7: Improving Classification with the AdaBoost (Adaptive Boost)

* Pros: Low generalization error, easy to code, works with most classifiers, no param- eters to adjust

Ensemble methods

Bagging (or Bootstrapping): new data sets are made with random sampling with replacement, take majority vote

Boosting: similar to bagging, but only use one type of classifier, and trained sequentially.
Boosting makes new classifiers focus on data that was previously misclassified. 

Decision stump: simple decision tree.

Classication Imbalance:

* Precision: TP / (True Positive + False Positive)
* Recall: TP/(TP + FN)
* ROC Curve

Cost Imbalance:

* AdaBoost: adjust error weight vector D
* Naive Bayes: predict the class with lowest expected cost instead of class with highest probability
* SVMS: use different C parameters in the cost function for different classes

Classification Imbalance (Rare events): can resample for better distribution

## Part 2: Forecasting Numeric Values With Regression

### Chapter 8: Predicting Numeric Values: Regression

* Pros: Easy to interpret results, computationally inexpensive 
* Cons: Poorly models nonlinear data


* LWLR give weight to data points near [Do more]

Shrink: 
Ridge regression: first of two shrinkage methods

pg 168

### Chapter 9: Tree-based

CART: Classification And Regression Trees. Pruning. Model Trees.

ID3: splits all possible values of feature and can't be used again (can do a binary split), can't handle continuous features

CART: makes binary splits and handles continuous variables. Can do regression with modification.

* Pros: Fits complex, nonlinear data

Find the best feature to split on:

## Part 3: Unsupervised Learning

### K-Means Clustering (Unsupervised Classification)

* Pros: Easy to implement
* Works with: Numeric

Pseudo-code:

```
Create k points for starting centroids (often randomly) 
	While any point has changed cluster assignment
```
The measure of closeness can be changed, use any distance measure as required.

One metric for quality can be: SSE (sum of squared error).

Bisecting K-Means: splits clusters that have high SSE

```
Start with all the points in one cluster 
While the number of clusters is less than k


### Apriori Algorithm

* Pros: Easy to code up

Association analysis (association rule learning): looking for hidden relationships in large datasets.

* Frequent item sets: collections of items that frequently occur together
* Association rules: suggest that a strong relationship exists between two items
* Support: percentage of the dataset that contains the itemset
* Confidence: association rules, support(two_items)/support(one_item)

Need to check all possible itemsets from powerset, so any sort of reducing the possibilities would be great. Otherwise it's 2^n.

Apriori Principle: if an itemset is frequent, then all of its subsets are frequent (or inverse)

Generating Candidate Itemsets:

```
For each transaction in tran the dataset:
For each candidate itemset, can:
	Check to see if can is a subset of tran
	If so increment the count of can
For each candidate itemset:
	If the support meets the minimum, keep this item
Return list of frequent itemsets
```
Apriori Algorithm:

```
While the number of items in the set is greater than 0: 
	Create a list of candidate itemsets of length k

If a rule doesn't meet the minimum confidence requirement, then subsets of that rule also won't meet the minimum.



### FP-Growth (frequent pattern)

* Pros: Usually faster than Apriori.

Uses idea of Apriori tree, but faster. 


Two steps:

* Build FP-tree
* Mine frequent itemsets from the FP-tree

## Part 4: Additional Tools

### PCA

PCA assumes the data to be statically dependent, finds the axises with the most variation.

Factor analysis: we assume some unobservable latent variables are generating the data. Assume data to be a linear combination of the latent variables and some noise. The number of latent variables is possisbly lower than the amount of observed data, so it is dimensionality reduction. Used in social sciences, finance, other areas.

Independent Component Analysis: Assumes data is generated by N sources, a mixture of sources, assumed to be statically independent, so data is uncorrelated.


* Pros: Reduces complexity of data, indentifies most important features 
* Cons: May not be needed, could throw away useful information

```
Remove the mean

### SVD

* Pros: Simplifies data, removes noise, may improve algorithm results. 
* Cons: Transformed data may be difficult to understand.












### Big Data and MapReduce(Hadoop)

* Pros: Processes a massive job in a short period of time.

UNIX alternative of MapReduce:

`cat inputFile.txt | python mapper.py | sort | python reducer.py > outputFile.txt`


## Appendix

### Appendix B: Linear Algebra

Dot product: how much one vector moves in the direction of another vector. Or find the cosine between two vectors.

Matrix Inverse: XY = I, not all invertible. Has to be square. If not invertible: singular/degenerate. 

Singular: if one column can be represened as a linear combination of other columns.

* L1 Norm: Manhattan Distance

Can take derivative of matrix wrt to another