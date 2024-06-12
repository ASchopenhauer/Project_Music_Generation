# GANSYNTH: ADVERSARIAL NEURAL AUDIO SYNTHESIS

### Abstract :

* WaveNEt : slow iterative sampling and lack global latent structure
* GANs : global latent conditioning and efficient parallel sampling, but struggle to generate locally-coherent audio waveforms 

### 1.2 Effective Audio Representations for GANs

* most audio waveforms (speech, music) are highly periodic.
* Human perception : highly sensitive to discontinuities and irregularities in periodic waveforms

=> maintaining the regularity of periodic signals over short to intermediate timescales (1ms - 100 ms) is crucial.

* at any time there are typically many different frequencies in a given signal.

=> This is a challenge for a synthesis network, as it must learn all the appropriate frequency and phase combinations and activate them in just the right combination to produce a coherent waveform.

--------------------------------------------------------------

### Dataset

* the NSynth dataset : rather than containing all types of audio, consists solely of individual notes from musical instruments across across a range of pitches, timbres, and volumes. all the data is aligned and cropped to reduce variance and focus on fine-scale details, which in audio corresponds to timbre and fidelity. each note is also accompanied by an array of attribute labels to enable exploring
conditional generation.
* CelebA

### Mots-clef :

* neural audio synthesis = training generative models to efficiently produce audio with both high-fidelity and global structure

### Etat de l'art :

* autoregressive models (WaveNet) : solve the scale problem by focusing on the finest scale possible (a single audio sample) and rely upon external conditioning signals for global structure. slow sampling speed.
* GANs : great recent success at generating high resolution images. achieve both efficient parallel sampling and global latent control
* attempts to adapt image GAN architectures to generate waveforms in a straightforward manner fail to reach the same level of perceptual fidelity as their image counterparts

### This work :

* exploring effective representations for non-causal convolutional generation ad typical found in GANs

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

### Bibliographie :

* Wavenet: A generative model for raw audio : https://arxiv.org/abs/1609.03499
* Adversarial audio synthesis : https://arxiv.org/abs/1802.04208
-> attempts to adapt image GAN architectures to generate waveforms in a straightforward manner
* The original NSynth paper



