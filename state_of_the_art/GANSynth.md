# GANSYNTH: ADVERSARIAL NEURAL AUDIO SYNTHESIS

### Abstract :

* WaveNEt : slow iterative sampling and lack global latent structure
* GANs : global latent conditioning and efficient parallel sampling, but struggle to generate locally-coherent audio waveforms 

### Dataset

* the NSynth dataset

### Mots-clef :

* neural audio synthesis = training generative models to efficiently produce audio with both high-fidelity and global structure

### Etat de l'art :

* autoregressive models (WaveNet) : solve the scale problem by focusing on the finest scale possible (a single audio sample) and rely upon external conditioning signals for global structure. slow sampling speed.
* GANs : great recent success at generating high resolution images. achieve both efficient parallel sampling and global latent control
* attempts to adapt image GAN architectures to generate waveforms in a straightforward manner fail to reach the same level of perceptual fidelity as their image counterparts

### Termes nouveaux :

* global structure
* fine-scale waveform coherence
* autoregressive models (WaveNet)
* log magnitude
* instantaneous frequencies
* conditioning a stack of transposed convolutions on a latent vector

### Bibliographie :

* Wavenet: A generative model for raw audio : https://arxiv.org/abs/1609.03499
* Adversarial audio synthesis : https://arxiv.org/abs/1802.04208
> attempts to adapt image GAN architectures to generate waveforms in a straightforward manner

