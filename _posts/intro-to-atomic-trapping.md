---
layout: post
title: Introduction to Atomic Trapping
---

# What is Atomic Physics?

The taxonomy of scientific disciplines is often arcane and unintuitive, and physics is no exception. When one hears the phrase ‘atomic physics’, they might be tempted to assume some relationship to ‘nuclear physics’ – after all, what is an atom but a nucleus with bound electrons? Yet these two fields could hardly be more distinct, sharing entirely separate histories, techniques, and applications.

The theory of atomic physics typically considers individual atoms in isolation. In the 20th century, this posed a seemingly insurmountable practical challenge – by what methods could one experimentally isolate an atom, so that those theories could be verified and further developed? At standard temperature and pressure, a molecule such as oxygen travels at over 400 meters per second, rendering existing observational tools at the time useless. It was not until the late 1980s (more than 30 years after the development of the atomic bomb, a major breakthrough of nuclear science!), when Bell Labs scientists William Phillips, Claude Cohen-Tannoudji, David Pritchard, and Steven Chu (among others) designed and fabricated the first apparatus for slowing and controlling ensembles of atoms in a gaseous or vapor form – the **magneto-optical trap**. This signaled a turning point in the study of atoms; for the first time, scientists could now create gases of atoms slow enough to be studied by conventional (e.g. spectroscopic) methods.

This practically instantly opened the door for a new generation of atomic physics. For example, in that same year, Steven Chu went on to utilize [optical tweezers](https://en.wikipedia.org/wiki/Optical_tweezers), a particle-trapping technique that had hitherto only been utilized for controlling macroscopic particles, to isolate individual atoms from within a magneto-optical trap. It only took a few more years for several more incredible achievements in the field; for instance, in 1985, Eric Cornell and Carl Weiman were able to cool an ensemble of Rubidium-87 atoms to below 170 nanokelvin, creating the first ‘pure’ Bose-Einstein condensate, a state of matter in which all constituent particles are occupying the same state.

**FIGURE: OPTICAL TWEEZERS OR BEC?**

Nowadays, the magneto-optical trap is ubiquitous in atomic physics labs, as it allows for researchers to experiment on individual (or arrays of individual) atoms. The objective of such experiments are typically investigating light-matter interactions, or how the trapped atoms behave under the influence of external electromagnetic waves. Modern uses of the magneto-optical trap include [quantum computation](https://siliconangle.com/2021/07/21/atom-computing-exits-stealth-quantum-computing-system-made-atoms-controlled-lasers/), atomic clocks ([which have been proven to be the most precise timekeepers currently existing](https://spectrum.ieee.org/optical-atomic-clock-advantage-expands-electronics)), and various quantum sensors [capable of detecting even the most minute changes in signals](https://syrte.obspm.fr/spip/science/iaci/projets-en-cours/gravimetre/article/gravimetre-a-atomes-froids?lang=en). The field of atomic physics is so nascent that every year, several novel applications are published, making it one of the most exciting and fastest-growing branches of science.

**FIGURE: COLDQUANTA COMPUTER?**

# Magneto-Optical Trapping

How does a magneto-optical trap work? The keys, as the name suggests, are **coherent light** (most commonly found in the form of **lasers**) and a sufficiently strong **magnetic field gradient**.

## Magnetics

Since non-ionized atoms are inherently ‘neutral’ (having just as many electrons as protons), one might expect them to not interact with an external magnetic field. However, this is not the case – since the electrons and protons share a different spatial density (i.e. are not directly on top of each other), every atom will have a (typically very small) [**magnetic dipole moment**](https://en.wikipedia.org/wiki/Magnetic_moment). This allows them to interact, albeit weakly, with an applied magnetic field.

A [magnetic trap](https://en.wikipedia.org/wiki/Magnetic_trap_(atoms)) works by creating an energy minima in a region of space through the interaction of the magnetic dipole with the external magnetic field. The spatial energy shift is given by:

$$\Delta E =- \vec{\mu} \cdot \vec{B}$$

where $$\vec{\mu}$$ is the magnetic dipole moment and $$\vec{B}$$ is the magnetic field vector.

**FIGURE: ENERGY DIAGRAM**

This creates a potential energy valley, in which an atom is ‘incentivized’ to be at the trough. However, analogously to classical mechanics, a ball rolling in a valley may ‘escape’ that valley if its kinetic energy is higher than the potential energy difference between the trough and peak of the valley. And, as mentioned earlier, atoms in gaseous or vapor form at room temperature and pressure move extremely fast – between this fact, and the relatively small magnetic dipole moment of neutral atoms, it would take an impractically strong magnetic field to trap room-temperature neutral atoms.

**FIGURE: ENERGY DIAGRAM ANIMATION**

However, if the kinetic energy of the atoms were to be reduced, then at some point, we could use a reasonably large magnetic field to create a shift in energy sufficient enough to trap said atoms in a desired region of space. This is where the other half of the magneto-optical trap comes in – the optics.

## Optics

As Einstein theorized in the early 20th century, light is [**quantized**](https://en.wikipedia.org/wiki/Photon), i.e. light waves are made up of individual particles known as photons. [](https://en.wikipedia.org/wiki/Photon)Atoms interact with light through their bound electrons, in a process during which an electron may absorb a photon and gain that photon’s energy. This process is known as [**electron excitation**](https://en.wikipedia.org/wiki/Electron_excitation), and has a reciprocal process known as **electron decay**, in which an ‘excited’ electron may re-emit the photon it absorbed, and lose that photon’s energy.

**FIGURE: ELECTRON DECAY DIAGRAM WITH ENERGY LEVELS**

These levels, at first glace, appear to be separated by fixed, definite amounts of energy, and therefore one might expect that a photon must have some exact energy for the atom to absorb it. However, due to [time-energy uncertainty](https://math.ucr.edu/home/baez/uncertainty.html), this is actually not the case; there is an ‘uncertainty’ inherent in the energy of the excited electronic state, which we denote the **line width** of the atomic transition. Moreover, by the time-energy uncertainty relation, the wider this line width is, the shorter the lifetime of the excited state (before it decays back to the original state), and vice versa.

**FIGURE: LINE WIDTH**

The line width of an atomic transition tells us what range of frequencies / wavelengths our laser has to be within to be able to excite the electrons in the atoms we’re shining it on. For an atom such as Rubidium-87, and a typical transition we might be interested in, such as the $$5^2 S_{1/2} \to 5^2 P_{3/2}$$ (a ground state to a ‘first’ excited state) transition, this line width would be around ~38 MHz, which corresponds to a range of tens of *femtometers* in terms of wavelength. In other words, if we want to shine a laser on a Rubidium-87 atom such that it will absorb photons and undergo this transition, we need to make sure that our laser has a wavelength no more than about 40 femtometers from the central transition wavelength of 780,241,209 femtometers.

The construction of such a laser is



Another source of variability in energy comes


# Fabricating a Magneto-Optical Trap

The magneto-optical trap (henceforth referred to as a ‘MOT’), at its very core, is a very simple apparatus. While the details of the components and specifications may change depending on the element you wish to trap and the downstream application, all MOTs consist of two main subsystems: at least one near-monochromatic (i.e. frequency-stabilized, more on this later) laser, and an ultra-high vacuum chamber.
