

# Standardize
Standard scaling of a FluidDataSet's contents






![](images/stddev_diagram.png)


[Exploring the Oboe with FluCoMa ](/explore/harker)[Levels of Translation ](/explore/moore)[Ecosystemic Interferences ](/explore/raw-green-rust)[Fleeting Networks ](/explore/tremblay)[Neural Network Parameters ](/learn/mlp-parameters)[Comparing Scalers ](/learn/comparing-scalers)[Outliers ](/learn/outliers)[Why Scale? Distance as Similarity ](/learn/why-scale)[Distribution and Histograms ](/learn/distribution)[RobustScale ](/reference/robustscale)[BufStats ](/reference/bufstats)[DataSet ](/reference/dataset)[Normalize ](/reference/normalize)Standardized data means that every dimension in the data set has a*mean*of 0 and a[standard deviation](/reference/bufstats#standard-deviation)of 1. This scaling can be useful for many machine learning algorithms, but since most data in the wild does not fit this criteria, standardizing data is often employed. Standardizing data (and scaling data generally) can also be important for transforming a[DataSet](/reference/dataset)so that all of the dimensions have similar ranges. With similar ranges, the distance metrics (such as euclidian distance) used by many machine learning algorithms will similarly weight each of the dimensions when calculating how near or far (similar or dissimilar) two data points are from each other.Using standardization to scale data implies the assumption that the data is generally[normally distributed](/learn/distribution). Small data sets derived from audio analyses are often not normally distributed and therefore standardization might not be the best choice for scaling. It maybe useful to test other scalers ([Normalize](/reference/normalize)or[RobustScale](/reference/robustscale)) and see which provides the best musical results.[](/learn/distribution/stddev_diagram.png)When data is normally distributed, it follows the 68/95/99.7 rule, indicating how much of the data is found within standard deviations of the mean. (image reproduced from[Wikipedia](https://en.wikipedia.org/wiki/Standard_deviation))