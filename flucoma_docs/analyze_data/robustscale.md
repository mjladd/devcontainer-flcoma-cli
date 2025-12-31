

# RobustScale
Robust scaling of a DataSet




- 
- 






## `high` and `low`[](#high-and-low)
These parameters (indicated as

[percentiles](/reference/bufstats#order-statistics)between 0 and 100) specify what percentage of the data on each extrema is not considered when determining how to scale the data. When set to the defaults of 25 and 75 (also known as the*interquartile range*), the values in the top and bottom*quartile*will have no affect on how the data gets scaled, so even if there are some extreme[outliers](/learn/outliers)in this dimension, the scaling that occurs will only reflect how the data in the two inner*quartiles*are positioned. Because this is strategic for preventing outliers from affecting the scaling of data, if you know what percentiles outliers occur at, you might adjust the`high`and`low`parameters accordingly.