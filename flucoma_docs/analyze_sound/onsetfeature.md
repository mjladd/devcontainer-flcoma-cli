# OnsetFeature

# OnsetFeature

Calculates the spectral difference feature of audio.

OnsetFeature is closely linked with OnsetSlice and exposes the underlying measure of change between spectral frames as a standalone audio descriptor. As a result it can be useful in understanding how the slicing object works at a lower-level, or as a feature in and of itself. Below is a plot that depicts the measurement of change between spectral frames across a drum loop sample.

The OnsetFeature object shares all the parameters that refer to the configuration of the algorithm as the OnsetSlice object. This does not include generic shared parameters such as Source, Features, Indices, etc.

The plot was calculated with the default parameters.
