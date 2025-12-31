# NMFMorph

Cross-synthesis using non-negative Matrix Factorisation (NMF)

NMFMorph uses a technique called Optimal Transport to provide real time interpolation between `source` and `target` bases of a [BufNMF](/reference/bufnmf) decomposition. Using Optimal Transport for the spectral interpolation provides richer results than a simple linear interpolation between spectral shapes. Activations from a BufNMF analysis are also provided to activate the interpolated spectral information through time.

If `autoassign` is set to 1, NMFMorph will determine which bases from `source` and `target` best match each other, and will interpolate between the matched pairings. If `autoassign` is set to 0, NMFMorph will interpolate between bases in the order they have been provided.

## Related Resources

### [Audio Morphing using Matrix Decomposition and Optimal Transport](https://pure.hud.ac.uk/en/publications/audio-morphing-using-matrix-decomposition-and-optimal-transport)

Paper by Roma, Green, & Tremblay describing the NMFMorph algorithm. (begins on PDF page 165 of the DAFx2020 Proceedings)

### [Audio Transport: A Generalized Portamento via Optimal Transport](https://arxiv.org/pdf/1906.06763.pdf)

The paper which inspired this implementation

### [Computational Optimal Transport](https://arxiv.org/pdf/1803.00567.pdf)

For those who really want to get down in the details

### [Optimal transport: a hidden gem that empowers today's machine learning](https://towardsdatascience.com/optimal-transport-a-hidden-gem-that-empowers-todays-machine-learning-2609bbf67e59)

A relatively easy to approach article on applications of optimal transport
