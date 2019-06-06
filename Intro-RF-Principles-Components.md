# 1. What is 'Radio Frequency', and why do we use it?

When we think of electricity, we naturally think of wires. From high-voltage transmission lines to tiny traces on a printed circuit board, wires are still the fundamental means of transferring electrical energy from one location to another.

But history has consistently demonstrated that human beings are rarely, if ever, satisfied with the fundamental way of doing things, and thus we should not be surprised to learn that the proliferation of electricity was followed by widespread efforts to free electrical functionality from the constraints of physical interconnections.

There are various ways to incorporate “wireless” functionality into an electrical system. One of these is the use of electromagnetic radiation, which is the basis for RF communication. However, it’s important to recognize that electromagnetic radiation is not unique in its ability to extend electrical circuitry into the wireless domain. Anything that can travel through a nonconductive material—mechanical motion, sound waves, heat—could be used as a (perhaps crude) means of converting electrical energy into information that does not rely on conductive interconnections.

![RF1](https://www.allaboutcircuits.com/uploads/articles/RFT_page1_1.JPG)

`Carefully manipulated sinusoidal voltage (or current) signals are the foundation of the modern wireless age.`

[Appendix 1 - Sine Waves](https://www.google.com "Appendix 1 - The Basic Mathematics of Sine Waves")


With this in mind, we can ask ourselves the more relevant questions: Why is electromagnetic radiation the preferred method? Why are other types of wireless communication of such secondary importance? Before we answer these questions, let’s make sure we understand what electromagnetic radiation is.

## Fields and Waves

You could spend years studying the details of electromagnetism. Fortunately, you don’t need that sort of expertise to successfully design and implement RF circuits. But you do need to have a basic idea of the mysterious energy being emitted from your device’s antenna.

As the name implies, electromagnetic radiation involves both electric fields and magnetic fields. If you have voltage—such as the voltage across the impedance of an antenna—you have an electric field (from a mathematical standpoint, electric field is proportional to the spatial rate of change of voltage). If you have electric current—such as the current passing through the impedance of an antenna—you have a magnetic field (the strength of the field is proportional to the magnitude of the current).

The electric and magnetic fields are present even if the magnitude of the voltage or current is constant. However, these fields would not propagate. If we want a wave that will propagate out into the universe, we need *changes* in voltage and current.

![RF2](https://www.allaboutcircuits.com/uploads/articles/RFT_ch1_page1_2-_CON-452_rs.jpg)

`The electric and magnetic components of an electromagnetic wave are represented as perpendicular sinusoids.`

The key to this propagation phenomenon is the self-sustaining relationship between the electric and magnetic components of electromagnetic radiation. A changing electric field generates a magnetic field, and a changing magnetic field generates an electric field. This mutual regeneration is manifested as a distinct entity, namely, an electromagnetic wave. Once generated, this wave will travel outward from its source, careening day after day, at the speed of light, toward the depths of the unknown.

## Creating EMR vs. Controlling EMR

Designing an entire RF communication system is not easy. However, it is extremely easy to generate electromagnetic radiation (EMR), and in fact you generate it even when you don’t want to. Any time-varying signal in any circuit will generate EMR, and this includes digital signals. In most cases this EMR is simply noise. If it’s not causing any trouble, you can ignore it. In some cases it can actually interfere with other circuitry, in which case it becomes EMI (electromagnetic interference).

We see, then, that RF design is not about merely generating EMR; rather, RF design is the art and science of generating and manipulating and interpreting EMR in a way that allows you to reliably transfer meaningful information between two circuits that have no direct electrical connection.

# Why EMR?
Now let’s return to the question of why EMR-based systems are so common compared to other forms of wireless communication. In other words, why does “wireless” almost always refer to RF when various other phenomena can transfer information without the aid of wires? There are a few reasons:

## (a) Agility
EMR is a natural extension of the electrical signals used in wired circuits. Time-varying voltages and currents generate EMR whether you want them to or not, and furthermore, that EMR is a precise representation of the AC components of the original signal.

![RF3](https://www.allaboutcircuits.com/uploads/articles/RFT_page1_3.JPG)

`Each portion of this intricate QPSK waveform transfers two bits of digital information.`

Let’s consider an extreme (and completely impractical) counterexample: a heat-based wireless communication system. Imagine that a room contains two separate devices. The transmitter device heats up the room to a certain temperature based on the message it wants to send, and the receiver device measures and interprets the ambient temperature. This is a sluggish, awkward system because the temperature of the room cannot precisely follow the variations of an intricate electrical signal. EMR, on the other hand, is highly responsive. Transmitted RF signals can faithfully reproduce even the complex, high-frequency waveforms used in state-of-the-art wireless systems.

## (b) Speed
In AC-coupled systems, the rate at which data can be transferred depends on how quickly a signal can experience variations. In other words, a signal must be doing something—such as increasing and decreasing in amplitude—in order to convey information. It turns out that EMR is a practical communication medium even at very high frequencies, which means that RF systems can achieve extremely high rates of data transfer.

## (c) Range
The pursuit of wireless communication is closely linked to the pursuit of long-distance communication; if the transmitter and receiver are in close proximity, it is often simpler and more cost-effective to use wires. Though the strength of an RF signal decreases according to the inverse-square law, EMR—in conjunction with modulation techniques and sophisticated receiver circuitry—still has a remarkable ability to transfer usable signals over long distances.

![RF4](https://www.allaboutcircuits.com/uploads/articles/RFT_page1_4.JPG)

`The intensity of EMR decreases exponentially as the emitted energy propagates outward in all directions.`

## (d) No Line of Sight Needed
The only wireless communication medium that can compete with EMR is light; this is perhaps not too surprising, since light is actually very-high-frequency EMR. But the nature of optical transmission highlights what is perhaps the definitive advantage offered by RF communication: a clear line of sight is not required.

Our world is filled with solid objects that block light—even very powerful light. We have all experienced the intense brightness of the summer sun, yet that intensity is greatly reduced by nothing more than a thin piece of fabric. In contrast, the lower-frequency EMR used in RF systems passes through walls, plastic enclosures, clouds, and—though it may seem a bit strange—every cell in the human body. RF signals are not completely unaffected by these materials and, in some cases, significant attenuation can occur. But compared to light, (lower-frequency) EMR goes just about anywhere.


## [1. In Summary:](https://github.com/markdown-it/markdown-it-container)

+ “RF” refers to the use of electromagnetic radiation for transferring information between two circuits that have no direct electrical connection.
+ Time-varying voltages and currents generate electromagnetic energy that propagates in the form of waves. We can wirelessly transfer analog and digital data by manipulating and interpreting these waves.
+ EMR is the dominant form of wireless communication. One alternative is the use of light (such as in fiber optics), but RF is much more versatile because lower-frequency EMR is not blocked by opaque objects.


# 2. The Frequency Domain

*What is the frequency domain? And why is it so valuable for RF design, analysis, and testing?*

Perhaps one of the most fundamental steps in the process of gaining proficiency in RF design is learning to think in the frequency domain. For most of us, the vast majority of our early experience with electrical circuits and signals remains within the context of voltages and currents that are either static or dynamic with respect to time. For example, when we measure the voltage of a battery with a multimeter, we have a static quantity, and when we look at a sinusoidal voltage on an oscilloscope, we have a time-varying quantity.

RF, on the other hand, is a world of frequencies. We do not send static voltages to antennas, and the oscilloscope is usually not an effective tool for capturing and visualizing the types of signal manipulation that are involved in wireless communication. Indeed, we can say that the time domain is simply not a convenient place for the design and analysis of RF systems. We need a different paradigm.

## Fourier
The Fourier transform is the mathematical path that leads to this alternative paradigm, because it provides a precise method of describing a signal according to its frequency content.

![RF5](https://www.allaboutcircuits.com/uploads/articles/RFT_ch1_pg2_1.JPG)

`This diagram shows some of the frequency content (red) in a square wave (blue).`

In the context of RF, the Fourier transform can take extremely complex signal variations and translate them into frequency-domain components that are far more informative than the original time-domain waveform.

The details involved in computing the Fourier transform or the discrete Fourier transform (DFT) are not trivial; however, this is not something we have to worry about at this point. You can understand and employ frequency-domain techniques even if you know very little about the underlying mathematical procedures.

The Fourier transform produces expressions that reveal a signal’s frequency content, and the DFT produces corresponding numerical data. However, in the context of practical engineering, a graphical representation is often much more convenient. Eventually these frequency-domain plots become as normal and intuitive as an oscilloscope trace.

## The “Spectrum”
A frequency-domain plot is referred to as a spectrum. The idealized spectrum for a 1 MHz sinusoid is as follows:

![RF6](https://www.allaboutcircuits.com/uploads/articles/RFT_ch1_pg2_2.JPG)

The vertical arrow indicates that a certain amount of “energy” is present at 1 MHz. The line portion of the arrow is so thin because this idealized signal has absolutely no other frequency components—all the energy is concentrated exactly at 1 MHz.

If we used a summing circuit to combine this perfect 1 MHz sinusoid with a perfect 2 MHz sinusoid, the spectrum would be the following:

![RF7](https://www.allaboutcircuits.com/uploads/articles/RFT_ch1_pg2_3.JPG)

This frequency-domain plot provides very clear data regarding the frequency characteristics of our new signal. If you are primarily interested in the non-instantaneous frequency-related behavior of your circuit, the spectrum gives you the information you need. In contrast, the time-domain waveform is not straightforward:

![RF8](https://www.allaboutcircuits.com/uploads/articles/RFT_ch1_pg2_4_2.JPG)

It is far less obvious that this trace is the result of adding one sinusoidal quantity of frequency f to a second sinusoidal quantity of frequency *2f*.

## Ideal vs. Real
The thin-vertical-arrow frequency components shown above are mathematical constructs; real-world spectral measurements look more like this:

![RF9](https://www.allaboutcircuits.com/uploads/articles/RFT_ch1_pg2_5_2.JPG)

Why the discrepancy? First of all, the resolution of the measurement system is limited, and such limitations inherently compromise whatever “ideal” qualities might be present in the original signal. But even if we had an infinitely accurate measuring device, the spectrum would differ from the mathematical version because of noise.

The only type of signal that could produce the “pure” spectral components shown in the previous section is a perfect sinusoid—i.e., no noise and no variations in period or amplitude. Any deviation from the characteristics of a perfect sinusoid would introduce additional frequency components.

An intuitive example is phase noise: It is not practical to expect a real-world oscillator to always produce the exact same frequency; inevitably there will be (hopefully small) variations in the actual duration of a cycle, and this is called phase noise. If you collect data covering one thousand cycles and then perform spectral analysis, you are effectively averaging the frequency content of those one thousand cycles. The result will be the spectral shape shown above; the width of the waveform corresponds to the averaged deviation from the nominal frequency.

## Spectral Measurements
Frequency-domain plots provide a very convenient means of discussing and analyzing RF systems. Modulation schemes, interference, harmonic distortion—even basic spectra drawn on a piece of scratch paper can really help to clarify a situation.

But we’ll generally need something more sophisticated when it comes time to successfully design an RF system. More specifically, we need something that gives us the spectral characteristics of an actual signal. This is important for characterizing the functionality of an existing system, but usually the more pressing need is diagnosis and resolution—i.e., why is this device not working, and how can we fix it.

Digital oscilloscopes offer “FFT” (fast Fourier transform) functionality, and this is one way to obtain spectral measurements. However, the tool of choice for real-world frequency analysis is called a spectrum analyzer. This is a piece of test equipment that is specifically designed to accept a high-frequency input signal and display the frequency-domain representation of this signal. Acquiring a bit of hands-on experience with a spectrum analyzer is an important initial step in becoming familiar with practical aspects of RF engineering.

![RF10](https://www.allaboutcircuits.com/uploads/articles/spectrum_analyzer.jpg)

## [2. In Summary:](https://github.com/markdown-it/markdown-it-container)

+ Engineers can interact with electrical signals via the time domain or the frequency domain. In the context of RF, it is generally more productive and intuitive to work in the frequency domain.
+ Frequency-domain analysis naturally suppresses details that are often of little importance in RF design and testing, and at the same time it emphasizes the characteristics that we need to focus on.
+ A frequency-domain plot is referred to as a spectrum. A spectrum can conveniently convey the salient characteristics of, for example, a modulation scheme or an actual signal that is experiencing problems caused by interference.
+ Theoretical spectra often consist of thin vertical arrows that correspond to idealized fixed-frequency sinusoids.
+ Real-world measurement equipment and real-world RF signals are always subject to imperfections that result in a wider frequency-domain waveform.
+ An essential piece of equipment for an RF design lab is the spectrum analyzer. These devices provide frequency-domain plots as well as various signal-analysis capabilities.

# 3. The Decibel

RF engineering, like all scientific disciplines and subdisciplines, involves quite a bit of specialized terminology. One of the most important words that you will need when working in the world of RF is “dB” (and some variants thereof). If you become deeply entrenched in an RF project, you may find that the word “dB” becomes as familiar to you as your own name.

As you probably know, dB stands for decibel. It’s a logarithmic unit that provides a convenient way of referring to ratios, such as the ratio between the amplitudes of an input signal and an output signal. It is *not* a unit of measurement, SI or otherwise.

![RF11](https://www.allaboutcircuits.com/uploads/articles/RFT_ch1_pg3_1_2.JPG)

In its simplest form, an amplifier’s gain is a ratio of output over input. Like all ratios, this form of gain is unitless. However, there is an actual unit intended to represent gain, and it is called the bel.

As a unit, the bel was actually devised as a convenient way to represent power loss in telephone system wiring rather than gain in amplifiers. The unit’s name is derived from Alexander Graham Bell, the famous Scottish inventor whose work was instrumental in developing telephone systems. Originally, the bel represented the amount of signal power loss due to resistance over a standard length of electrical cable. Now, it is defined in terms of the common (base 10) logarithm of a power ratio (output power divided by input power). Because the bel is a logarithmic unit, it is nonlinear. To give you an idea of how this works, consider the following table of figures, comparing power losses and gains in bels versus simple ratios:

![DB1](https://sub.allaboutcircuits.com/images/13029.png)

### Moving from the Bel to Decibel

It was later decided that the bel was too large of a unit to be used directly, and so it became customary to apply the metric prefix deci (meaning 1/10) to it, making it decibels, or dB. Now, the expression “dB” is so common that many people do not realize it is a combination of “deci-” and “-bel,” or that there even is such a unit as the “bel.” To put this into perspective, here is another table contrasting power gain/loss ratios against decibels:

![DB2](https://sub.allaboutcircuits.com/images/13030.png)

As a logarithmic unit, this mode of power gain expression covers a wide range of ratios with a minimal span in figures. It is reasonable to ask, “why did anyone feel the need to invent a logarithmic unit for electrical signal power loss in a telephone system?” The answer is related to the dynamics of human hearing, the perceptive intensity of which is logarithmic in nature. Human hearing is highly nonlinear: in order to double the perceived intensity of a sound, the actual sound power must be multiplied by a factor of ten. Relating telephone signal power loss in terms of the logarithmic “bel” scale makes perfect sense in this context: a power loss of 1 bel translates to a perceived sound loss of 50 percent, or 1/2. A power gain of 1 bel translates to a doubling in the perceived intensity of the sound.

A great reason for the adoption of the dB as a unit for gain is for simple expression of system gains and losses. Consider a system where two amplifiers were connected in series to amplify a signal. The respective gain for each amplifier is expressed as a ratio, and the overall gain for the system was the product (multiplication) of those two ratios:

`Overall gain = (3)(5) = 15`

If these figures represented power gains, we could directly apply the unit of bels to the task of representing the gain of each amplifier, and of the system altogether:

![DB3](https://sub.allaboutcircuits.com/images/03170.png)

The power gain in bels is additive: 0.477 B + 0.699 B = 1.176 B.

Close inspection of these gain figures in the unit of “bel” yields a discovery: they’re additive. Ratio gain figures are multiplicative for staged amplifiers, but gains expressed in bels add rather than multiply to equal the overall system gain. The first amplifier with its power gain of 0.477 B adds to the second amplifier’s power gain of 0.699 B to make a system with an overall power gain of 1.176 B. Recalculating for decibels rather than bels, we notice the same phenomenon.

![DB4](https://sub.allaboutcircuits.com/images/03171.png)

The gain of amplifier stages in decibels is also additive: 4.77 dB + 6.99 dB = 11.76 dB.

[Appendix 2 - Decibels](https://www.google.com "Appendix 2 - The Basic Mathematics of Decibels")

## Why dB?

It would certainly be possible to design and test RF systems without the use of dB, but in practice dB’s are everywhere. One advantage is that the dB scale allows us to express very large ratios without using very large numbers: a power gain of 1,000,000 is only 60 dB. Also, the total gain or loss of a signal chain is easily computed in the dB domain, because the individual dB figures are simply added (whereas multiplication would be required if we were working with ordinary ratios).

Another advantage is something that we’re familiar with from our experience with filters. RF systems revolve around frequencies and the various ways in which frequencies are generated, controlled, or affected by components and parasitic circuit elements. The dB scale is convenient in a context such as this because frequency response plots are intuitive and visually informative when the frequency axis uses a logarithmic scale and the amplitude axis uses a dB scale.

![DB5](https://www.allaboutcircuits.com/uploads/articles/134053_FIG-2.jpg)

`A Bode plot showing the magnitude response of different band-pass filters.`

## Absolute dBs

We’ve established that dB is a ratio and thus cannot describe the absolute power or amplitude of a signal. However, it would be awkward to be constantly switching back and forth between dB and non-dB values, and perhaps this is why RF engineers developed the dBm unit.

We can avoid the “ratios only” problem by simply creating a new unit that always includes a reference value. In the case of dBm, the reference value is 1 mW. Thus, if we have a 5 mW signal and we want to stay within the realm of dB, we can describe this signal as having a power of 7 dBm:

![DB6](https://www.allaboutcircuits.com/uploads/articles/134053_FIG-2.jpg)

\\[ x = {-b \pm \sqrt{b^2-4ac} \over 2a} \\]

