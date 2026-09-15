# Neural Signal Analysis — One-Day MCQ Revision (Answers Next to Questions)

> **What this is:** the whole course condensed into **220 MCQs**, each followed **immediately** by its answer and a short explanation. Finish it in **one day (about 6–7 hours)**.
> **Built from:** lecture slides (Ch 1–9, Signal & Noise deck), MATLAB labs, and the previous exam.
> **How to use:** read the question, pick your answer, **then** read the ✅ line right below it. Put a ✗ next to every miss and redo those at the end of the day.
> **Two formats:** most questions are **single best answer**. Questions marked **(Select all)** copy the real exam style: any number of options can be correct.

---

## Contents

- [Study Plan](#study-plan)
- [Part 1 — Neurophysiology (Q1–Q40)](#part-1--neurophysiology-q1q40)
- [Part 2 — Brain Anatomy and Origin of EEG (Q41–Q60)](#part-2--brain-anatomy-and-origin-of-eeg-q41q60)
- [Part 3 — EEG Acquisition (Q61–Q90)](#part-3--eeg-acquisition-q61q90)
- [Part 4 — Fourier Analysis (Q91–Q130)](#part-4--fourier-analysis-q91q130)
- [Part 5 — Noise, Random Processes, SNR (Q131–Q150)](#part-5--noise-random-processes-snr-q131q150)
- [Part 6 — Signal Averaging and Evoked Potentials (Q151–Q175)](#part-6--signal-averaging-and-evoked-potentials-q151q175)
- [Part 7 — Preprocessing and Artifacts (Q176–Q205)](#part-7--preprocessing-and-artifacts-q176q205)
- [Part 8 — Brain Rhythms, Filters, Time-Domain Methods, Labs (Q206–Q220)](#part-8--brain-rhythms-filters-time-domain-methods-labs-q206q220)
- [Final 15-Minute Cheat Sheet](#final-15-minute-cheat-sheet)

---

## Study Plan

| Session | Time | Questions |
|---|---|---|
| 1 | 09:00–10:15 | Part 1 (Q1–Q40) |
| 2 | 10:30–11:30 | Parts 2–3 (Q41–Q90) |
| 3 | 11:45–13:00 | Part 4 (Q91–Q130) |
| Lunch | 45 min | |
| 4 | 13:45–14:45 | Parts 5–6 (Q131–Q175) |
| 5 | 15:00–16:00 | Parts 7–8 (Q176–Q220) |
| 6 | 16:15–17:15 | Redo every ✗ question + cheat sheet |

**Exam technique:** the real exam is "select ALL correct statements". Judge each option on its own. Words like *only, always, never, guarantees, optimal, irrelevant, permanently, zero noise* are almost always false. A slide sentence with one changed number, ion, direction or band is false.

---

## Part 1 — Neurophysiology (Q1–Q40)

**Q1.** Which cells carry out electrical signalling over long distances?
- A. Astrocytes
- B. Schwann cells
- C. Neurons
- D. Glial cells

> ✅ **Answer: C.** Neurons signal over long distances. Glia support signalling, repair damage, act as stem cells in some areas and prevent regeneration in others.

**Q2.** The slides compare dendrites to:
- A. A radio antenna
- B. A radio transmitter
- C. A battery
- D. Telephone wires

> ✅ **Answer: A.** Dendrites **receive** (antenna). Axon = telephone wires (transmit over distance). Axon terminal = radio transmitter.

**Q3.** The number of targets innervated by one neuron is its:
- A. Summation
- B. Convergence
- C. Divergence
- D. Threshold

> ✅ **Answer: C.** Divergence = number of targets. Convergence = number of inputs.

**Q4.** Which cell has **no axon at all**?
- A. Cortical pyramidal cell
- B. Retinal amacrine cell
- C. Cerebellar Purkinje cell
- D. Retinal bipolar cell

> ✅ **Answer: B.** Amacrine: no axon. Bipolar: very short axon.

**Q5. (Select all)** Which statements about synaptic transmission are correct?
- A. Neurotransmitter is released from synaptic vesicles into the synaptic cleft.
- B. Neurotransmitter is released from postsynaptic dendrites into the presynaptic terminal.
- C. Transmitter binds to receptor proteins on the postsynaptic cell.
- D. Binding can generate electrical or chemical signals in the postsynaptic cell.

> ✅ **Answer: A, C, D.** B reverses the direction: release is **presynaptic**.

**Q6.** The ionic equilibrium potential is best defined as:
- A. The membrane potential at threshold
- B. The potential at which the pump stops
- C. The average of all ionic potentials
- D. The electrical potential difference that exactly balances an ionic concentration gradient

> ✅ **Answer: D.** At $E_{ion}$ diffusion and electrostatic forces balance, so there is no net current for that ion.

**Q7.** In the Nernst equation, the concentration ratio is:
- A. $[ion]_{out}-[ion]_{in}$
- B. $[ion]_{out}/[ion]_{in}$
- C. $[ion]_{out}\times[ion]_{in}$
- D. $[ion]_{in}/[ion]_{out}$

> ✅ **Answer: B.** $E_{ion}=\frac{2.303RT}{zF}\log\frac{[ion]_{out}}{[ion]_{in}}$. The inverted ratio was a distractor in the old exam.

**Q8.** Which quantity does **not** appear in the Nernst equation?
- A. Membrane thickness
- B. Ion charge z
- C. Absolute temperature T
- D. Faraday's constant F

> ✅ **Answer: A.** Only concentrations, charge, temperature and constants appear.

**Q9.** With $[K^+]_o=5$ mM and $[K^+]_i=100$ mM at 37 °C, $E_K$ is about:
- A. −65 mV
- B. −80 mV
- C. +80 mV
- D. −123 mV

> ✅ **Answer: B.** $61.54\log(1/20)=61.54\times(-1.30)\approx-80$ mV.

**Q10.** With $[Na^+]_o=150$ and $[Na^+]_i=15$ mM, $E_{Na}$ is about:
- A. +123 mV
- B. +30.8 mV
- C. −61.5 mV
- D. +61.5 mV

> ✅ **Answer: D.** Ratio 10 gives $61.54\times1$. Positive because Na⁺ is concentrated outside.

**Q11.** Why is the Nernst prefactor for Ca²⁺ only 30.77 mV?
- A. Ca²⁺ has charge z = 2
- B. Ca²⁺ is intracellular
- C. Ca²⁺ is less permeable
- D. Ca²⁺ is measured at a lower temperature

> ✅ **Answer: A.** The factor is divided by z, so 61.54/2. $E_{Ca}$ for a 10,000:1 ratio is $30.77\times4=+123$ mV.

**Q12.** $E_{Cl}$ for $[Cl^-]_o=150$ and $[Cl^-]_i=13$ mM is about:
- A. 0 mV
- B. +65 mV
- C. −65 mV
- D. −80 mV

> ✅ **Answer: C.** z = −1 flips the sign: $-61.54\log(11.5)\approx-65$ mV. The slide table prints "65 mV" without the sign.

**Q13.** How does temperature affect $E_{ion}$?
- A. Through the $RT/F$ term; higher T gives a larger magnitude
- B. It has no effect
- C. Only through permeability
- D. It changes the ion's charge

> ✅ **Answer: A.** At 20 °C the factor is ≈ 58 mV instead of 61.5 mV.

**Q14.** If a membrane were permeable **only** to K⁺, the resting potential would be:
- A. −65 mV
- B. Equal to $E_K$ (about −80 mV)
- C. Equal to $E_{Na}$
- D. 0 mV

> ✅ **Answer: B.** Only K⁺ can move, so $V_m$ settles at K⁺'s equilibrium.

**Q15.** Why is the real resting potential (−65 mV) less negative than $E_K$?
- A. The pump is inactive at rest
- B. K⁺ permeability is zero at rest
- C. The resting membrane also has some Na⁺ permeability
- D. Cl⁻ permeability only

> ✅ **Answer: C.** Slide explanation: real neurons are not exclusively K⁺-permeable.

**Q16.** The resting membrane permeability to K⁺ is how many times that to Na⁺?
- A. 40
- B. 20
- C. 4
- D. 80

> ✅ **Answer: A.** **40×**. "80×" was an exam distractor (confused with −80 mV).

**Q17.** The Goldman equation differs from Nernst because it:
- A. Ignores concentrations
- B. Applies only to Ca²⁺
- C. Gives the equilibrium potential of a single ion
- D. Weights several ions by their permeabilities

> ✅ **Answer: D.** $V_m=61.54\log\frac{P_K[K]_o+P_{Na}[Na]_o}{P_K[K]_i+P_{Na}[Na]_i}$. With 40:1 this gives ≈ −65 mV.

**Q18.** A membrane is equally permeable to Na⁺ and Cl⁻, with 10 mM NaCl on one side and 2 mM on the other. At the end:
- A. A large positive potential develops
- B. Cl⁻ moves against its gradient
- C. Both sides reach 6 mM and the membrane potential is 0
- D. Only Na⁺ moves

> ✅ **Answer: C.** Both ions move together, so no charge separation builds up.

**Q19.** Which transporter moves ions **against** their concentration gradients using ATP?
- A. Gap junction
- B. Leak channel
- C. Sodium–potassium pump
- D. Voltage-gated Na⁺ channel

> ✅ **Answer: C.** Channels are passive; only the pump uses metabolic energy.

**Q20. (Select all)** Leak channels:
- A. Are normally open
- B. Have different permeability for different ions
- C. Require ATP for every ion that passes
- D. Help set the resting potential

> ✅ **Answer: A, B, D.** C is false: that describes the pump, not channels.

**Q21.** At the resting potential (−65 mV), voltage-gated Na⁺ and K⁺ channels are:
- A. Na⁺ open, K⁺ closed
- B. Both closed
- C. Both open
- D. Na⁺ closed, K⁺ open

> ✅ **Answer: B.** Resting K⁺ permeability comes from **leak** channels, not voltage-gated ones.

**Q22.** Threshold is the membrane potential at which:
- A. Enough voltage-gated Na⁺ channels open that permeability favours Na⁺ over K⁺
- B. The pump reverses
- C. K⁺ channels open fully
- D. $V_m$ equals $E_K$

> ✅ **Answer: A.** Beyond threshold, Na⁺ influx becomes self-reinforcing.

**Q23.** Why does the AP peak not reach $E_{Na}$?
- A. The pump removes Na⁺ instantly
- B. K⁺ channels never open
- C. Cl⁻ enters the cell
- D. Na⁺ channels quickly inactivate (close)

> ✅ **Answer: D.** The inactivation gate closes ~1 ms after the activation gate opens.

**Q24.** The two gates of the voltage-gated Na⁺ channel are:
- A. Inner and outer pump gates
- B. Ligand gate and voltage gate
- C. Activation gate and inactivation gate
- D. K⁺ gate and Cl⁻ gate

> ✅ **Answer: C.** Activation opens on depolarization; inactivation closes about 1 ms later.

**Q25.** The falling phase of the AP is caused by:
- A. Na⁺ channel inactivation plus opening of voltage-gated K⁺ channels
- B. Na⁺ influx
- C. Ca²⁺ influx
- D. The pump alone

> ✅ **Answer: A.** K⁺ flows out; K⁺ channels were triggered ~1 ms earlier but open with a delay.

**Q26.** During the undershoot, $V_m$ moves toward:
- A. $E_{Ca}$
- B. $E_K$
- C. $E_{Na}$
- D. 0 mV

> ✅ **Answer: B.** Voltage-gated K⁺ channels are still open while Na⁺ permeability is very low.

**Q27.** In the summed-current figure during an AP:
- A. K⁺ current comes first
- B. Na⁺ current is outward and long
- C. Both currents are inward
- D. Na⁺ current is brief and inward; K⁺ current is slower and outward

> ✅ **Answer: D.** Net current: inward first (Na⁺ influx), then outward (K⁺ efflux).

**Q28.** During the absolute refractory period:
- A. Na⁺ channels are inactivated and no AP can be generated
- B. A strong stimulus can fire a smaller AP
- C. K⁺ channels are closed
- D. The membrane is at rest

> ✅ **Answer: A.** Na⁺ channels need sufficient repolarization before they can open again.

**Q29.** During the relative refractory period:
- A. Na⁺ channels are permanently disabled
- B. No stimulus can trigger an AP
- C. The membrane is hyperpolarized (K⁺ channels open), so more depolarizing current is needed
- D. The threshold is lower than normal

> ✅ **Answer: C.** Na⁺ channels are responsive again; the extra current overcomes the hyperpolarization.

**Q30.** The all-or-none law states that:
- A. AP amplitude grows with stimulus strength
- B. All neurons fire together
- C. Subthreshold stimuli produce small APs
- D. AP strength does not depend on stimulus strength

> ✅ **Answer: D.** Stronger stimuli increase the **firing rate**, not the AP size.

**Q31.** Injecting small **hyperpolarizing** current pulses produces:
- A. Only passive changes in membrane potential
- B. Overshoot
- C. Increased firing rate
- D. Action potentials

> ✅ **Answer: A.** Small depolarizing pulses are passive too; APs need threshold.

**Q32.** A subthreshold potential injected into an axon, recorded 2 mm away, is:
- A. Unchanged in amplitude but delayed
- B. Larger than at the injection site
- C. Converted into an AP
- D. Smaller, because current leaks out (passive decay)

> ✅ **Answer: D.** Passive signals fall to a small fraction within a few millimetres.

**Q33.** In active conduction along an axon:
- A. Amplitude stays constant ("without decrement"); only arrival time is delayed
- B. Amplitude decays with distance
- C. There is no delay
- D. Only subthreshold stimuli propagate

> ✅ **Answer: A.** The AP regenerates, overcoming the membrane's leakiness.

**Q34.** In myelinated axons, voltage-gated Na⁺ channels are concentrated:
- A. Under the myelin sheath
- B. In the dendrites
- C. In the soma
- D. At the nodes of Ranvier

> ✅ **Answer: D.** Excitation happens only at nodes, so current jumps node to node (saltatory conduction).

**Q35.** Which pairing is correct?
- A. Both are found only in the CNS
- B. Schwann cells: CNS, many axons each
- C. Oligodendrocytes: CNS, several axons each; Schwann cells: PNS, one axon each
- D. Oligodendrocytes: PNS, one axon each

> ✅ **Answer: C.**

**Q36.** The spike-initiation zone of a **primary sensory neuron** is:
- A. The soma
- B. The axon terminal
- C. Near the sensory nerve endings
- D. The axon hillock

> ✅ **Answer: C.** In CNS neurons such as pyramidal cells it is the **axon hillock**. Dendrites and soma have few voltage-gated Na⁺ channels.

**Q37. (Select all)** Electrical synapses:
- A. Occur at gap junctions about 3 nm wide
- B. Are formed by two connexons, each made of six connexins
- C. Are mostly bidirectional
- D. Are slow but flexible compared with chemical synapses

> ✅ **Answer: A, B, C.** D is false: electrical synapses are **very fast** (very little delay) and support synchronization.

**Q38.** Who provided solid support for chemical synapses in 1921?
- A. Furshpan and Potter
- B. Herbert Jasper
- C. Bernard Katz
- D. Otto Loewi

> ✅ **Answer: D.** Loewi stimulated the vagus nerve of one frog heart; the collected fluid slowed a second heart. Katz: neuromuscular transmission is chemical. Furshpan & Potter (late 1950s): electrical synapses. Jasper: 10–20 system (1958).

**Q39.** According to the slides, EPSPs and IPSPs are produced by:
- A. EPSP: Cl⁻ entry; IPSP: K⁺ exit
- B. Both by Ca²⁺ entry
- C. EPSP: Na⁺ entry (depolarization); IPSP: Cl⁻ entry (hyperpolarization)
- D. EPSP: K⁺ entry; IPSP: Na⁺ entry

> ✅ **Answer: C.** "K⁺ entry" was the old-exam distractor.

**Q40.** Two excitatory synapses (E1, E2) are each subthreshold. E1+E2 together fire an AP. Adding an inhibitory synapse (E1+E2+I):
- A. Always produces two APs
- B. Has no effect
- C. Converts the IPSP into an EPSP
- D. Can keep the neuron below threshold, so no AP

> ✅ **Answer: D.** Different inputs at the same time add up (**spatial summation**). The **same** input firing rapidly adds up too (**temporal summation**).

---

## Part 2 — Brain Anatomy and Origin of EEG (Q41–Q60)

**Q41.** The precentral gyrus is involved in:
- A. Voluntary movement
- B. Vision
- C. Audition
- D. Somatic sensation

> ✅ **Answer: A.** Precentral (in front of the central sulcus) = primary motor. Postcentral = somatic sensation. Superior temporal gyrus = audition.

**Q42.** Broca's and Wernicke's areas are responsible for:
- A. Broca: comprehension; Wernicke: production
- B. Both: vision
- C. Both: smell
- D. Broca: speech production (frontal); Wernicke: language comprehension (temporal)

> ✅ **Answer: D.**

**Q43.** The insula:
- A. Is visible on the lateral surface without retraction
- B. Is buried cortex that separates the temporal and frontal lobes
- C. Controls voluntary eye movements
- D. Is part of the cerebellum

> ✅ **Answer: B.** Revealed by pulling apart the lateral (Sylvian) fissure; involved in taste and visceral sensation. Voluntary eye movements = frontal eye field.

**Q44.** Which recording method is **semi-invasive**?
- A. EEG
- B. fMRI
- C. MEG
- D. ECoG

> ✅ **Answer: D.** EEG, MEG and fMRI are non-invasive. LFP, single-unit APs and patch clamp are invasive.

**Q45.** fMRI relies on:
- A. Magnetic fields of neurons
- B. Coupling between cerebral blood flow and neuronal activation
- C. Scalp electrical potentials
- D. Direct measurement of neuronal currents

> ✅ **Answer: B.** It is indirect and slow (seconds).

**Q46.** EEG mainly records:
- A. Magnetic fields
- B. Extracellular currents arising from synaptic activity in dendrites of cortical neurons
- C. Blood oxygenation
- D. Intracellular action potentials

> ✅ **Answer: B.**

**Q47.** The extracellular electric field that forms the EEG is mainly generated by:
- A. The Na⁺/K⁺ pump
- B. Postsynaptic potentials (EPSPs and IPSPs)
- C. Glial cells
- D. Action potentials

> ✅ **Answer: B.** APs are brief (~1 ms) and rarely overlap in time; PSPs last longer, so they summate.

**Q48.** Why are pyramidal cells the main contributors to EEG?
- A. They are inhibitory
- B. They are spatially aligned perpendicular to the cortex, so their dipoles add
- C. They are the only cortical neurons
- D. They lack dendrites

> ✅ **Answer: B.** They are mostly excitatory, with parallel apical dendrites.

**Q49.** The dipole of a single neuron:
- A. Is impossible to measure on the scalp; only the sum of many dipoles is measurable
- B. Is magnetic only
- C. Is larger than an EEG signal
- D. Is easily measured on the scalp

> ✅ **Answer: A.**

**Q50.** Which dipole contributes the **strongest** EEG signal?
- A. Tangential dipole on a sulcal wall
- B. Radial dipole deep at the bottom of a sulcus
- C. Radial dipole at the crown of a gyrus, just below the electrode
- D. Randomly oriented dipoles

> ✅ **Answer: C.**

**Q51.** Dipoles on opposite walls of a sulcus are unlikely to be measured because:
- A. They are too close to the electrode
- B. They produce fields of opposite polarity that cancel
- C. They have identical polarity
- D. They are radial

> ✅ **Answer: B.** The old exam's distractor said "identical polarity".

**Q52.** A radial dipole deep at the bottom of a sulcus contributes:
- A. More than a crown dipole
- B. Nothing at all
- C. Only to MEG
- D. Less than a crown dipole, because it is further from the electrode

> ✅ **Answer: D.**

**Q53.** When six pyramidal neurons are activated **synchronously** rather than irregularly, the summed EEG:
- A. Is smaller
- B. Changes frequency only
- C. Becomes zero
- D. Has high amplitude

> ✅ **Answer: D.** Irregular activation gives a small summed amplitude.

**Q54.** Adjacent neurons receive excitatory and inhibitory input at the same moment. The scalp signal is:
- A. Reduced, because the dipoles have opposite orientations and cancel
- B. Enhanced
- C. Converted into a magnetic signal
- D. Unchanged

> ✅ **Answer: A.** Summation needs similar orientation, the same transmitter type, and near-simultaneous activation.

**Q55. (Select all)** Advantages of EEG according to the slides:
- A. Perfectly non-invasive, without radiation or high magnetic field
- B. A direct measure of electrical brain activity
- C. High spatial resolution
- D. Temporal resolution matches the speed of cognition

> ✅ **Answer: A, B, D.** C is false: EEG spatial resolution is **poor**. Other advantages: portable, rich information, open environment, economical.

**Q56.** EEG's main advantage over fMRI and PET is:
- A. Superior temporal resolution (tens of milliseconds)
- B. Deeper source localization
- C. Measuring metabolism
- D. Better spatial resolution

> ✅ **Answer: A.**

**Q57.** The cerebellum is mainly involved in:
- A. Smell
- B. Coordination, precision and timing of movements, and motor learning
- C. Language comprehension
- D. Vision

> ✅ **Answer: B.**

**Q58.** Lobes of the cerebrum are named after:
- A. The skull bones that lie over them
- B. Their blood supply
- C. Their discoverers
- D. Their functions

> ✅ **Answer: A.** The central sulcus separates frontal from parietal; the temporal lobe lies below the lateral fissure.

**Q59.** Rich information in EEG allows analysis of:
- A. Oscillations, synchronization and connectivity
- B. Only single-neuron spikes
- C. Blood flow
- D. Only amplitude

> ✅ **Answer: A.**

**Q60. (Select all)** Which conditions lead to **cancellation** of dipoles?
- A. Randomly oriented neurons
- B. Adjacent excitatory and inhibitory inputs
- C. Same orientation, same transmitter, synchronous activation
- D. Opposing walls of a sulcus

> ✅ **Answer: A, B, D.** C is the condition for **summation**.

---

## Part 3 — EEG Acquisition (Q61–Q90)

**Q61.** The correct order of the analog front end is:
- A. Electrodes → pre-amp → amp → band filter → notch → anti-alias filter → S/H
- B. Anti-alias filter → electrodes → amplifier
- C. ADC → amplifier → electrodes
- D. Electrodes → ADC → anti-alias filter

> ✅ **Answer: A.** Then MUX → ADC (digital side).

**Q62.** The anti-aliasing filter must be placed:
- A. Before the ADC
- B. After spectral analysis
- C. Only in software
- D. After the ADC

> ✅ **Answer: A.** Once aliasing has happened, the alias looks like a real low frequency and cannot be removed.

**Q63.** The sample-and-hold circuit:
- A. Amplifies the signal
- B. Samples the analog signal and holds it constant during conversion
- C. Removes line noise
- D. Chooses the reference

> ✅ **Answer: B.**

**Q64.** The main problem with metal electrodes in ionic solution is:
- A. They are too large
- B. They cannot conduct
- C. The metal–solution interface creates a material- and solution-specific electrode potential
- D. They reduce amplifier gain

> ✅ **Answer: C.** This is usually not a problem when both electrodes are of the same material.

**Q65. (Select all)** The Ag/AgCl coating:
- A. Facilitates the transition from ionic to electronic conduction
- B. Reduces electrode capacitance at the interface
- C. Makes recording of low-frequency components easier
- D. Guarantees zero noise pickup

> ✅ **Answer: A, B, C.** D is false (absolute claim). Ag/AgCl also doesn't remove the need for amplification.

**Q66.** The simplified equivalent circuit of an electrode is:
- A. An inductor
- B. A diode
- C. A single resistor
- D. A resistor in parallel with a capacitor

> ✅ **Answer: D.**

**Q67.** How many levels does a 3-bit ADC have?
- A. 3
- B. 9
- C. 6
- D. 8

> ✅ **Answer: D.** $2^3=8$ levels (000–111).

**Q68.** A 16-bit ADC has:
- A. 1,024 levels
- B. 16 levels
- C. 256 levels
- D. 65,536 levels

> ✅ **Answer: D.** $2^{16}$.

**Q69.** ADC bit depth determines:
- A. The reference
- B. The amplitude resolution
- C. The epoch length
- D. The maximum frequency that can be sampled

> ✅ **Answer: B.** The maximum frequency is set by the **sampling rate**.

**Q70.** Sampling is modelled mathematically as:
- A. Differentiating the signal
- B. Adding a Dirac comb
- C. Multiplying the signal by a Dirac comb
- D. Integrating the signal

> ✅ **Answer: C.** $x^s=x(t)\sum_n\delta(t-nT_s)$.

**Q71.** In the frequency domain, sampling makes the spectrum:
- A. Periodic with period $F_s$ (copies of the spectrum)
- B. Symmetric only around $F_s$
- C. Continuous and non-periodic
- D. Disappear above Nyquist

> ✅ **Answer: A.** Multiplication in time = convolution in frequency. Overlap of the copies = aliasing.

**Q72.** The unit impulse (Dirac delta) is:
- A. A sine wave
- B. The derivative of the unit step, with area 1
- C. The integral of the unit step
- D. Zero everywhere

> ✅ **Answer: B.** It can be viewed as a pulse of width τ and height 1/τ with τ → 0.

**Q73.** For a 20 Hz sine wave, the minimum sampling rate is:
- A. 20 Hz
- B. 10 Hz
- C. 40 Hz
- D. 30 Hz

> ✅ **Answer: C.** Nyquist rate = $2f_{max}$.

**Q74.** The Nyquist **frequency** of a system sampling at $F_s$ is:
- A. $2F_s$
- B. $F_s$
- C. $F_s/2$
- D. $F_s/5$

> ✅ **Answer: C.** Nyquist rate ($2f_{max}$) and Nyquist frequency ($F_s/2$) are **not** the same value.

**Q75.** A 20 Hz sine is sampled at 24 Hz. It appears as:
- A. 12 Hz
- B. 4 Hz
- C. 20 Hz
- D. 44 Hz

> ✅ **Answer: B.** $\lvert20-24\rvert=4$ Hz (the lab and slide figure).

**Q76.** A 20 Hz sine sampled at 59 Hz:
- A. Cannot be recorded
- B. Is aliased to 39 Hz
- C. Keeps its frequency content, but the waveform looks distorted in time
- D. Appears as DC

> ✅ **Answer: C.** 59 > 40, so there is no aliasing. This is why ~5× oversampling is common.

**Q77.** A 35 Hz component sampled at 50 Hz without filtering appears at:
- A. 25 Hz
- B. 15 Hz
- C. 85 Hz
- D. 35 Hz

> ✅ **Answer: B.** $\lvert35-50\rvert=15$ Hz.

**Q78.** Sampling a 20 Hz sine exactly at 40 Hz, at its peaks and valleys, gives:
- A. Only zeros in all cases
- B. A 20 Hz triangular-looking wave
- C. A 10 Hz wave
- D. A perfect sine

> ✅ **Answer: B.** Sampled at other phases it looks even more distorted.

**Q79.** The International 10–20 system was proposed by:
- A. Cooley and Tukey, 1965
- B. Otto Loewi, 1921
- C. Herbert Jasper, 1958
- D. Bernard Katz, 1950

> ✅ **Answer: C.**

**Q80.** "10" and "20" in the 10–20 system refer to:
- A. Percentages of skull distances (nasion–inion, preauricular points)
- B. Centimetres
- C. Hz
- D. Numbers of electrodes

> ✅ **Answer: A.** Edge electrodes are 10% from the landmarks; the others are 20% apart.

**Q81.** Electrode C4 is located:
- A. Left occipital
- B. Midline central
- C. Right central
- D. Left central

> ✅ **Answer: C.** Odd numbers = left, even = right, "z" = midline.

**Q82.** Why does EEG use three electrodes (active, reference, ground) per channel?
- A. To increase ADC bits
- B. To measure magnetic fields
- C. To triple the amplitude
- D. So the differential amplifier can cancel noise common to both measurements

> ✅ **Answer: D.** A single electrode against the circuit ground would mostly measure static electricity, which is much larger than neural activity.

**Q83.** The differential amplifier output for an EEG channel is:
- A. $V_{AG}\times V_{RG}$
- B. $V_{RG}$ only
- C. $V_{AG}-V_{RG}$
- D. $V_{AG}+V_{RG}$

> ✅ **Answer: C.**

**Q84.** Which statement about the ground electrode is correct?
- A. It is usually on the frontal bone to minimize muscle noise, and its potential cancels
- B. It is the neutral reference
- C. It can be omitted in practice
- D. Its location is more important than the reference location

> ✅ **Answer: A.**

**Q85.** Which statement about the reference electrode is correct?
- A. It is always placed on Cz
- B. Every channel reflects both the active and the reference electrode; there is no neutral site
- C. A perfectly neutral site exists
- D. Its choice cannot affect topography

> ✅ **Answer: B.** It is usually placed on one or both ear lobes.

**Q86.** An artifact is present at the active electrode but not at the reference. In the differential channel it:
- A. Doubles
- B. Is cancelled
- C. Moves to the ground
- D. Remains, because it is not common-mode

> ✅ **Answer: D.** Common-mode rejection only works when the interference is the same at both inputs.

**Q87.** In the bipolar derivation:
- A. All channels share one ear reference
- B. The mean of all channels is subtracted
- C. Only one channel is recorded
- D. Each channel is the difference between neighbouring electrodes

> ✅ **Answer: D.** It suppresses widespread activity common to both electrodes.

**Q88.** In the common average reference (CAR):
- A. Each channel has the mean of all channels subtracted
- B. Neighbouring electrodes are subtracted
- C. Each channel has the average of both ears subtracted
- D. No reference is used

> ✅ **Answer: A.** Subtracting the average of both ears is the **biauricular** reference.

**Q89.** The main weakness of CAR is that it:
- A. Requires an ear electrode
- B. Cannot be computed
- C. Increases single-point failure
- D. Suffers from outlier (bad) channels, and from artifacts shared by many electrodes

> ✅ **Answer: D.** Remove bad channels before CAR (robust average reference). CAR **reduces** single-point failure.

**Q90. (Select all)** Which referencing statements are correct?
- A. Changing the reference can change waveforms even when brain activity is unchanged.
- B. The reference should not be correlated with task-induced activity.
- C. Referencing cannot change the topography.
- D. Laplacian and LAR are free-reference spatial filters.

> ✅ **Answer: A, B, D.** C is false.

---

## Part 4 — Fourier Analysis (Q91–Q130)

**Q91.** The Fourier series represents:
- A. Only square waves
- B. A signal as a sum of Dirac impulses
- C. Any non-periodic signal as an integral
- D. A periodic function $f(t)=f(t+T)$ as a sum of sines and cosines

> ✅ **Answer: D.** Non-periodic signals need the Fourier **transform**.

**Q92.** In $P(t)=\frac12a_0+\sum[a_n\cos n\omega t+b_n\sin n\omega t]$, the DC component is:
- A. $b_0$
- B. $a_1$
- C. $\frac12a_0$
- D. $a_0$

> ✅ **Answer: C.** The $a_n$, $b_n$ terms are the AC components. There is no $b_0$.

**Q93.** Angular frequency is defined as:
- A. $\omega=2\pi T$
- B. $\omega=f/2\pi$
- C. $\omega=T/2\pi$
- D. $\omega=2\pi f$, with $f=1/T$

> ✅ **Answer: D.**

**Q94.** The Fourier coefficient $a_n$ equals:
- A. $\frac2T\int_Tf(t)dt$
- B. $\frac2T\int_Tf(t)\cos(n\omega t)dt$
- C. $\int f(t)e^{-j\omega t}dt$
- D. $\frac1T\int_Tf(t)\sin(n\omega t)dt$

> ✅ **Answer: B.** $b_n$ uses sine with the same $2/T$; $a_0=\frac2T\int_Tf\,dt$.

**Q95.** The coefficients are derived by:
- A. Minimizing the squared error $E^2=\int_T[P(t)-f(t)]^2dt$
- B. Averaging trials
- C. Sampling at Nyquist
- D. Maximizing the signal power

> ✅ **Answer: A.** Set $\partial E^2/\partial a_n=0$ and $\partial E^2/\partial b_n=0$, then use orthogonality.

**Q96.** Over one full period, $\int_T\cos(n\omega t)\cos(m\omega t)dt$ for $m=n$ equals:
- A. 0
- B. T/2
- C. T
- D. 1

> ✅ **Answer: B.** It is 0 for $m\neq n$. $\int_T\sin\cdot\cos$ is 0 for all m, n.

**Q97.** For an **even** periodic function $f(t)=f(-t)$:
- A. $a_0$ must be nonzero
- B. Only sines remain
- C. All $b_n=0$ (cosines only)
- D. All $a_n=0$

> ✅ **Answer: C.** An odd function $f(t)=-f(-t)$ has all $a_n=0$ (sines only).

**Q98.** A symmetric zero-mean triangle wave (even, amplitude A) has:
- A. $a_n=8A/(n^2\pi^2)$ for odd n, 0 for even n, and $b_n=0$
- B. A nonzero DC term
- C. Harmonics decaying as 1/n
- D. Only even harmonics

> ✅ **Answer: A.** The slide prints $8A/(n\pi^2)$; the correct decay is $1/n^2$.

**Q99.** For a ±1 square wave (odd), the fundamental amplitude and the harmonic decay are:
- A. $\pi/4$ and no harmonics
- B. $4/\pi$ and $1/n$ (odd harmonics)
- C. $1$ and $1/n^2$
- D. $2/\pi$ and even harmonics only

> ✅ **Answer: B.** Its discontinuities need slowly decaying high-frequency content.

**Q100.** The slides use which analogy for spectral decomposition?
- A. A battery
- B. A prism splitting white light into colours
- C. A mirror
- D. A lens focusing light

> ✅ **Answer: B.** Also: splitting sound into pure tones.

**Q101.** The complex Fourier series is written as:
- A. A product of exponentials
- B. $\sum_{-\infty}^{\infty}c_ne^{jn\omega t}$, with $c_n=\frac1T\int_Tf e^{-jn\omega t}dt$
- C. A sum of sines and cosines
- D. An integral over all frequencies

> ✅ **Answer: B.** "Sum of sines and cosines" was an old-exam distractor; that describes the real series.

**Q102. (Select all)** Complex Fourier series:
- A. Coefficients are evaluated over a full period; the start point is not important
- B. It is connected to the real series by Euler's relation
- C. It contains no phase information
- D. Real and complex notations are equivalent

> ✅ **Answer: A, B, D.** C is false: the angle of $c_n$ is the phase.

**Q103.** For $n>0$, the complex coefficient relates to the real coefficients as:
- A. $c_n=a_n+jb_n$
- B. $c_n=b_n/a_n$
- C. $c_n=(a_n-jb_n)/2$
- D. $c_n=2a_n$

> ✅ **Answer: C.** $c_0=a_0/2$; $c_{-n}=\overline{c_n}$; harmonic amplitude $=2\lvert c_n\rvert$.

**Q104.** Euler's relation is:
- A. $e^{jx}=j\cos x+\sin x$
- B. $e^{jx}=\cos x+j\sin x$
- C. $e^{x}=\cos x+\sin x$
- D. $e^{jx}=\cos x-j\sin x$

> ✅ **Answer: B.**

**Q105.** The Fourier transform of a Dirac impulse $\delta(t)$ is:
- A. An impulse at zero frequency
- B. Two impulses at $\pm\omega_0$
- C. Zero
- D. A constant (flat): all frequencies

> ✅ **Answer: D.**

**Q106.** The Fourier transform of a DC signal (constant 1) is:
- A. A sinc function
- B. $2\pi\delta(\omega)$, an impulse at zero frequency
- C. A flat spectrum
- D. Two impulses

> ✅ **Answer: B.**

**Q107.** The Fourier transform of $\cos(\omega_0t)$ is:
- A. $\pi[\delta(\omega+\omega_0)+\delta(\omega-\omega_0)]$
- B. 1
- C. $j\pi[\delta(\omega+\omega_0)-\delta(\omega-\omega_0)]$
- D. $2\pi\delta(\omega)$

> ✅ **Answer: A.** The sine transform has $j$ and a minus sign.

**Q108.** The order of Fourier methods on the overview slide is:
- A. Real series → complex series → CFT → DFT → FFT → power spectrum
- B. Power spectrum → FFT → series
- C. DFT → real series → FFT
- D. FFT → DFT → CFT → series

> ✅ **Answer: A.**

**Q109.** A signal is observed for T = 10 s with sampling interval 1 ms. The frequency precision is:
- A. 0.01 Hz
- B. 0.1 Hz
- C. 1 Hz
- D. 10 Hz

> ✅ **Answer: B.** $\Delta f=1/T$. The full range is $1/\Delta t=1000$ Hz, shown up to 500 Hz.

**Q110.** A 0.5 s epoch sampled at 1 kHz has precision and range of:
- A. 2 Hz and 500 Hz
- B. 1 Hz and 500 Hz
- C. 2 Hz and 1000 Hz
- D. 0.5 Hz and 1000 Hz

> ✅ **Answer: A.** "1 Hz" was the old-exam distractor.

**Q111.** A 5 s epoch sampled at 200 Hz has precision and range of:
- A. 0.2 Hz and 100 Hz
- B. 0.2 Hz and 200 Hz
- C. 0.1 Hz and 100 Hz
- D. 5 Hz and 100 Hz

> ✅ **Answer: A.** "0.1 Hz" was the old-exam distractor.

**Q112.** Which change improves (refines) frequency precision?
- A. Using a notch filter
- B. Increasing the epoch length
- C. Increasing ADC bits
- D. Increasing the sampling rate

> ✅ **Answer: B.** Precision $=1/T$ depends only on the epoch length. Sampling rate sets the range.

**Q113.** To separate peaks at 9.5 Hz and 10.0 Hz, the minimum epoch length is:
- A. 2 s
- B. 10 s
- C. 1 s
- D. 0.5 s

> ✅ **Answer: A.** Need $\Delta f\le0.5$ Hz, so $T\ge2$ s.

**Q114.** The DFT is defined as:
- A. $X(k)=\sum_{n=0}^{N-1}x(n)W_N^{kn}$
- B. $X(k)=x(k)^2$
- C. $X(k)=\int x(t)e^{-j\omega t}dt$
- D. $X(k)=\frac1N\sum x(n)W_N^{-kn}$

> ✅ **Answer: A.** The inverse is $x(n)=\frac1N\sum_kX(k)W_N^{-kn}$.

**Q115.** In deriving the DFT from the CFT, what is "smuggled out"?
- A. $2\pi$
- B. N
- C. $\Delta t$
- D. $W_N$

> ✅ **Answer: C.** Then $f(t_n)\to x(n)$ and $F_a(j\omega_k)\to X(k)$.

**Q116.** Why does the inverse-DFT sum stop at N/2 − 1 instead of N/2?
- A. N/2 is always zero
- B. Because of aliasing filters
- C. On the circular frequency scale, −N/2 and N/2 are the same point
- D. To save computation

> ✅ **Answer: C.**

**Q117.** The twiddle factor is:
- A. $W_N=e^{+j2\pi N}$
- B. $W_N=e^{-j2\pi/N}$
- C. $W_N=2\pi/N$
- D. $W_N=N\log_2N$

> ✅ **Answer: B.** Its powers are points on the unit circle.

**Q118.** The key property of the twiddle factor that makes the FFT efficient is:
- A. It grows with N
- B. It is periodic: $W_N^m=W_N^{m+N}$
- C. It is real
- D. It is always 1

> ✅ **Answer: B.**

**Q119.** For N = 4, the values $W_4^0, W_4^1, W_4^2, W_4^3$ are:
- A. $0, 1, 0, -1$
- B. $1, 1, 1, 1$
- C. $1, j, -1, -j$
- D. $1, -j, -1, +j$

> ✅ **Answer: D.** The exponent is negative, so the rotation is clockwise. So $W_4^0=W_4^4$, $W_4^1=W_4^5$, $W_4^2=W_4^6=-1$.

**Q120. (Select all)** Twiddle factor statements:
- A. $W_4^3=W_4^4$
- B. $W_8^2=W_8^{10}$
- C. $\theta=0$ and $\theta=2\pi$ give identical values
- D. It appears in both the DFT and the inverse DFT

> ✅ **Answer: B, C, D.** A is false: $W_4^3=+j$ but $W_4^4=1$ (old-exam distractor).

**Q121.** Compared with the direct DFT, the FFT needs:
- A. $N/2$ multiplications
- B. $N^2$ instead of $N\log_2N$ multiplications
- C. The same number but less memory
- D. $N\log_2N$ instead of $N^2$ multiplications

> ✅ **Answer: D.** Cooley & Tukey, 1965. For N = 1024: 10,240 vs 1,048,576.

**Q122.** Which statement about the FFT is correct?
- A. It gives lower frequency resolution than the DFT
- B. It is an exact, faster algorithm giving the same result as the DFT
- C. It is a hardware filter that removes noise
- D. It works on continuous-time signals directly

> ✅ **Answer: B.** The lab showed the maximum DFT–FFT difference ≈ 0.

**Q123.** The power spectrum is:
- A. $S=\frac2N\sqrt{XX^{\ast}}$
- B. $S=XX^{\ast}/N$, power vs frequency
- C. $\arctan(\mathrm{Im}X/\mathrm{Re}X)$
- D. Amplitude vs time

> ✅ **Answer: B.** The amplitude spectrum is $\frac2N\sqrt{XX^{\ast}}$; the phase is $\arctan$ (no normalization needed).

**Q124.** Why is the one-sided amplitude spectrum normalized by 2/N?
- A. So peak heights match the time-domain sine amplitudes (energy is split between ± frequencies)
- B. To convert to dB
- C. To reduce leakage
- D. To remove DC

> ✅ **Answer: A.** Lab: sines of amplitude 2, 3, 8, 3 gave peaks of 2, 3, 8, 3.

**Q125.** On the circular frequency scale of the DFT:
- A. π is the DC component
- B. 0→π are positive and π→2π are negative frequencies
- C. 0→2π are all positive frequencies
- D. Negative frequencies do not exist

> ✅ **Answer: B.** The power spectrum is **even**, so only the first half (up to Nyquist) is usually shown.

**Q126.** Analysing a finite epoch is equivalent to:
- A. Low-pass filtering
- B. Sampling at Nyquist
- C. Adding noise
- D. Multiplying the signal by a rectangular window, which convolves the spectrum with the window spectrum

> ✅ **Answer: D.** This spreads energy next to a pure tone's peak (leakage).

**Q127.** For a rectangular window of T = 4 s, the spectral ripples are spaced by:
- A. 1 Hz
- B. 4 Hz
- C. 0.5 Hz
- D. 0.25 Hz

> ✅ **Answer: D.** Spacing $=1/T$ (T = 2 → 0.5 Hz; T = 1 → 1 Hz). "0.5 Hz for T = 4" was the old-exam distractor.

**Q128.** Which is the **Hamming** window?
- A. $1$
- B. $0.54+0.46\cos(\pi t/T)$
- C. $1-\lvert t\rvert/T$
- D. $0.5+0.5\cos(\pi t/T)$

> ✅ **Answer: B.** Hann is $0.5+0.5\cos$, Bartlett (triangular) is $1-\lvert t\rvert/T$, rectangular is 1.

**Q129.** A neonatal respiratory spectrum shows peaks at 1.5 Hz and about 3 Hz. The 3 Hz peak is best explained as:
- A. A second independent breathing rhythm
- B. DC offset
- C. Aliasing
- D. A harmonic, because the waveform is not purely sinusoidal

> ✅ **Answer: D.** Harmonics do **not** require a DC offset.

**Q130. (Select all)** Why must spectra of physiological signals be interpreted with caution?
- A. The signals are rarely stationary.
- B. Low-frequency power can come from trends or periods longer than the analysis window.
- C. High frequencies can be contaminated by sudden events.
- D. Window choice is unimportant because they are stationary.

> ✅ **Answer: A, B, C.** D is false.

---

## Part 5 — Noise, Random Processes, SNR (Q131–Q150)

**Q131.** Which is an example of **random** noise?
- A. 50 Hz hum from power lines
- B. Thermal noise from resistors
- C. Systematic bias
- D. Artifacts from switching instruments

> ✅ **Answer: B.** Hum and switching artifacts are man-made and non-random.

**Q132.** "Measuring appetite after dinner" is used as an example of:
- A. Systematic bias
- B. Thermal noise
- C. Dynamical noise
- D. Aliasing

> ✅ **Answer: A.**

**Q133.** In $M_i=x_i+N_i$ with $x_i=0.8x_{i-1}+3.5$, the process $x$ is:
- A. Deterministic; only its measurement is noisy
- B. Stochastic
- C. Chaotic
- D. Non-stationary

> ✅ **Answer: A.** Its fixed point is $3.5/(1-0.8)=17.5$.

**Q134.** In $x_i=[0.8x_{i-1}+3.5]+D_{i-1}$, the noise D is:
- A. Quantization noise
- B. Measurement noise
- C. Hum
- D. Dynamical noise; the process becomes stochastic

> ✅ **Answer: D.** The noise enters the state and carries forward.

**Q135.** Compared with additive measurement noise, dynamical noise produces:
- A. Faster, independent fluctuations
- B. Only DC shifts
- C. No visible difference
- D. Slower trends, because sequential values are correlated

> ✅ **Answer: D.** "Additive noise creates slower trends" was the old-exam distractor.

**Q136.** Which is an example of dynamical noise?
- A. Temperature fluctuations that physically influence membrane processes during recording
- B. Quantization error
- C. A loose electrode
- D. Thermal noise in the amplifier

> ✅ **Answer: A.**

**Q137.** Why are dynamical noise terms often used in models?
- A. As a statistical proxy for unknown details of complex physiological systems
- B. They improve sampling
- C. They make processes deterministic
- D. They remove measurement noise

> ✅ **Answer: A.**

**Q138.** A probability density function must satisfy:
- A. $p(x)=1$ everywhere
- B. $p(x)<0$ for some x
- C. $\int_{-\infty}^{\infty}p(x)dx=1$
- D. $\int p(x)dx=0$

> ✅ **Answer: C.** Cumulative $F(x)=\int_{-\infty}^xp$; survival $=1-F(x)$.

**Q139.** A collection of sample functions of a random process is called:
- A. A montage
- B. A window
- C. An ensemble
- D. A spectrum

> ✅ **Answer: C.** A sample function is one realization.

**Q140.** A random process is **stationary** if:
- A. Its variance is zero
- B. $x(t)$ is constant over time
- C. The distribution from which $x(t)$ originates does not change over time
- D. It is deterministic

> ✅ **Answer: C.**

**Q141.** A process is **ergodic** if:
- A. Each sample function has a different PDF
- B. You may only average across trials
- C. Its variance is zero
- D. Any sample function is representative of the whole ensemble, so time averages give the statistics

> ✅ **Answer: D.**

**Q142.** Each trial is a flat line at a random level (different per trial). This process is:
- A. Stationary but not ergodic
- B. Deterministic
- C. Stationary and ergodic
- D. Ergodic but not stationary

> ✅ **Answer: A.** One trial's time average only gives its own level, not the ensemble mean.

**Q143.** Similar amplitude histograms across sample functions support assuming:
- A. Harmonics
- B. Stationarity
- C. Aliasing
- D. Determinism

> ✅ **Answer: B.**

**Q144.** Signal-to-noise ratio is defined in the slides as:
- A. Signal peak minus noise peak
- B. $ms_{signal}\times ms_{noise}$
- C. $ms_{signal}/ms_{noise}$, or $10\log_{10}$ of that ratio in dB
- D. $rms_{noise}/rms_{signal}$

> ✅ **Answer: C.** Using rms values: $20\log_{10}(rms_s/rms_n)$.

**Q145.** SNR expressed in dB:
- A. Has units of µV²
- B. Is always positive
- C. Is dimensionless
- D. Has units of volts

> ✅ **Answer: C.** The plain ratio is used by manufacturers as a figure of merit.

**Q146.** Signal rms 20 µV, noise rms 10 µV. The SNR is:
- A. 4 (≈ 6 dB)
- B. 100 (20 dB)
- C. 2 (3 dB)
- D. 20 (13 dB)

> ✅ **Answer: A.** Power ratio $=(20/10)^2=4$; $10\log_{10}4\approx6$ dB.

**Q147.** A sine of amplitude 10 µV has a mean-square value of:
- A. 7.07 µV²
- B. 10 µV²
- C. 100 µV²
- D. 50 µV²

> ✅ **Answer: D.** $A^2/2$. The rms is $A/\sqrt2\approx7.07$ µV.

**Q148.** In the amplitude figure, the largest noise source is:
- A. Thermal noise of electrodes
- B. Quantization noise
- C. Amplifier noise
- D. Hum

> ✅ **Answer: D.** Hum is "enemy #1" and can even spoil averaging.

**Q149.** Which signal has the smallest amplitude?
- A. Evoked potentials
- B. EMG/ECG
- C. Intracellular potentials
- D. EEG

> ✅ **Answer: A.** Order: EP < EEG < EMG/ECG < intracellular. EP, EEG and EMG/ECG are extracellular.

**Q150. (Select all)** Correct statements:
- A. Stationarity and ergodicity are often implicitly assumed.
- B. Techniques can be useful even if these assumptions are not strictly met.
- C. Stationarity guarantees the process is deterministic.
- D. For a stationary ergodic process, $\hat x=\frac1N\sum x_i$ estimates the mean.

> ✅ **Answer: A, B, D.** C is false.

---

## Part 6 — Signal Averaging and Evoked Potentials (Q151–Q175)

**Q151. (Select all)** Assumptions behind signal averaging:
- A. Signal and noise are uncorrelated
- B. The timing of the signal is known
- C. The signal changes substantially across trials
- D. Noise is random with zero mean

> ✅ **Answer: A, B, D.** C is false: the signal must be **consistent**. Averaging is robust to minor violations.

**Q152.** The ultimate reason to perform signal averaging is to:
- A. Increase the signal-to-noise ratio
- B. Change the reference
- C. Remove harmonics
- D. Increase the sampling rate

> ✅ **Answer: A.**

**Q153.** Averaging N trials of random zero-mean noise reduces the residual noise rms by a factor of:
- A. $\sqrt N$
- B. $N^2$
- C. $\log_2N$
- D. N

> ✅ **Answer: A.** The time-locked signal is preserved; power SNR improves by N.

**Q154.** After averaging 256 trials, the residual noise rms is reduced by:
- A. 256×
- B. 64×
- C. 16×
- D. 8×

> ✅ **Answer: C.** $\sqrt{256}=16$ (the slide figure used 256 trials).

**Q155.** A 2 µV evoked response sits in 20 µV rms noise. How many trials give amplitude SNR = 1?
- A. 10
- B. 100
- C. 400
- D. 40

> ✅ **Answer: B.** $20/\sqrt N=2$ gives $N=100$.

**Q156.** To halve the residual noise again, you need:
- A. 2× the trials
- B. 4× the trials
- C. Half the trials
- D. 8× the trials

> ✅ **Answer: B.** Noise falls as $1/\sqrt N$.

**Q157.** Averaging 400 trials improves power SNR by about:
- A. 26 dB
- B. 52 dB
- C. 13 dB
- D. 20 dB

> ✅ **Answer: A.** $10\log_{10}400\approx26$ dB.

**Q158.** In the slide figure, the difference between the odd-trial and even-trial averages shows:
- A. An estimate of the residual noise
- B. The prestimulus baseline
- C. The harmonic content
- D. The signal doubled

> ✅ **Answer: A.** Their sum gives the signal average.

**Q159.** Prestimulus noise estimation assumes that:
- A. The data are stored offline
- B. The noise is periodic
- C. The signal occurs both before and after the trigger
- D. The time-locked signal occurs only after the trigger

> ✅ **Answer: D.**

**Q160.** Prestimulus estimation is **not** appropriate for a spike-triggered average because:
- A. Activity surrounds the trigger (there is no clean pre-trigger period)
- B. Spikes are too small
- C. Spikes are periodic
- D. It needs random triggers

> ✅ **Answer: A.**

**Q161.** With repetitive stimulation, the prestimulus epoch can be unreliable because:
- A. The amplifier saturates
- B. Noise becomes zero
- C. The trigger is unknown
- D. Late components of the previous response continue into the next prestimulus epoch

> ✅ **Answer: D.** Mitigations: longer inter-stimulus intervals, high-pass filtering of slow components, or another estimator.

**Q162.** The bootstrap method forms a control average by:
- A. Using only prestimulus data
- B. Inverting every other trial
- C. Using random triggers instead of the true triggers
- D. Filtering at 50 Hz

> ✅ **Answer: C.** Random triggers destroy time-locking, so the signal is not enhanced (it is still present, just not aligned).

**Q163.** Bootstrapping works best when:
- A. There is no noise
- B. The time-locked component is small relative to the noise, and data are stored (offline)
- C. The time-locked component is much larger than the noise
- D. Stimulation is online only

> ✅ **Answer: B.** Repeated bootstraps give control averages to statistically validate the true average.

**Q164.** The ± average is computed by:
- A. Averaging only positive values
- B. Inverting every other trial before averaging
- C. Using random triggers
- D. Subtracting the prestimulus mean

> ✅ **Answer: B.** The consistent signal cancels; the residual noise remains.

**Q165.** The residual noise rms of the ± average compared with the standard average is:
- A. The same
- B. Smaller
- C. Zero
- D. Larger

> ✅ **Answer: A.** Inverted random noise has the same distribution.

**Q166.** A 50 Hz hum and a 10 Hz stimulus rate:
- A. Every stimulus lands on the same hum phase, leaving a large 50 Hz component in the average
- B. Hum always averages out
- C. The hum doubles in frequency
- D. The signal is removed

> ✅ **Answer: A.** 50/10 = 5 whole cycles between stimuli.

**Q167.** Which remedy avoids phase-locking between stimulus and hum?
- A. Increasing ADC bits
- B. Using CAR
- C. Using a 10 Hz rate
- D. Randomizing the stimulus interval or using a noninteger rate (e.g., 7.7 Hz)

> ✅ **Answer: D.**

**Q168.** With 50 Hz mains, which stimulus rate **also locks** to the hum despite being noninteger?
- A. 12.5 Hz
- B. 7.7 Hz
- C. 11 Hz
- D. 3.3 Hz

> ✅ **Answer: A.** 50/12.5 = 4 (integer). The precise rule: $f_{hum}/f_{stim}$ is an integer.

**Q169.** Background EEG spans roughly:
- A. 1–10 Hz
- B. 100–1000 Hz
- C. 0.01–100 Hz
- D. 0–10 kHz

> ✅ **Answer: C.** Amplitude ~100 µV; power-law PSD; five bands.

**Q170.** Typical background EEG amplitude is about:
- A. 1 nV
- B. 1 V
- C. 100 µV
- D. 100 mV

> ✅ **Answer: C.**

**Q171. (Select all)** Background EEG:
- A. Is considered stochastic
- B. Long-term EEG is non-stationary
- C. Short-term EEG can be approximately stationary (seconds to minutes)
- D. Is divided into four bands

> ✅ **Answer: A, B, C.** D is false: there are **five** bands.

**Q172.** The P300 in the oddball paradigm is:
- A. An artifact
- B. A centrally located positive wave at about 300 ms to rare stimuli, reflecting novelty
- C. A frontal negative wave before a button press
- D. A negative wave at 300 ms to frequent stimuli

> ✅ **Answer: B.**

**Q173.** The contingent negative variation (CNV) is:
- A. Visible in every single trial
- B. A muscle artifact
- C. A positive wave after a rare stimulus
- D. A centrofrontal negative wave between a warning stimulus and a second stimulus requiring a button press

> ✅ **Answer: D.** Recorded at Cz; weak, so it needs averaging (32 trials in the example).

**Q174.** AEP, VEP and SEP are evoked potentials from stimulation of:
- A. Autonomic, vestibular and sensory systems
- B. Eyes only
- C. Auditory, visual and somatosensory systems
- D. Alpha, beta, theta rhythms

> ✅ **Answer: C.** They capture the primary perception process.

**Q175.** Why was the CNV averaged over trials?
- A. It is periodic
- B. It is weak relative to ongoing EEG
- C. It only appears in the average of one trial
- D. It is larger than ongoing EEG

> ✅ **Answer: B.** The ± average served as the residual noise estimate.

---

## Part 7 — Preprocessing and Artifacts (Q176–Q205)

**Q176. (Select all)** Notch filtering for line noise:
- A. Is used to eliminate 50/60 Hz line noise
- B. Is the optimal option with no drawbacks
- C. Can distort signal components between 50 and 70 Hz
- D. Can introduce transient oscillations in baseline activity

> ✅ **Answer: A, C, D.** B is false.

**Q177.** Low-pass filtering below 50 Hz after a notch filter can:
- A. Increase gamma power
- B. Alter EEG temporal structure or cause spurious interactions between channels
- C. Never affect the data
- D. Remove all artifacts

> ✅ **Answer: B.**

**Q178.** The multitaper line-noise removal pipeline is:
- A. Sliding window → multitaper transform → regression → statistical test → subtract significant noise → repeat
- B. Notch → low-pass → CAR
- C. Averaging → bootstrap
- D. ICA → PCA → notch

> ✅ **Answer: A.** It avoids damaging background spectral components.

**Q179.** Multitaper spectral estimation is **most** useful for:
- A. Low-SNR, higher-frequency activity, or single-trial power estimates
- B. Separating narrow peaks below 30 Hz
- C. Detecting QRS complexes
- D. Removing sweat artifact

> ✅ **Answer: A.** Below ~30 Hz SNR is already high and its spectral smoothing blurs nearby bands.

**Q180.** A multitaper spectrum is obtained by:
- A. Averaging trials
- B. Multiplying data by several tapers and averaging their power spectra
- C. Notch filtering
- D. Using a single Hann taper

> ✅ **Answer: B.** A standard short-time FFT uses one taper.

**Q181.** Which is **not** a bad-channel detection criterion from the slides?
- A. Channel name ending in an odd number
- B. High ratio of high- to low-frequency power
- C. Robust z-score of amplitude above a threshold
- D. Low correlation with other channels after low-pass filtering

> ✅ **Answer: A.**

**Q182.** Correlation-based bad-channel detection works because:
- A. EEG is stationary
- B. Normal EEG shows low-frequency correlations across channels
- C. Normal EEG channels are uncorrelated
- D. Bad channels are always correlated with each other

> ✅ **Answer: B.**

**Q183.** Which interpolation method gives accurate scalp potential estimates with dense electrode mapping?
- A. Notch filtering
- B. Radial basis functions
- C. Nearest-neighbour averaging
- D. Spherical splines

> ✅ **Answer: D.** Radial basis functions are cost-effective with lower computational load.

**Q184.** Artifacts from heart, eyes and muscles are classified as:
- A. Equipment
- B. External
- C. Internal
- D. Environmental

> ✅ **Answer: C.** External: environment (e.g., wireless), electrode attachment, recording equipment.

**Q185.** Which artifacts can be inhibited once identified?
- A. External
- B. Both equally
- C. Internal
- D. Neither

> ✅ **Answer: A.** Internal artifacts permeate EEG and are hard to prevent; most removal methods target them.

**Q186.** Electrically, the eye is a dipole with:
- A. Cornea negative, retina positive
- B. Both positive
- C. No charge separation
- D. Cornea positive, retina negative

> ✅ **Answer: D.**

**Q187.** Bell's phenomenon refers to:
- A. Heartbeat artifact
- B. Eyes rolling up slightly during a blink
- C. Eyes moving laterally
- D. Pupil dilation

> ✅ **Answer: B.**

**Q188.** During a blink, the cornea moves:
- A. Closer to the frontal electrodes Fp1/Fp2
- B. Farther from Fp1/Fp2
- C. Toward O1/O2
- D. Toward T3/T4

> ✅ **Answer: A.** Blink artifacts are very high amplitude, bifrontal, maximal at Fp1/Fp2, with no posterior field.

**Q189.** Opposite polarities at F7 and F8 are the signature of:
- A. ECG artifact
- B. Lateral eye movements
- C. Blinks
- D. Sweat

> ✅ **Answer: B.** Looking right: right cornea toward F8 (positive), F7 negative.

**Q190. (Select all)** Blink artifacts:
- A. Are strong enough to be visible in EEG
- B. Are low amplitude and hard to see
- C. Mostly affect channels near the eyes
- D. Primarily create opposite polarities at F7 and F8

> ✅ **Answer: A, C.** B and D are false.

**Q191. (Select all)** Muscle artifacts:
- A. Originate from muscle contractions in various body parts
- B. Have a single stereotyped waveform
- C. Have a wide, almost uniform scalp distribution
- D. Affect both high- and low-frequency EEG components

> ✅ **Answer: A, C, D.** B is false: they are more diverse than ocular artifacts. They are detected by EMG and often task-related, which makes removal hard.

**Q192.** Why is muscle-artifact removal challenging?
- A. It is always at 50 Hz
- B. Diverse sources, wide distribution, varying spectra and task-related timing
- C. EMG cannot detect it
- D. It only affects one electrode

> ✅ **Answer: B.**

**Q193.** Chewing artifact originates from:
- A. The temporalis muscle
- B. The eyes
- C. The heart
- D. The tongue

> ✅ **Answer: A.** Sudden, intermittent bursts of generalized very fast activity.

**Q194.** Compared with chewing artifact, generalized periodic fast activity is:
- A. Slightly slower (beta frequency) and lower amplitude
- B. Faster and higher amplitude
- C. A cardiac artifact
- D. Identical

> ✅ **Answer: A.**

**Q195.** Hypoglossal artifact:
- A. Comes from tongue movement, shows synchronous slow diffuse waves, and is reproducible by saying "la la la"
- B. Is time-locked to QRS
- C. Comes from the temporalis muscle
- D. Is below 0.1 Hz sweat activity

> ✅ **Answer: A.**

**Q196.** ECG artifact is characterized by:
- A. Right-sided, high-amplitude waves
- B. Waveforms time-locked to the QRS complex, mostly left-sided, relatively low amplitude
- C. Waves 200 ms after the QRS at one electrode
- D. Very slow waves below 0.5 Hz

> ✅ **Answer: B.** The heart lies in the left chest.

**Q197.** Cardioballistic artifact occurs when:
- A. An electrode sits over an artery and the pulse moves it (~200 ms after each QRS)
- B. The ground electrode is loose
- C. The heart's electrical field reaches the scalp
- D. The patient chews

> ✅ **Answer: A.** It is a motion artifact, much less common than ECG artifact.

**Q198.** Sweat artifact is:
- A. Very slow (< 0.5 Hz), low amplitude, from NaCl charge, with any localization
- B. Always bilateral
- C. Fast, high-amplitude activity
- D. At 50 Hz

> ✅ **Answer: A.**

**Q199.** Dense 50 Hz activity appears only in derivations containing Fp1. The most likely cause is:
- A. Blinks
- B. Ground electrode failure
- C. Sweat
- D. A bad Fp1 electrode

> ✅ **Answer: D.** A notch filter would greatly reduce it; proper electrode placement prevents it.

**Q200.** Electrical artifacts at 60 Hz (50 Hz in Europe) can come from:
- A. Tongue movement
- B. Sweat
- C. Electrical appliances and cell-phone charging
- D. Eye movements

> ✅ **Answer: C.**

**Q201.** The slide ECG example also warns that the display was at the wrong speed. The advice is to:
- A. Ignore the timing
- B. Always check reading speed and calibrate the screen before reading
- C. Apply a notch filter
- D. Re-reference to CAR

> ✅ **Answer: B.** It appeared to be 60 mm/s instead of 30 mm/s.

**Q202.** The most frequent physiological EEG contaminants are:
- A. Hum and quantization
- B. Wireless, electrode and equipment artifacts
- C. Sweat and chewing only
- D. Ocular, muscular and cardiac artifacts

> ✅ **Answer: D.**

**Q203.** Why are external artifacts increasingly important?
- A. They cannot be identified
- B. They are always internal
- C. Hospitals ban EEG
- D. EEG is moving toward in-home healthcare systems

> ✅ **Answer: D.**

**Q204.** Before computing CAR, you should:
- A. Detect and remove (or interpolate) bad channels
- B. Apply a notch filter at 10 Hz
- C. Add bad channels to the average
- D. Increase the sampling rate

> ✅ **Answer: A.**

**Q205. (Select all)** Artifact pairs matched correctly:
- A. Lateral eye movement — F7/F8 opposite polarities
- B. Cardioballistic — simultaneous with QRS
- C. Sweat — < 0.5 Hz
- D. Chewing — temporalis muscle

> ✅ **Answer: A, C, D.** B is false: cardioballistic artifact comes ~200 ms **after** the QRS; ECG artifact is simultaneous.

---

## Part 8 — Brain Rhythms, Filters, Time-Domain Methods, Labs (Q206–Q220)

**Q206.** Delta rhythm (0.5–4 Hz) is strongest during:
- A. Dreamless, restorative (deep) sleep
- B. Eyes-closed relaxation
- C. Active problem solving
- D. Conversation

> ✅ **Answer: A.** The slowest waves; the state of healing and rejuvenation.

**Q207.** Theta (4–8 Hz) is associated with:
- A. Alert active thinking
- B. Eye blinks
- C. Creativity, insight, dreams, reduced consciousness, deep meditation and daydreaming
- D. Peak mental state in monks only

> ✅ **Answer: C.** Its source is probably **frontal**, not occipital.

**Q208.** Alpha (8–13 Hz):
- A. Comes from tongue movement
- B. Becomes detectable when the eyes are closed and the mind is relaxed; among the most easily observed and first discovered
- C. Is the fastest EEG rhythm
- D. Is associated with alert conversation

> ✅ **Answer: B.** Also seen in yoga and just before falling asleep.

**Q209.** Beta (13–32 Hz) is associated with:
- A. Alert, normal consciousness and active thinking (conversation, decisions, problem solving, learning)
- B. Deep sleep
- C. Relaxation with eyes closed
- D. Dreaming

> ✅ **Answer: A.** "Alpha is 13–32 Hz and alert" was an old-exam distractor.

**Q210.** Gamma (32–100 Hz):
- A. Is the fastest measurable rhythm, linked to heightened perception (peak state), and stronger in very long-term meditators
- B. Occurs only in sleep
- C. Is the slowest EEG rhythm
- D. Is below 4 Hz

> ✅ **Answer: A.**

**Q211. (Select all)** Correct brain-rhythm statements:
- A. Theta is 8–13 Hz.
- B. Theta is strongly detectable during dreaming.
- C. Gamma involves simultaneous processing of information from different brain parts.
- D. Alpha is among the first discovered rhythms.

> ✅ **Answer: B, C, D.** A is false: theta is 4–8 Hz.

**Q212.** Reduced frontal gamma activity may indicate:
- A. Restless legs syndrome
- B. Deep sleep
- C. Sweat artifact
- D. Declined cognitive function

> ✅ **Answer: D.** Increased midline beta may indicate restless legs syndrome.

**Q213.** A band-stop filter (such as a notch filter):
- A. Passes only one band
- B. Passes only high frequencies
- C. Passes only low frequencies
- D. Removes a band and passes frequencies on both sides

> ✅ **Answer: D.** Ideal filters have sharp edges; realistic filters have gradual transitions.

**Q214.** Which filter reduces slow drifts such as sweat artifact?
- A. High-pass
- B. Notch at 50 Hz
- C. Low-pass
- D. Band-stop at 100 Hz

> ✅ **Answer: A.**

**Q215.** QRS-complex detection typically involves:
- A. Multitaper analysis
- B. Notch filtering only
- C. Pretreating the signal to remove artifacts, then detecting extreme values above a threshold
- D. Averaging with random triggers

> ✅ **Answer: C.** This is peak detection, which also gives intervals between events.

**Q216.** Auto-correlation is:
- A. Cross-correlation of a signal with itself (different parts of the same signal)
- B. Correlation of two different signals
- C. Level detection
- D. Template matching with a wavelet

> ✅ **Answer: A.** Template matching correlates a known template; wavelets are special templates.

**Q217.** In the dot-product lab, why use complex exponentials $e^{j2\pi ft}$ as templates?
- A. The magnitude detects the frequency regardless of phase, and the angle gives the phase
- B. They are faster to compute
- C. They remove noise
- D. Real sines cannot be multiplied

> ✅ **Answer: A.** A real sine template can give ≈ 0 at the right frequency if the phase is 90° off.

**Q218.** In the FFT lab (fs = 1000 Hz, T = 2 s), N and the frequency resolution are:
- A. 500 and 0.5 Hz
- B. 1000 and 1 Hz
- C. 2000 and 0.5 Hz
- D. 2000 and 2 Hz

> ✅ **Answer: C.** Peaks at 4, 6, 8, 10 Hz had heights 2, 3, 8, 3 using $2\lvert X\rvert/N$.

**Q219.** The lab code `Amp*exp(2*1i*pi*f0*t + phas)`:
- A. Produces a real sine
- B. Does not shift the phase; because `phas` lacks `1i`, it scales the amplitude by $e^{phas}$
- C. Produces aliasing
- D. Correctly shifts the phase

> ✅ **Answer: B.** Correct form: `Amp*exp(1i*(2*pi*f0*t + phas))`.

**Q220.** The dot product of $[2,4,2,1,5,3,1]$ and $[4,2,2,-3,2,5,0]$ is:
- A. 32
- B. 42
- C. 45
- D. 0

> ✅ **Answer: B.** $8+8+4-3+10+15+0=42$.

---

## Final 15-Minute Cheat Sheet

| Topic | Must-remember |
|---|---|
| Nernst | out/in; 61.54 mV/decade (Ca²⁺ 30.77); $E_K$ −80, $E_{Na}$ +62, $E_{Ca}$ +123, $E_{Cl}$ −65 mV |
| Resting potential | −65 mV; $P_K:P_{Na}$ = 40:1 (Goldman) |
| AP | rest: VG channels closed; Na⁺ in → overshoot (never reaches $E_{Na}$) → Na⁺ inactivates (~1 ms) + K⁺ out → undershoot toward $E_K$ |
| Refractory | absolute: Na⁺ inactivated; relative: K⁺ open, bigger stimulus needed |
| All-or-none | size fixed; firing rate codes strength |
| Conduction | passive decays in mm; active no decrement; Na⁺ channels at nodes; oligodendrocyte CNS-many, Schwann PNS-one |
| Spike-initiation | axon hillock (CNS), sensory endings (sensory neurons) |
| Synapses | gap junction 3 nm, 6 connexins, 2 connexons, bidirectional, fast; EPSP Na⁺, IPSP Cl⁻; Loewi 1921 |
| EEG origin | PSPs of perpendicular pyramidal cells; radial crown strongest; sulcal walls cancel; deep weaker; synchrony needed |
| Why EEG | non-invasive, direct, portable, ms resolution, rich, open, cheap; poor spatial |
| Sampling | Nyquist rate $2f_{max}$; Nyquist frequency $F_s/2$; 5× in practice; anti-alias before ADC; alias $\lvert f-kF_s\rvert$ |
| ADC | $2^n$ levels |
| Electrodes | Ag/AgCl: ionic→electronic, lower capacitance, low frequencies |
| Amplifier | $V_{AG}-V_{RG}$; ground (frontal) matters less; no neutral reference; ear lobes |
| 10–20 | Jasper 1958; odd left, even right, z midline |
| Montages | bipolar neighbours; biauricular ear average; CAR mean of all (bad channels first) |
| Fourier series | DC $a_0/2$; $a_n,b_n=\frac2T\int f\cos/\sin$; even → $b_n=0$; odd → $a_n=0$ |
| Complex series | $c_n=\frac1T\int fe^{-jn\omega t}$; equivalent; has phase; start point irrelevant |
| FT pairs | δ ↔ 1; 1 ↔ 2πδ(ω); cos ↔ π[δ(ω+ω₀)+δ(ω−ω₀)] |
| DFT | $X(k)=\sum x(n)W_N^{kn}$; $W_N=e^{-j2\pi/N}$ periodic; inverse has 1/N |
| Resolution | precision $1/T$; range $F_s/2$; 0.5 s/1 kHz → 2 Hz/500 Hz; 5 s/200 Hz → 0.2 Hz/100 Hz |
| FFT | Cooley–Tukey 1965; $N\log_2N$ vs $N^2$; exact |
| Spectra | $S=XX^{\ast}/N$; $AS=\frac2N\sqrt{XX^{\ast}}$; phase arctan, no normalization; power spectrum even |
| Windows | finite epoch = rectangular; ripples 1/T (T = 4 → 0.25 Hz); Hann 0.5+0.5cos; Hamming 0.54+0.46cos |
| Noise | dynamical → correlated slow trends, stochastic; stationary = distribution constant; ergodic = one sample represents all |
| SNR | $ms_s/ms_n$; 10 log (power) = 20 log (rms); dimensionless; hum = enemy #1 |
| Averaging | noise ÷ √N; assumptions: uncorrelated, known timing, consistent signal, random zero-mean noise |
| Noise estimates | prestimulus (late responses contaminate); bootstrap (random triggers, offline, small signal); ± average (same rms) |
| Hum | 10 Hz locks 50 Hz; use noninteger / random rate |
| Background EEG | 0.01–100 Hz, ~100 µV, power law, 5 bands, stochastic, long-term non-stationary |
| EPs | P300 positive 300 ms oddball; CNV negative, warning → second stimulus, Cz |
| Preprocessing | notch distorts 50–70 Hz + ringing; multitaper > 30 Hz; bad channels: z-score, correlation, HF/LF ratio |
| Artifacts | blink Fp1/Fp2 closer (Bell's); lateral F7/F8 opposite; muscle wide & broadband; chewing temporalis; tongue "la la la"; ECG left QRS-locked; cardioballistic +200 ms; sweat < 0.5 Hz; internal hard / external preventable |
| Rhythms | δ 0.5–4 deep sleep; θ 4–8 dreams/creativity (frontal); α 8–13 eyes closed relaxed; β 13–32 alert; γ 32–100 peak state, meditators |

**Good luck!**
