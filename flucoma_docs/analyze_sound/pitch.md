# Pitch

# Pitch

Fundamental pitch analysis

The Pitch object returns both pitch and confidence values. The 3 algorithms provided are specialised in monophonic pitch tracking and thus will not be very accurate on signals with multiple notes. When no pitch can be detected, a pitch of 0 Hz is returned (or -999.0 when the unit is in MIDI note mode).

The confidence output is a value between 0 and 1 indicating how confident the algorithm is in validity of the pitch estimation it provides. In effect, the confidence output can describe how “noisy” (closer to 0) or “harmonic” (closer to 1) the spectrum is. The pitch confidence may also be low when a signal contains polyphony, as the algorithms are not intended for multiple pitch streams.

![](images/pitch_img_1.jpg)

Pitch (blue) and confidence (orange) analyses for a series of trombone tones. Note how in the silences the pitch analysis is not stable, but also the confidence value is much lower.

The Pitch object has three algorithms to choose from (by setting the algorithm parameter):
1. Cepstrum: Returns a pitch estimate as the location of the second highest peak in the Cepstrum of the signal (after DC).
2. Harmonic Product Spectrum: Implements the Harmonic Product Spectrum algorithm for pitch detection. See reference below.
3. YinFFT: (the default) Implements the frequency domain version of the YIN algorithm. This is the most advanced and reliable algorithm offered here. It is also the most CPU intensive. See reference below.


The unit argument indicates whether the pitch output should be in hertz (indicated by 0) or MIDI note numbers (indicated by 1). MIDI note numbers may be useful, not only because of their direct relationship to MIDI-based synthesis systems, but also because of the logarithmic relationship to hertz, making them perceptually evenly-spaced units (1 MIDI unit = 1 semitone).

## Related Resources

### An Introduction to Audio Content Analysis: Applications in Signal Processing and Music Informatics.

Paper by A. Lerch describing the implementation of the Harmonic Product Spectrum algorithm

### Automatic Annotation of Musical Audio for Interactive Applications.

Paper by P. M. Brossier describing the implementation of the YIN algorithm
