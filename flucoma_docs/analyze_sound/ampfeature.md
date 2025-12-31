# AmpFeature

# AmpFeature

Calculate the amplitude differential feature of audio.

AmpFeature is closely linked with AmpSlice and AmpGate and exposes the underlying measure of amplitude change these slicing objects use as a standalone audio descriptor. As a result it can be useful in understanding how the slicing object works at a lower-level, or as a feature in and of itself. Below is a plot that depicts the amplitude measurement across a drum loop sample.

The AmpFeature object shares all the parameters that refer to the configuration of the algorithm as AmpGate and AmpSlice. This does not include generic shared parameters such as Source, Features, Indices, etc.

It was calculated with these parameters:
- FastRampUp 1000
- FastRampDown 1000
- SlowRampUp 3000
- SlowRampDown 3000
- Floor -48

