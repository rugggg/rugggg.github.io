---
title: data science with Julia
layout: post
categories: <programming> <julia> <computing> <data science>
---

# Data
### Covering how to read, store, and understand your data

#### Download 
Julia has a built in download function - which uses curl, wget, or fetch depending on what is installed.

Remeber you can use shell commands in Julia by preprending ;, like ;ls
 
Can load text files via DelimitedFiles, or CSV, or DataFrames.jl


### Project Requirements

Use a Project.toml file to define the required packages for the project, and then run ] instantiate to install!


### Statistics 

Can use describe on a DataFrame as you would in Pandas or R.

KernelDensity.jl is the package for kernel densities
Distributions.jl has the standard stats distributions like Normal, Binomial etc
HypothesisTests.jl has hypothesis testing tools like OneSampleTTest etc

You can import scipy from python via pyimport("scipy.stats")! This is wicked cool and helps with the language adoption!

MLBase.jl package has ML base tools like confusmat for confusion matrix, and the roc function, precision, and recall

### Dimensionality Reduction

MultivariateStats.jl
StatsBase.jl
Statistics.jl
ScikitLearn.jl
Distances.jl

labelmap, labelencode is label encoding from MLBase.jl

PCA and fit, transform, reconstruct are from MultivariateStats.jl
fit, transform, and reconstruct are used for other functions that PCA I believe
note: you need to transpose matrix to pass to PCA

Makie.jl has 3d visualizations you can rotate

TSNE is in scikit-learn. You can use @sk_import manifold : TSNE to get it, and I assume this is a common way to import from sklearn in Julia

UMAP.jl has UMAP functions in it.

### Clustering

VegaLite.jl has super cool plotting overlays like maps
Clustering.jl has kmeans, and other usual suspects including hierarchical clustering, dbscan
- You can convert a DataFrame to a Matrix via casting

### Classification

DecisionTree.jl has a base DecisionTreeClassifier, you call fit on that model, it also has RandomForestClassifier
NearestNeighbors.jl has knn, kdtree (used in knn call)
GLMNet.jl has Lasso, Ridge, and Elastic, just change the alpha factor to vary between them. Lasso minimizes L1 norm, Ridge minimizes L2 norm. 0 for Ridge, 1 for Lasso, 0.5 for Elastic
randsubseq from Random.jl 
LIBSVM.jl has Support Vector Machines in it


### Regression

### Graphs

### Numerical Optimization

### Neural Nets






