# FluCoMa CLI

`flucoma-cli` generates command-line executables for core FluCoMa processes; slicing, feature extraction, decomposition, etc...

## Batch Feature Extraction

```shell
# The output .json can be used for clustering, sorting, or ML models
for file in /path/to/corpus/*.wav; do
  mfcc --source "$file" --output "features/${file##*/}.json"
done
```

## Audio Slicing

```shell
# Output slice boundaries can be used to chop audio or additional processing
noveltyslice --source input.wav --threshold 0.15 --output slices.json
```

## Decomposition and Source Seperation

```shell
# Separate a file into harmonic and percussive components
hpss --source input.wav --harmonic out_harm.wav --percussive out_perc.wav

# Perform non-negative matric factorization (NMF) to decompose timbral content
nmf --source input.wav --rank 8 --resynth out_nmf.wav
```

## Best Practices

### Automate with Shell Scripts

```shell
#!/bin/bash
for src in "$1"/*.wav; do
  base=$(basename "$src" .wav)
  hpss --source "$src" --harmonic "out/${base}_h.wav" --percussive "out/${base}_p.wav"
done
```

### Integrate with Python

- Bradbury FTIS library
- combine with NumPy or scikit-learn