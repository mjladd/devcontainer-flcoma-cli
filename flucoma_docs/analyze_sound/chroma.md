# Chroma

# Chroma

A histogram of pitch classes

Chroma is an audio analysis that models the composition of pitch classes in a sound. In this context, a pitch class are bins of the spectrum derived through an FFT. By default, the Chroma algorithm will return 12 pitch classes, which conveniently maps on to a western model of tonal harmony (C, C#, D, D# etc…). The number of pitch classes can be changed, allowing you to tune the algorithm to return more or less granular bins in terms of what pitch class they represent.

Chroma is not a fundamental pitch tracker and won’t tell you about the structure of pitch classes, only their relative strength to each other. Furthermore, the entire spectrum is wrapped into a single octave, meaning any notion of register is lost. As such it is useful for perhaps identifying rough tonal components a sound might be comprised of, but nothing about their relationship to each other as a chord.

## Related Resources

### Chroma and Shepherd Tones

An article describing the relationship between Shephard tones and Chroma
