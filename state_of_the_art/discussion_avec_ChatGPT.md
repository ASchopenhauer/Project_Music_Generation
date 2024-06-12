Eléments qui m'intéressent issus de cette discussion, réorganisés.

## Représentations musicales

Pour que les GAN puissent travailler avec la musique, il est important de choisir une représentation appropriée :

* MIDIs : informations sur les notes, leur durées, autres aspects musicaux. Peuvent être convertis en séquences de notes et durées que les GAN peuvent apprendre
* Spectogrammes : images qui représentent les fréquences sonores au fil du temps. peuvent être utilisés avec des GAN basés sur des CNN pour capturer les caractéristiques musicales.
* Pianorolls : représentation visuelle des notes de musiques jouées au fil du temps, souvent utilisée dans les logiciels de production musicale.

représentations symboliques de la musique (MIDI) VS formes d'onde audio

## Modèles et extensions

* GANs conditionnels : générer de la musique conditionnée sur des infromations supplémentaires (genre musical, style particulier)
* Wasserstein GAN : fonction de perte différente pour stabiliser l'entraînement et produire des résultats de meilleure qualité
* MuseGAN : modèle spécifique pour la génération de musique qui utilis eune architecture de GAN pour créer des morceaux polyphoniques (avec plusieurs instruments)

## GANsynth

### Problème de la "Phase Precession"

1) Régularité des Signaux Périodiques : La musique et les sons, en général, sont composés de nombreuses fréquences qui se répètent régulièrement.
2) Filtres Convolutifs et Audio : Les GAN utilisent des filtres convolutifs (comme des fenêtres glissantes) pour analyser et générer des sons. Un filtre convolutif regarde une petite portion du signal (comme une petite fenêtre) et avance par petits pas réguliers (strides).
3) Alignement de la Phase : Si le pas de cette fenêtre (stride) ne correspond pas exactement à la longueur de la vague, l'alignement de la vague change au fur et à mesure que la fenêtre se déplace. C'est ce qu'on appelle la "phase precession".

### Solution Proposée : Fréquence Instantanée (Instantaneous Frequency, IF)

1) Unwrapping de la Phase : "dérouler" la phase de l'onde. La phase est comme l'angle d'une roue qui tourne. Si l'onde est une sinusoïde, la phase monte et descend régulièrement. Quand on déroule la phase (ajoute 2π2π chaque fois qu'on fait un tour complet), on transforme cette oscillation périodique en une ligne droite qui montre la progression régulière de la phase.
2) Fréquence Instantanée (IF) : La fréquence instantanée est la dérivée de cette phase déroulée par rapport au temps. Cela signifie qu'elle mesure comment la fréquence de l'onde change à chaque instant. Pour une onde régulière, cette fréquence instantanée est constante.




----------------------------------------------------------------------------------

## Prompts

1) Comment peut-on générer de la musique en utilisant des GAN ? Fais comme si je n'avais aucune connaissance dans le domaine de la musique et dans celui du Machine Learning

2) Merci ! Pourrais-tu me donner plus de détails techniques ?

3) Je suis en train de lire ce paper à ce sujet : 
GANSYNTH: ADVERSARIAL NEURAL AUDIO SYNTHESIS
de Jesse Engel, Kumar Krishna Agrawal, Shuo Chen, Ishaan Gulrajani, Chris Donahue, & Adam Roberts
est-ce que tu en as entendu parler ?

4) Dans ce papier il y a le passage suivant : "1.2 EFFECTIVE AUDIO REPRESENTATIONS FOR GANS
Unlike images, most audio waveforms—such as speech and music—are highly periodic. Convolutional
filters trained for different tasks on this data commonly learn to form logarithmically-scaled
frequency selective filter banks spanning the range of human hearing (Dieleman&Schrauwen, 2014;
Zhu et al., 2016). Human perception is also highly sensitive to discontinuities and irregularities in
periodic waveforms, so maintaining the regularity of periodic signals over short to intermediate
timescales (1ms - 100ms) is crucial. Figure 1 shows that when the stride of the frames does not
exactly equal a waveform’s periodicity, the alignment (phase) of the two precesses over time. This
condition is assured as at any time there are typically many different frequencies in a given signal.
This is a challenge for a synthesis network, as it must learn all the appropriate frequency and
phase combinations and activate them in just the right combination to produce a coherent waveform.
This phase precession is exactly the same phenomena observed with a short-time Fourier transform
(STFT), which is composed of strided filterbanks just like convolutional networks. Phase precession
also occurs in situations where filterbanks overlap (window or kernel size < stride).
In the middle of Figure 1, we diagram another approach to generating coherent waveforms loosely
inspired by the phase vocoder (Dolson, 1986). A pure tone produces a phase that precesses. Unwrapping
the phase, by adding 2 whenever it crosses a phase discontinuity, causes the precessing
phase to grow linearly. We then observe that the derivative of the unwrapped phase with respect to
time remains constant and is equal to the angular difference between the frame stride and signal periodicity.
This is commonly referred to as the instantaneous angular frequency, and is a time varying
measure of the true signal oscillation. With a slight abuse of terminology we will simply refer to
it as the instantaneous frequency (IF) (Boashash, 1992). Note that for the spectra at the bottom of
Figure 1, the pure harmonic frequencies of a trumpet cause the wrapped phase spectra to oscillate at
different rates while the unwrapped phase smoothly diverges and the IF spectra forms solid bands
where the harmonic frequencies are present."

Il semble décrire un problème important mais j'ai du mal à le comprendre. Souviens toi que je n'ai aucune connaissance dans le domaine, et pas non plus en physique.

5) Merci, je crois avoir compris le problème. Est-ce que tu pourrais cependant m'expliquer plus en détails la solution proposée ? Je ne sais pas très bien ce qu'est une phase. Si c'est possible tu pourrais peut-être illustrer ton propos par des images ?
