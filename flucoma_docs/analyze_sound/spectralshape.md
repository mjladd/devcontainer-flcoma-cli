# SpectralShape

# SpectralShape

Seven spectral shape descriptors

SpectralShape is an object that calculates several audio descriptors and bundles them together. This collection of audio descriptors describe the shape of a spectrum, and might tell us something about the characteristics of a sound. It can give us indications about how “spread out” a spectrum is, where the “centre” is or perhaps how “flat” or “tilted” the overall shape is. As always, audio descriptors have the potential to be misleading, after all, machines only model narrow models of listening. Therefore, it is important to keep in mind how the values themselves are derived so that we can apply our musical judgement to them and derive usefulness from what they are actually describing about the spectrum. Alex Harker has an informative talk about this in the Related Resources.

The widget below shows you the spectrum that has its shape analysed alongside some explanations for how each value is derived from its analysis of that spectrum. The spectral centroid is shown in red and the spectral rolloff in blue.

## Spectral Centroid

Centroid is the centre of gravity or centre of mass in the spectrum. If you had to balance the spectrum on the tip of your finger, where would you place it?

## Spectral Spread

The spectral spread describes the amount of
Deviation of the energy around the spectral centroid.

## Spectral Skewness

How skewed, or symmetrical the spectrum is around the mean.

## Spectral Kurtosis

How “peaky” or “pointy” the spectrum is.

## Spectral Rolloff

The frequency below which is contained 99% of the energy of the spectrum.

## Spectral Flatness

Literally how flat your spectrum is. White noise occupies equal energy in each frequency bin of a spectral analysis and is therefore very flat. A single sinusoidal peak will be not flat at all. It might be useful for differentiating noisy and tonal sounds.

## Spectral Crest

Crest is the ratio between the loudest magnitude and the RMS of the analysis frame. A larger number is an indication of a loud peak poking out from the overall spectral curve.

## Related Resources

### Meaningless Numbers: Using Audio Descriptors in a Musical Manner

An introduction to audio descriptors, how they can be used musically, as well as their assumptions and pitfalls.
