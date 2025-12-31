

# UMAP
Uniform Manifold Approximation and Projection (UMAP) on a FluidDataSet







## Parameters[](#parameters)
UMAP has three key parameters that affect the result it produces. It is good to remember that UMAP is trying to work within the constraints you provide while giving the “best” possible result. Configuring UMAP with the the right parameters, (i.e constraints) allows you to balance the





### Minimum Distance (`mindist`)[](#minimum-distance-mindist)




### Number of Neighbours (`numneighbours`)[](#number-of-neighbours-numneighbours)
You can think of the



### Iterations[](#iterations)
UMAP works iteratively to calculate the lower-dimension representation of the input data. As such, performing more or less iterations will drastically effect the result. It is hard to say whether the results will be “better” or “worse” in any case. In fact, you might find something musically useful at any given point of the process. That said, if you find that the low-dimension embedding that UMAP gives you doesn’t make sense it might be the case that more iterations can help it to discern some structure of your data.



## Related Resources[](#related-resources)


### Understsanding UMAP




### UMAP: Uniform Manifold Approximation and Projection for Dimension Reduction




### UMAP at SciPy 2018




### How to Use t-SNE Effectively


 Discusses another similar dimension reduction algorithim, t-SNE which might be enriching when thinking about the wider world of machine learning and techniques in this space. https://distill.pub/2016/misread-tsne](https://distill.pub/2016/misread-tsne)