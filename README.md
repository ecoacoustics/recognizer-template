# recognizer-template

A template repository for publishing an ecoacoustics or bioacoustics recognizer.

This template is an attempt to set up a standard layout for publishing recognizers.

## Contents

- [Getting started](#getting-started)
- [Layout](#layout)
- [FAQ](#faq)
- [Minting a DOI with Zenodo](#minting-a-doi-with-zenodo)
- [Tips for audio data](#tips-for-audio-data)

## Getting started

You should fork (make a copy) of this repository. When it is forked, you'll
get your own copy, owned by you, that you can change.

In GitHub, you can use the _Use this template_ button to create your own repository based on this template. See [creating a repository from a template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template) for more information.

![Use this template button](https://docs.github.com/assets/cb-76823/mw-1440/images/help/repository/use-this-template-button.webp)

You can also start a new repository using this template by clicking the button that says _Use this template_ and then selecting _Create a new repository_.

## Layout

```
.
├── LICENSE                                - the license for this recogniser
├── README.md                              - this file. Change this to describe your recogniser and how to use it.
├── CITATION.cff                           - citation information for this repository (repository-level)
├── src                                    - source code for this recogniser including code, container specifications, and tests
└── recognisers                            - contains all recognisers in this repository
    └── <name>                             - recogniser name (species, group, or general name). Can have multiple recognisers in a single repository.
        ├── README.md                      - [optional] list of targeted species/call types
        │                                    and version history with performance metrics
        ├── CITATION.cff                   - [optional] if attribution varies per recogniser
        ├── src                            - [optional] code specific to this recogniser
        └── <version>                      - version number (e.g., v1, v2, v3)
            ├── artifacts
            │   └── <artifact>             - the "recogniser". Could be a model, a tflite file, or a JSON file.
            ├── data
            │   ├── training               - training data references and/or audio files
            │   │   ├── data.json          - JSON format training data (see example below)
            │   │   ├── data.csv           - [or] CSV format training data
            │   │   └── [audio files]      - [or] direct audio files
            │   └── test
            │       └── ...                 - test data in the same format as training data
            ├── src                            - [optional] code specific to this recogniser version
```

### The `recognisers` folder

Each recognizer is organized in its own directory with versioned subdirectories. This allows multiple recognizers to be published in a single repository and enables clear version tracking.

### Recognizer directories

Each recogniser directory should  contain:

- **README.md**: A description of the recogniser, targeted species/call types, and version history with performance metrics
  - **Targeted species / call types**: A clear list of what the recognizer detects
  - **Version history**: For each version, document:
    - Significant changes between versions (e.g., new data sources, methodology changes)
    - Performance metrics (precision, recall, F1 score, etc.)
    - Date of release
    - Any breaking changes
- **src/**: [Optional] Code specific to this recognizer
- **CITATION.cff**: [Optional] If attribution differs from the repository-level citation
- **Version directories**: Each version of the recognizer should be stored in its own subdirectory (e.g., v1, v2, etc.) to maintain a clear history of changes and performance over time.

### Version Directories

Versions should increment when:

- After you have published a recogniser or results
  - You should maintain old major versions for reproducibility
- AND
  - Adding new training or test data
  - Changing methodology or model architecture
  - Making significant improvements
- While you are developing your recogniser you should just update the same version (e.g., v1) until you are ready to publish.
- Version numbers can take whatever format you like, but
  - we recommend a simple monotonic increasing format like v1, v2, v3, etc.
  - Or semantic versioning (e.g., v1.0.0, v1.1.0, etc.) if you prefer.

Each version directory contains:

- **artifacts/**: Contains the "recogniser" artifact, which could be a model file, a tflite file, a JSON file, or any other format that represents the recognizer.
- **data/training/**: Training data as JSON references, CSV, or audio files
  - Format example for `data.json`:

    ```json
    [
      {
        "source": "https://ecosounds.org/audio_recordings/123/original",
        "offsets": [
          {"start": 1.0, "end": 6.0, "label": "call_type", "species": "Species name"}
        ]
      }
    ]
    ```

- **data/test/**: Test data in the same format as training data
- **src/**: [Optional] Code specific to this recognizer version

## FAQ

### Q: I'm not ready to publish my recognizer

After forking this repository you can make your copy private. See
[setting repository visibility](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility).

### Q: What rights do I have after I publish my recognizer?

That's up to you. If make your repository private, only you have access.

### Q: What license should I use?

When it is time to publish you recognizer, you'll need to choose an appropriate
license. This repository by default uses the Apache 2.0 license but there are a
number of suitable licenses available. See [choosing a license](https://choosealicense.com/).

Other good choices are:

- the [Creative Commons Attribution-ShareAlike 4.0 International](https://choosealicense.com/licenses/cc-by-sa-4.0/) license 
  - This is a better choice for your data rather than your code. Different licenses are good for different things. The [choosing a license](https://choosealicense.com/) link can help you choose.
- and the [Academic Free License 3.0](https://choosealicense.com/licenses/afl-3.0/)

### Q: What is this CITATION.cff file?

The citation file is a new standard recognized by GitHub and other tools as the
place to put citation information. You should modify the citation file in your
forked repository so that the information is correct.

See help about [CITATION](https://docs.github.com/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-citation-files)
files.

### Q: How do I work with my repository on my computer?

You can clone your repository. See [cloning a repository](https://help.github.com/articles/cloning-a-repository/).

We recommend using [GitHub Desktop](https://desktop.github.com/).

### Q: Will this FAQ be in my published recognizer's readme?

Yeah, but you can delete it! Open the README.md file now can delete this sentence.

### Q: This template seems incomplete...

It is! This template is a work in progress. You can help by adding more documentation
or by suggestion improvements.

### Q: Where can I get help?

Head on over to the [discussions](https://github.com/ecoacoustics/recognizer-template/discussions)
tab and ask us a question!

## Minting a DOI with Zenodo

A DOI (Digital Object Identifier) gives your recognizer a permanent, citable
reference. [Zenodo](https://zenodo.org/) is a free, open repository hosted by
CERN that integrates directly with GitHub to automatically archive your
repository and assign a DOI.

### Steps to mint a DOI

1. **Create a Zenodo account**: Go to [zenodo.org](https://zenodo.org/) and sign
   in with your GitHub account.
2. **Link your repository**: In Zenodo, go to your
   [GitHub settings](https://zenodo.org/account/settings/github/) and toggle the
   switch to enable your recognizer repository.
3. **Create a release**: Back in GitHub, [create a new release](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository)
   for your repository (e.g., `v1.0.0`). Zenodo will automatically archive
   the release and mint a DOI.
4. **Get your DOI badge**: After the release is archived, visit your Zenodo
   record page to find the DOI and a badge you can add to your README.
5. **Update your CITATION.cff**: Add the DOI to your `CITATION.cff` file so
   that citations point to the permanent DOI. For example:

   ```yaml
   identifiers:
     - type: doi
       value: "10.5281/zenodo.XXXXXXX"
       description: "Zenodo archive of this recognizer"
   ```

### Tips

- Zenodo creates a **concept DOI** that always resolves to the latest version,
  as well as **version-specific DOIs** for each release. Use the concept DOI in
  your README badge and the version-specific DOI when citing a particular
  release.
- Make sure your repository has a license before creating a release—Zenodo will
  include it in the archived metadata.
- You can edit the metadata (title, authors, description) on Zenodo after the
  archive is created.

## Tips for audio data

You don't have to store your audio data in your repository. If you don't, you
need to ensure that your data is accessible and stored in an appropriate place.

You can store small datasets in this repository.

Don't add audio files directly to Git, rather, use [Git-LFS](https://git-lfs.github.com) which
makes it look like you are adding files directly to Git. GitHub offers 1GB of
bandwidth per month per user for free. I'd suggest keeping no more than 100MiB
of data directly in the repository.

For larger datasets you can use:

- An ecoacoustics repository
    - like Ecosounds, the A2O, or ...others...
- A bioacoustics repository
    - like Xeno Canto
- Cloud storage options like DropBox, OneDrive, etc.
- Commercial services like Amazon S3, Google Cloud Storage, etc.

Egret, included in this template, can download samples from the internet for you.
