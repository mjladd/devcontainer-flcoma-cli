# OnsetSlice

Onset detection with various spectral slicers


## Introduction[](#introduction)
OnsetSlice calculates slice points in a sound based on changes in its

## A Visual Example[](#a-visual-example)
Let’s first start with this vocal recording:

Your browser does not support the audio tag.Tremblay-AaS-VoiceQC-B2K vocal recordingIf we create a spectrogram from this sound, it is visually explicit where significant changes in the spectrum occur. Aligning these visual differences, they seem to coincide with the utterances of each letter from the alphabet.


![spectrogram of a voice recording](images/voice-spec.jpg)


## Metrics[](#metrics)
There are 10 different metrics that OnsetSlice can use for calculating the changes in the spectrum. It can be overwhelming to know which one might be best for each scenario, and in many cases it might be a red herring to experiment with the metrics blindly. In all cases, we highly recommend starting your experimentation with

### Metric 0 (Energy)[](#metric-0-energy)
Difference between sum of squares of the magnitude of frames. Good for material that has large differences in amplitude.

### Metric 1 (High Frequency Content)[](#metric-1-high-frequency-content)
Similar to metric 0 except that each frequency bin is weighted by the bin number. This means that the high frequency content is weighted more strongly in the calculation of difference.

### Metric 2 (Spectral Flux)[](#metric-2-spectral-flux)
Measures difference between the magnitudes of spectral frames. A popular algorithm and a suitable choice for a variety of sound types.

### Metric 3 (Modified Kullback-Leibler)[](#metric-3-modified-kullback-leibler)
Similarly to metrics 6, 7, 8, 9, metric 3 compares a projection of the spectrum based on frames in the past and compares the reality to this projection. Importantly, this uses log magnitudes per bin, whereas most other metrics don’t.

### Metric 4 (Itakura-Saito)[](#metric-4-itakura-saito)
Uses the Itakura-Saito divergence to measure the difference between the past spectrum and an approximate projection from thatinto the future. For more information, see

### Metric 5 (Cosine)[](#metric-5-cosine)
Calculates the difference between spectral frames using


### Metric 6 (Phase Deviation)[](#metric-6-phase-deviation)
Phase deviation uses past spectral frames to projects what the next frame from those will be. It then compares the projection to the reality. If the difference between projection and reality exceeds the threshold, a slice is output. This is especially useful for sounds which alternate or change between stable and unstable sonic states. An example of this might be sinusoidal or tonal material that rapidly becomes noisy.

### Metric 7 (Weighted Phase Deviation)[](#metric-7-weighted-phase-deviation)
Very similar to metric 6, except the phase is weighted by the magnitude.

### Metric 8 (Complex Phase Deviation)[](#metric-8-complex-phase-deviation)
The same as metric 6 but calculated in the complex domain.

### Metric 9 (Rectified Complex Phase Deviation)[](#metric-9-rectified-complex-phase-deviation)
The same as metric 8 but rectified.

## Related Resources[](#related-resources)

### Onset Detection Revisited


### Onset Detection in Musical Audio Signals


 This paper presents work on changepoint detection in musical audio signals, focusing on the case where there are note
changes with low associated energy variation. https://quod.lib.umich.edu/cgi/p/pod/dod-idx/onset-detection-in-musical-audio-signals.pdf?c=icmc;idno=bbp2372.2003.047;format=pdf](https://quod.lib.umich.edu/cgi/p/pod/dod-idx/onset-detection-in-musical-audio-signals.pdf?c=icmc;idno=bbp2372.2003.047;format=pdf)