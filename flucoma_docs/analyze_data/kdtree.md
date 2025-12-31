

# KDTree
K-Dimensional tree for searching data









## Why a Kdtree Is Not Always Faster Than a Brute Force Search[](#why-a-kdtree-is-not-always-faster-than-a-brute-force-search)
Whilst k-d trees can offer very good performance relative to naïve search algorithms, they suffer from something called

[“the curse of dimensionality”](https://en.wikipedia.org/wiki/Curse_of_dimensionality)(like many algorithms for multi-dimensional data). In practice, this means that as the number of dimensions of your data goes up, the relative performance gains of a k-d tree go down.