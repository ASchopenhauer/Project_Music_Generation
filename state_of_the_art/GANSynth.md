# GANSYNTH: ADVERSARIAL NEURAL AUDIO SYNTHESIS

### Abstract :

* WaveNEt : slow iterative sampling and lack global latent structure
* GANs : global latent conditioning and efficient parallel sampling, but struggle to generate locally-coherent audio waveforms 

## 1 Introduction

### 1.2 Effective Audio Representations for GANs

* most audio waveforms (speech, music) are highly periodic.
* Human perception : highly sensitive to discontinuities and irregularities in periodic waveforms

=> maintaining the regularity of periodic signals over short to intermediate timescales (1ms - 100 ms) is crucial.

* at any time there are typically many different frequencies in a given signal.

=> This is a challenge for a synthesis network, as it must learn all the appropriate frequency and phase combinations and activate them in just the right combination to produce a coherent waveform.

* Phase precession also occurs in situations where filterbanks overlap (window or kernel size < stride).

## 2 Experimental Details

### 2.1 Dataset

NSynth dataset

* 300,000 musical notes from 1,000 different instruments aligned and recorded in isolation.
* a difficult dataset composed of highly diverse timbres and pitches
* highly structured with labels for pitch, velocity, instrument, acoustic qualities.
* each sample is four seconds long, and sampled at 16kHz, giving 64,000 dimensions
* included human evaluations on audio quality => restriction : training on the subset of acoustic instruments and fundamental pitches ranging from MIDI 24-84 (~32-1000Hz) > those timbres are most likely to sound natural to an average listener.
* 70,379 examples from instruments (mostly strings, brass, woodwinds, mallets)
* test/train 80/20 split from shuffled data (original split divided along instrument type).

### 2.2 Architecture and Representation

## 3 Metrics

Evaluating generative models. goals : perceptually-realistic audio generation > hard to formalize

* Human Evaluation
* Number of Statistically-Different Bins (NDB) : measure the diversity of generated examples
* Inception Score (IS) : a de-facto standard in GAN literature
* Pitch Accuracy (PA) and Pitch Entropy (PE)
* Fréchet Inception Distance (FID)

## 4 Results 



--------------------------------------------------------------

### Dataset

* the NSynth dataset : rather than containing all types of audio, consists solely of individual notes from musical instruments across across a range of pitches, timbres, and volumes. all the data is aligned and cropped to reduce variance and focus on fine-scale details, which in audio corresponds to timbre and fidelity. each note is also accompanied by an array of attribute labels to enable exploring
conditional generation.
* CelebA

### Mots-clef :

* neural audio synthesis = training generative models to efficiently produce audio with both high-fidelity and global structure

### Etat de l'art :

* autoregressive models (WaveNet) : solve the scale problem by focusing on the finest scale possible (a single audio sample) and rely upon external conditioning signals for global structure. slow sampling speed. currently the state of the art in generative modeling of audio.
* GANs : great recent success at generating high resolution images. achieve both efficient parallel sampling and global latent control
* attempts to adapt image GAN architectures to generate waveforms in a straightforward manner fail to reach the same level of perceptual fidelity as their image counterparts
* WaveGAN : the current state of the art in waveform generation with GANs

### This work :

* exploring effective representations for non-causal convolutional generation ad typical found in GANs
* the musically-desirable goal of achieving independent control of pitch and timbre.

### Sound

* Harmonic frequencies are multiples of the fundamental,
so low pitches have tightly-spaced harmonics, which can cause blurring and overlap.

### Termes nouveaux / recherches personnelles à effectuer :

* global structure
* fine-scale waveform coherence
* autoregressive models (WaveNet)
* log magnitude
* instantaneous frequencies
* conditioning a stack of transposed convolutions on a latent vector
* instrument timbre
* autoregressive WaveNet autoencoders
* bottleneck spectogram autoencoders
* frame-based regression models
* inverse scattering networks
* VAEs with perceptual priors
* adversarial regularization for domain transfer
* convolutional filters
* learn to form logarithmically-scaled frequency selective filter banks spanning the range of human hearing
* the stride of the frames VS a waveform's periodicity
* a short-time Fourier transform (STFT) : composed of strided filterbanks just like convolutional networks.
* strided filterbanks
* phase precession
* phase vocoder
* log-magnitude spectograms
* automatic / human evaluations
* latent and pitch vectors
* generatte perceptually smooth interpolation in timbre, and consistent timbral identity across pitch
* instruments : strings, brass, woodwinds, mallets
* gradient penalty to promote Lipschitz continuity
* pixel normalization at each layer
* progressive / nonprogressive variants
* Progressive GAN
* conditioning on an additional source of information
* auxiliary classification loss
* the Nyquist frequency
* the STFT frame size and stride
* WaveGAN
* Amazon Mechanical Turk

### Bibliographie :

* Wavenet: A generative model for raw audio : https://arxiv.org/abs/1609.03499
* Adversarial audio synthesis : https://arxiv.org/abs/1802.04208
-> attempts to adapt image GAN architectures to generate waveforms in a straightforward manner
* The original NSynth paper
* A note on the evaluation of generative models : https://arxiv.org/abs/1511.01844


