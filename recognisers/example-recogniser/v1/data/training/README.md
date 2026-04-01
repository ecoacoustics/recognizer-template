# Training Data

This directory contains training data references and/or audio files used to train the recogniser.

## Format

Training data can be provided in multiple formats:

### Option 1: JSON Reference File (data.json)

A JSON file containing references to audio files with labeled offsets:

```json
[
  {
    "source": "https://ecosounds.org/audio_recordings/123/original",
    "offsets": [
      {
        "start": 1.0,
        "end": 6.0,
        "label": "call type",
        "species": "Species name"
      }
    ]
  }
]
```

### Option 2: CSV File (data.csv)

A CSV file with columns for audio sources and annotations.

### Option 3: Audio Files

Direct audio files stored in this directory with corresponding annotation files.

## Data Sources

[List the sources of your training data here, including any relevant citations or acknowledgments]
