# BufStats - Statistical Analysis of Buffer Channels

**Source:** https://learn.flucoma.org/reference/bufstats/

---

BufStats statistically summarises a set of values that are in a buffer channel, by returning seven statistics: the [mean](#mean), [standard deviation](#standard-deviation), [skewness](#skewness), [kurtosis](#kurtosis), [low](#low) (by default the minimum), [middle](#middle) (by default the median), and [high](#high) (by default the maximum) values. The mean and median are a measure of the central tendency of the data, while the others help describe how the data are distributed around this tendency.

A buffer typically holds time-series information as "frames," either in the form of audio samples (as an audio buffer for playback) or as a series of audio descriptors created by an analysis process (as is the case with FluCoMa's buffer-based analyses). If different time-series (such as sound slices) are all a different number of frames long, it may be difficult to compare them. The statistical summary provided by BufStats can be useful for comparing these time series (for example, the mean analysis value from one time-series can be compared to the mean analysis value from another time series even if the original slices are different lengths).

In addition to computing these statistical descriptions on the original buffer channel, BufStats can also:

- compute these statistics on up to two [derivatives](#derivatives) of the original time-series with the `numDerivs` parameter
- apply [weights](#weights) to the various frames to produce a weighted statistical summary using a `weights` buffer
- find and remove [outliers](#outliers) frames with the `outliersCutoff` parameter

> **Pointer:** While it can be difficult to discern how to use some of these analyses practically (i.e., what does the kurtosis of the first derivative of spectral centroid indicate musically?), these statistical summaries can sometimes represent differences between analyses that dimensionality reduction and machine learning algorithms can pick up on. Including these statistical descriptions in training or analysis may provide better distinction between data points.

The `stats` output buffer of FluidBufStats will have the same number of channels as the `source` buffer, each one containing the statistics of it's corresponding channel in the `source` buffer. Because the dimension of time is summarised statistically, the frames in the `stats` buffer do not represent time as they normally would. The first seven frames in every channel of the `stats` buffer will have the seven statistics computed on the `source` buffer channel. After these first seven frames, there will be seven more frames for each derivative requested, each containing the seven statistical summaries for the corresponding derivative.

## Mean

The average value of the data. This is calculated by adding up all the numbers and the dividing by how many numbers there are. The mean can be used to describe the central tendency of a set of values.

## Standard Deviation

Standard deviation describes of the amount of variation within the data *in relation to the mean*, which implies that it may only be useful when the mean truly represents a central tendency of the data. A lower standard deviation indicates that the values are generally nearer to the mean, while a higher standard deviation indicates that many values are more spread out, further from the mean. Standard deviation is measured in the same units as the data itself.

Standard deviation could also help calculate where most of our data points can be found. For more information about the normal distribution and the 68/95/99.7 rule see the learn page on [distribution and histograms](https://learn.flucoma.org/learn/distribution).

![Standard Deviation Diagram](https://learn.flucoma.org/learn/distribution/stddev_diagram.png)

*When data is normally distributed, it follows the 68/95/99.7 rule, indicating how much of the data is found within standard deviations of the mean. (image reproduced from [Wikipedia](https://en.wikipedia.org/wiki/Standard_deviation))*

## Skewness

Skewness indicates asymmetry in the [distribution](https://learn.flucoma.org/learn/distribution) of the data in relation to the mean. If the data is perfectly normally distributed, the distribution to the left and right sides of the mean will be mirrored, and skewness will be 0. If either side has a longer "tail" than the other, the skewness will not be zero. If the left side (lower values) have a longer tail, the skewness will be less than 0, if the right side (higher values) have a longer tail, the skewness will be greater than 0. The larger the tail, the larger the magnitude of the skewness value.

![Skewness Diagram](https://learn.flucoma.org/reference/bufstats/skewness_diagram-01.jpg)

*Data distributions with a larger tail to the left have a negative skewness while data distributions with a larger tail to the right have a positive skewness. (image reproduced from [Wikipedia](https://en.wikipedia.org/wiki/Skewness))*

## Kurtosis

Kurtosis describes the how much of the data is concentrated in the tails (more extreme values) in relation to the peak of the distribution. It is often characterized as representing the "peakedness" of a distribution; however, this definition has been shown to be misleading (see the [Kurtosis as Peakedness paper](#related-resources) below).

Unlike skewness, kurtosis does not measure which side of the data has the longer tail—it is a measure of how much of the data is distributed in *both* the tails and the peak combined in relation to the "shoulders" of the distribution (the area about one standard deviation from the mean). A normal distribution has a kurtosis of 3. Higher kurtosis values (greater than 3) indicate "heavy" tails (more outliers), while lower kurtosis values (less than 3) indicate "light" tails (fewer outliers).

![Kurtosis Diagram](https://learn.flucoma.org/reference/bufstats/kurtosis_diagram-01.jpg)

*Distributions with kurtosis greater than 3 have heavier tails while distributions with kurtosis less than 3 have lighter tails.*

## Order Statistics

Order statistics are characteristics of the data found by analyzing the data in ascending order. The low, middle, and high statistics produced by BufStats are order statistics. Each of these three statistics are determined by the `low`, `middle`, and `high` parameters. These parameters accept a number between 0 and 100 (as a percentile) and will calculate that percentile of the data in ascending order.

For example, to find the middle value, the `middle` parameter is set to 50 by default, which corresponds to the 50th percentile—the value in the middle of the data when sorted from lowest to highest (also known as the median). Similarly, the `low` parameter is set to 0 by default, which is the 0th percentile or the minimum value. The `high` parameter is set to 100 by default, corresponding to the maximum value.

If you want the 25th percentile value instead of the minimum, you would set the `low` parameter to 25. If you want the 75th percentile value instead of the maximum, you would set the `high` parameter to 75. By analyzing different percentiles of the data, you can gain insight into the distribution and outliers in your data.

> **Pointer:** The 25th and 75th percentiles are known as the first quartile (Q1) and third quartile (Q3). The interquartile range (IQR = Q3 - Q1) is often used to identify [outliers](https://learn.flucoma.org/learn/outliers) in a dataset.

## Derivatives

BufStats is able to calculate the statistics on the first and second *derivative* of a buffer channel by setting the `numDerivs` parameter to 1 or 2. A derivative describes the *rate of change* between values in a time-series. In the context of BufStats, taking the derivative can be thought of as asking:

> How much and in what direction does this value change in relation to the previous value?

Computing the derivative of an audio descriptor time-series may be useful because it describes how fast the values are changing. Notably, it can be helpful for describing how the intensity of a sound evolves. Consider how the loudness of a sound starting from silence and quickly growing to a loud peak would compare to the loudness of a sound starting from silence and slowly growing to the same loud peak. In the first example, the derivative of the loudness analysis would have larger values, indicating the faster rate of change.

### Derivative Example

To demonstrate why this is useful, imagine two snare hits: one that plays forward and one that is reversed. If we analyze the loudness of these hits, we will see two very different curves. The forward snare will have a quick attack and slower decay while the reversed snare will have a slow attack and quick decay:

![Forward Snare Loudness](https://learn.flucoma.org/reference/bufstats/00_loudness_derivative.jpg)

*A single snare hit and its loudness analysis.*

![Reversed Snare Loudness](https://learn.flucoma.org/reference/bufstats/01_reversed_loudness_derivative.jpg)

*A reversed snare hit and its loudness analysis.*

### Approximating Derivatives

The derivative of a time-series is approximated by finding the *difference* between each consecutive value in a series. For example, the derivative of the input time-series in the top row is seen in the bottom row:

**A time-series and its derivative**

| Original Time-Series | 10 | 15 | 30 | 20 | 25 | 12 | 0 | 24 | 40 |
|---------------------|----|----|----|----|----|----|---|----|----|
| **First Derivative** | 5 | 15 | -10 | 5 | -13 | -12 | 24 | 16 | - |

> Note that the derivative has one fewer value than the original series because each value represents the amount and direction of change between two adjacent values in the original.

To find the second derivative, BufStats computes the derivative of the first derivative:

**A time-series and two derivatives**

| Original Time-Series | 10 | 15 | 30 | 20 | 25 | 12 | 0 | 24 | 40 |
|----------------------|----|----|----|----|----|----|---|----|----|
| **First Derivative** | 5 | 15 | -10 | 5 | -13 | -12 | 24 | 16 | - |
| **Second Derivative** | 10 | -25 | 15 | -18 | 1 | 36 | -8 | - | - |

After computing the number of derivatives indicated by the user, BufStats calculates the same seven statistical summaries on these new series of numbers: mean, standard deviation, skewness, kurtosis, low, middle, and high.

## Outliers

BufStats can find and remove [outliers](https://learn.flucoma.org/learn/outliers) by using an analysis of the data to set boundaries for each channel in the buffer. Any frames that have a value outside the its channel's boundaries will not be used to compute the statistics. The strictness of these boundaries is determined by `outliersCutoff` (see the page on [outliers](https://learn.flucoma.org/learn/outliers) to learn more).

## Weights

The `weights` parameter can be passed a buffer, the values of which will be used for relative weighting of each corresponding frame in the `source` buffer. This will create "weighted" statistics where some values in the data have more impact on the resulting statistical summary than others. All seven of the resulting statistics may be affected by using the weights.

This can be useful for weighting certain moments in descriptor time-series by the value of other descriptors. For example, one might want to weight the influence of pitch analyses using the pitch confidence descriptor so the resulting mean pitch value is more strongly influenced by moments in the analysis when the pitch confidence is high. Similarly, one might want to weight a descriptor time-series (such as MFCC) by amplitude so the louder moments of the sound slice have greater impact than the quieter moments on the resulting statistical summary.

> **Pointer:** For an example of using a `weights` buffer to influence the statistical summary in a musical way, visit the [Weighting Stats](https://learn.flucoma.org/learn/weighting-stats) Overview.

> **Warning:** Not providing a `weights` buffer will cause all the frames to be considered equally. Any negative values in the `weights` buffer will be treated as a weight of 0. The provided `weights` buffer must be a single channel with exactly the same number of frames as `source` (each frame in `weights` will be the weight amount for the corresponding frame in `source`).

## Related Resources

### Kurtosis as Peakedness, 1905 – 2014. R.I.P.

Paper by Peter H. Westfall (2014) describing a common misconception about kurtosis.

[https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4321753/pdf/nihms-599845.pdf](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4321753/pdf/nihms-599845.pdf)

---

## Related Pages

### Local Documentation
- [BufSelectEvery](../utility_objects/bufselectevery.md)
- [Loudness](../analyze_sound/loudness.md)
- [RobustScale](robustscale.md)
- [Standardize](standardize.md)
- [Stats](stats.md)

### External Resources
- [Sound Into Sound](https://learn.flucoma.org/explore/constanzo)
- [Get Started](https://learn.flucoma.org/learn/getting-started)
- [Outliers](https://learn.flucoma.org/learn/outliers)
- [Refining Pitch Analysis](https://learn.flucoma.org/learn/refining-pitch-analysis)
- [Dealing with Time](https://learn.flucoma.org/learn/time)
- [Weighting Stats](https://learn.flucoma.org/learn/weighting-stats)
- [Distribution and Histograms](https://learn.flucoma.org/learn/distribution)
