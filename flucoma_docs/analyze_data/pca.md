

# PCA
Principal component analysis of a FluidDataSet









## Calculating the Principal Components[](#calculating-the-principal-components)
In order to calculate the principal components, PCA analyses the original DataSet and determines how to “rotate” the data so that an axis can be drawn through the data along which the most variance in the data can be observed (for a excellent visual explanation, see the YouTube video above). The new axis, or attribute, is a principal component of the DataSet. PCA continues the process of “drawing axes”, through the data (always maximising variance) until all the principal components have been determined. PCA computes as many principal components as there are dimensions in the original DataSet. This process orders the principal components (starting at 1) according to how much of the variance in the DataSet they are able to demonstrate (from demonstrating the most variance to the least). The lower ordered principal components are therefore



## PCA for Dimensionality Reduction[](#pca-for-dimensionality-reduction)
Because PCA orders the principal components from those that demonstrate the most variance in the data to the least, one can effectively perform dimensionality reduction by removing some of the higher ordered principal components (in the transformed data set) because they are less useful at representing the variance in the data. This allows the data set to have fewer dimensions, while retaining the aspects of the data that are more useful in understanding the differences between the data points (the lower order principal components).

As this is often how PCA is used, FluidPCA allows the user to specify the number of output dimensions desired, so that



## `whiten`[](#whiten)
PCA “whitening” can be turned on by setting the





## Related Resources[](#related-resources)


### Principal Component Analysis (PCA) - Computerphile




### PCA Whitening


 Some of the maths behind PCA whitening. http://ufldl.stanford.edu/tutorial/unsupervised/PCAWhitening/](http://ufldl.stanford.edu/tutorial/unsupervised/PCAWhitening/)