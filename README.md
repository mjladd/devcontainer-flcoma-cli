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

```
.
├── audio/          # Place your input audio files here
├── output/         # Processed files will be saved here
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

- [FluCoMa Learn](https://learn.flucoma.org/) - Tutorials and guides
- [FluCoMa Reference](https://learn.flucoma.org/reference/) - Detailed tool documentation
- [FluCoMa Discourse](https://discourse.flucoma.org/) - Community forum

## Notes

- On Apple Silicon Macs, the container runs via x86-64 emulation. You may see a platform warning, but everything works correctly.
- Output files are buffer descriptors. For audio slicing tools, the indices file contains sample positions of detected slice points.

## License

FluCoMa is released under a BSD-style license. See the [FluCoMa repository](https://github.com/flucoma/flucoma-cli) for details.
