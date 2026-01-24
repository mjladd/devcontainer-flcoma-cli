# FluCoMa CLI Devcontainer

A containerized environment for [FluCoMa (Fluid Corpus Manipulation)](https://www.flucoma.org/) command-line tools. This devcontainer provides a ready-to-use setup for audio analysis and decomposition tasks.

## Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [VS Code](https://code.visualstudio.com/) with the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Getting Started

1. Clone or download this repository
2. Open the folder in VS Code
3. When prompted, click **"Reopen in Container"** (or run `Dev Containers: Reopen in Container` from the command palette)
4. Wait for the container to build (first time only)

Once inside the container, all FluCoMa CLI tools are available in your terminal.

## Directory Structure

```shell
.
├── audio/          # Place your input audio files here
├── output/         # Processed files will be saved here
├── flucoma_docs/   # Detailed documentation for all FluCoMa tools
└── .devcontainer/  # Container configuration
```

Files in `audio/` and `output/` persist on your local machine when the container stops.

## Available Tools

| Tool | Description |
|------|-------------|
| `fluid-ampslice` | Amplitude-based onset detection |
| `fluid-ampgate` | Amplitude gating |
| `fluid-audiotransport` | Optimal transport between sounds |
| `fluid-chroma` | Chromagram analysis |
| `fluid-hpss` | Harmonic-percussive source separation |
| `fluid-loudness` | Loudness analysis |
| `fluid-melbands` | Mel-frequency band analysis |
| `fluid-mfcc` | Mel-frequency cepstral coefficients |
| `fluid-nmf` | Non-negative matrix factorization |
| `fluid-noveltyslice` | Novelty-based segmentation |
| `fluid-onsetslice` | Onset detection |
| `fluid-pitch` | Pitch estimation |
| `fluid-sines` | Sinusoidal modeling |
| `fluid-spectralshape` | Spectral shape descriptors |
| `fluid-stats` | Statistical analysis of features |
| `fluid-transients` | Transient extraction |
| `fluid-transientslice` | Transient-based segmentation |

Run any tool with `--help` for detailed options:

```bash
fluid-noveltyslice --help
```

## Usage Examples

### Slice audio by novelty detection

```bash
fluid-noveltyslice -source audio/drums.wav -indices output/slices.wav -threshold 0.5
```

### Separate harmonic and percussive components

```bash
fluid-hpss -source audio/music.wav -harmonic output/harmonic.wav -percussive output/percussive.wav
```

### Extract pitch from audio

```bash
fluid-pitch -source audio/vocal.wav -pitch output/pitch.wav -confidence output/confidence.wav
```

### Decompose audio using NMF

```bash
fluid-nmf -source audio/mix.wav -resynth output/components.wav -components 4
```

### Analyze spectral shape

```bash
fluid-spectralshape -source audio/sound.wav -centroid output/centroid.wav -spread output/spread.wav
```

## Supported Audio Formats

FluCoMa CLI supports common audio formats including:

- WAV
- AIFF
- FLAC

## Documentation

### Local Documentation

This repository includes comprehensive documentation for all FluCoMa tools in the `flucoma_docs/` directory:

#### Analyze Sound

- [ampfeature](flucoma_docs/analyze_sound/ampfeature.md) - Amplitude feature extraction
- [bufcompose](flucoma_docs/analyze_sound/bufcompose.md) - Buffer composition
- [bufstft](flucoma_docs/analyze_sound/bufstft.md) - Short-time Fourier transform
- [chroma](flucoma_docs/analyze_sound/chroma.md) - Chromagram analysis
- [loudness](flucoma_docs/analyze_sound/loudness.md) - Loudness analysis
- [melbands](flucoma_docs/analyze_sound/melbands.md) - Mel-frequency band analysis
- [mfcc](flucoma_docs/analyze_sound/mfcc.md) - Mel-frequency cepstral coefficients
- [nmfmatch](flucoma_docs/analyze_sound/nmfmatch.md) - NMF matching
- [noveltyfeature](flucoma_docs/analyze_sound/noveltyfeature.md) - Novelty feature extraction
- [onsetfeature](flucoma_docs/analyze_sound/onsetfeature.md) - Onset feature extraction
- [pitch](flucoma_docs/analyze_sound/pitch.md) - Pitch estimation
- [spectralshape](flucoma_docs/analyze_sound/spectralshape.md) - Spectral shape descriptors

#### Decompose Sound

- [bufnmf](flucoma_docs/decompose_sound/bufnmf.md) - Non-negative matrix factorization
- [bufnmfseed](flucoma_docs/decompose_sound/bufnmfseed.md) - Seeded NMF
- [hpss](flucoma_docs/decompose_sound/hpss.md) - Harmonic-percussive source separation
- [sines](flucoma_docs/decompose_sound/sines.md) - Sinusoidal modeling
- [transients](flucoma_docs/decompose_sound/transients.md) - Transient extraction

#### Slice Sound

- [ampgate](flucoma_docs/slice_sound/ampgate.md) - Amplitude gating
- [ampslice](flucoma_docs/slice_sound/ampslice.md) - Amplitude-based slicing
- [noveltyslice](flucoma_docs/slice_sound/noveltyslice.md) - Novelty-based segmentation
- [onsetslice](flucoma_docs/slice_sound/onsetslice.md) - Onset detection
- [transientslice](flucoma_docs/slice_sound/transientslice.md) - Transient-based segmentation

#### Transform Sound

- [audiotransport](flucoma_docs/transform_sound/audiotransport.md) - Optimal transport between sounds
- [bufnmfcross](flucoma_docs/transform_sound/bufnmfcross.md) - Cross-synthesis with NMF
- [nmffilter](flucoma_docs/transform_sound/nmffilter.md) - NMF filtering
- [nmfmorph](flucoma_docs/transform_sound/nmfmorph.md) - NMF morphing

#### Analyze Data

- [bufstats](flucoma_docs/analyze_data/bufstats.md) - Buffer statistics
- [dataset](flucoma_docs/analyze_data/dataset.md) - Dataset management
- [datasetquery](flucoma_docs/analyze_data/datasetquery.md) - Dataset querying
- [grid](flucoma_docs/analyze_data/grid.md) - Grid-based analysis
- [kdtree](flucoma_docs/analyze_data/kdtree.md) - K-dimensional tree
- [kmeans](flucoma_docs/analyze_data/kmeans.md) - K-means clustering
- [knnclassifier](flucoma_docs/analyze_data/knnclassifier.md) - K-nearest neighbors classifier
- [knnregressor](flucoma_docs/analyze_data/knnregressor.md) - K-nearest neighbors regressor
- [labelset](flucoma_docs/analyze_data/labelset.md) - Label set management
- [mds](flucoma_docs/analyze_data/mds.md) - Multidimensional scaling
- [mlpclassifier](flucoma_docs/analyze_data/mlpclassifier.md) - Multi-layer perceptron classifier
- [mlpregressor](flucoma_docs/analyze_data/mlpregressor.md) - Multi-layer perceptron regressor
- [normalize](flucoma_docs/analyze_data/normalize.md) - Data normalization
- [pca](flucoma_docs/analyze_data/pca.md) - Principal component analysis
- [plotter](flucoma_docs/analyze_data/plotter.md) - Data plotting
- [robustscale](flucoma_docs/analyze_data/robustscale.md) - Robust scaling
- [skmeans](flucoma_docs/analyze_data/skmeans.md) - Spherical K-means
- [standardize](flucoma_docs/analyze_data/standardize.md) - Data standardization
- [stats](flucoma_docs/analyze_data/stats.md) - Statistical analysis
- [umap](flucoma_docs/analyze_data/umap.md) - Uniform manifold approximation

#### Utility Objects

- [bufcompose](flucoma_docs/utility_objects/bufcompose.md) - Buffer composition
- [bufflatten](flucoma_docs/utility_objects/bufflatten.md) - Buffer flattening
- [bufscale](flucoma_docs/utility_objects/bufscale.md) - Buffer scaling
- [bufselect](flucoma_docs/utility_objects/bufselect.md) - Buffer selection
- [bufselectevery](flucoma_docs/utility_objects/bufselectevery.md) - Periodic buffer selection
- [bufthreaddemo](flucoma_docs/utility_objects/bufthreaddemo.md) - Threading demonstration
- [bufthresh](flucoma_docs/utility_objects/bufthresh.md) - Buffer thresholding

### External Resources

- [FluCoMa Learn](https://learn.flucoma.org/) - Tutorials and guides
- [FluCoMa Reference](https://learn.flucoma.org/reference/) - Online tool documentation
- [FluCoMa Discourse](https://discourse.flucoma.org/) - Community forum

## Notes

- On Apple Silicon Macs, the container runs via x86-64 emulation. You may see a platform warning, but everything works correctly.
- Output files are buffer descriptors. For audio slicing tools, the indices file contains sample positions of detected slice points.

## License

FluCoMa is released under a BSD-style license. See the [FluCoMa repository](https://github.com/flucoma/flucoma-cli) for details.
