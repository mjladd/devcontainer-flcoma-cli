# BufNMF

Non-negative matrix factorisation
[Event Detection and Improvisation](/explore/hayes)[​​Combining FluCoMa with bach](/explore/pasquet)[Interface Design with FluCoMa](/explore/pluta)[NMF Piano Tracker for Symbolic Audio Effects](/explore/tutschku)[Audio Decomposition using BufNMF](/learn/bufnmf)[Seeding BufNMF with Bases and Activations](/learn/seeding-nmf)[Decomposition Overview](/learn/decomposition-overview)[BufNMFCross](/reference/bufnmfcross)[BufSTFT](/reference/bufstft)[NMFMorph](/reference/nmfmorph)[Sines](/reference/sines)
BufNMF uses non-negative matrix factorisation (NMF) to decompose the magnitudes of a spectrogram into a number of components specified by the user. Each component is represented by the combination of two elements: a spectral template (“basis”, plural: “bases”) and an amplitude envelope (“activation”). Activations and bases can be used in various ways, including to resynthesize the audio of a single decomposed component. NMF is a popular technique in signal processing research for things like source separation and transcription.

### A Useful Simile

NMF could be thought as a vocoder, in which each bandpass filter is instead a finely tuned spectral template, for which its respective activation is the envelope.
[vocoder](https://en.wikipedia.org/wiki/Vocoder#Artistic_effects)
### Example Code
[SuperCollider Example](/learn/bufnmf/bufnmf-overview-example.scd)[Max Example](/learn/bufnmf/bufnmf-overview-example.maxpat)
For an example of audio decomposition using NMF, see the Decomposition with NMF Overview.
[Decomposition with NMF](/learn/bufnmf)
![](image_001.png)

Bases or 'Spectral Templates' of a decomposed drum loop. Each is a spectrum of magnitudes. (blue = kick drum, orange = snare drum, green = hi-hat)

![](image_002.png)

Activations from the same decomposed drum loop, overlaid on the decomposed audio components. (blue = kick drum, orange = snare drum, green = hi-hat)

NMF is a form of unsupervised machine learning. It begins either from seeded activations and bases or in a stochastic state (where the bases and activations of the components are initially random) and works iteratively. Using stochastic gradient descent, NMF tries to find a combination of components that, when summed together, minimize the difference from the original spectrum. In this implementation, the components are reconstructed by masking the original spectrum, such that they will always sum to yield the original sound.

There is no single correct solution to this process. There are different ways of accounting for an spectrum in terms of some set of bases and activations. NMF tends to converge very quickly at first and then level out. Fewer iterations mean less processing, but also less predictable results.

### Outputs

BufNMF can return any or all of the following:
* The bases of the components in the form of a magnitude spectrum for each.
* The activations of the components in the form of an amplitude envelope for each.
* An audio reconstruction of each component.


### Different Modes

Some additional options and flexibility can be found through combinations of the basesMode and actMode arguments.
`basesMode``actMode`
If either or both of these arguments are set to 1, BufNMF expects to be supplied with the corresponding elements (activations or bases) to use as seeds for the decomposition, providing more guided results. It is possible to set both arguments equal to 1.

If either of these arguments are set to 2, BufNMF will not modify the supplied corresponding elements (activations or bases), instead using them as templates to match against. BufNMF will modify the other elements which will represent their best match to the supplied spectrogram, given the fixed elements provided. Thus, you can use the second mode of each together to do resynthesis with activations and bases from disparate or synthetic sources.

For more information on using basesMode and actMode, see the Seeding NMF Overview.
`basesMode``actMode`[Seeding NMF](/learn/seeding-nmf)
If supplying pre-formed data (for actMode and basesMode 1 and 2), it’s up to the user to make sure that the supplied buffers are the right size: bases must be (fft size / 2) + 1 frames and components * input channels channels
activations must be (input frames / hopSize) + 1 frames and components * input channels channels. FFT settings can be set in the BufNMF object.
`actMode``basesMode`**(fft size / 2) + 1****components * input channels****(input frames / hopSize) + 1****components * input channels**
## Related Resources
[Learning the Parts of Objects by Non-Negative Matrix Factorization Lee, Daniel D., and H. Sebastian Seung. 1999. ‘Learning the Parts of Objects by Non-Negative Matrix Factorization’. Nature 401 (6755): 788–91. https://doi.org/10.1038/44565](https://doi.org/10.1038/44565)
### Learning the Parts of Objects by Non-Negative Matrix Factorization

Lee, Daniel D., and H. Sebastian Seung. 1999. ‘Learning the Parts of Objects by Non-Negative Matrix Factorization’. Nature 401 (6755): 788–91.
[Non-Negative Matrix Factorization for Polyphonic Music Transcription Smaragdis and Brown https://ieeexplore.ieee.org/document/1285860](https://ieeexplore.ieee.org/document/1285860)
### Non-Negative Matrix Factorization for Polyphonic Music Transcription

Smaragdis and Brown
