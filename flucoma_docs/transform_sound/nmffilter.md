

# NMFFilter
Decomposes and resynthesises a signal against a set of spectral templates






![](images/flowchart.jpg)




### Example Code[](#example-code)
MaxSuperCollider





### Audio stream output based on basis 1:[](#audio-stream-output-based-on-basis-1)
Your browser does not support the audio tag.The output audio of the original drum loop filtered by basis 1 in NMFFilter

### Audio stream output based on basis 2:[](#audio-stream-output-based-on-basis-2)
Your browser does not support the audio tag.The output audio of the original drum loop filtered by basis 2 in NMFFilter

### Audio stream output based on basis 3:[](#audio-stream-output-based-on-basis-3)
Your browser does not support the audio tag.The output audio of the original drum loop filtered by basis 3 in NMFFilterThis will give us very similar sounding results as BufNMF’s resynthesized buffer–the difference here is that results are produced in real-time. This means that one could send a live input of this drummer and (hopefully) get similarly successful results decomposing the drum loop into the individual drum instruments in real-time.



## Audio Input From a Different Source[](#audio-input-from-a-different-source)
One could also send a different audio signal through these bases using NMFFilter. Here we’ll use an excerpt from an ensemble recording that also has kick drum, snare drum, and hi-hat.



### Original ensemble recording:[](#original-ensemble-recording)
Your browser does not support the audio tag.Source ensemble recording.

### Audio stream output based on basis 1:[](#audio-stream-output-based-on-basis-1-1)
Your browser does not support the audio tag.The output audio of the ensemble recording filtered by basis 1 of the drum loop BufNMF analysis

### Audio stream output based on basis 2:[](#audio-stream-output-based-on-basis-2-1)
Your browser does not support the audio tag.The output audio of the ensemble recording filtered by basis 2 of the drum loop BufNMF analysis

### Audio stream output based on basis 3:[](#audio-stream-output-based-on-basis-3-1)
Your browser does not support the audio tag.The output audio of the ensemble recording filtered by basis 3 of the drum loop BufNMF analysisNMFFilter has relatively well separated the hi hat, kick drum, and snare drum sounds in this song, because those are the bases from the drum loop. One can hear other sounds from the song mixed into these streams as well, as all of the sound from the original will be represented



## Filtering Noise[](#filtering-noise)
Sending some pink noise through NMFFilter can provide another way of hearing and thinking about what it offers. Below are short clips of steady volume pink noise going through the three bases used above.

Your browser does not support the audio tag.Pink noise filtered by basis 1 of the drum loop BufNMF analysisYour browser does not support the audio tag.Pink noise filtered by basis 2 of the drum loop BufNMF analysisYour browser does not support the audio tag.Pink noise filtered by basis 3 of the drum loop BufNMF analysisOne can hear that the noise is filtered by the spectral templates of the bases (seen below as spectra).


![](images/01_Bases_plot.jpg)


[](/reference/nmffilter/01_Bases_plot.jpg)The bases used above seen as spectra. x axis = FFT bins; y axis = magnitudes