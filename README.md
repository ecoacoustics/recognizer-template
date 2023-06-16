# recognizer-template

A template repository for publishing an ecoacoustics or bioacoustics recognizer

This template is an attempt to set up a standard layout for publishing recognizers.

You should fork (make a copy) of this repository. When it is forked, you'll
get your own copy, owned by you, that you can change. 

You can also start a new repository using this template by clicking the button that says _Use this template_ and then selecting _Create a new repository_.

## Getting started

### Q: I'm not ready to publish my recognizer

After forking this repository you can make your copy private. See
[setting repository visibility](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility).

### Q: What rights do I have after I publish my recognizer?

That's up to you. If make your repository private, only you have access.

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

## Directory structure

```
.
├── LICENSE.md      - the license for this recognizer
├── README.md       - the first page people see when they visit the repository
├── CITATION.cff    - citation information for this repository
├── src             - [optional] if you want to publish code with your recognizer,
│                     put it in this folder
├── artefacts       - [optional] if you have a trained model or other artifacts
│                     produced while developing your recognizer, put them in this folder
├── data            - contains or describes your data set
│   ├── training
│   │   ├── xxx     - the name of the species or target you are training on
│   │   ├── yyy     - [optional] further folders containing training samples
│   │   └── zzz     
│   ├── test
│   │   ├── xxx     - the name of the species or target you are evaluating your recognizer against
│   │   ├── yyy     - [optional] further folders containing testing samples
│   │   └── zzz     
|   └── README.md   - information on the included datasets or on how to obtain them
```

# The `data` folder

Storing data in a repository is not always the right choice. See the [_Tips for audio data_](#tips-for-audio-data) section below.

In each folder where it is relevant you should include:

1. Small sets of audio samples 
2. A README.md containing
  - provenance of any data included
  - instructions on how to obatain more data
3. Any scripts needed to download data from remote repositories

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
- Cloud storage options like DropBox, CloudStor, OneDrive, etc.
- Commersial services like Amazon S3, Google Cloud Storage, etc.

Egret, included in this template, can download samples from the internet for you.
