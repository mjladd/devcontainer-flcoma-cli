# AmpGate

Absolute amplitude threshold gate detection

[Decomposition Overview](/learn/decomposition-overview)[AmpFeature](/reference/ampfeature)[AmpSlice](/reference/ampslice)
AmpGate is an absolute amplitude threshold gate detector. In this object, the term “gate” refers to a signal that reports whether or not there is the presence of sound above the provided amplitude threshold. The gate detects an onset (opens) when the internal envelope follower (controlled by rampUp and rampDown) goes above a specified onThreshold (in dB) for at least minLengthAbove samples. The gate will stay open until the envelope follower goes below offThreshold (in dB) for at least minLengthBelow samples, which triggers an offset. minSliceLength and minSilenceLength specify a duration of time (in samples) to ignore any state changes after an onset and offset (respectively).
`rampUp``rampDown``onThreshold``minLengthAbove``offThreshold``minLengthBelow``minSliceLength``minSilenceLength`
![](image_001.jpg)

Temporal relationship of many of the AmpGate parameters (see descriptions below).

## Parameters

* onThreshold: The threshold (in dB) the envelope follower must go above to trigger an onset.
* minLengthAbove: The length in samples that the envelope follower must be above onThreshold to consider it a valid onset.
* minSliceLength: The minimum length in samples for which the gate will stay open after an onset. Changes of states during this period after an onset will be ignored.
* lookBack: When an onset is detected, the algorithm will look in the recent past (this length in samples) for the minimum in the envelope follower within this window to identify as the onset point.
* offThreshold: The threshold (in dB) the envelope follower must go below to trigger an offset.
* minLengthBelow: The length in samples that the envelope follower must be below offThreshold to consider it a valid offset.
* minSilenceLength: The minimum length in samples for which the gate will stay closed after an offset. Changes of states during that period after an offset will be ignored.
* lookAhead: When an offset is detected, the algorithm will wait this duration (in samples) to find the minimum in the envelope follower within this window to identify as the offset point.

onThreshold: The threshold (in dB) the envelope follower must go above to trigger an onset.
**onThreshold:**
minLengthAbove: The length in samples that the envelope follower must be above onThreshold to consider it a valid onset.
**minLengthAbove:**`onThreshold`
minSliceLength: The minimum length in samples for which the gate will stay open after an onset. Changes of states during this period after an onset will be ignored.
**minSliceLength:**
lookBack: When an onset is detected, the algorithm will look in the recent past (this length in samples) for the minimum in the envelope follower within this window to identify as the onset point.
**lookBack:**
offThreshold: The threshold (in dB) the envelope follower must go below to trigger an offset.
**offThreshold:**
minLengthBelow: The length in samples that the envelope follower must be below offThreshold to consider it a valid offset.
**minLengthBelow:**`offThreshold`
minSilenceLength: The minimum length in samples for which the gate will stay closed after an offset. Changes of states during that period after an offset will be ignored.
**minSilenceLength:**
lookAhead: When an offset is detected, the algorithm will wait this duration (in samples) to find the minimum in the envelope follower within this window to identify as the offset point.
**lookAhead:**
See the AmpGate help file for more parameters.
*See the AmpGate help file for more parameters.*

## Using Only the Onsets

The other FluCoMa amplitude-based slicer, AmpSlice, is not based on an absolute threshold, but instead on a relative threshold. For onset detection based on an absolute amplitude threshold, use AmpGate and ignore the offset information.
[AmpSlice](/reference/ampslice)
