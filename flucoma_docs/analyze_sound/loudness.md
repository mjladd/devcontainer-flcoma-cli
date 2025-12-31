# Loudness

# Loudness

EBUR128 loudness and true peak

Our perception of how “loud” a sound is can be complex to understand and measure. Human hearing is not constant or linear across the range of frequencies that we are sensitive to. It is possible to have sounds that register as loud when measured that nonetheless are perceived as weak (and vice versa) depending on their frequency content. Loudness is an audio descriptor that attempts to model such characteristics of human hearing according to the EBU R128 specification. This specification uses an approach that both respects the natural filtering of our ears across the audible spectrum of frequencies and incorporates a notion of differing time scales into the analysis. The graph below depicts a k-weighting filter, which approximates the human ear’s sensitivity to different frequencies but is not a rigorous isosonic curve.

Like most descriptors, this object works over a short configurable window of time. For instant loudness, the EBU standard recommends a window size of 400ms that is updated every 100ms. For each window, the object provides a measurement of loudness of the signal (in LUFS) and also provides the true-peak of that window (in dBFS). With these pieces of information, we might hope that our musical systems and programs can “listen” to sounds and infer their loudness in a way that is more similar to how we might perceive them. This is a murky area to untangle when a computer is involved, and our biological processes responsible for hearing are subject to all sorts of other influences and contextual pieces of information. Aspects such as fatigue and expectation play a large role in the perceived loudness of a sound. In other words, it is important to appreciate the model that is being used, while being aware that it can fall short for replicating complex human hearing.

## What is True Peak?

Most digital meters (such as those in your DAW of choice) display sample peaks i.e the highest number it identifies in a given time window. When you play digital audio back, you are hearing an analog reconstruction of that sound as the digital data is converted into an analog signal for the loudspeakers. The reconstructed analog signal can, in certain conditions, peak beyond the maximum sampled values: these are known as inter-sample peaks. True peak is a measurement that takes into account inter-sample peaks by means of oversampling the signal.

## Related Resources

### Loudness and Metering (Part 1)

A musicianly deep-dive into the nuances of perceived loudness and metering

### Loudness Penalty: Analyzer

A website that analyses an audio file to calculate the attenuation or amplification of different music streaming services

### MASTERING - LOUDNESS for streaming services with Ian Shepherd

An interview with Ian Shepherd on measuring loudness and its relationship to the mastering process

### EBU: Loudness

The EBU's official resournce on loudness

### ITU-R BS.1771-1 Requirements for loudness and true-peak indicating meters

A technical document describing the requirements for measuring loudness and true-peak meters
