# Neural Signal Analysis — Complete Exam Preparation Guide

> **Course:** Introduction to Neural Signal Analysis (BTU Cottbus–Senftenberg)
> **Built from:** Chapters 1–9, the "Signal and Noise / Signal Averaging & Artifacts" deck, all MATLAB labs, and the 36-question previous exam (prev-q).
> **Goal:** This is the only thing you will study, so it teaches the material rather than just summarising it, and it is weighted toward what the professor actually asks.

---

## Table of Contents

- [0. How to Use This Guide (2-Day Plan)](#0-how-to-use-this-guide-2-day-plan)
- [1. Exam Analysis: What the Professor Asks and How](#1-exam-analysis-what-the-professor-asks-and-how)
- [2. The Previous Exam, Solved and Explained](#2-the-previous-exam-solved-and-explained)
- [Part A — Neurophysiology Foundations 🔥](#part-a--neurophysiology-foundations-)
- [Part B — Brain Anatomy, Recording Methods and the Origin of EEG 🔥](#part-b--brain-anatomy-recording-methods-and-the-origin-of-eeg-)
- [Part C — EEG Acquisition: Electrodes, Sampling, ADC, Amplifiers, Montages 🔥](#part-c--eeg-acquisition-electrodes-sampling-adc-amplifiers-montages-)
- [Part D — Fourier Analysis: Series, CFT, DFT, FFT, Spectra, Windows 🔥](#part-d--fourier-analysis-series-cft-dft-fft-spectra-windows-)
- [Part E — Noise, Random Processes, Stationarity, Ergodicity, SNR 🔥](#part-e--noise-random-processes-stationarity-ergodicity-snr-)
- [Part F — Signal Averaging, Noise Estimates, Evoked Potentials 🔥](#part-f--signal-averaging-noise-estimates-evoked-potentials-)
- [Part G — EEG Preprocessing: Line Noise, Multitaper, Referencing, Bad Channels ⭐](#part-g--eeg-preprocessing-line-noise-multitaper-referencing-bad-channels-)
- [Part H — EEG Artifacts and Pattern Recognition 🔥](#part-h--eeg-artifacts-and-pattern-recognition-)
- [Part I — Brain Rhythms 🔥](#part-i--brain-rhythms-)
- [Part J — Time-Domain Techniques and Digital Filtering (Medium)](#part-j--time-domain-techniques-and-digital-filtering-medium)
- [Part K — MATLAB Labs: Sine Waves, Complex Numbers, Dot Products, DFT vs FFT (Medium)](#part-k--matlab-labs-sine-waves-complex-numbers-dot-products-dft-vs-fft-medium)
- [High-Yield Revision Notes](#high-yield-revision-notes)
- [Formula Sheet](#formula-sheet)
- [Key Comparisons](#key-comparisons)
- [Common MCQ Traps](#common-mcq-traps)
- [100 Practice MCQs with Explanations](#100-practice-mcqs-with-explanations)
- [Full Mock Exam (36 Questions, Previous-Exam Format)](#full-mock-exam-36-questions-previous-exam-format)
- [Mock Exam Answer Key and Explanations](#mock-exam-answer-key-and-explanations)
- [Last-Minute Revision: 2 Hours, 1 Hour, 30 Minutes](#last-minute-revision-2-hours-1-hour-30-minutes)

**Priority legend**

- 🔥 **Very High Priority**: asked directly in the previous exam, usually several times. Know it cold.
- ⭐ **High Priority**: in the slides with exam-style detail; very likely to appear.
- **Medium Priority**: background or lab material; could turn up as one option inside a question.

---

## 0. How to Use This Guide (2-Day Plan)

| Block | Time | What to do |
|---|---|---|
| **Day 1 morning** | 3.5 h | Sections 1–2 (exam analysis + solved past exam), Part A (neuro), Part B (EEG origin). Do the in-part MCQs. |
| **Day 1 afternoon** | 3.5 h | Part C (acquisition), Part D (Fourier). Part D is the most mathematical, so take it slowly. |
| **Day 1 evening** | 2 h | Part E (noise) and Part F (averaging). Redo any MCQ you got wrong. |
| **Day 2 morning** | 3 h | Parts G, H, I, J, K. Then High-Yield Notes, Formula Sheet, Comparisons, Traps. |
| **Day 2 afternoon** | 3 h | 100 Practice MCQs under time pressure. Mark wrong ones and re-read those sections. |
| **Day 2 evening** | 2 h | Full Mock Exam (timed, about 60–75 min), then review the key. |
| **Exam morning** | 30–120 min | Last-Minute Revision section. |

**How to answer "select all correct" questions (the exam format):**

1. Judge **each option independently** as true or false. Never think "only one can be right". The number of correct options varies, from 1 up to 5 or more.
2. Look for **absolute words**: *only, always, never, guarantees, must, cannot, irrelevant, permanently, zero noise*. These are false most of the time in this course.
3. Look for **swapped details**: inverted ratios ($[\text{in}]/[\text{out}]$ instead of $[\text{out}]/[\text{in}]$), swapped ions (K⁺ vs Cl⁻), swapped bands (alpha 13–32 Hz), wrong numbers (40× vs 80×), and wrong directions (cornea *farther* vs *closer*).
4. If an option is a **near-verbatim slide sentence**, it is usually true. If it is a slide sentence with **one word changed**, it is false.

---

## 1. Exam Analysis: What the Professor Asks and How

### 1.1 Format

- Title: **"Introduction to Neural Signal Analysis Exam"**.
- Instruction: *"For each question, select **all correct statements**. The number of correct options varies."*
- **36 questions** in **6 sections**. Each question has 4–7 statements (A–G) and no question stem beyond a topic line.

| Section | Title | Questions | Chapters |
|---|---|---|---|
| A | Neurophysiology basics | Q1–Q8 (8) | Ch 1 |
| B | EEG biophysics & acquisition | Q9–Q15 (7) | Ch 2, Ch 3, referencing (Ch 8) |
| C | Frequency domain fundamentals | Q16–Q21 (6) | Ch 4, 5, 6 |
| D | Random processes & averaging | Q22–Q29 (8) | Ch 7, 8 |
| E | Artifacts & pattern recognition | Q30–Q34 (5) | Signal & Noise deck (artifacts, notch) |
| F | Brain rhythms | Q35–Q36 (2) | Ch 9, Signal & Noise |

### 1.2 Question style

1. **Statement verification.** Almost every option is a slide sentence that is either copied (true) or altered (false).
2. **Numbers from worked examples get changed**: "80× greater permeability" (slide: 40×), "T = 4 → 0.5 Hz ripples" (slide: 0.25 Hz), "0.5 s at 1 kHz → precision 1 Hz" (slide: 2 Hz).
3. **Definitions get inverted**: "stationary if the distribution *changes* over time", "ergodic implies variance zero", "Theta is 8–13 Hz".
4. **Mechanism or direction swaps**: "EPSPs from K⁺ entry" (really Na⁺), "cornea moves *farther* from frontal electrodes", "ratio [ion]inside/[ion]outside".
5. **Over-generalisation**: "differential recording *always* cancels *all* noise", "Ag/AgCl guarantees zero noise", "notch filters are *the optimal* option", "bootstrapping *guarantees* the control has no trace".
6. **Figure-based questions**: dipole orientation in a sulcus (radial/tangential/deep), 10 Hz vs 7.7 Hz stimulus-rate figure, AP phases.
7. **Light numerics**: Nyquist (20 Hz sine → 40 Hz), spectral precision $1/T$ and range $f_s/2$, twiddle factor periodicity for $N=4$.

### 1.3 Topic heat map (what repeats)

| Topic | Past exam weight | Priority |
|---|---|---|
| Membrane potential, Nernst, Goldman, channels, AP, refractory periods | Q3, Q4, Q5, Q6 | 🔥 |
| Neuron structure, synapses (electrical/chemical), EPSP/IPSP, summation, conduction | Q1, Q2, Q7, Q8 | 🔥 |
| EEG origin (PSPs, pyramidal cells, dipoles, orientation) | Q9, Q10 | 🔥 |
| Why EEG (advantages) | Q11 | ⭐ |
| Nyquist, sampling | Q12 | 🔥 |
| Electrodes Ag/AgCl, differential amplifier, referencing/CAR/bipolar | Q13, Q14, Q15 | 🔥 |
| Fourier series (real/complex), FT/FFT/power spectrum | Q16, Q17, Q18 | 🔥 |
| Twiddle factor, DFT precision/range, circular frequency scale | Q19, Q20 | 🔥 |
| Windowing, rectangular window, harmonics | Q21 | 🔥 |
| Noise types, stationarity, ergodicity | Q22, Q23, Q24 | 🔥 |
| Averaging assumptions, prestimulus, bootstrap, hum and stimulus rate, background EEG | Q25–Q29 | 🔥 |
| Notch filtering, artifact classes, ocular, lateral eye movement, muscle | Q30–Q34 | 🔥 |
| Brain rhythms (gamma, beta, alpha, theta) | Q35, Q36 | 🔥 |
| Brain anatomy (lobes), 10–20 system, ADC bits, multitaper, bad channels, EPs (P300/CNV), filtering, labs | not in past exam | ⭐ / Medium (likely new questions) |

> **Prediction:** The next exam will reuse the same six sections and slide sentences, with different sentences and different altered details. Expect new questions on **Goldman/Nernst numbers, saltatory conduction and myelin, spike-initiation zone, 10–20 naming, ADC bits, the ± average, CNV/P300, multitaper, bad-channel detection, ECG/cardioballistic/sweat/chewing artifacts, delta band, window functions, the DFT formula, and $N^2$ vs $N\log_2 N$**.

### 1.4 Slide inconsistencies you must know (the exam follows the slides)

| Issue | What the slides say | What is physically correct | Exam strategy |
|---|---|---|---|
| Band limits | Two versions: (i) Gamma 32–100, Beta 13–32, Alpha 8–13, Theta 4–8, Delta 0.5–4; (ii) table: Gamma >35, Beta 12–35, Alpha 8–12, Theta 4–8, Delta 0.5–4; (iii) Ch 9 text: gamma 30–50, beta 13–30 | Conventions vary | The **exam used version (i)**. Use it. |
| $E_{Cl}$ sign | Slide table "65 mV", formula written with $+61.54$ | $z=-1$ gives $E_{Cl}\approx -65$ mV | If asked, the physics is $-65$ mV. The magnitude is 65 either way. |
| Blink polarity wording | "very high amplitude negative waveforms in bifrontal regions" **and** "frontal electrodes see a positive signal" | The cornea is positive and moves toward Fp1/Fp2, so the potential there is **positive**. Clinical EEG plots negative **up**, so the deflection *looks* like a big downward (positive) wave. | The past exam tested "cornea moves closer to Fp1/Fp2" and "frontal electrodes see a stronger artifact". Choose those. |
| Twiddle text | "1 + j0 is associated with θ = π" | $1+j0$ is at $\theta=0$ (or $2\pi$). $-1+j0$ is at $\theta=\pi$. | Trust the math. |
| Triangle wave coefficient | "$a_n = 8A/(n\pi^2)$" | $a_n = 8A/(n^2\pi^2)$ for odd $n$ | Know the correct form. The $1/n^2$ decay is the concept. |
| Gap-junction spacing | Text "about 3 nm", figure "3.5 nm" | ~3–3.5 nm | Either is fine. Both are *very* narrow compared with the chemical cleft (~20–40 nm). |
| DFT "maximum frequency" | "Maximum frequency fits within the sample interval is $1/\Delta t$ = 1000 Hz" (the full circle, $\Omega$) | The full periodic range is $f_s$. The usable, unambiguous range shown in a spectrum is $f_s/2$ (Nyquist). | When a question says "range" with $f_s/2$ (as in Ch 6: 1 kHz → 500 Hz), use $f_s/2$. |

---

## 2. The Previous Exam, Solved and Explained

> Do this section actively. Cover the answer, decide T/F for each option, then check. Every explanation points to the concept you need (taught in depth later).

### Section A: Neurophysiology basics

**Q1.** A. Dendrites primarily receive signals from other neurons. B. Axons primarily transmit signals over distance. C. The soma is the main site of long-distance signal propagation. D. Axon terminals transmit signals to other neurons' dendrites or soma via synapses. E. Glial cells are described as the primary cells for long-distance electrical signalling.

- **Correct: A, B, D.**
- C ✗: long-distance propagation is the **axon's** job ("like telephone wires"). The soma (~20 µm) holds the nucleus and integrates input.
- E ✗: **neurons** do long-distance electrical signalling. Glia *support* signalling, repair damage, act as stem cells in some areas, and prevent regeneration elsewhere.

**Q2.** A. Neurotransmitter is released from synaptic vesicles into the synaptic cleft. B. Neurotransmitter binds to receptor proteins on the postsynaptic cell. C. Binding generates electrical and/or chemical signals in the postsynaptic cell. D. Neurotransmitter is released from postsynaptic dendrites into the presynaptic terminal. E. Action potentials are passed to the next neuron only by direct electrical continuity.

- **Correct: A, B, C.**
- D ✗: direction reversed. Release is from the **presynaptic terminal**.
- E ✗: most transmission is **chemical** (synaptic transmission). Electrical synapses exist but are not the "only" route, and even they work through gap-junction channels, not "continuity".

**Q3.** A. $E_{ion}$ is the electrical potential difference that exactly balances an ionic concentration gradient. B. The formula uses the ratio $[ion]_{inside}/[ion]_{outside}$. C. $E_{ion}$ is independent of ion concentration; only membrane thickness matters. D. Increasing temperature $T$ changes $E_{ion}$ through the $RT/F$ term.

- **Correct: A, D.**
- B ✗: the Nernst ratio is **out/in**: $E = \frac{2.303RT}{zF}\log\frac{[ion]_{out}}{[ion]_{in}}$.
- C ✗: concentration is the whole point, and membrane thickness does not appear anywhere.

**Q4.** A. If the membrane were permeable only to K⁺, resting potential would equal $E_K$. B. Real resting membranes have some Na⁺ permeability, so $V_m$ deviates from $E_K$. C. The resting membrane is more permeable to Na⁺ than to K⁺. D. Resting membrane permeability to K⁺ is about 80× greater than to Na⁺. E. The discrepancy is explained only by Cl⁻ permeability; Na⁺ is irrelevant.

- **Correct: A, B.**
- C ✗: reversed. At rest it is **K⁺ ≫ Na⁺**.
- D ✗: the slide says **40×**. "80" is a decoy from $E_K\approx -80$ mV.
- E ✗: the slide explanation is **Na⁺ permeability**.

**Q5.** A. The sodium–potassium pump moves ions against concentration gradients using metabolic energy. B. Leak channels are normally open and can differ in permeability for different ions. C. Voltage-gated channels open/close in response to changes in membrane voltage. D. Leak channels require ATP directly for each ion that passes through them.

- **Correct: A, B, C.**
- D ✗: channels are **passive** (ions flow down electrochemical gradients). Only the **pump** uses ATP.

**Q6.** A. During the absolute refractory period, Na⁺ channels are inactivated and cannot be reopened until sufficient repolarization occurs. B. During the relative refractory period, more depolarizing current is needed to reach threshold because the membrane is hyperpolarized. C. The all-or-none law states AP strength depends on stimulus strength. D. The relative refractory period happens because Na⁺ channels are permanently disabled after one AP. E. The undershoot occurs because voltage-gated K⁺ channels increase K⁺ permeability and $V_m$ moves toward $E_K$.

- **Correct: A, B, E.**
- C ✗: all-or-none means AP strength is **not** dependent on stimulus strength.
- D ✗: not permanent. In the relative refractory period Na⁺ channels are **again responsive**. The obstacle is the hyperpolarization from still-open K⁺ channels.

**Q7.** A. In passive conduction, response amplitude attenuates with distance because current leaks out. B. In active conduction, AP amplitude remains constant along the axon, but arrival time is delayed with distance. C. In passive conduction, distant responses are delayed but have the same amplitude as at the injection site. D. In active conduction, "non-decrement" indicates action potentials overcome the neuron's leakiness. E. If a suprathreshold pulse is used, recorded responses must be purely passive because the stimulus is brief.

- **Correct: A, B, D.**
- C ✗: passive responses **decay** (to a small fraction within a few mm).
- D ✓: "propagation without decrement" is the textbook way of saying the regenerating AP overcomes membrane leak.
- E ✗: suprathreshold means an **active** response (an AP).

**Q8.** A. Electrical synapses occur at gap junctions and allow direct ionic current flow cell-to-cell. B. In electrical synapses, most gap junctions pass ionic current equally well in both directions, so electrical synapses are typically bidirectional. C. A gap junction channel is formed by two connexons; each connexon is formed by eight connexin subunits. D. EPSPs are described as resulting from transmitter-gated channels that allow K⁺ entry, producing depolarization. E. IPSPs are described as resulting from transmitter-gated channels that allow Cl⁻ entry, producing hyperpolarization. F. Adding an inhibitory synapse (IPSP) to a suprathreshold EPSP combination can keep the postsynaptic neuron below threshold. G. Electrical synapses are emphasized as slow but flexible compared to chemical synapses.

- **Correct: A, B, E, F.**
- C ✗: **six** connexins make a connexon, and two connexons make one gap-junction channel.
- D ✗: EPSP comes from **Na⁺ entry**.
- G ✗: electrical synapses are **very fast** (very little delay).

### Section B: EEG biophysics & acquisition

**Q9.** A. EEG mainly records extracellular currents arising as a consequence of synaptic activity in dendrites of cortical neurons. B. EEG mainly records single-neuron action potentials directly because APs are ~100 mV. C. The extracellular electric field measured by EEG is mainly generated by postsynaptic potentials (EPSPs/IPSPs). D. Pyramidal cells are major contributors partly because they are spatially aligned perpendicular to the cortex. E. EEG is primarily a direct measure of magnetic fields produced by neural currents.

- **Correct: A, C, D.**
- B ✗: EEG is **summed PSPs**, not APs. A single neuron's dipole is impossible to measure from the scalp.
- E ✗: magnetic fields are **MEG**. EEG is a *direct measure of electrical* activity.

**Q10 (figure: radial dipole (a) at gyral crown, oblique (b) and tangential (c) dipoles on sulcal walls, deep radial dipole (d) at sulcus bottom).** A. Dipoles oriented like case (a) contribute the strongest EEG signal. B. Dipoles on opposing sides of a sulcus can cancel and become unlikely to be measured. C. Dipoles further from the electrode contribute more strongly than closer dipoles. D. Orientation does not matter; only dipole magnitude matters. E. Cancellation in sulci happens because both sides always generate identical polarity fields.

- **Correct: A, B.**
- C ✗: (d) contributes **less** because it is **further away**.
- D ✗: orientation is essential (radial ≫ tangential).
- E ✗: cancellation happens because the opposing walls produce **opposite** polarity fields.

**Q11.** A. EEG is an invasive method while it has no exposure to radiation or high magnetic field. B. Temporal resolution matches the speed of cognition. C. EEG has the highest spatial resolution among brain imaging methods. D. EEG has the highest temporal resolution among brain imaging methods. E. EEG devices do not generate any noise. F. EEG can be recorded in open environments.

- **Correct: B, F, and most likely D.**
- A ✗: EEG is **perfectly noninvasive**.
- C ✗: EEG spatial resolution is **poor** (cm scale, volume conduction).
- D: the slides say "high/superior temporal resolution" (vs fMRI/PET). The exam pairs C (spatial, false) with D (temporal), so D is most likely intended as **true**. Among *noninvasive imaging* methods, EEG/MEG do have the best temporal resolution.
- E ✗: all analog equipment adds at least thermal noise.

**Q12.** A. For a 20 Hz sine wave, 40 Hz is the minimum sampling rate to preserve frequency content. B. The Nyquist frequency of sampled data is $F_s/2$. C. Sampling at 30 Hz is sufficient to preserve a 20 Hz sine wave without aliasing. D. "Nyquist sampling rate" and "Nyquist frequency" refer to the same value.

- **Correct: A, B.**
- C ✗: 30 < 40. A 20 Hz sine sampled at 30 Hz aliases to $\lvert 20-30\rvert = 10$ Hz.
- D ✗: Nyquist **rate** $=2f_{max}$ (a sampling rate). Nyquist **frequency** $=f_s/2$ (the highest representable frequency for a given $f_s$).

**Q13.** A. The Ag/AgCl layer supports ionic-to-electronic conduction at the interface. B. Electrode choice is irrelevant once you digitize at high bit depth. C. Ag/AgCl coatings can reduce interface-related issues compared to bare metal. D. Ag/AgCl electrodes remove the need for amplification. E. Using Ag/AgCl guarantees zero noise pickup.

- **Correct: A, C.**
- B ✗: bits cannot fix a bad analog interface.
- D ✗: µV signals still need amplification.
- E ✗: "guarantees zero" is always false.

**Q14 (In EEG acquisition).** A. Differential recording measures the difference between two electrode potentials. B. A third ground electrode arrangement is optional for a single-channel recording and can be omitted in practice. C. Any noise source affects both input electrodes equally, so differential recording always cancels all noise. D. Common-mode noise cancellation works best when interference is similar at both measurement electrodes. E. If an artifact is present primarily at one electrode, it can remain in the differential channel. F. Differential amplifiers are used mainly to increase ADC bits rather than suppress noise.

- **Correct: A, D, E.**
- B ✗: the EEG amplifier uses **three electrodes** (active, reference, ground) per channel.
- C ✗: "always/all". Only **common** (identical) noise cancels.
- F ✗: the purpose is **noise (common-mode) rejection**.

**Q15 (Referencing).** A. Changing the reference can change measured waveforms even when brain activity is unchanged. B. A "neutral reference" is guaranteed to be electrically silent and therefore cannot influence recordings. C. Referencing choice cannot affect the apparent spatial distribution (topography) of activity. D. CAR can be affected if many electrodes share the same artifact. E. Bipolar derivations can reduce widespread common activity present similarly at both electrodes.

- **Correct: A, D, E.**
- B ✗: "There is **no ideally neutral place**". Every channel reflects **both** active and reference electrodes.
- C ✗: the reference changes every channel, so it changes the topography.

### Section C: Frequency domain fundamentals

**Q16.** A. A periodic function $f(t)=f(t+T)$ can be represented as a sum of sines and cosines. B. The DC component in the real Fourier series is represented by $a_0/2$. C. The AC components correspond to weighted sine and cosine terms ($a_n, b_n$). D. The Fourier series applies only to nonperiodic signals; periodic signals require the Fourier transform. E. The angular frequency is defined as $\omega=2\pi f$ with $f=1/T$. F. A power spectrum plot is mainly described as amplitude versus time.

- **Correct: A, B, C, E.**
- D ✗: reversed. The Fourier **series** is for **periodic** signals.
- F ✗: a power spectrum is power **versus frequency**.

**Q17.** A. The complex Fourier series is frequently written as a sum of cosine and sine waves. B. Complex coefficients are evaluated over a full period and the start point is not important. C. Euler's relation connects the sine/cosine representation to complex exponentials. D. The complex Fourier series contains no information about phase. E. Real and complex Fourier series notations are equivalent.

- **Correct: B, C, E.**
- A ✗: the complex series is written as a sum of **complex exponentials** $c_n e^{jn\omega t}$. The real series is the sum of sines/cosines.
- D ✗: $c_n$ is complex. Its **angle is the phase**.

**Q18.** A. Fourier series represent periodic functions as sums of waves. B. Continuous and discrete Fourier transforms are approximate estimations of signals in the frequency domain. C. FFT reduces computational effort required to obtain a Fourier transform. D. FFT is a hardware filter that removes noise. E. FFT replaces the need to sample; it operates on continuous-time signals directly. F. Power spectrum shows power of different frequency components and can be computed from FFT results.

- **Correct: A, C, F, and probably B.**
- B: the slide says CFT and DFT "provide the basis for examining real-world signals in the frequency domain", and the DFT is a *discrete approximation* of the CFT. B is most likely intended true.
- D ✗: the FFT is an **algorithm** (Cooley & Tukey, 1965), not a filter.
- E ✗: the FFT works on **sampled** (discrete) data.

**Q19.** A. The twiddle factor is periodic, and this periodicity supports FFT efficiency. B. For N=4, examples like $W_4^0=W_4^4$ and $W_4^3=W_4^4$ are given. C. The twiddle factor is introduced only for inverse DFT. D. $W_N^k$ is never equal to 1 except when $k=0$. E. $\theta=0$ and $\theta=2\pi$ give identical complex values due to periodicity.

- **Correct: A, E.**
- B ✗: $W_4^0=W_4^4=1$ is right, but $W_4^3=+j$ while $W_4^4=1$. The slide examples are $W_4^1=W_4^5$ and $W_4^2=W_4^6$.
- C ✗: $W_N$ appears in **both** the DFT ($W_N^{kn}$) and the inverse DFT ($W_N^{-kn}$).
- D ✗: $W_N^{N}=W_N^{2N}=\dots=1$.

**Q20.** A. For a 0.5-s epoch sampled at 1 kHz: precision = 1 Hz and range = 500 Hz. B. For a 5-s epoch sampled at 200 Hz: precision = 0.1 Hz and range = 100 Hz. C. The spectrum is odd, not even. D. Because the power spectrum is even, it is common to depict only the first half up to Nyquist. E. Increasing epoch length worsens precision while improving range. F. Positive frequencies are described as $0\to\pi$ and negative as $\pi\to 2\pi$ on the circular scale.

- **Correct: D, F.**
- A ✗: precision $=1/T=1/0.5=$ **2 Hz** (range 500 Hz is right).
- B ✗: precision $=1/5=$ **0.2 Hz** (range 100 Hz is right).
- C ✗: the power spectrum is **even**.
- E ✗: longer $T$ **improves** precision ($1/T$ smaller). Range depends only on $f_s$.

**Q21.** A. Using a finite epoch is equivalent to multiplying by a rectangular window in time. B. Multiplication in time corresponds to convolution in frequency. C. Rectangular windows yield ripples in frequency with spacing inverse to window duration (e.g., T=4 → 0.5 Hz). D. Physiological signals are typically stationary, so window choice is unimportant. E. Harmonics occur only when the signal contains a DC offset. F. Non-sinusoidal periodic activity does not lead to harmonics.

- **Correct: A, B.**
- C ✗: the principle is right but the example is wrong. $T=4$ gives **0.25 Hz** ($T=2$ gives 0.5 Hz, $T=1$ gives 1 Hz).
- D ✗: physiological signals are **rarely stationary**.
- E ✗ and F ✗: harmonics arise because periodic activity is **not purely sinusoidal** (e.g., respiration at 1.5 Hz with a harmonic near 3 Hz).

### Section D: Random processes & averaging

**Q22.** A. Dynamical noise is associated with correlation between sequential values, creating slower trends. B. Additive noise necessarily creates slower trends than dynamical noise. C. A time series with only dynamical noise appears more rapidly varying than one with random noise added. D. Dynamical noise is always preferable because it eliminates measurement noise.

- **Correct: A.**
- B ✗ and C ✗: reversed. **Dynamical** noise gives the slower trends.
- D ✗: nonsense. Dynamical noise is part of the process and does not remove measurement noise.

**Q23.** A. A process is stationary if the distribution generating x(t) changes over time. B. Stationarity means x(t) must be constant over time. C. Similarity of amplitude distributions across sample functions supports assuming stationarity. D. Many signal processing techniques assume stationarity and ergodicity even if not strictly satisfied. E. Stationarity guarantees the process is deterministic.

- **Correct: C, D.**
- A ✗: stationary means the distribution does **not** change.
- B ✗: the *statistics* are constant, not the signal values.
- E ✗: a stationary process can be fully random.

**Q24.** A. If stationary and ergodic, statistics can be obtained from time averages of a single sample function. B. Ergodicity implies the variance must be zero. C. Ergodicity means each sample function has a different PDF. D. Ergodicity implies you must average only across different trials, never over time. E. Ergodicity means a particular sample function is representative of the whole ensemble.

- **Correct: A, E.**
- B ✗, C ✗, D ✗: all contradict "any sample function represents the ensemble, so time averages can replace ensemble averages".

**Q25 (Assumptions behind signal ensemble averaging).** A. Signal and noise are assumed correlated. B. Noise is assumed periodic with a fixed phase relative to the trigger. C. The timing of the signal is assumed known (time-locked). D. The signal component is assumed to change substantially across trials. E. Noise is assumed truly random with zero mean. F. The signal component is assumed consistent across repeated measurements.

- **Correct: C, E, F.** (The fourth assumption, signal and noise **uncorrelated**, is the negation of A.)
- B ✗: periodic, phase-locked noise is exactly what **breaks** averaging (hum).
- D ✗: the signal must be **consistent**.

**Q26 (Prestimulus noise estimation).** A. It assumes the time-locked signal occurs only after the trigger. B. Prestimulus noise is the best estimator in all circumstances. C. Prestimulus noise is always reliable for stimulus-evoked potentials. D. Late components cannot overlap into the next trial's prestimulus interval. E. Late/slow components can contaminate the prestimulus if the inter-stimulus interval is short. F. Increasing the inter-stimulus interval can mitigate prestimulus contamination.

- **Correct: A, E, F.**
- B ✗ and C ✗: "all/always". The slide says it is *not necessarily reliable* for EPs.
- D ✗: they **can** overlap, and that is the main problem.

**Q27 (Bootstrapping).** A. Bootstrapping forms a control average using random triggers instead of true triggers. B. Random triggers enhance the time-locked component more than true triggers. C. Random triggers destroy alignment, so time-locked components are not enhanced in the control average. D. Bootstrapping requires online stimulation during acquisition. E. Bootstrapping works only when the time-locked component dominates strongly. F. Bootstrapping guarantees the control contains no trace of time-locked activity.

- **Correct: A, C.**
- B ✗: reversed.
- D ✗: it works especially well **offline** with stored data.
- E ✗: reversed. It works well when the time-locked component is **small** relative to noise.
- F ✗: the control "still includes the effects of the time-locked signal". The signal is present but not enhanced.

**Q28.** A. Averaging fails or is biased if the noise is random (e.g., white noise). B. A 10-Hz stimulus rate always reduces 50-Hz hum in the average. C. A 10-Hz stimulus rate can lock to the same phase of 50-Hz hum in the average. D. Using a noninteger stimulus rate makes stimulus onset coincide with the same hum phase every trial, creating a strong artifact. E. Periodic noise never affects averaging because it cancels like random noise. F. Randomizing stimulus intervals or using a noninteger stimulus rate can avoid phase-locking to hum.

- **Correct: C, F.**
- A ✗: random zero-mean noise is the **ideal** case for averaging.
- B ✗: 50/10 = 5 whole cycles, so every trigger hits the same hum phase and the hum **survives**.
- D ✗: that describes the integer case. A noninteger rate (7.7 Hz) *changes* the phase each trial.
- E ✗: periodic noise does not cancel when phase-locked.

**Q29.** A. Background EEG spans roughly 0.01–100 Hz. B. Typical EEG amplitudes are around 100 µV. C. Long-term EEG is stationary over hours if the subject is relaxed. D. EEG is divided into four bands: theta, alpha, beta, gamma. E. EEG is deterministic because genuine measurements are unlimited. F. Long-term EEG is non-stationary; short-term EEG can be approximately stationary.

- **Correct: A, B, F.**
- C ✗: long-term EEG is **non-stationary**.
- D ✗: there are **five** bands, including delta.
- E ✗: EEG is considered **stochastic** because genuine measurements are **limited**.

### Section E: Artifacts & pattern recognition

**Q30.** A. Notch filtering is used to eliminate 50/60 Hz line noise. B. Notch filters are the optimal option for reducing power line noise. C. Notch filtering can distort signal components in the 50–70 Hz range. D. Notch filtering cannot distort the signal. E. Notch filtering can introduce transient oscillations that affect interpretation.

- **Correct: A, C, E.**
- B ✗: "optimal" is not claimed. The slides present drawbacks and an alternative (multitaper regression).
- D ✗: contradicts C.

**Q31.** A. EEG artifact sources are categorized into internal and external sources. B. Internal artifacts originate only from recording equipment malfunction. C. Internal sources include physiological systems such as heart, eyes, and muscles. D. External sources are only physiological (e.g., cardiac signals). E. External sources can include environmental signals and electrode/recording equipment issues. F. Internal artifacts are easy to prevent once identified.

- **Correct: A, C, E.**
- B ✗ and D ✗: internal and external are swapped.
- F ✗: **external** sources can be inhibited once identified. **Internal** artifacts permeate EEG and are hard to prevent.

**Q32.** A. During blinking, the eyes roll up slightly (Bell's phenomenon). B. During blinking, the cornea moves farther away from frontal electrodes. C. The cornea moves closer to frontal electrodes such as Fp1, Fp2 during blinking. D. Frontal electrodes see a stronger artifact during blinking. E. Blinks primarily create opposing polarities at F7 and F8. F. Blink artifact is low-amplitude and hard to see.

- **Correct: A, C, D.**
- B ✗: the cornea moves **closer**.
- E ✗: opposing F7/F8 polarities are the signature of **lateral eye movement**, not blinks (blinks are symmetric bifrontal).
- F ✗: blinks are **very high amplitude** and clearly visible.

**Q33.** A. Lateral eye movements can produce opposing polarities in F7 and F8 leads. B. Looking to the right moves the right cornea closer to F8, producing a deflection there. C. Lateral eye movements are strongest in Pz and Oz channels. D. Lateral eye movement polarity is unrelated to cornea/retina charge separation.

- **Correct: A, B.**
- C ✗: the effect is at lateral **frontal** electrodes (F7/F8), near the eyes.
- D ✗: the polarity comes **precisely** from the corneo-retinal dipole (cornea +, retina −).

**Q34.** A. Muscle artifacts originate from muscle contractions in various body parts. B. Muscle artifacts have a single stereotyped waveform unlike ocular artifacts. C. Their spatial distribution is described as wider and almost uniform over the entire scalp. D. They affect only high-frequency EEG and never low-frequency components. E. Spectral properties vary across sources and can affect both high- and low-frequency EEG components. F. Task-associated temporal patterns make muscle artifact removal challenging. G. EMG cannot detect muscle activity.

- **Correct: A, C, E, F.**
- B ✗: muscle artifacts have **more diverse forms** than ocular ones.
- D ✗: "only/never". They affect both high and low frequencies.
- G ✗: muscle artifacts are **detected through EMG**.

### Section F: Brain rhythms

**Q35.** A. Gamma is 32–100 Hz and described as the fastest measurable EEG brainwaves. B. Gamma is linked to heightened perception (peak mental state) when information from different brain parts is processed simultaneously. C. Alpha is 13–32 Hz and associated with alert/active thinking. D. Alpha is most easily observed when eyes are closed and mind is relaxed. E. Gamma is stated to be stronger/more regularly observed in very long-term meditators.

- **Correct: A, B, D, E.**
- C ✗: 13–32 Hz with alert/active thinking is **beta**. Alpha is 8–13 Hz, relaxed.

**Q36.** A. Theta is 8–13 Hz and becomes detectable when eyes are closed and mind is relaxed. B. Alpha is described as among the most easily observed and the first discovered. C. Theta is 4–8 Hz and linked to creativity/insight/dreams/reduced consciousness. D. Theta is strongly detectable during dreaming and can appear during deep meditation and daydreaming. E. Theta is described as coming from occipital parts of the brain.

- **Correct: B, C, D.**
- A ✗: that is the **alpha** description.
- E ✗: the slide says the theta source is **probably frontal** (monitoring of other mental processes). Occipital is where alpha is classically strongest.

---

## Part A — Neurophysiology Foundations 🔥

> **Why this matters for a signal-analysis course:** EEG is the summed electrical footprint of neurons. To reason about what EEG can and cannot see, you need to know where currents come from (ion gradients, channels, PSPs) and how fast and how far they travel (APs vs passive potentials). The exam spent **8 of 36 questions** here.

### A1. Cells of the nervous system 🔥

The nervous system has two cell classes:

| | **Neurons** | **Glial cells** |
|---|---|---|
| Main role | **Electrical signalling over long distances** | **Support** the signalling functions of nerve cells |
| Other roles | Information processing and integration | **Repair** nervous-system damage; act as **stem cells in some brain areas**; in other regions **prevent regeneration** where uncontrolled regrowth might do more harm; **myelinate** axons (oligodendrocytes, Schwann cells) |

**Neuron parts** (memorise the analogies; the exam paraphrases them):

| Part | Function | Slide analogy |
|---|---|---|
| **Soma (cell body)** | Spherical central part, **~20 µm** diameter; contains the nucleus and cytoplasm (organelles, cytosol) | — |
| **Dendrites** | **Receive** signals from neighbouring neurons | "like a radio **antenna**" |
| **Axon** | **Transmit** signals over a distance | "like **telephone wires**" / "telegraph wire" |
| **Axon terminal** | Transmit signals to other neurons' **dendrites or somata** (or tissues) | "like a radio **transmitter**" |
| **Axon hillock** | Where the axon leaves the soma; the **spike-initiation zone** in CNS neurons | — |
| **Axon collaterals** | Branches of the axon that send the signal to several targets | — |

**Morphology facts (⭐):**

- Dendrite **size and branching** vary, which gives neurons different **information-processing capacity**.
- **Convergence** is the **number of inputs** to one neuron. **Divergence** is the **number of targets** one neuron innervates. A common trap swaps them.
- Some cells have **very short axons** (retinal **bipolar** cell). Some have **no axon at all** (retinal **amacrine** cell).
- The slides show example morphologies: cortical **pyramidal** cell, retinal bipolar, retinal ganglion, retinal amacrine, mesencephalic trigeminal, cerebellar **Purkinje** (huge flat dendritic tree).

**Synaptic transmission** is the process by which information encoded by action potentials is passed on at synaptic contacts to a target cell. When an AP arrives at the **presynaptic** terminal, neurotransmitter is released from **synaptic vesicles** into the **synaptic cleft**, binds to **receptor proteins** on the postsynaptic cell, and produces **electrical or chemical signals** in the postsynaptic cell.

### A2. Ion distribution and the membrane potential 🔥

**Membrane potential** is the **electrical charge difference across the cell membrane** (inside relative to outside).

**Where the ions are (typical mammalian neuron):**

| Ion | Outside (mM) | Inside (mM) | Out:In | $E_{ion}$ at 37 °C |
|---|---|---|---|---|
| K⁺ | 5 | 100 | 1:20 | **−80 mV** |
| Na⁺ | 150 | 15 | 10:1 | **+62 mV** |
| Ca²⁺ | 2 | 0.0002 | 10,000:1 | **+123 mV** |
| Cl⁻ | 150 | 13 | 11.5:1 | **−65 mV** (slide prints "65 mV") |

Inside the cell there are also large **organic anions (OA⁻ / A⁻)**, such as proteins, which cannot leave. The pump (ATP) maintains the gradients.

**Three rules for ion movement** (slide):

1. **Diffusion:** ions move from **higher to lower concentration**.
2. **Electrostatics:** ions move **away from like charges** and **toward opposite charges**.
3. **Permeability:** ions can only cross where **ion channels** let them through.

**The two teaching examples (understand them, they explain everything):**

- **Membrane equally permeable to Na⁺ and Cl⁻.** Start with 10/10 on the left and 2/2 on the right. Both ions diffuse together, ending at 6/6 on both sides. Charges stay balanced, so the **membrane potential is 0**. *Lesson: if every ion can cross freely, no potential builds up.*
- **Membrane permeable only to Na⁺.** Na⁺ diffuses right (10 → 7 on the left, 2 → 5 on the right) but Cl⁻ cannot follow. The left side becomes −3 and the right side +3. The resulting **electrostatic force pulls Na⁺ back**. Equilibrium is reached when diffusion and electrostatic forces balance and there is **no net current for Na⁺**. The voltage at that point is the **Na⁺ equilibrium potential**. *Lesson: selective permeability plus a concentration gradient creates a voltage.*

### A3. The Nernst equation (equilibrium potential) 🔥

**Definition (verbatim-level):** *The electrical potential difference that exactly balances an ionic concentration gradient is called an ionic equilibrium potential ($E_{ion}$).*

$$E_{ion} = \frac{2.303\,RT}{zF}\,\log_{10}\frac{[ion]_{out}}{[ion]_{in}}$$

| Symbol | Meaning |
|---|---|
| $R$ | gas constant |
| $T$ | **absolute temperature** (Kelvin) |
| $z$ | **charge (valence)** of the ion (+1 K⁺/Na⁺, +2 Ca²⁺, −1 Cl⁻) |
| $F$ | Faraday's constant |
| $[ion]_{out}$, $[ion]_{in}$ | concentrations outside and inside |

At 37 °C, $2.303RT/F \approx 61.54$ mV, so:

$$E_K = 61.54\log\frac{[K^+]_o}{[K^+]_i},\quad E_{Na}=61.54\log\frac{[Na^+]_o}{[Na^+]_i},\quad E_{Ca}=30.77\log\frac{[Ca^{2+}]_o}{[Ca^{2+}]_i},\quad E_{Cl}=-61.54\log\frac{[Cl^-]_o}{[Cl^-]_i}$$

**Intuition:**

- The potential is set by the **ratio**, not the absolute amount. A 10× gradient is worth ~61.5 mV for a monovalent ion. Every extra 10× adds another ~61.5 mV.
- **Divalent** ions (Ca²⁺, $z=2$) need only **half** the voltage per decade (30.77 mV) because each ion carries twice the charge.
- **Sign logic:** K⁺ is concentrated **inside** and leaks out, leaving the inside negative, so $E_K<0$. Na⁺ is concentrated **outside**, so $E_{Na}>0$.
- **Temperature** enters through $RT/F$. Higher $T$ gives a larger magnitude (at 20 °C the factor is ~58 mV).
- **Not in the equation:** membrane thickness, permeability, or channel number. Nernst is for **one ion at equilibrium**.

**Worked numbers (practice these):**

- $[K^+]_o/[K^+]_i = 5/100 = 1/20$: $E_K = 61.54\times\log(0.05) = 61.54\times(-1.301) \approx$ **−80 mV**.
- $[Na^+]_o/[Na^+]_i = 150/15=10$: $E_{Na}=61.54\times 1=$ **+61.5 mV**.
- $[Ca^{2+}]_o/[Ca^{2+}]_i = 10{,}000$: $E_{Ca}=30.77\times 4=$ **+123 mV**.
- If extracellular K⁺ rises from 5 to 10 mM: $E_K = 61.54\log(10/100) =$ **−61.5 mV**, which is less negative (depolarised). This is the classic "hyperkalaemia depolarises neurons" scenario.

### A4. The resting membrane potential and the Goldman equation 🔥

**The key paragraph (the exam turned it into Q4):**
*If the membrane of a real neuron were permeable only to K⁺, the resting membrane potential would equal $E_K$ (about −80 mV). But the measured resting potential of a typical neuron is about −65 mV. The discrepancy is explained because real neurons at rest are **not exclusively permeable to K⁺**; there is also **some Na⁺ permeability**. The relative permeability of the resting membrane is **high to K⁺ and low to Na⁺**. The resting membrane permeability to K⁺ is **40 times** greater than to Na⁺.*

**Goldman equation** (Na⁺ and K⁺ version on the slide):

$$V_m = 61.54\,\text{mV}\;\log\frac{P_K[K^+]_o + P_{Na}[Na^+]_o}{P_K[K^+]_i + P_{Na}[Na^+]_i}$$

**Intuition:** $V_m$ is a **permeability-weighted compromise** between the equilibrium potentials. Whichever ion the membrane is most permeable to pulls $V_m$ toward its own $E$.

- If $P_{Na}=0$, Goldman reduces to Nernst for K⁺, so $V_m = E_K$.
- At rest ($P_K : P_{Na} = 40:1$): $V_m = 61.54\log\frac{40\cdot5+150}{40\cdot100+15} = 61.54\log(0.0872) \approx$ **−65 mV**. ✔
- At the AP peak, $P_{Na}\gg P_K$, so $V_m$ swings toward $E_{Na}$ (positive).
- If $P_K/P_{Na}$ increased to 100, $V_m \approx -73$ mV (closer to $E_K$). If it decreased to 25, $V_m\approx -59$ mV.

> **Nernst vs Goldman (classic comparison)**
> Nernst: **one** ion, **equilibrium** potential, no permeability term.
> Goldman: **several** ions, **steady-state resting** potential, **weighted by permeabilities**.

### A5. Membrane channels and the pump 🔥

| Protein | Opens when | Energy | Role |
|---|---|---|---|
| **Leak channels** | **Normally open** | Passive (no ATP) | Set the resting permeability. They have **different permeability for different ions** (many K⁺ leak channels, few Na⁺ leak channels, hence the 40:1). |
| **Sodium–potassium pump** | Continuously active | **ATP** (metabolic energy) | Transports ions **against their concentration gradients**, maintaining the gradients (textbook: 3 Na⁺ out, 2 K⁺ in per ATP). |
| **Voltage-gated channels** | **Change in membrane voltage** (slide figure: closed at −65 mV, open at −40 mV) | Passive | Charged segments of the channel protein move when voltage changes, opening the pore. The basis of the AP. |
| **Transmitter-gated (ligand-gated) channels** | Neurotransmitter binding | Passive | Produce EPSPs/IPSPs at synapses. |

**Trap:** "Leak channels require ATP" ✗. "The pump is a channel that lets ions flow down their gradient" ✗. The pump works **against** gradients.

### A6. The action potential (AP) 🔥

**Phases (numbered as in the slides):**

1. **Resting state (~−65 mV):** both voltage-gated Na⁺ **and** K⁺ channels are **closed**.
2. **Depolarization:** a stimulus opens **some** Na⁺ channels. If depolarization reaches **threshold**, many more open (positive feedback).
3. **Rising phase:** Na⁺ **floods in down its concentration gradient** (large driving force because the inside is negative). $V_m$ rushes toward $E_{Na}$ (~+60 mV) and **overshoots** above 0 mV, but it **never reaches $E_{Na}$ because Na⁺ channels quickly close (inactivate)**.
4. **Falling phase:** about **1 ms** after opening, Na⁺ channels **inactivate**, and voltage-gated **K⁺ channels open** (they were triggered ~1 ms earlier by the depolarization but are slow). K⁺ **floods out** (large driving force when the inside is positive), so $V_m$ becomes negative again.
5. **Undershoot (after-hyperpolarization):** the voltage-gated K⁺ channels **stay open** a bit too long. They add to the resting K⁺ permeability while Na⁺ permeability is very low, so $V_m$ goes **toward $E_K$**, more negative than rest, until those K⁺ channels close.

**Definitions (slide "Review"):**

- **Threshold:** the membrane potential at which enough voltage-gated Na⁺ channels open that the relative ionic permeability ($g$) **favours Na⁺ over K⁺**.
- **Overshoot:** because permeability greatly favours Na⁺, $V_m$ approaches $E_{Na}$, which is **greater than 0 mV**.
- **Undershoot:** $g_K\gg g_{Na}$, so $V_m$ heads toward $E_K$.

**Na⁺ channel has two gates:**

1. **Activation gate:** opens in response to depolarization.
2. **Inactivation gate:** closes **~1 ms after** the activation gate opens.

**Currents during the AP (Bear Fig. 4.12):**

- Individual Na⁺ channels open with little delay at threshold, stay open **no more than ~1 ms**, then inactivate. The summed Na⁺ current is a brief **inward** current (plotted downward).
- K⁺ channels open later and stay open longer. The summed K⁺ current is a larger, slower **outward** current.
- **Net current:** inward first (Na⁺ influx) then outward (K⁺ efflux).

**Refractory periods (Q6 material):**

| | **Absolute refractory period** | **Relative refractory period** |
|---|---|---|
| Cause | Na⁺ channels are **inactivated** (strong depolarization) | Membrane is still **hyperpolarized** because voltage-gated **K⁺ channels are still open** |
| Can another AP fire? | **No, never**, until $V_m$ becomes sufficiently negative to **de-inactivate** the Na⁺ channels | **Yes, but** it needs a **larger depolarizing stimulus** (more current to reach threshold) |
| Na⁺ channel state | Inactivated | **Responsive again** |

**All-or-none law:** the **strength of an AP does not depend on the strength of the stimulus**. Once threshold is crossed you get a full, stereotyped AP. How, then, is stimulus intensity coded? By **firing rate**, as below.

**Current injection experiments (Bear Box 4.3, Purves Fig. 2.x):**

- Two microelectrodes: one **stimulates** (injects current), one **records** $V_m$ relative to ground.
- **Hyperpolarizing** current pulses give **only passive** changes.
- **Small depolarizing** currents also give **only passive** responses (subthreshold).
- Depolarization that **meets or exceeds threshold** evokes APs.
- **The AP firing rate increases as the depolarizing current increases.** (Intensity is rate-coded, AP size is constant.)

### A7. Passive vs active conduction; myelin; spike-initiation zone 🔥

**Passive (electrotonic) conduction:** inject a **subthreshold** current into an axon and record at increasing distances. The **amplitude decays with distance** because **current leaks out** across the membrane. It falls to a small fraction within **a few millimetres** (the slide plot shows −60 mV at the injection site decaying toward −65 mV by ~2 mm).

**Active conduction:** a **suprathreshold** stimulus triggers APs that regenerate at each point, so the **amplitude stays constant** ("propagation **without decrement**", which overcomes the membrane's leakiness). The only thing that changes with distance is **arrival time** (a delay proportional to distance / conduction velocity).

**Saltatory conduction (⭐):**

- **Myelin** is an insulating sheath interrupted every few millimetres by **nodes of Ranvier**, where the axon is exposed to extracellular fluid.
- **Voltage-gated Na⁺ channels are concentrated at the nodes.** Sites of excitation and permeability change exist **only at the nodes**, so current "jumps" node to node. This is **faster**, and myelin lets current spread farther and faster between nodes.
- **Oligodendrocytes (oligodendroglia):** found **only in the CNS** (brain and spinal cord). **One cell myelinates several axons.**
- **Schwann cells:** found **only in the PNS**. **Each Schwann cell myelinates only one axon.**

**Spike-initiation zone (⭐):**

- **Dendrites and soma** have **very few voltage-gated Na⁺ channels**, so they do not generate Na⁺-dependent APs. Axonal membrane is identified by its **high density of voltage-gated Na⁺ channels**.
- **Typical CNS neuron (e.g., pyramidal cell):** the spike-initiation zone is the **axon hillock**. Synaptic depolarization of dendrites and soma fires an AP **if the axon hillock is depolarized beyond threshold**.
- **Primary sensory neurons:** the spike-initiation zone is **near the sensory nerve endings**, where sensory stimulation depolarizes the membrane.

### A8. Synapses: electrical and chemical 🔥

**History (⭐, easy one-option material):**

- **Otto Loewi, 1921:** solid support for **chemical** synapses. He stimulated the **vagus nerve** of frog heart A (heart rate decreased), collected the fluid, and applied it to heart B. Heart B also slowed, so a **chemical** had been released.
- **Bernard Katz** (University College London) showed that fast transmission at the **motor neuron–skeletal muscle** synapse is **chemically mediated**.
- **Edwin Furshpan and David Potter, late 1950s:** proved that **electrical** synapses exist.

**Electrical synapses:**

- Occur at **gap junctions**. Membranes are only **~3 nm (3.5 nm in the figure)** apart.
- **Six connexin** subunits form a **connexon**. **Two connexons** (one from each cell) form a **gap-junction channel**.
- Ions (and small molecules) pass **directly from the cytoplasm of one cell to the other**.
- Most gap junctions pass current **equally well in both directions**, so electrical synapses are **bidirectional**, unlike most chemical synapses. The cells are **electrically coupled**.
- **Very fast, with very little delay.** A presynaptic AP can trigger a postsynaptic AP almost immediately. The postsynaptic response is an **electrical PSP** (slide: a presynaptic AP of ~+100 mV amplitude produces a ~1 mV PSP in cell 2, within ~1 ms).
- Found where neighbouring neurons must be **highly synchronized**.

**Chemical synapses: the 11 steps (Purves Fig. 5.4):**

1. Transmitter is **synthesized and stored in vesicles**.
2. An **AP invades** the presynaptic terminal.
3. Depolarization **opens voltage-gated Ca²⁺ channels**.
4. **Ca²⁺ influx**.
5. Ca²⁺ causes **vesicles to fuse** with the presynaptic membrane.
6. Transmitter is **released into the cleft by exocytosis**.
7. Transmitter **binds to receptors** in the postsynaptic membrane.
8. **Postsynaptic channels open or close**.
9. Postsynaptic current causes an **EPSP or IPSP**, changing excitability.
10. Transmitter is **removed** by glial uptake or enzymatic degradation.
11. Vesicular membrane is **retrieved** from the plasma membrane.

Flowchart version: *release → receptor binding → ion channels open/close → conductance change causes current → postsynaptic potential changes → cell excited or inhibited → summation determines whether an AP occurs.*

**EPSP vs IPSP:**

| | **EPSP** | **IPSP** |
|---|---|---|
| Channel | Transmitter-gated | Transmitter-gated |
| Ion (slide) | **Na⁺ enters** | **Cl⁻ enters** |
| Effect | **Depolarization** (toward threshold) | **Hyperpolarization** (away from threshold) |
| Typical transmitter | Glutamate, ACh | GABA, glycine |
| Time course (slide) | Peaks ~2 ms after the presynaptic AP, lasts ~6–8 ms | Similar, but downward |

**Summation (Purves Fig. 5.x, Bear Fig. 5.19):**

- One excitatory synapse (E1 or E2) gives a **subthreshold** EPSP.
- **E1 + E2** together give a **suprathreshold** EPSP and an AP.
- **I** alone gives a hyperpolarizing IPSP.
- **E1 + I:** the IPSP **reduces** the EPSP amplitude.
- **E1 + E2 + I:** the IPSP keeps the neuron **below threshold**, so **no AP**. (Inhibition can veto excitation.)
- **Spatial summation:** **different inputs** active **at the same time** add up.
- **Temporal summation:** the **same input** firing APs **in quick succession** adds up.

**Neurotransmitters and their postsynaptic effect (table on slide 36):**

| Transmitter | Class | Effect |
|---|---|---|
| Acetylcholine (ACh) | — | Excitatory |
| Glutamate | Amino acid | **Excitatory** |
| Aspartate | Amino acid | (Excitatory) |
| **GABA** | Amino acid | **Inhibitory** |
| **Glycine** | Amino acid | **Inhibitory** |
| Catecholamines (dopamine, norepinephrine, epinephrine) | Biogenic amines | Excitatory |
| Serotonin (5-HT) | Indoleamine | Excitatory |
| Histamine | Imidazoleamine | Excitatory |
| ATP | Purine | Excitatory |
| Neuropeptides (>100, usually 3–36 amino acids; e.g., Met-enkephalin) | Peptide | Excitatory **and** inhibitory |
| Endocannabinoids | — | **Inhibits inhibition** |
| Nitric oxide | — | Excitatory and inhibitory |

> **Why synaptic transmission matters (slide):** psychoactive drugs, mental disorders, learning and memory, "indeed all operations of the nervous system", cannot be understood without it.

### Part A — Practice MCQs (select all correct)

**A-1.** Regarding the Nernst equation and equilibrium potentials:
- A. At equilibrium, the net flux of the ion across the membrane is zero.
- B. A divalent cation with the same concentration ratio as Na⁺ has an equilibrium potential of about half $E_{Na}$.
- C. Doubling the absolute concentrations inside and outside (same ratio) doubles $E_{ion}$.
- D. For Cl⁻ with $[Cl^-]_o > [Cl^-]_i$, the equilibrium potential is negative.
- E. $E_{ion}$ depends on the permeability of the membrane to that ion.

> **Answer: A, B, D.**
> - A ✓: definition. Diffusion and electrostatic forces balance, so there is no net current.
> - B ✓: $z=2$ halves the factor (30.77 vs 61.54 mV per decade).
> - C ✗: only the **ratio** matters.
> - D ✓: $z=-1$ flips the sign, giving $-61.54\log(11.5)\approx-65$ mV.
> - E ✗: permeability appears in **Goldman**, not Nernst. Nernst gives the potential that *would* exist if the membrane were permeable to that ion.

**A-2.** A neuron has $[K^+]_o = 5$ mM, $[K^+]_i=100$ mM, $[Na^+]_o=150$ mM, $[Na^+]_i=15$ mM, and $P_K:P_{Na}=40:1$ at 37 °C. Which statements are correct?
- A. $E_K\approx -80$ mV.
- B. $V_m\approx -65$ mV.
- C. If $P_{Na}$ became 0, $V_m$ would move to about −80 mV.
- D. If $P_{Na}$ became much larger than $P_K$, $V_m$ would approach about +62 mV.
- E. $V_m$ would be exactly midway between $E_K$ and $E_{Na}$.

> **Answer: A, B, C, D.**
> - A ✓: $61.54\log(0.05)$.
> - B ✓: $61.54\log(350/4015)$.
> - C ✓: Goldman reduces to Nernst for K⁺.
> - D ✓: this is what happens at the AP peak.
> - E ✗: the weighting is by **permeability**, and K⁺ dominates at rest, so $V_m$ sits much closer to $E_K$.

**A-3.** Which statements about the action potential are correct?
- A. At rest, voltage-gated Na⁺ channels are closed but voltage-gated K⁺ channels are open.
- B. The overshoot does not reach $E_{Na}$ because Na⁺ channels inactivate quickly.
- C. The inactivation gate of the Na⁺ channel closes about 1 ms after the activation gate opens.
- D. Voltage-gated K⁺ channels open at the same instant as Na⁺ channels, producing the rising phase.
- E. The undershoot is a period of hyperpolarization relative to rest.

> **Answer: B, C, E.**
> - A ✗: at rest **both** voltage-gated Na⁺ and K⁺ channels are closed. Resting K⁺ permeability comes from **leak** channels.
> - D ✗: K⁺ channels are **delayed** (triggered by depolarization but open about 1 ms later) and cause the **falling** phase.

**A-4.** A stronger depolarizing current is injected into a neuron that is already firing. Which are correct?
- A. The individual AP amplitude increases.
- B. The firing rate increases.
- C. The all-or-none law is violated.
- D. Stimulus intensity is encoded mainly by AP frequency.
- E. Hyperpolarizing current of the same size would produce more APs.

> **Answer: B, D.**
> - A ✗ and C ✗: amplitude is fixed (all-or-none), and a changing rate does not violate that law.
> - E ✗: hyperpolarizing current produces only passive responses.

**A-5.** Which statements about conduction are correct?
- A. Subthreshold potentials spread passively and decay to a small fraction within a few millimetres.
- B. Myelin increases the number of voltage-gated Na⁺ channels along the internode.
- C. In myelinated axons, voltage-gated Na⁺ channels are concentrated at the nodes of Ranvier.
- D. One Schwann cell myelinates many axons in the CNS.
- E. Oligodendroglia are found only in the CNS.

> **Answer: A, C, E.**
> - B ✗: channels concentrate at the **nodes**. Internodes are insulated.
> - D ✗: Schwann cells are **PNS** and **one axon each**. Oligodendrocytes are CNS and myelinate several axons.

**A-6.** The spike-initiation zone:
- A. In a cortical pyramidal cell, is the axon hillock.
- B. In a primary sensory neuron, is near the sensory nerve endings.
- C. Is defined by a low density of voltage-gated Na⁺ channels.
- D. In most neurons, is the dendritic tree because it receives synaptic input.
- E. Must be depolarized beyond threshold for synaptic input to trigger an AP in CNS neurons.

> **Answer: A, B, E.**
> - C ✗: it has a **high** density.
> - D ✗: dendrites and soma have **few** voltage-gated Na⁺ channels.

**A-7.** Electrical vs chemical synapses:
- A. Electrical synapses are generally bidirectional.
- B. Chemical synapses require Ca²⁺ entry into the presynaptic terminal for vesicle fusion.
- C. The gap between membranes at a gap junction is about 3 nm.
- D. Chemical synapses are faster than electrical synapses because vesicles are pre-filled.
- E. Furshpan and Potter proved electrical synapses; Loewi supported chemical synapses.
- F. Cells joined by gap junctions are said to be electrically coupled.

> **Answer: A, B, C, E, F.**
> - D ✗: electrical synapses are **faster** (very little delay).

**A-8.** Postsynaptic integration (select all correct):
- A. Spatial summation is the addition of EPSPs from different synapses active at about the same time.
- B. Temporal summation requires at least two different presynaptic neurons.
- C. An IPSP can prevent an AP that two EPSPs alone would have produced.
- D. GABA and glycine are classically inhibitory.
- E. Endocannabinoids are listed as "inhibits inhibition".

> **Answer: A, C, D, E.**
> - B ✗: temporal summation is the **same** fibre firing in rapid succession.

**A-9.** Glia and neuron morphology:
- A. Glial cells can act as stem cells in some brain areas.
- B. Glial cells can prevent regeneration in some regions.
- C. Divergence refers to the number of inputs a neuron receives.
- D. The retinal amacrine cell has no axon.
- E. The soma is about 20 µm in diameter.

> **Answer: A, B, D, E.**
> - C ✗: that is **convergence**. Divergence is the number of **targets**.

**A-10.** Channels and pumps:
- A. The Na⁺/K⁺ pump uses metabolic energy to move ions against their gradients.
- B. Voltage-gated channels open because charged parts of the protein move when membrane voltage changes.
- C. Leak channels open only during an action potential.
- D. Leak channels have equal permeability for all ions.
- E. Without the pump, concentration gradients would slowly run down.

> **Answer: A, B, E.**
> - C ✗: leak channels are **normally open**.
> - D ✗: they have **different** permeabilities for different ions.

---

## Part B — Brain Anatomy, Recording Methods and the Origin of EEG 🔥

### B1. Gross brain anatomy ⭐

- An adult human brain weighs about **1.4 kg (3 lb)**; it is wet and spongy.
- Views: **dorsal** (top), **ventral** (bottom, rests on the skull floor), **lateral** (side, "ram's horn" cerebrum), **medial** (cut down the midline, shows the brain stem).
- **Three major parts:** the large **cerebrum**, the **brain stem** (its stalk), and the rippled **cerebellum**. The small **olfactory bulb** is visible in the lateral view.
- **Cerebellum:** coordination, precision and **timing** of movements, and **motor learning**.
- **Gyri** are bumps. **Sulci** are grooves. **Fissures** are especially deep sulci. The pattern varies between individuals, but landmarks are common.
- **Central sulcus:** **precentral gyrus** (anterior to it) controls **voluntary movement** (primary motor). **Postcentral gyrus** (posterior to it) handles **somatic sensation (touch)**.
- **Superior temporal gyrus:** **audition**.
- **Lateral (Sylvian) fissure:** the temporal lobe lies immediately **ventral** to it.
- **Lobes are named after the skull bones** that lie over them. The central sulcus divides frontal from parietal. The occipital lobe is at the very back, bordering parietal and temporal lobes.
- **Insula** ("island"): buried cortex seen by pulling apart the lateral fissure. It **borders and separates the temporal and frontal lobes**.

**Functional map (⭐; the exam could use one option from this):**

| Lobe | Area | Function |
|---|---|---|
| **Frontal** | Primary motor cortex | **Voluntary movements** |
| | Motor association cortex | **Planning, sequencing and execution** of movement |
| | Frontal eye field | **Voluntary eye movements** |
| | Prefrontal cortex | Memory, learning, **personality**, reasoning, judgment, **decision making** |
| | **Broca's area** | **Speech production** |
| **Temporal** | Primary auditory cortex | **Perception of sound** (pitch, frequency, location) |
| | Auditory association cortex | Analysis and **recognition** of sound |
| | **Wernicke's area** | **Language comprehension** |
| | Primary olfactory cortex | **Awareness of smell** |
| **Parietal** | Primary somatosensory cortex | Awareness of somatosensory sensation (pressure, vibration...) |
| | Somatosensory association cortex | Analysis and recognition of somatic sensation |
| | Posterior association area | **Multimodal** association (auditory, visual, somatosensory), **spatial coordination**, communication with other areas |
| **Occipital** | Primary visual cortex | **Awareness of visual stimuli** |
| | Visual association cortex | Analysis of colour, angle, movement; recognition |
| **Insula** | Gustatory cortex | **Awareness of taste** |
| | Association gustatory cortex | Analysis of taste |
| | Visceral sensation | Pain from thoracic, pelvic and abdominal viscera (organs) |

**Traps:** Broca = **production** (frontal) vs Wernicke = **comprehension** (temporal). Precentral = motor vs postcentral = sensory.

### B2. Methods for recording neural signals ⭐

Space–time map (Oweiss Fig 1.1), with invasiveness:

| Method | Invasiveness | Spatial scale | Temporal scale | Measures |
|---|---|---|---|---|
| **EEG** | **Non-invasive** | ~cm (1–10 cm) | ~ms | Scalp potentials from summed PSPs |
| **MEG** | **Non-invasive** | ~cm | ~ms | **Magnetic** fields of neural currents |
| **ECoG** (electrocorticography) | **Semi-invasive** (electrodes on cortex under skull/dura) | ~mm–cm | ~ms | Cortical surface potentials |
| **fMRI** | **Non-invasive** | ~mm | ~1–10 s (slow) | Blood oxygenation. Relies on the fact that **cerebral blood flow and neuronal activation are coupled** (indirect) |
| **LFP** (local field potential) | **Invasive** | ~100 µm–1 mm | ~ms | Extracellular summed synaptic activity near an electrode |
| **Action potentials (single/multi-unit)** | **Invasive** | ~10–100 µm | <1 ms | Spikes |
| **Patch clamp** | **Invasive** | ~µm (single cell/channel) | ~100 µs | Membrane currents |

**Key idea:** EEG trades **spatial** resolution (poor) for **temporal** resolution (excellent), and it is **non-invasive**. fMRI is the opposite: better spatial, poor temporal, indirect.

### B3. Origin of the EEG 🔥 (Q9, Q10)

**Core facts (near-verbatim):**

1. **EEG mainly records the extracellular currents that arise as a consequence of synaptic activity in dendrites of neurons in the cerebral cortex.**
2. The extracellular electric field is **mainly generated by postsynaptic potentials (PSPs)**: **EPSPs or IPSPs**.
3. When the AP reaches the postsynaptic dendrites, it causes a current that **enters through the synapse** into the postsynaptic dendrite.
4. **Pyramidal cells** (mostly excitatory) are the main contributors because they are **spatially aligned perpendicularly to the cortex** (parallel apical dendrites).
5. **The dipole of an individual neuron is impossible to measure** at the scalp. Only when **many neurons' dipoles add** (under specific conditions) is there a measurable field.

**Why PSPs and not APs? (the deep reason, useful for tricky options)**

- An **AP lasts ~1 ms**. APs from many neurons rarely overlap perfectly in time, so they do not sum well. An AP travelling along an axon also produces a *quadrupole*-like field that falls off quickly.
- A **PSP lasts tens of milliseconds**, so thousands of PSPs overlap in time and **summate**. The current enters at the synapse (a **sink**, negative extracellularly for an EPSP) and returns out along the rest of the cell (a **source**, positive), forming a **dipole** along the apical dendrite.
- Therefore EEG is the **summed, synchronized PSP activity of parallel pyramidal cells**. The "~100 mV AP" in a distractor is irrelevant.

**The dipole picture (slide 13):**

- (a) A single pyramidal neuron during a PSP: negative charges near the apical dendrite synapses, positive near the soma/basal dendrites. This is a **bipolar (dipole) field**.
- (b) An active cortical region folded into a sulcus: many aligned dipoles.
- (c) The whole region is summarised by one **equivalent current dipole**, which gives a positive/negative potential pattern over the skull.

**Orientation relative to the skull (slide 14, Q10 figure):**

| Dipole | Location | Contribution |
|---|---|---|
| **(a) Radial** | Crown of a gyrus, pointing at the electrode | **Strongest** EEG signal |
| **(b) Oblique** and **(c) Tangential** | Walls of a sulcus | **Unlikely to be measured**: dipoles on **opposing sides of the sulcus** produce fields of **opposite polarity** that **cancel** |
| **(d) Radial but deep** | Bottom of the sulcus | **Smaller** contribution than (a) because it is **further from the electrode** |

> **Background (not on slides, but helps you reason):** MEG is most sensitive to **tangential** sources and nearly blind to radial ones, which is the reverse of EEG. Potentials fall off steeply with distance, so deep sources are weak.

**Synchrony and alignment (slide 15):**

- Six pyramidal neurons activated at **irregular times** give a summed EEG of **small** amplitude.
- The same neurons activated **synchronously** give a summed EEG of **high** amplitude.
- **Cancellation conditions:**
  - **Randomly oriented** neurons: the positivity of one dipole is cancelled by the negativity of the adjacent one.
  - **Adjacent neurons receiving different transmitter types** (one **excitatory**, one **inhibitory**): opposite dipole orientations, so they **cancel**.
- **Addition condition:** **many neurons with similar orientation, the same transmitter type, stimulated at approximately the same moment** produce dipoles that add and can be measured on the scalp.

**Layers between cortex and electrode:** scalp, skull, dura mater, arachnoid mater, subarachnoid space, pia mater, cortex. The skull strongly smears (low conductivity), which is part of why spatial resolution is poor.

**"Content of EEG?" slide:** the scalp trace is a mixture of many sources and cell types (pyramidal, interneurons, "?"). Interpreting it is hard, which is why the course needs signal processing.

### B4. Why EEG? (advantages) ⭐ (Q11)

1. **Perfectly non-invasive**, with **no exposure to radiation or high magnetic field**.
2. **Direct measure of electrical brain activity** (fMRI is indirect, via blood flow).
3. Devices can be **small and portable**.
4. **High temporal resolution**: it **matches the speed of cognition** (ms). It is **superior** to hemodynamic/neurochemical methods (**fMRI, PET**) and can follow activity changing on the order of tens of ms.
5. **Very rich information**, allowing physiologically inspired analysis (**oscillations, synchronization, connectivity**).
6. Can be recorded in an **open environment**.
7. **Economical**.

**Not advantages (traps):** high spatial resolution ✗, invasive ✗, noise-free ✗, needs shielding room ✗, measures magnetic fields ✗, measures single-neuron APs ✗.

### Part B — Practice MCQs (select all correct)

**B-1.** The EEG signal recorded at the scalp:
- A. Is dominated by summed postsynaptic potentials of cortical pyramidal neurons.
- B. Is dominated by action potentials because they have the largest transmembrane voltage.
- C. Requires many neurons with similar orientation to be synchronously active.
- D. Is enhanced when adjacent neurons receive excitatory and inhibitory input simultaneously.
- E. Reflects extracellular currents.

> **Answer: A, C, E.**
> - B ✗: APs are too brief and asynchronous to sum.
> - D ✗: opposite dipoles **cancel**.

**B-2.** Considering source orientation and depth:
- A. A radial dipole at a gyral crown gives the largest scalp potential.
- B. Tangential dipoles on facing sulcal walls tend to cancel in EEG.
- C. A radial dipole at the bottom of a deep sulcus gives a larger EEG potential than an identical one at the crown because it is surrounded by more tissue.
- D. The equivalent current dipole summarizes an active cortical region.
- E. Dipole orientation does not matter for EEG.

> **Answer: A, B, D.**
> - C ✗: deeper means further from the electrode, so **smaller**.
> - E ✗.

**B-3.** Which statements about recording modalities are correct?
- A. ECoG is semi-invasive.
- B. fMRI relies on coupling between cerebral blood flow and neuronal activation.
- C. LFP and patch clamp are non-invasive.
- D. MEG and EEG both have millisecond temporal resolution.
- E. fMRI has better temporal resolution than EEG.

> **Answer: A, B, D.**
> - C ✗: both are **invasive**.
> - E ✗: fMRI is seconds.

**B-4.** Advantages of EEG listed in the course:
- A. It is a direct measure of electrical brain activity.
- B. It is portable and economical.
- C. It gives very rich information for oscillation, synchronization and connectivity analysis.
- D. It has high spatial resolution because electrodes sit close to the cortex.
- E. It involves no radiation and no strong magnetic fields.

> **Answer: A, B, C, E.**
> - D ✗: EEG spatial resolution is **poor** because the skull and scalp smear the field.

**B-5.** Brain anatomy:
- A. The central sulcus separates frontal and parietal lobes.
- B. The postcentral gyrus is primary motor cortex.
- C. Wernicke's area (temporal) is associated with language comprehension.
- D. The insula separates temporal and frontal lobes.
- E. Broca's area (frontal) is associated with speech production.
- F. The frontal eye field controls voluntary eye movements.

> **Answer: A, C, D, E, F.**
> - B ✗: postcentral = **somatosensory**, precentral = motor.

**B-6.** A cortical patch shows high-amplitude EEG oscillations. Which explanations are consistent with the slides?
- A. Many pyramidal cells in the patch receive the same type of input nearly simultaneously.
- B. The patch is on a gyral crown with radially oriented cells.
- C. The cells fire APs asynchronously at high rates.
- D. Cells are randomly oriented.
- E. The PSPs are synchronized.

> **Answer: A, B, E.**
> - C ✗: asynchronous activity gives a small summed amplitude.
> - D ✗: random orientation leads to cancellation.

---

## Part C — EEG Acquisition: Electrodes, Sampling, ADC, Amplifiers, Montages 🔥

### C1. The data acquisition chain ⭐

Most acquisition systems have **analog** and **digital** components (van Drongelen Fig. 2.1):

$$\text{Biological process}\;\to\;\underbrace{\text{Electrodes/Transducer}\to\text{Pre-amplifier}\to\text{Amplifier}\to\text{Band filter}\to\text{Notch filter}\to\text{Anti-alias filter}\to\text{S/H}}_{\text{ANALOG}}\;\to\;\underbrace{\text{MUX}\to\text{ADC}\to\text{time series}\to\text{analysis}}_{\text{DIGITAL}}$$

| Stage | Purpose |
|---|---|
| **Transducer / electrode pair** | Picks up the biological signal |
| **Pre-amplifier + amplifier** | Amplification usually happens **in two steps** |
| **Band-pass filter** | Attenuates undesired frequency components |
| **Notch filter** | Removes line interference (50/60 Hz) |
| **Anti-aliasing filter** | **Critical step:** attenuates frequencies **too high to be digitized** (above Nyquist) **before** sampling |
| **Sample-and-hold (S/H)** | Samples the analog signal and **holds it constant during the ADC conversion** |
| **MUX (multiplexer)** | Switches many channels into one ADC |
| **ADC** | Converts amplitude to integers |

**Trap:** the anti-aliasing filter must be **analog** and placed **before** the ADC. Once aliasing has happened, digital filtering cannot undo it because the alias sits at a legitimate low frequency.

### C2. Electrodes and the Ag/AgCl interface 🔥 (Q13)

- **Metal electrodes** measure potentials in an **ionic solution**. The fundamental problem is the **metal–solution interface**.
- The interface generates an **electrode potential** that is **material- and solution-specific**. This is **usually not a problem when both electrodes of a pair are the same material** (the potentials cancel in the difference).
- **Silver electrodes with a silver chloride (Ag/AgCl) coating** are widely used. The AgCl layer:
  1. facilitates the **transition from ionic (Ag⁺ / Cl⁻) to electronic conduction**,
  2. **reduces the electrode capacitance** at the solution interface,
  3. and **consequently facilitates recording of signals with low-frequency components**.
- **Equivalent circuit:** a **resistor in parallel with a capacitor**.

**Why capacitance matters (intuition):** a capacitor blocks DC and slow signals ($Z_C = 1/(j\omega C)$ is huge at low $\omega$). A polarizable bare-metal electrode behaves like a capacitor and filters out slow EEG. Ag/AgCl is (nearly) **non-polarizable**: charge crosses the interface through a reversible chemical reaction ($\text{AgCl} + e^- \leftrightarrow \text{Ag} + \text{Cl}^-$), so slow signals pass.

**Traps:** "Ag/AgCl removes the need for amplification" ✗. "guarantees zero noise" ✗. "Electrode choice is irrelevant with a high-bit ADC" ✗.

### C3. Analog-to-digital conversion: amplitude resolution ⭐

- Biomedical signals are **analog**: **continuous in amplitude and time**. Digital processing needs discretization in both:
  - **Time** is discretized by **sampling** at interval $T_s$ (rate $F_s=1/T_s$).
  - **Amplitude** is discretized by the **ADC**, which is like **rounding/truncating** a real value to an integer.
- **Amplitude resolution is measured in bits.** An $n$-bit ADC has $2^n$ levels.

$$\text{levels} = 2^{n},\qquad \Delta V = \frac{V_{range}}{2^{n}}\;(\text{approximately})$$

- Slide example: **3-bit** gives $2^3=$ **8 levels (0–7)**, codes **000–111**. The signal is amplified (A×) then rounded to the nearest level. Where the amplified signal exceeds the top level, it **clips** ("distortion" at level 7 in the figure).
- Examples: 12 bits = 4096 levels; 16 bits = 65,536; 24 bits = 16,777,216.
- **Quantization noise** is the rounding error. It is the lowest noise in the noise figure (~$10^{-6}$ V).
- Numeric: a ±5 mV input range (10 mV span) on a 16-bit ADC gives $\Delta V = 10\text{ mV}/65536\approx 0.15\ \mu$V.

### C4. Sampling in time: Dirac impulse, Dirac comb, Nyquist, aliasing 🔥 (Q12)

**Dirac delta (unit impulse):**

| Continuous | Discrete |
|---|---|
| $\delta(t)=0$ for $t\ne0$, $\int_{-\infty}^{\infty}\delta(t)\,dt=1$ | $\delta(n)=0$ for $n\ne0$, $\sum_{n}\delta(n)=1$ |

- The unit impulse is the **derivative of the unit step** $U(t)$.
- It can be viewed as a **square pulse of duration $\tau$ and amplitude $1/\tau$** (area 1) with $\tau\to0$, the derivative of a ramp.

**Sampling as multiplication by a Dirac comb:**

$$x^{s}(nT_s)=\sum_{n=-\infty}^{\infty}x(nT_s)\,\delta(t-nT_s)=x(t)\sum_{n=-\infty}^{\infty}\delta(t-nT_s)$$

**What sampling does in the frequency domain (the key picture, Fig 2.6/2.7):**

- **Multiplication in time equals convolution in frequency.**
- The FT of a Dirac comb with spacing $T_s$ is another comb with spacing $F_s = 1/T_s$ (scaled by $1/T_s$).
- Convolving the signal spectrum $F(f)$ with that comb **copies $F(f)$ at every multiple of $F_s$**. **The spectrum of a sampled signal is periodic with period $F_s$.**
- If the width of $F(f)$ exceeds $F_s/2$, neighbouring copies **overlap**. That overlap is **aliasing**: high frequencies masquerade as low ones.
- **Condition to avoid overlap:** the maximum frequency in the signal must be **less than $F_s/2$**.

**Nyquist terms (do not confuse them):**

| Term | Value | Meaning |
|---|---|---|
| **Nyquist sampling frequency / Nyquist limit / Nyquist rate** | $2 f_{max}$ | The **minimum sampling rate** for a signal with max frequency $f_{max}$ |
| **Nyquist frequency** | $F_s/2$ | The **highest frequency representable** for a given sampling rate |

**The 20 Hz example (slides and Lab 1):**

- At **500 Hz**: looks like a clean sine.
- At **59 Hz**: above the 40 Hz Nyquist rate, so the frequency content is preserved, **but the time-domain shape looks distorted** (amplitude appears to wax and wane, a beat pattern).
- At **24 Hz**: below 40 Hz, so it **aliases**. The plot shows a wave at $\lvert 20-24\rvert=$ **4 Hz**.
- At **exactly 40 Hz**, samples taken at peaks and valleys give a **20 Hz triangular** wave. Samples taken elsewhere look even more distorted. (At exactly $2f$ you can even hit the zero crossings and see nothing, which is why "at least" / "more than" matters.)

**Practical rule (slide):** to avoid time-domain distortion, **sampling at 5× the maximum frequency is common**. Also **always use an anti-aliasing filter** that removes everything above the Nyquist frequency.

**Aliasing formula (for numeric questions):** a tone at $f$ sampled at $F_s$ appears at

$$f_{alias} = \left\lvert f - k\,F_s \right\rvert \quad\text{with the integer } k \text{ that brings it into } [0, F_s/2]$$

Examples: 20 Hz at 30 Hz gives 10 Hz. 20 Hz at 24 Hz gives 4 Hz. 50 Hz hum at 60 Hz sampling gives 10 Hz. 70 Hz at 100 Hz gives 30 Hz. 120 Hz at 100 Hz gives 20 Hz.

### C5. The International 10–20 System ⭐

- Proposed by **Herbert Jasper in 1958**. Used worldwide for **naming and placing** scalp electrodes.
- Reference landmarks: **nasion** (bridge of nose), **inion** (bump at the back of the skull), **preauricular points** (in front of the ears), and the **vertex** (Cz).
- **"10" and "20" are percentages** of the nasion–inion (through the vertex) and preauricular–preauricular distances. **Edge electrodes are 10%** from the landmarks, and **the rest are 20% apart**.
- **Naming:**
  - Letter = lobe/region: **Fp** (frontal pole), **F** (frontal), **C** (central), **P** (parietal), **O** (occipital), **T** (temporal), **A** (auricular/ear).
  - **Odd numbers = left** hemisphere, **even numbers = right**. (Mnemonic: *odd = left*.)
  - **z ("zero") = midline** (Fz, Cz, Pz).
- Standard set: Fp1, Fp2, F7, F3, Fz, F4, F8, T3, C3, Cz, C4, T4, T5, P3, Pz, P4, T6, O1, O2 (19 scalp) plus A1, A2.
- **Spatial logic for artifacts:** Fp1/Fp2 are **above the eyes** (blinks), F7/F8 are **lateral frontal near the outer canthi** (lateral eye movements), T3/T4 are over the **temporalis** muscles (chewing), and O1/O2 are **occipital** (alpha).

### C6. The differential amplifier: active, reference and ground 🔥 (Q14)

**Why not a single electrode?** Measuring one scalp electrode relative to the **acquisition circuit ground** would mainly capture the **static electricity difference** between body and circuit, which is **much larger than neural activity**.

**Why not just two electrodes?** Even the difference of two scalp electrodes measured against the circuit would be masked by **noise affecting the ground or power of the acquisition circuit**.

**Solution: differential amplifier with three electrodes per channel.**

- **A = active** (e.g., O1), **R = reference** (e.g., ear), **G = ground** (e.g., forehead).
- The amplifier computes

$$C = V_{AG} - V_{RG}$$

- Anything **common** to both $V_{AG}$ and $V_{RG}$ (the ground noise, the "common mode") **is eliminated**. Only the **difference** between active and reference is amplified.

**Ground electrode:** usually on the **frontal bone** to **minimize noise of muscular origin**. **Its potential is cancelled** during differential amplification, so its **location is not as important as the reference location**.

**Reference electrode:** **there is no ideally "neutral" place.** Every EEG channel **reflects contributions of both active and reference electrodes**. Usually placed on **one or both ear lobes** (or mastoids).

**Slide example:** ground frontal, reference left ear, active O1 over an active cortical dipole. Here $V_{AG} < V_{RG}$, so channel O1 is **negative**.

**Consequences (the exam tests these):**

- Common-mode rejection works **best when the interference is identical at both inputs**.
- An artifact present at **only one** electrode (e.g., a loose active electrode, or a pulse under the reference) is **not common**, so it **stays in the channel**. A noisy **reference** contaminates **every** channel that uses it.
- Differential amplification is about **noise rejection**, not ADC bits.

### C7. Derivations, montages and referencing 🔥 (Q15)

Three families of derivation (slide 11 of Ch 3):

| Method | Formula (slide) | What it does | Pros | Cons |
|---|---|---|---|---|
| **Bipolar** | Neighbouring pairs: $T_3 = V_{A_1G}-V_{A_2G}$, $C_3 = V_{A_2G}-V_{A_3G}$, ... | Difference between **adjacent** electrodes | Removes activity **common to both neighbours** (widespread activity, far sources); good localization of focal events (phase reversal) | Hides widespread activity; amplitude depends on inter-electrode distance |
| **Unipolar / common reference** | $C_3 = V_{A_1G}-V_{RG}$, $C_z = V_{A_2G}-V_{RG}$, $C_4 = V_{A_3G}-V_{RG}$ | All channels vs one reference R | Simple; preserves waveform shape | Reference activity contaminates **all** channels |
| **Biauricular (linked ears)** | $V'_{RG} = \frac{V_{R1G}+V_{R2G}}{2}$, then $C_3 = V_{A_1G}-V'_{RG}$ | Reference = mean of both ears | Avoids lateral bias of a single ear | Still not neutral |
| **Common Average Reference (CAR)** | $M=\frac{C_3+C_z+C_4}{3}$, $C_3' = C_3-M$, etc. | Subtract the **mean of all channels** from each channel | Reduces the impact of a **single-point failure** of a reference; approximates a neutral reference with dense, whole-head coverage | Sensitive to **outlier/bad channels**, and to an **artifact shared by many electrodes** (it spreads into the mean and then into every channel) |
| **Laplacian / Local Average Reference (LAR)** | Subtract the average of **nearest neighbours** | **Spatial high-pass filter** | Emphasizes local sources | Edge electrodes lack neighbours |

**Referencing rules from Ch 8 (the exam's source for Q15):**

- Standard practice: **subtract a reference signal with the same time resolution** from each channel.
- Common choices: **mastoid channel, a specific EEG channel, the average of two mastoids, or the average of all channels**.
- The reference should **remain unchanged relative to the EEG**. Inspect it for **comparable amplitude** and **no correlation with task-induced brain activity**.
- **CAR** reduces single-point failure but **may suffer from outlier channels**, so **detect and remove bad channels before CAR**. The slide example contrasts ordinary average reference (A: all channels contaminated) with **robust average reference** (B: clean).
- **Changing the reference changes the waveforms and topography even if brain activity is unchanged.**

### Part C — Practice MCQs (select all correct)

**C-1.** A 35 Hz component is present in an analog EEG signal. Which statements are correct?
- A. Sampling at 70 Hz is the theoretical minimum (Nyquist rate).
- B. Sampling at 50 Hz makes the component appear at 15 Hz.
- C. The Nyquist frequency when sampling at 250 Hz is 125 Hz.
- D. After sampling at 50 Hz, a digital low-pass filter at 20 Hz can completely remove the alias.
- E. A 5× rule of thumb suggests sampling at about 175 Hz.

> **Answer: A, B, C, E.**
> - B ✓: $\lvert 35-50\rvert=15$ Hz.
> - D ✗: the alias now **is** a 15 Hz signal, indistinguishable from real 15 Hz content. A 20 Hz low-pass keeps it. Aliasing must be prevented **before** the ADC with an analog anti-aliasing filter.

**C-2.** Sampling and the frequency domain:
- A. Sampling can be modelled as multiplying $x(t)$ by a Dirac comb.
- B. The spectrum of a sampled signal is periodic with period equal to the sampling frequency.
- C. Aliasing results from overlap of spectral copies when the signal bandwidth exceeds $F_s/2$.
- D. Sampling corresponds to convolution in the time domain.
- E. The unit impulse can be viewed as the derivative of the unit step.

> **Answer: A, B, C, E.**
> - D ✗: multiplication in **time** corresponds to convolution in **frequency**.

**C-3.** ADC:
- A. A 3-bit converter has 8 levels.
- B. Going from 12 to 16 bits increases the number of levels 16-fold.
- C. Bit depth determines the maximum frequency that can be digitized.
- D. Amplitude discretization can be thought of as rounding to integers.
- E. An ADC with more bits can recover aliased frequencies.

> **Answer: A, B, D.**
> - B ✓: $2^{16}/2^{12}=2^4=16$.
> - C ✗: that is the **sampling rate**.
> - E ✗.

**C-4.** In the 10–20 system:
- A. C4 lies over the right hemisphere.
- B. Fz lies on the midline.
- C. The "10" and "20" refer to electrode spacing in centimetres.
- D. It was proposed by Herbert Jasper in 1958.
- E. T3 lies over the left temporal region.
- F. A1/A2 are auricular (ear) electrodes.

> **Answer: A, B, D, E, F.**
> - C ✗: they are **percentages** of skull distances.

**C-5.** Differential amplification with active (A), reference (R) and ground (G) electrodes:
- A. The channel value is $V_{AG}-V_{RG}$.
- B. The ground electrode position is critical because its potential appears in the output.
- C. Noise that is identical on A and R is rejected.
- D. A pulse artifact under the reference electrode appears in every channel referenced to it.
- E. The ground is often placed on the forehead to minimize muscle noise.

> **Answer: A, C, D, E.**
> - B ✗: the ground potential **cancels**, so its position matters **less** than the reference position.

**C-6.** Ag/AgCl electrodes:
- A. The chloride layer eases the transition from ionic to electronic conduction.
- B. They reduce electrode capacitance at the interface.
- C. They make recording of low-frequency components easier.
- D. Their electrode potential is a problem even when both electrodes are Ag/AgCl.
- E. Their equivalent circuit is a resistor in parallel with a capacitor.

> **Answer: A, B, C, E.**
> - D ✗: electrode potentials are usually **not** a problem with matched-material pairs.

**C-7.** Referencing and montages:
- A. CAR subtracts the mean of all channels from each channel.
- B. CAR is robust to a single extremely noisy channel.
- C. A bipolar montage subtracts neighbouring electrodes and suppresses activity common to both.
- D. With a biauricular reference, the reference is the average of both ear electrodes.
- E. A reference correlated with task-related brain activity is acceptable if its amplitude is small.
- F. The Laplacian acts as a spatial high-pass filter emphasizing local activity.

> **Answer: A, C, D, F.**
> - B ✗: CAR **suffers** from outlier channels, so remove them first.
> - E ✗: the reference should have **no correlation** with task activity.

**C-8.** The order of stages in the analog front end is:
- A. Electrodes, pre-amplifier, amplifier, band filter, notch, anti-alias, sample-and-hold.
- B. Electrodes, ADC, anti-alias filter, amplifier.
- C. The anti-aliasing filter comes after the ADC to save computation.
- D. The S/H circuit holds the value constant during conversion.
- E. A multiplexer can feed multiple channels to the ADC.

> **Answer: A, D, E.**
> - B ✗ and C ✗: the anti-alias filter must come **before** the ADC.

---

## Part D — Fourier Analysis: Series, CFT, DFT, FFT, Spectra, Windows 🔥

> **Big picture (slide "different types of Fourier analysis"):**
> Real Fourier Series → Complex Fourier Series → Continuous Fourier Transform (CFT) → Discrete Fourier Transform (DFT) → Fast Fourier Transform (FFT) → Power Spectrum $S = X X^{\ast}/N$.
> The **series** represents **periodic** functions as sums of waves. **CFT/DFT** are the basis for examining **real-world signals** in the frequency domain. The **FFT** is an efficient **algorithm** for the DFT. The **power spectrum** is computed from FFT results.

### D0. Mathematical toolkit (from the labs) ⭐

**Complex numbers.** $z = a + jb$ with real part $a$ and imaginary part $b$ (engineers write $j$, MATLAB accepts `1i`).

- Magnitude: $\lvert z\rvert=\sqrt{a^2+b^2}=\sqrt{z\,\bar z}$ (MATLAB `abs`).
- Phase: $\varphi=\arctan(b/a)$ (quadrant-aware `angle`).
- Conjugate: $\bar z = a-jb$.

**Euler's formula.**

$$e^{jx}=\cos x + j\sin x,\qquad \cos x=\frac{e^{jx}+e^{-jx}}{2},\qquad \sin x=\frac{e^{jx}-e^{-jx}}{2j}$$

- $A e^{j\varphi}$ is a point at **distance $A$** from the origin at **angle $\varphi$** (lab: $4e^{j\pi/3}$ is 4 units at 60°, i.e., $2 + 3.46j$).
- $e^{j2\pi f t}$ is a point **rotating** around the unit circle $f$ times per second. Its real part is a cosine and its imaginary part a sine (lab "complex sine wave" 3-D helix).
- Useful values: $e^{j0}=1$, $e^{j\pi/2}=j$, $e^{j\pi}=-1$, $e^{j3\pi/2}=-j$, $e^{j2\pi}=1$.

**Dot product as similarity (the intuition behind every Fourier coefficient).**

$$\langle a,b\rangle=\sum_n a_n b_n \quad(\text{real}),\qquad \langle a,b\rangle=\sum_n \overline{a_n}\,b_n\quad(\text{complex})$$

- Large when two vectors "point the same way", zero when **orthogonal**.
- **Lab:** the dot product of a 5 Hz Gaussian-windowed sine with test sines at 1–10 Hz **peaks at 5 Hz**. The Fourier transform is exactly this, done for every frequency.
- With a **real** sine as template, the result depends on **phase** (a signal with $\theta=\pi/2$ relative to the template gives ~0 even at the right frequency). With a **complex** sine $e^{j2\pi ft}$, the **magnitude** measures the frequency match **regardless of phase**, and the **angle** gives the **phase difference**. **This is why Fourier analysis uses complex exponentials.**

### D1. The real Fourier series 🔥 (Q16)

A periodic function $f(t)=f(t+T)$ with period $T$, frequency $f=1/T$ and angular frequency $\omega = 2\pi f$ can be represented by

$$P(t)=\frac{1}{2}a_0+\sum_{n=1}^{\infty}\left[a_n\cos(n\omega t)+b_n\sin(n\omega t)\right]$$

- $\frac12 a_0$ is the **DC (direct current) component**, the **mean** of the signal.
- $a_n$, $b_n$ weight the **AC (alternating current) components** at **harmonics** $n\omega$.
- $n=1$ is the **fundamental**. $n\ge2$ are **harmonics**.

**How the coefficients are found (derivation logic you should be able to recognise):**

1. Define the error $E^2=\int_{t}^{t+T}[P(t)-f(t)]^2\,dt$.
2. Minimize it: $\partial E^2/\partial a_n=0$ and $\partial E^2/\partial b_n=0$. This gives $2\int_T (P-f)\,\frac{\partial P}{\partial a_n}\,dt=0$.
3. $\partial P/\partial a_0 = 1/2$, $\partial P/\partial a_n=\cos(n\omega t)$, $\partial P/\partial b_n=\sin(n\omega t)$. **There is no $b_0$.**
4. Use two facts:
   - The integral of $\cos$ or $\sin$ over whole periods is **0**.
   - **Orthogonality:**

$$\int_T \cos(n\omega t)\cos(m\omega t)\,dt=\begin{cases}T/2 & m=n\\ 0 & m\neq n\end{cases},\quad \int_T \sin(n\omega t)\sin(m\omega t)\,dt=\begin{cases}T/2 & m=n\\ 0 & m\neq n\end{cases},\quad \int_T\sin(n\omega t)\cos(m\omega t)\,dt=0$$

5. Every term vanishes except the matching one. With $\cos^2 A=\frac12[1+\cos 2A]$ and $\sin^2A=\frac12[1-\cos2A]$, the integral gives $T/2$.

**Results (memorise):**

$$a_0=\frac{2}{T}\int_T f(t)\,dt,\qquad a_n=\frac{2}{T}\int_T f(t)\cos(n\omega t)\,dt,\qquad b_n=\frac{2}{T}\int_T f(t)\sin(n\omega t)\,dt$$

**Reading the formulas:** each coefficient is a **dot product** (correlation) of the signal with a cosine or sine template, normalized by $2/T$. Because of the $2/T$ in $a_0$, the DC term is written $\frac12 a_0$, so DC $=\frac1T\int_T f\,dt$, the mean.

**Symmetry shortcuts (⭐ very useful):**

| Symmetry | Definition | Consequence |
|---|---|---|
| **Even** | $f(t)=f(-t)$ (mirror about $t=0$, like cosine) | **$b_n = 0$** (only cosines) |
| **Odd** | $f(t)=-f(-t)$ (like sine) | **$a_n=0$** (and $a_0=0$; only sines) |
| **Any function** | $f=f_{even}+f_{odd}$ with $f_{even}=\frac{f(t)+f(-t)}{2}$, $f_{odd}=\frac{f(t)-f(-t)}{2}$ | Cosines capture the even part, sines the odd part |

**Worked example: triangle wave** (amplitude $A$, peak at $t=0$, period $T$):

- The **DC component is absent**, so $a_0=0$ (equal area above and below zero).
- It is **even**, so $b_n=0$.
- On $-T/2\le t\le0$: $A(t)=A+4At/T$. On $0\le t\le T/2$: $A(t)=A-4At/T$. Split the integral there to avoid the kink at $t=0$.
- Result: $a_n=\dfrac{8A}{n^2\pi^2}$ for **odd** $n$, and $a_n=0$ for **even** $n$ (slide prints $8A/(n\pi^2)$; the $n^2$ is correct).
- **Concept:** coefficients fall as $1/n^2$. The triangle is smooth (continuous), so the harmonics decay fast.

**Square wave** (±1, odd, intro slide): the sum of five sines approximates it, with amplitudes $\frac{4}{\pi}\cdot\frac1n$ at $n=1,3,5,7,9$ (odd harmonics only, decaying as $1/n$). **Concept:** a discontinuous signal has slowly decaying harmonics, so sharp edges need high frequencies.

**Analogy:** a prism splits white light into colours. Sound can be split into pure tones. The Fourier series splits a periodic waveform into sinusoids. The amplitude-vs-frequency plot is the **frequency-domain representation**.

### D2. The complex Fourier series 🔥 (Q17)

$$P(t)=\sum_{n=-\infty}^{\infty}c_n\,e^{jn\omega t},\qquad c_n=\frac{1}{T}\int_T f(t)\,e^{-jn\omega t}\,dt$$

- $\int_T$ means over **one full period**, and **the starting point does not matter** (e.g., $-T/2\to T/2$ or $0\to T$).
- Connected to the real series by **Euler's relation** $e^{jx}=\cos x+j\sin x$. **The real and complex notations are equivalent.**
- **Relationships:** $c_0 = \tfrac12 a_0$ (DC). For $n>0$: $c_n=\tfrac12(a_n - j b_n)$ and $c_{-n}=\tfrac12(a_n+jb_n)=\overline{c_n}$ (for real $f$).
- The sum runs over **negative and positive** $n$. Each real sinusoid is a pair of counter-rotating phasors at $\pm n\omega$.
- $c_n$ is **complex**: $\lvert c_n\rvert$ gives the **amplitude** (harmonic amplitude $=2\lvert c_n\rvert=\sqrt{a_n^2+b_n^2}$) and $\arg c_n$ gives the **phase**. **The complex series contains phase information.**

**Traps:** "the complex series is written as a sum of sines and cosines" ✗ (it is written as a sum of complex exponentials). "No phase information" ✗. "Coefficients depend on the start point" ✗. The **normalization differs**: $2/T$ in the real series vs $1/T$ in the complex series.

### D3. The continuous Fourier transform (CFT) and standard pairs 🔥

For **non-periodic** signals the harmonic spacing $\omega = 2\pi/T\to 0$ as $T\to\infty$, and the series becomes an integral:

$$F(j\omega)=\int_{-\infty}^{\infty}f(t)\,e^{-j\omega t}\,dt\qquad\Longleftrightarrow\qquad f(t)=\frac{1}{2\pi}\int_{-\infty}^{\infty}F(j\omega)\,e^{j\omega t}\,d\omega$$

**Standard pairs (Table 6.1, memorise with the pictures):**

| Time domain $f(t)$ | Frequency domain $F(\omega)$ | Intuition |
|---|---|---|
| $\delta(t)$ (impulse) | $1$ (flat, **all frequencies**) | An infinitely brief event needs every frequency |
| $1$ (DC) | $2\pi\,\delta(\omega)$ (impulse at **zero** frequency) | The reverse: constant in time is a single line at 0 |
| $\cos(\omega_0 t)$ | $\pi[\delta(\omega+\omega_0)+\delta(\omega-\omega_0)]$ | Two **real** lines at $\pm\omega_0$ |
| $\sin(\omega_0 t)$ | $j\pi[\delta(\omega+\omega_0)-\delta(\omega-\omega_0)]$ | Two **imaginary** lines of opposite sign |

- In general, a coefficient $c_n$ in $F(j\omega)$ has **real ($a_n$) and imaginary ($b_n$) parts**, drawn as a vector in the complex plane (polar plot) with angle $\phi_n$.
- **Duality:** narrow in time means wide in frequency, and vice versa (impulse vs flat; DC vs impulse; short window vs broad sinc).
- **Key theorem used everywhere:** **multiplication in one domain equals convolution in the other.**

### D4. The discrete Fourier transform (DFT) 🔥 (Q19, Q20)

**Why a DFT:** real signals are **sampled** and observed over a **finite** interval, so both the time and frequency scales must be **discrete and finite**, and **they are related**.

**Time scale:** $N$ samples, interval $\Delta t$, epoch $T=N\Delta t$, $t_n=n\Delta t$.

**Frequency scale:**

$$\Delta f=\frac{1}{T}=\frac{1}{N\Delta t}=\frac{F_s}{N}\quad(\textbf{precision / resolution}),\qquad \Delta\omega = \frac{2\pi}{N\Delta t},\qquad \omega_k = k\,\Delta\omega$$

$$\text{full periodic range } \Omega = N\Delta\omega=\frac{2\pi}{\Delta t}\;(\text{i.e. } F_s \text{ in Hz}),\qquad \text{usable range (shown)} = \frac{F_s}{2}\;(\text{Nyquist})$$

**Slide example (Ch 5):** $T=10$ s, $\Delta t=1$ ms. **Precision** $\Delta f = 1/10 =$ **0.1 Hz** ($\Delta\omega = 2\pi\times0.1$ rad/s). **Full range** $1/\Delta t=$ **1000 Hz** ($\Omega=2\pi\times1000$ rad/s), shown up to 500 Hz.

**Intuition for precision $=1/T$:** within $T$ seconds you cannot tell two frequencies apart unless one completes at least **one more cycle** than the other over the window. That difference is $1/T$ Hz.

**Derivation (recognise it):**

1. Approximate the CFT integral by a sum over $N$ samples: $F_a(j\omega_k)=\sum_{n} f(t_n)e^{-j\omega_k t_n}\Delta t$.
2. Substitute $t_n=n\Delta t$ and $\omega_k=k\,2\pi/(N\Delta t)$, so $\omega_k t_n = \frac{2\pi}{N}kn$. The $\Delta t$ cancels inside the exponent.
3. $F_a(j\omega_k)=\Delta t\sum_{n=0}^{N-1} f(t_n)\,e^{-j\frac{2\pi}{N}kn}=\Delta t\sum_{n=0}^{N-1}f(t_n)W_N^{kn}$.
4. "Smuggle out" $\Delta t$ and rename $f(t_n)\to x(n)$, $F_a\to X(k)$:

$$\boxed{X(k)=\sum_{n=0}^{N-1}x(n)\,W_N^{kn}}\qquad\text{with}\qquad W_N = e^{-j2\pi/N}$$

**Inverse DFT:**

1. Approximate the ICFT: $f_a(t_n)=\frac1{2\pi}\sum_{k=-N/2}^{N/2-1}F_a(j\omega_k)e^{j\omega_kt_n}\Delta\omega$.
2. **The upper limit excludes $N/2$** because on the circular frequency scale **$-N/2$ and $N/2$ are the same point**. Shift the sum to $0\ldots N-1$.
3. With $\Delta\omega=2\pi/(N\Delta t)$: $f_a(t_n)=\frac{1}{N\Delta t}\sum_{k=0}^{N-1}F_a(j\omega_k)e^{j\omega_kt_n}$.
4. Put $\Delta t$ back and rename:

$$\boxed{x(n)=\frac1N\sum_{k=0}^{N-1}X(k)\,e^{j\frac{2\pi}{N}kn}=\frac1N\sum_{k=0}^{N-1}X(k)\,W_N^{-kn}}$$

- **Where the $1/N$ goes:** in this convention (van Drongelen and MATLAB `fft`), the forward DFT has **no** $1/N$ and the inverse has $1/N$. That is why spectra are normalized by $N$ (power $XX^{\ast}/N$, amplitude $\frac{2}{N}\lvert X\rvert$).
- **Sample counting:** each time sample represents the preceding sample interval. Depending on convention, the first sample is the **zeroth** ($0\ldots N-1$) or the **first** ($1\ldots N$).

**The circular frequency scale (Fig 6.1 / Ch 6):**

- The discrete spectrum is **periodic** (period $F_s$, or $2\pi$ in normalized angle). Picture it on a **circle**.
- Going round the circle: **$0\to\pi$ are positive frequencies** and **$\pi\to2\pi$ are negative frequencies**. $\pi$ corresponds to the **Nyquist frequency**.
- Bin $k$ corresponds to $f_k = k\,F_s/N$ for $k< N/2$. Bins $k>N/2$ correspond to $(k-N)F_s/N$ (negative).
- The DFT gives **real (even) and imaginary (odd) parts**. The **power spectrum** $a^2+b^2$ is **even**: the negative-frequency half **mirrors** the positive half. **So only the first half (up to Nyquist) is usually shown.**

**Epoch/sampling examples (Ch 6, Fig 7.1; Q20 changed these numbers):**

| Epoch $T$ | Sampling | Precision $1/T$ | Range $F_s/2$ |
|---|---|---|---|
| 10 s | $\Delta t=0.5$ s ($F_s=2$ Hz) | **0.1 Hz** | full circle 2 Hz, shown up to **1 Hz** |
| **0.5 s** | **1 kHz** (1 ms) | **2 Hz** | **500 Hz** |
| **5 s** | **200 Hz** (5 ms) | **0.2 Hz** | **100 Hz** |

**Rules that follow:**

- **Longer epoch gives better (finer) precision.** Sampling rate does **not** change precision.
- **Higher sampling rate gives a wider range.** Epoch length does **not** change range.
- Number of positive-frequency bins $= N/2$ = range/precision $= (F_s/2)\,T$.

### D5. The twiddle factor $W_N$ 🔥 (Q19)

$$W_N = e^{-j\frac{2\pi}{N}},\qquad W_N^{m}=e^{-j\frac{2\pi}{N}m}$$

- $W_N^m$ is a point on the **unit circle**. Increasing the power by 1 steps **clockwise** by $2\pi/N$.
- **Periodic:** $W_N^{m}=W_N^{m+N}$. **A full cycle takes $N$ steps.** $\theta=0$ and $\theta=2\pi$ give the identical value $1+j0$.
- **$N=4$:** $W_4^0=1$, $W_4^1=-j$, $W_4^2=-1$, $W_4^3=+j$, $W_4^4=1$. So $W_4^0=W_4^4$, $W_4^1=W_4^5$, $W_4^2=W_4^6=-1$ (slide), and $W_4^3=W_4^7$.
- **$N=8$:** $W_8^0=W_8^8$, $W_8^2=W_8^{10}$, etc. (cycle of 8).
- It appears in **both** the DFT ($W_N^{kn}$) and the inverse DFT ($W_N^{-kn}$).
- **Its periodicity is what makes the FFT efficient** (terms can be combined).

**Quick check:** $W_4^{6}=e^{-j\frac{2\pi}{4}\cdot 6}=e^{-j3\pi}=e^{-j\pi}=-1$ ✓. $W_4^{4}=e^{-j2\pi}=1$ ✓.

### D6. The fast Fourier transform (FFT) 🔥 (Q18)

- **Cooley and Tukey, 1965.** It uses the **periodicity of the twiddle factor** to **combine terms** and reduce the number of computationally demanding **multiplications**.
- **Cost:** direct DFT needs **$N^2$** multiplications. FFT needs **$N\log_2 N$**.
  - $N=1024$: $N^2 = 1{,}048{,}576$ vs $N\log_2N=10{,}240$, about **100× fewer**.
  - $N=8$: 64 vs 24.
- **$N=4$ example (why it works):** split the sum into even and odd samples,

$$X(k)=\sum_{r=0}^{1}x(2r)\,W_4^{2rk}+\sum_{r=0}^{1}x(2r+1)\,W_4^{(2r+1)k},\qquad W_4^{(2r+1)k}=W_4^{2rk}\,W_4^{k}$$

$$X(k)=\big[x(0)+x(2)W_4^{2k}\big]+W_4^{k}\big[x(1)+x(3)W_4^{2k}\big]$$

  - $X(0)=[x(0)+x(2)W_4^0]+W_4^0[x(1)+x(3)W_4^0]$
  - $X(1)=[x(0)+x(2)W_4^2]+W_4^1[x(1)+x(3)W_4^2]$
  - $X(2)=[x(0)+x(2)W_4^4]+W_4^2[x(1)+x(3)W_4^4]$
  - $X(3)=[x(0)+x(2)W_4^6]+W_4^3[x(1)+x(3)W_4^6]$
  - Since $W_4^4=W_4^0$ and $W_4^6=W_4^2$, the bracketed sub-sums computed for $X(0), X(1)$ are **reused** for $X(2), X(3)$. Applied recursively (halving each time), this gives $N\log_2N$.
- **What the FFT is not:** not an approximation of the DFT (same result; the lab shows max difference ≈ 0), not a filter, not hardware, and it does not work on continuous signals. Classic FFT implementations are fastest for $N$ a **power of 2**.

### D7. Power, amplitude and phase spectra 🔥

$$\text{Power spectrum: } S=\frac{X\,X^{\ast}}{N}=\frac{\lvert X\rvert^2}{N},\qquad \text{Amplitude spectrum: } AS=\frac{2}{N}\sqrt{X\,X^{\ast}}=\frac{2}{N}\lvert X\rvert,\qquad \text{Phase: } \varphi=\arctan\frac{\mathrm{Im}(X)}{\mathrm{Re}(X)}$$

- The **amplitude spectrum is the square root of the power spectrum** (up to normalization).
- **Why $2/N$:** $1/N$ undoes the unnormalized forward DFT. The **factor 2** is needed because a sinusoid's energy is split equally between the $+f$ and $-f$ bins, and we show only one side. Then a sine of amplitude 8 shows a peak of height 8 (lab `FastFourierTransformm`: amplitudes 2, 3, 8, 3 at 4, 6, 8, 10 Hz).
- **Phase needs no normalization** (a ratio of imaginary to real, so scaling cancels).
- **Power spectrum = power vs frequency** (not vs time). It can be computed from FFT results.

### D8. Finite epochs, windowing and spectral leakage 🔥 (Q21)

**The problem:** analysing $N$ samples **implicitly multiplies** the (theoretically infinite) signal by a **rectangular window**. **Multiplication in time equals convolution in frequency**, so the true spectrum gets **convolved with the window's spectrum**.

**The cosine example (Fig 7.5):** an infinite $\cos(\omega_0 t)$ (spectrum: two impulses at $\pm\omega_0$) times a rectangular window $w_R(t)$ (spectrum $W_R(j\omega)$: a main lobe plus ripples) gives a truncated cosine whose spectrum is **two copies of $W_R$ centred at $\pm\omega_0$**. Instead of clean lines you see **peaks with side ripples**: energy "leaks" into neighbouring frequencies.

**Ripple spacing (Fig 7.4):** the rectangular window's spectrum has ripples at intervals of **$1/T$**:

| $T$ | Ripple spacing |
|---|---|
| 1 s | 1 Hz |
| 2 s | 0.5 Hz |
| 4 s | **0.25 Hz** |

A longer window gives a narrower main lobe and closer ripples. This is why the discrete spectrum of a pure $\cos(2\pi ft)$ shows **energy adjacent to the main peak**.

**Commonly used windows (Table 7.2, epoch $-T\to T$):**

| Window | $w(t)$ for $\lvert t\rvert\le T$ (0 elsewhere) | Edges | Notes |
|---|---|---|---|
| **Rectangular** | $1$ | Abrupt | Narrowest main lobe, **largest sidelobes/ripples** (most leakage) |
| **Bartlett** (triangular, Fejér) | $1-\dfrac{\lvert t\rvert}{T}$ | Goes to 0 linearly | Moderate |
| **Hann** (von Hann, "hanning") | $0.5+0.5\cos\left(\dfrac{\pi t}{T}\right)$ | **Goes to 0** smoothly | Low leakage, wider main lobe |
| **Hamming** | $0.54+0.46\cos\left(\dfrac{\pi t}{T}\right)$ | **Does not reach 0** (0.08 at edges) | Very low first sidelobe |

- All tapered windows equal 1 at the centre ($t=0$).
- **Trade-off (background):** tapering reduces leakage (sidelobes) but **widens the main lobe** (poorer ability to separate close frequencies) and reduces the effective amplitude.
- The **Gaussian envelope** in the labs ($e^{-t^2/2\sigma^2}$) is another smooth taper. It localizes the signal in time and gives a smooth, bell-shaped spectrum.

**EEG example (Fig 7.3):** a trace from **O2** with strong alpha. Its power spectrum shows a clear peak **slightly below 10 Hz** (the alpha rhythm), smoothed with a **1.5 Hz rectangular window in the frequency domain** for clarity. It also shows a large low-frequency component near 0 Hz.

### D9. Spectral analysis of physiological signals 🔥 (Q21)

Spectra of pure sine waves are simple. **Physiological spectra need caution** because:

1. The signals are **rarely stationary**.
2. They contain **nonperiodic and periodic** components.
3. Even after **removing DC**, **low-frequency power** can come from **slow nonperiodic trends** or from **periodic activity with a period longer than the analysis window**.
4. **High-frequency power** can be contaminated by **sudden nonperiodic events** (transients, spikes, artifacts).
5. Periodic activity is **rarely purely sinusoidal**, which produces **harmonics** at integer multiples of the fundamental.

**Neonatal respiration example (Fig 7.7):** main peak at **1.5 Hz** (breathing rate, i.e., 90 breaths/min) and a smaller peak near **3 Hz**, a **harmonic** caused by the **imperfectly sinusoidal** waveform.

**Traps:** "Harmonics occur only with a DC offset" ✗. "A peak at 3 Hz must be a separate physiological process" ✗ (check for integer multiples first). "Physiological signals are stationary so window choice doesn't matter" ✗.

### Part D — Practice MCQs (select all correct)

**D-1.** An EEG epoch of 4 s is sampled at 250 Hz. Which are correct?
- A. $N = 1000$ samples.
- B. Frequency precision is 0.25 Hz.
- C. The highest frequency shown in a one-sided spectrum is 125 Hz.
- D. Doubling the sampling rate to 500 Hz improves precision to 0.125 Hz.
- E. The number of positive-frequency bins up to Nyquist is 500.

> **Answer: A, B, C, E.**
> - B ✓: $1/4$ Hz.
> - C ✓: $250/2$.
> - D ✗: precision depends only on $T$. Doubling $F_s$ doubles the range (250 Hz), not the precision.
> - E ✓: $N/2 = 125/0.25 = 500$.

**D-2.** You need to separate two alpha peaks at 9.5 Hz and 10.0 Hz. Which choices are adequate?
- A. A 1-s epoch at 1000 Hz.
- B. A 2-s epoch at 100 Hz.
- C. A 4-s epoch at 64 Hz.
- D. A 0.5-s epoch at 4000 Hz.
- E. Precision is set by $1/T$, so $T\geq 2$ s is needed at minimum.

> **Answer: B, C, E.**
> - Need $\Delta f\le 0.5$ Hz, so $T\ge2$ s. A gives 1 Hz and D gives 2 Hz, both too coarse no matter how high $F_s$ is. With leakage, longer than the minimum is better in practice.

**D-3.** Fourier series:
- A. For an even periodic function, all $b_n$ are zero.
- B. For an odd periodic function, all $a_n$ (including $a_0$) are zero.
- C. $a_0 = \frac{1}{T}\int_T f(t)\,dt$.
- D. The derivation uses the orthogonality of sines and cosines over a full period.
- E. The integral $\int_T\cos^2(n\omega t)\,dt = T/2$.

> **Answer: A, B, D, E.**
> - C ✗: $a_0=\frac{2}{T}\int_T f\,dt$. The **DC term** is $\frac12 a_0 = \frac1T\int_T f\,dt$.

**D-4.** For a zero-mean symmetric triangle wave of amplitude $A$ peaking at $t=0$:
- A. $a_0 = 0$.
- B. $b_n = 0$ for all $n$.
- C. Only even harmonics are present.
- D. Harmonic amplitudes decrease proportionally to $1/n^2$.
- E. $a_3 = a_1/9$.

> **Answer: A, B, D, E.**
> - C ✗: only **odd** harmonics.
> - E ✓: $a_n\propto1/n^2$, so $a_3=a_1/9$.

**D-5.** Complex Fourier series:
- A. $c_n = \frac{1}{T}\int_T f(t)e^{-jn\omega t}dt$.
- B. For real signals, $c_{-n}$ is the complex conjugate of $c_n$.
- C. The magnitude of $c_n$ carries amplitude and its angle carries phase.
- D. The sum runs only over non-negative $n$.
- E. The complex form is obtained from the real form using Euler's relation.

> **Answer: A, B, C, E.**
> - D ✗: it runs over $-\infty$ to $\infty$.

**D-6.** Fourier transform pairs:
- A. A Dirac impulse in time has a flat spectrum.
- B. A constant (DC) signal has a spectrum that is an impulse at zero frequency.
- C. $\cos(\omega_0 t)$ transforms to impulses at $\pm\omega_0$ with weight $\pi$.
- D. $\sin(\omega_0 t)$ transforms to purely real impulses at $\pm\omega_0$ of the same sign.
- E. A shorter event in time generally occupies a broader frequency range.

> **Answer: A, B, C, E.**
> - D ✗: they are **imaginary** and of **opposite sign**: $j\pi[\delta(\omega+\omega_0)-\delta(\omega-\omega_0)]$.

**D-7.** Twiddle factor $W_N=e^{-j2\pi/N}$:
- A. $W_8^{3}=W_8^{11}$.
- B. $W_4^{2}=-1$.
- C. $W_4^{1}=j$.
- D. The periodicity of $W_N$ allows terms in the DFT to be combined.
- E. $W_N^{kn}$ appears in the forward DFT and $W_N^{-kn}$ in the inverse DFT.

> **Answer: A, B, D, E.**
> - A ✓: period 8.
> - C ✗: $W_4^1=e^{-j\pi/2}=-j$ (the **negative** exponent gives clockwise rotation). $W_4^3 = +j$.

**D-8.** DFT/FFT computation:
- A. For $N=2048$, the FFT requires about $2048\times11$ multiplications.
- B. The direct DFT requires about $N^2$ multiplications.
- C. The FFT gives a slightly less accurate spectrum than the DFT.
- D. The FFT was introduced by Cooley and Tukey in 1965.
- E. The FFT is used to compute power spectra.

> **Answer: A, B, D, E.**
> - A ✓: $\log_2 2048 = 11$.
> - C ✗: same result, just faster.

**D-9.** Spectra:
- A. The amplitude spectrum is $\frac{2}{N}\sqrt{XX^{\ast}}$.
- B. The phase spectrum requires normalization by $N$.
- C. The power spectrum is $XX^{\ast}/N$.
- D. The power spectrum of a real signal is symmetric about zero frequency.
- E. Because of that symmetry, spectra are often shown only up to the Nyquist frequency.

> **Answer: A, C, D, E.**
> - B ✗: phase needs **no** normalization.

**D-10.** A pure 10 Hz cosine is recorded for exactly 1 s with a rectangular window, but the true frequency is 10.3 Hz. Which statements are correct?
- A. The spectrum shows energy spread to bins adjacent to 10 Hz.
- B. The spread is caused by convolution of the true spectrum with the window spectrum.
- C. The ripples in the window spectrum are spaced by 1 Hz.
- D. A Hann window would reduce side ripples.
- E. Increasing the sampling rate removes the leakage.

> **Answer: A, B, C, D.**
> - E ✗: leakage depends on the window length and shape, not on $F_s$.

**D-11.** Physiological spectra:
- A. A slow trend can create low-frequency power even after DC removal.
- B. Periodic activity with a period longer than the analysis window can appear as low-frequency power.
- C. Sudden transients can contaminate high frequencies.
- D. A peak at twice the respiratory frequency may be a harmonic.
- E. Harmonics only appear if the waveform is perfectly sinusoidal.

> **Answer: A, B, C, D.**
> - E ✗: reversed. Harmonics appear because the waveform is **not** purely sinusoidal.

**D-12.** Window functions:
- A. The Hann window is $0.5+0.5\cos(\pi t/T)$.
- B. The Hamming window reaches exactly zero at its edges.
- C. The Bartlett window is triangular.
- D. The rectangular window is 1 inside the epoch and 0 outside.
- E. All three tapered windows equal 1 at the centre of the epoch.

> **Answer: A, C, D, E.**
> - B ✗: Hamming reaches $0.54-0.46=0.08$.

---

## Part E — Noise, Random Processes, Stationarity, Ergodicity, SNR 🔥

### E1. Where noise comes from 🔥

| Type | Examples (slides) | Character |
|---|---|---|
| **Man-made** | Artifacts from **switching instruments**; **50–60 Hz hum from power lines** | Often **nonrandom / periodic** |
| **Random, from equipment** | **Thermal noise from resistors** in the measurement chain | Unpredictable, but **describable by statistics** |
| **Measurement-procedure noise** | **Systematic bias** (e.g., "measuring appetite after dinner") or **random measurement noise** (e.g., thermal noise added by recording equipment) | Bias shifts the mean; random noise adds variance |
| **Dynamical noise** | **Intrinsic** to the process, e.g., **temperature fluctuations** during membrane-potential measurement that **physically influence the processes** determining the potential | Interacts with the process |

### E2. Measurement (additive) noise vs dynamical noise 🔥 (Q22)

**Measurement noise, Eq. (1):**

$$M_i = x_i + N_i,\qquad x_i = 0.8\,x_{i-1}+3.5$$

- The **process $x$ is deterministic**. Only its **measurement** $M$ is corrupted by independent noise $N_i$.
- The noise at step $i$ does **not** affect $x_{i+1}$.
- Side calculation: $x_i$ converges to the fixed point $x^\ast = 3.5/(1-0.8) =$ **17.5**.

**Dynamical noise, Eq. (2):**

$$M_i = x_i + N_i,\qquad x_i = \left[0.8\,x_{i-1}+3.5\right] + D_{i-1}$$

- The noise $D$ **enters the state**: a kick at step $i-1$ changes $x_i$, which carries into $x_{i+1}$ (multiplied by 0.8), and so on. Noise is **remembered**.
- So the process is **stochastic**: it has a deterministic component, but noise is **part of the process itself**.
- **Consequence visible in the plot (Fig 3.1):** because sequential values become **correlated**, dynamical noise produces **slower trends / wandering** compared with a series with only additive noise, which looks like fast, independent jitter around the deterministic value.

> **Why use dynamical noise terms at all?** Often we do not know all the details needed to model a physiological system's complex interactions. The random term is a **statistical proxy for what we don't know**.

**Intuition via analogy:** measurement noise is a shaky camera filming a steady walker (the walker's path is fine, the video jitters). Dynamical noise is a walker being randomly pushed: each push changes where the walker is from then on, so the path drifts.

### E3. Describing randomness: PDF, CDF, survival function 🔥

- A **probability density function (PDF)** $p(x)$ describes how likely particular values of $x(t)$ are. It is normalized:

$$\int_{-\infty}^{\infty}p(x)\,dx = 1$$

- **Cumulative distribution function:** $F(x)=\int_{-\infty}^{x}p(y)\,dy$, the probability that the value is $\le x$. It rises from 0 to 1.
- **Survival function:** $S(x) = 1-F(x)=\int_{x}^{\infty}p(y)\,dy$, the probability that the value is $>x$.

**Slide examples (Fig 3.2):**

| | Distribution | Shape |
|---|---|---|
| A | **Fair die** (discrete) | $p(1)=\dots=p(6)=1/6$, zero elsewhere |
| B | **Continuous uniform** on 0–6 | Flat; every value in range equally likely (height $1/6$) |
| C | **Normal (Gaussian)** | Most values near the mean; extremes less likely |

### E4. Ensembles, stationarity and ergodicity 🔥 (Q23, Q24)

- **Sample function:** one observed series, i.e., **one instance** of the random process (one trial or one recording).
- **Ensemble:** the **collection of sample functions**.
- The slide shows each sample function with its **amplitude distribution histogram**. Similar histograms across sample functions make **stationarity a reasonable assumption**.

**Stationary process:** the **distribution from which $x(t)$ originates does not change over time**. (The values change; the **statistics** do not.)

**Ergodic process:** **any particular sample function is representative of the whole ensemble**, so **statistics can be obtained from averages over time** (one long recording) instead of averages across many realizations.

**If stationary and ergodic**, estimate the mean and variance from **any single** sample function:

$$\hat{x}=\frac1N\sum_{i=1}^{N}x_i,\qquad \widehat{\mathrm{Var}}(x)=\frac1N\sum_{i=1}^{N}(x_i-\hat{x})^2$$

**Practical reality:** stationarity and ergodicity are frequently (often implicitly) **assumed**, and **many techniques are useful even when these assumptions are not strictly met**.

**Understanding the difference (examples):**

| Example | Stationary? | Ergodic? | Why |
|---|---|---|---|
| Thermal noise in a resistor | Yes | Yes | Same statistics at all times; one long record represents all |
| Each trial is a random constant $c$ (different per trial), i.e., $x(t)=c$ | Yes (distribution does not change in time) | **No** | A time average of one trial gives just its own $c$, not the ensemble mean |
| EEG over hours (sleep–wake changes) | **No** | — | Statistics drift |
| A few seconds of resting EEG | **Approximately** | Assumed | Short-term quasi-stationarity |

**Traps:** "stationary means $x(t)$ is constant" ✗. "stationary means deterministic" ✗. "ergodic implies zero variance" ✗. "ergodic means each sample function has a different PDF" ✗. "ergodicity means only average across trials, never over time" ✗.

### E5. Signal-to-noise ratio 🔥

Every measurement is corrupted by at least a small amount of **thermal noise** from analog instruments (amplifiers, analog filters).

$$ms=\frac1N\sum_{i=1}^{N}x_i^2\quad(\text{mean squared amplitude, i.e. power}),\qquad rms=\sqrt{\frac1N\sum_{i=1}^{N}x_i^2}$$

$$SNR=\frac{ms(\text{signal})}{ms(\text{noise})},\qquad SNR_{dB}=10\log_{10}\frac{ms(\text{signal})}{ms(\text{noise})}$$

- **The dB scale has no physical dimension.** It is just the log of a ratio.
- The **SNR without the log** is sometimes used as a **figure of merit (FOM)** by manufacturers.
- **If SNR ≈ 1 or < 1, signal processing can help increase SNR in special cases** (e.g., averaging, filtering when signal and noise occupy different bands).

**Power vs amplitude ratios (a classic numeric trap):**

$$SNR_{dB}=10\log_{10}\frac{P_s}{P_n}=20\log_{10}\frac{rms_s}{rms_n}$$

| rms ratio | Power ratio | dB |
|---|---|---|
| 1 | 1 | 0 dB |
| 2 | 4 | +6 dB |
| 10 | 100 | +20 dB |
| 0.5 | 0.25 | −6 dB |
| $\sqrt{10}\approx3.16$ | 10 | +10 dB |

**Useful facts:** a sine of amplitude $A$ has $ms = A^2/2$ and $rms = A/\sqrt2$. For zero-mean noise, $ms$ equals the **variance** $\sigma^2$ and $rms=\sigma$.

**Worked example:** EP signal rms = 5 µV, background EEG noise rms = 50 µV. SNR = $(5/50)^2 = 0.01$, i.e., **−20 dB**. The signal is invisible in single trials.

### E6. Amplitudes of biopotentials and noise (Fig 3.5) ⭐

Log amplitude scale (volts):

| Level | Signals | Noise |
|---|---|---|
| $10^{-7}$–$10^{-6}$ V (0.1–1 µV) | **Evoked potentials (EP)** | **Quantization noise** (~$10^{-6}$) |
| ~$10^{-5}$ V (10 µV) | **EEG** (tens to ~100 µV) | **Amplifier noise** (~$10^{-5}$) |
| ~$10^{-4}$–$10^{-3}$ V | **EMG/ECG** (~mV) | **Giga-seal** noise (patch clamp, ~$10^{-4}$–$10^{-3}$) |
| ~$10^{-3}$ V | — | **Hum** (~mV, the largest) |
| $10^{-2}$–$10^{-1}$ V | **Intracellular signals** (tens of mV) | — |

- EP, EEG and EMG/ECG are **extracellular** signals.
- **"Enemy #1 in any recording of biopotentials is hum."** Hum is **nonrandom** (periodic), and it can even **spoil signal averaging** (see F4).
- Noise amplitudes are often comparable to the biopotentials, so **noise-reduction strategies are required**.

### Part E — Practice MCQs (select all correct)

**E-1.** Consider $x_i=0.8x_{i-1}+3.5$ with $M_i=x_i+N_i$ ($N_i$ white).
- A. The underlying process is deterministic.
- B. $x_i$ converges to 17.5.
- C. $N_i$ at one step influences $x_{i+1}$.
- D. If a noise term $D_{i-1}$ is added inside the recursion, the process becomes stochastic.
- E. Adding $D_{i-1}$ inside the recursion produces smoother, slower fluctuations than adding the same noise only to $M_i$.

> **Answer: A, B, D, E.**
> - C ✗: measurement noise does not feed back into the state.

**E-2.** Stationarity and ergodicity:
- A. A stationary process has statistics that do not change over time.
- B. An ergodic process allows time averages to replace ensemble averages.
- C. A process can be stationary but not ergodic.
- D. EEG recorded over a full night is a good example of a stationary process.
- E. Many analysis techniques remain useful when stationarity is only approximately satisfied.

> **Answer: A, B, C, E.**
> - D ✗: long-term EEG is **non-stationary** (sleep stages).

**E-3.** SNR:
- A. A signal rms of 20 µV and noise rms of 10 µV give SNR ≈ 6 dB.
- B. The same values give a power SNR of 4.
- C. SNR in dB has units of volts.
- D. SNR (not in dB) is sometimes used as a figure of merit.
- E. When SNR < 1, no processing can ever recover the signal.

> **Answer: A, B, D.**
> - C ✗: dimensionless.
> - E ✗: averaging can help in special cases.

**E-4.** PDFs:
- A. The area under a PDF equals 1.
- B. The survival function equals $1-F(x)$.
- C. For a fair die, each outcome has probability 1/6.
- D. For a uniform continuous distribution on 0–6, some values are more likely than others.
- E. The cumulative function is obtained by integrating the PDF from $-\infty$ to $x$.

> **Answer: A, B, C, E.**
> - D ✗: all values are equally likely.

**E-5.** Noise sources:
- A. Thermal noise from resistors is random.
- B. 50 Hz hum is random noise with zero mean and no structure.
- C. Measuring appetite after dinner is an example of systematic bias.
- D. Hum is described as "enemy #1" in biopotential recordings.
- E. Evoked potentials can be smaller than amplifier noise.

> **Answer: A, C, D, E.**
> - B ✗: hum is **periodic / nonrandom**.
> - E ✓: EPs are ~$10^{-7}$–$10^{-6}$ V, and amplifier noise is ~$10^{-5}$ V.

---

## Part F — Signal Averaging, Noise Estimates, Evoked Potentials 🔥

### F1. The four assumptions of signal averaging 🔥 (Q25)

Signal averaging estimates **low-amplitude signals buried in noise**. It usually assumes:

1. **Signal and noise are uncorrelated.**
2. **The timing of the signal is known** (time-locked to a trigger or stimulus).
3. **The signal component is consistent** across repeated measurements.
4. **The noise is truly random with zero mean.**

In reality all four may be violated to some degree, but **averaging is robust to minor violations**.

### F2. Why averaging works: the $\sqrt{N}$ law 🔥

Trial $i$: $M_i(t) = s(t) + n_i(t)$. Average of $N$ trials:

$$\bar M(t)=\frac1N\sum_{i=1}^N M_i(t) = s(t) + \frac1N\sum_{i=1}^N n_i(t)$$

- The **signal** is identical in every trial, so its average is $s(t)$: **unchanged**.
- The **noise** is independent with zero mean and variance $\sigma^2$, so the average has variance $\sigma^2/N$ and **rms $\sigma/\sqrt N$**.

$$\text{Amplitude SNR improves by } \sqrt N,\qquad \text{Power SNR improves by } N\;(\text{i.e. } +10\log_{10}N \text{ dB})$$

| Trials $N$ | Residual noise rms | Power SNR gain |
|---|---|---|
| 4 | $\sigma/2$ | ×4 (+6 dB) |
| 16 | $\sigma/4$ | ×16 (+12 dB) |
| 64 | $\sigma/8$ | ×64 (+18 dB) |
| 100 | $\sigma/10$ | ×100 (+20 dB) |
| **256** (slide figure) | **$\sigma/16$** | ×256 (+24 dB) |

**Diminishing returns:** to halve the residual noise you need **4×** the trials.

**The slide figure (Fig 4.2):** a sine "signal", random noise, a single trial (signal invisible), 256 superimposed trials, the **odd-trial average (blue) and even-trial average (red)** superimposed (they agree, so the result is reproducible), their sum = signal average (green, signal plus small residual noise), and their difference = **± average** (dark blue, residual noise only).

**Worked example:** single-trial SNR (power) = 0.01 (−20 dB). Target SNR = 1 (0 dB). You need a power gain of 100, so **$N=100$** trials. For SNR = 4 (6 dB) you need $N=400$.

### F3. Estimating the residual noise in an average 🔥 (Q26, Q27)

"The ultimate reason to perform signal averaging is to **increase the signal-to-noise ratio**." In real data you do not know the signal or noise separately, so you must **estimate the residual noise**. Three methods:

#### (1) Prestimulus noise

- Use the **epoch before the trigger** as a noise estimate, assuming **the time-locked signal occurs only after the trigger** (e.g., an evoked potential).
- **Does not work** without a clear post-stimulus response window, e.g., a **spike-triggered average** (activity surrounds the spike on both sides).
- **Not necessarily reliable for stimulus-evoked potentials:** with repetitive stimulation, the **late component of one response can still be ongoing in the prestimulus epoch of the next stimulus**, so the "noise" estimate contains signal.
- **Mitigations:** **longer inter-stimulus intervals**, **high-pass filtering** to remove late/slow components, or **another noise estimator**.

#### (2) Bootstrap

- Works well **especially offline** (signals previously recorded and stored).
- Build a **control average** using **random triggers** instead of the true triggers.
- Random triggers **destroy the time-locked alignment**, so the time-locked signal is **not enhanced**. It is **still included** in the data (not removed), just not aligned.
- **Works well when the power of the time-locked component is small relative to the noise**, which is usually the case (that is why you average in the first place).
- Repeat many times to get a **series of control averages**. Compare their statistics with the "true" average to **validate** it (a statistical test: is the true average larger than what random alignment produces?).

#### (3) ± average (plus-minus average)

- Use **the same epochs** as the true average, but **invert every other trial** before averaging:

$$\bar M_{\pm}(t)=\frac1N\sum_{i=1}^{N}(-1)^{i}M_i(t)$$

- The **consistent signal cancels** (alternating + and −, with an even $N$).
- The **residual noise is maintained**. Its **rms equals that of the standard average**, because an inverted random noise sample has **the same distribution** as a non-inverted one (Fig 4.3: sum $X+Y$ and difference $X-Y$ of two random series have identical histograms).
- It is efficient: no extra data or prestimulus window needed.

**Comparison:**

| | Prestimulus | Bootstrap | ± Average |
|---|---|---|---|
| Data used | Pre-trigger segment | Random trigger positions | Same trials, alternate inversion |
| Key assumption | Signal only after trigger | Time-locked power ≪ noise | Signal identical across trials; noise symmetric |
| Fails when | Late responses overlap next pre-stimulus; spike-triggered averages | Signal power is large relative to noise | Signal changes across trials (e.g., habituation, latency jitter) or $N$ is odd |
| Best for | Evoked potentials with long ISIs | Offline stored data; statistical validation | Quick residual-noise estimate (e.g., CNV) |

### F4. Nonrandom (periodic) noise and the stimulus rate 🔥 (Q28)

Averaging relies on noise being **random, zero-mean, and unrelated to the signal**. **Periodic noise (hum)** breaks this if it is **phase-locked to the stimulus**.

**Slide figure (Fig 4.5):** 50 Hz hum.

- **10 Hz stimulus rate:** the interval is 100 ms = exactly **5 hum cycles**. Every stimulus lands on the **same hum phase** (black dots), so the hum adds **coherently**, like a signal. **The average contains a large 50 Hz component.**
- **7.7 Hz stimulus rate (noninteger):** the interval is ≈129.9 ms ≈ 6.49 hum cycles. The **relative phase changes with each stimulus** (red dots), so the hum **averages out**.

**Remedies (slide):** **randomize the stimulus interval** or use a **noninteger stimulus rate**.

**Deeper rule (for tricky numeric options):** hum survives averaging when the phase advance per stimulus, $f_{hum}/f_{stim}$, is a **whole number** (every trigger lands on the same phase).

| Stimulus rate | 50 Hz hum: $50/f_{stim}$ | Outcome |
|---|---|---|
| 10 Hz | 5 (integer) | **Locks**, so hum stays |
| 25 Hz | 2 | **Locks** |
| 12.5 Hz | 4 | **Locks** (a noninteger rate that still locks!) |
| 7.7 Hz | 6.49 | Phase drifts, so hum cancels |
| 20 Hz | 2.5 | Phase alternates 0/π, so hum cancels |
| 3 Hz | 16.67 | Drifts, so hum cancels |

For 60 Hz hum: 10 Hz (6), 15 Hz (4), 7.5 Hz (8) all lock. The slide rule "use a noninteger rate" is a **rule of thumb**. Randomizing intervals is the safest remedy.

### F5. Characteristics of background EEG 🔥 (Q29)

- **Frequency range: 0.01 to 100 Hz.**
- **Amplitudes: typically around 100 µV.**
- **Power spectral density follows a power law** (roughly $1/f^\alpha$: more power at low frequencies).
- **Five bands: delta, theta, alpha, beta, gamma.**
- **EEG is considered stochastic** because genuine measurements are **limited**.
- **Long-term EEG is non-stationary.** **Short-term EEG can be approximately stationary.**
- Stationary window lengths vary, **typically several seconds to minutes**.
- The most frequent physiological contaminants are **ocular (EOG), muscular (EMG) and cardiac (ECG)** artifacts (Urigüen 2015 figure).

### F6. Evoked potentials (EPs) ⭐

- EPs are **commonly used in clinical diagnosis** and are the showcase application of signal averaging.
- Recorded with EEG electrodes in response to stimulation of the:
  - **auditory** system (**AEP**, e.g., clicks in each ear, recorded A1–Cz / A2–Cz),
  - **visual** system (**VEP**),
  - **somatosensory** system (**SEP**).
- These capture the **primary perception** process.
- **Specialized EPs** capture more complex tasks:
  - **Oddball paradigm:** frequent baseline stimuli occasionally interrupted by a **rare** test stimulus. The rare stimulus elicits a **centrally located positive wave at ~300 ms**, the **P300**, interpreted as a neural response to **stimulus novelty**.
  - **Contingent negative variation (CNV):** a **warning stimulus** (usually a short tone burst) announces an imminent **second stimulus** (continuous tone or light flashes) that the subject must **turn off with a button press**. **Between the warning and the second stimulus**, a **centrofrontal negative wave** develops (measured at **Cz**). The CNV is **weak relative to ongoing EEG**, so it **requires averaging**. The slide shows that **32 trials** clearly reveal the negative slope, and the **± average** serves as the residual-noise estimate.

| | P300 | CNV |
|---|---|---|
| Paradigm | Oddball (rare vs frequent) | Warning stimulus, then imperative stimulus with button press |
| Polarity | **Positive** | **Negative** |
| Timing | ~**300 ms** after the rare stimulus | **Between** the two stimuli (anticipation) |
| Location | **Central** | **Centrofrontal**, measured at **Cz** |
| Interpretation | Novelty | Expectation / preparation |

### Part F — Practice MCQs (select all correct)

**F-1.** An evoked response of 2 µV is buried in EEG noise with rms 20 µV (random, zero mean). Which are correct?
- A. After 100 trials, the residual noise rms is 2 µV.
- B. After 100 trials, the amplitude SNR is 1.
- C. To halve the residual noise from that point you need 400 trials in total.
- D. Averaging reduces the signal amplitude by $\sqrt N$ as well.
- E. The power SNR improves by a factor of 100 with 100 trials.

> **Answer: A, B, C, E.**
> - A ✓: $20/\sqrt{100}=2$.
> - C ✓: quadruple the trials.
> - D ✗: the time-locked signal is **preserved**.

**F-2.** Assumptions of averaging:
- A. Signal and noise are uncorrelated.
- B. Signal latency may vary randomly across trials without any effect.
- C. Noise is random with zero mean.
- D. The trigger timing relative to the signal is known.
- E. The technique tolerates minor violations of the assumptions.

> **Answer: A, C, D, E.**
> - B ✗: latency jitter violates "consistent signal / known timing". It **smears and reduces** the averaged waveform.

**F-3.** The ± average:
- A. Inverts every other trial before averaging.
- B. Removes the consistent signal component.
- C. Produces residual noise with a larger rms than the standard average.
- D. Uses the same epochs as the true average.
- E. Relies on random noise having the same distribution when inverted.

> **Answer: A, B, D, E.**
> - C ✗: the rms is the **same**.

**F-4.** Bootstrapping:
- A. Uses random triggers to build control averages.
- B. Removes the time-locked signal from the data.
- C. Is particularly suitable for offline analysis.
- D. Can be repeated to build a distribution of control averages for statistical validation.
- E. Works best when the time-locked signal power is large compared with noise.

> **Answer: A, C, D.**
> - B ✗: the signal is still in the data, just not aligned.
> - E ✗: it works best when the signal power is **small**.

**F-5.** Prestimulus noise estimation:
- A. Is invalid for a spike-triggered average where activity surrounds the trigger.
- B. May be contaminated by late responses from the previous stimulus.
- C. Can be improved with longer inter-stimulus intervals.
- D. Can be improved by high-pass filtering slow components.
- E. Is always the preferred estimator.

> **Answer: A, B, C, D.**
> - E ✗.

**F-6.** A lab in Europe (50 Hz mains) records auditory EPs. Which stimulus-rate choices risk a strong hum artifact in the average?
- A. 10 Hz.
- B. 25 Hz.
- C. 7.7 Hz.
- D. Randomized intervals with mean 8 Hz.
- E. 12.5 Hz.

> **Answer: A, B, E.**
> - $50/10=5$, $50/25=2$ and $50/12.5=4$ are whole numbers of hum cycles per interval, so every trigger hits the same phase. 7.7 Hz and randomized intervals shift the phase.

**F-7.** Evoked potentials:
- A. The P300 is a positive wave at about 300 ms elicited by rare stimuli in an oddball paradigm.
- B. The CNV is a positive wave after the button press.
- C. The CNV appears between a warning stimulus and a second stimulus.
- D. AEP, VEP and SEP reflect primary perception processes.
- E. The P300 is interpreted as a response to stimulus novelty.

> **Answer: A, C, D, E.**
> - B ✗: the CNV is **negative** and occurs **before** the second stimulus / response.

**F-8.** Background EEG:
- A. Its power spectrum follows a power law.
- B. It is commonly treated as deterministic.
- C. Its frequency range is about 0.01–100 Hz.
- D. Short segments can be treated as approximately stationary.
- E. Stationary windows are typically milliseconds long.

> **Answer: A, C, D.**
> - B ✗: stochastic.
> - E ✗: several **seconds to minutes**.

---

## Part G — EEG Preprocessing: Line Noise, Multitaper, Referencing, Bad Channels ⭐

### G1. Power line noise and notch filtering 🔥 (Q30)

- **Notch filtering** is used to **eliminate line noise at 50 or 60 Hz** (50 Hz in Europe, 60 Hz in the Americas).
- Implemented with a **certain frequency width** (e.g., **10 Hz**).
- **Successful** at removing line noise **but may distort signal components between 50 and 70 Hz** (i.e., genuine gamma activity near the notch).
- **Can generate transient oscillations in baseline activity** (ringing), which **impacts data interpretation**.
- **Follow-up low-pass filtering below 50 Hz** may address this, **but can alter EEG temporal structures or cause spurious interactions between channels**.
- Note the harmonics: line noise also appears at **120, 180 Hz** (60 Hz mains) or 100, 150 Hz (50 Hz). The slide example (64-channel Biosemi) shows sharp peaks at **60 and 180 Hz**, and a channel with **non-stationary transformer noise** that had to be **interpolated** later.

**Trap:** "Notch filtering is the optimal method" ✗. "Notch filtering cannot distort the signal" ✗.

### G2. Multitaper line-noise removal ⭐

**Goal:** estimate and subtract line noise **without damaging background spectral components** (unlike a notch, which cuts everything in the band).

**Pipeline (slide flowchart):**

1. **Sliding time window** over the EEG, giving a windowed signal.
2. **Multitaper transformation**, giving spectral energy.
3. **Regression**, giving the estimated line-noise magnitude (fit a sinusoid at the line frequency).
4. **Statistical test**: reconstruct the line noise **only if significant**.
5. Move to the next window until the end of the signal.
6. **Any significant noise?** If yes, **subtract the noise from the EEG** and **repeat with the noise-reduced signal**. If no, stop.

**Multitaper method (Cohen-style slide):**

- The time series is multiplied by **several different tapers** (orthogonal window shapes, Slepian/DPSS), each product's **power spectrum** is computed, and the spectra are **averaged**. A standard short-time FFT uses **one** taper (e.g., Hann).
- **Useful for low SNR** situations.
- **Particularly effective for higher-frequency activity** or **single-trial estimates of power**.
- **Less appropriate below ~30 Hz**, because SNR is **already relatively high** at lower frequencies, and the **spectral smoothing** of multitaper **impedes frequency isolation**: activity from **multiple nearby bands can be averaged together**.

**Intuition:** averaging several independent spectral estimates reduces **variance** (a noisy spectrum becomes smoother and more reliable) at the cost of **frequency resolution** (bias/smoothing). This is good for broad gamma bursts, bad for separating 8 Hz from 10 Hz.

### G3. Referencing (Ch 8 slides) 🔥

Covered in C7. Key sentences again, because Q15 came from here:

- Subtract the reference from each channel at the **same time resolution**.
- Choices: **mastoid, specific channel, average of both mastoids, average of all channels (CAR)**.
- The reference must **remain unchanged relative to EEG**, have **comparable amplitude**, and have **no correlation with task-induced activity**.
- **CAR reduces single-point failure impact but suffers from outlier channels.** **Detect and remove bad channels before CAR** ("robust average reference").

### G4. Bad channel detection and interpolation ⭐

**Detection criteria:**

| # | Method | Idea | Decision rule |
|---|---|---|---|
| 1 | **Amplitude** (robust z-score) | Bad channels have **excessively large amplitudes** | Bad if **robust z-score > threshold**. "Robust" = based on median/MAD so the bad channels themselves do not inflate the scale. |
| 2 | **Correlation** | **Normal EEG shows low-frequency correlations across channels** (volume conduction) | **Low-pass filter**, then correlate each channel with the others. Poorly correlated channels are bad. Also try **prediction** of a channel from others (if two bad channels correlate with each other). |
| 3 | **Frequency (noisiness)** | Bad channels have excess high-frequency noise | **Ratio of high-frequency power to low-frequency power**. Bad if **above threshold**. |

**Replacement:** replace bad channels with **virtual healthy channels**, i.e., **reconstruct** the global brain response.

**Interpolation schemes:**

| Scheme | Note |
|---|---|
| **Spherical splines** | **Accurate scalp potential estimation with dense electrode mapping** |
| Higher-order polynomials | — |
| Nearest-neighbour averaging | Simple |
| **Radial basis functions** (statistical) | **Cost-effective, lower computational load** |

**Recommended order:** bad-channel detection, then interpolation, then (robust) average reference. Doing CAR first spreads the bad channel into all others.

### Part G — Practice MCQs (select all correct)

**G-1.** A 50 Hz notch filter with 10 Hz width is applied to EEG containing gamma activity at 55–65 Hz.
- A. The gamma activity near 55 Hz may be distorted.
- B. The filter may create transient oscillations in the baseline.
- C. The filter guarantees the rest of the signal is untouched.
- D. Low-pass filtering below 50 Hz afterwards may alter temporal structure or create spurious inter-channel interactions.
- E. Notch filtering is the only available method for line noise removal.

> **Answer: A, B, D.**
> - C ✗.
> - E ✗: multitaper regression is an alternative.

**G-2.** Multitaper methods:
- A. Average power spectra from several tapers.
- B. Are especially useful at low SNR and higher frequencies.
- C. Provide the best separation of closely spaced low-frequency rhythms (e.g., 8 vs 10 Hz).
- D. Can be used within a regression and statistical test to remove only significant line noise.
- E. Spectral smoothing can mix activity from neighbouring frequency bands.

> **Answer: A, B, D, E.**
> - C ✗: smoothing **impedes** frequency isolation, and it is less appropriate below ~30 Hz.

**G-3.** Bad channel detection:
- A. A robust z-score of channel amplitude above a threshold can flag a bad channel.
- B. Normal EEG channels are uncorrelated at low frequencies, so correlation is not useful.
- C. A high ratio of high- to low-frequency power suggests a bad channel.
- D. Spherical splines are an interpolation scheme giving accurate estimates with dense electrode coverage.
- E. Radial basis function interpolation is computationally cheaper.
- F. Bad channels should be removed or interpolated before computing CAR.

> **Answer: A, C, D, E, F.**
> - B ✗: normal EEG **is** correlated at low frequencies, which is why a lack of correlation flags a bad channel.

---

## Part H — EEG Artifacts and Pattern Recognition 🔥

> The exam gave artifacts **5 of 36** questions. Learn each artifact's **source, frequency, amplitude, spatial distribution, temporal pattern, and how to recognise or confirm it**.

### H1. Classification of artifact sources 🔥 (Q31)

| | **Internal (physiological)** | **External (non-physiological)** |
|---|---|---|
| Sources | **Heart** (ECG, pulse), **eyes** (blinks, movements), **muscles** (EMG: jaw, tongue, scalp), sweat | **Environment** (e.g., **wireless signals**, power lines), **electrode attachment**, **recording equipment** |
| Prevention | **Hard to prevent**: they **permeate** EEG | **Can be inhibited once identified** (fix the electrode, move the phone, shield) |
| Research focus | **Most removal methods target internal artifacts** | Increasingly important as EEG moves to **in-home healthcare systems** |

**Trap:** the exam swaps "internal" and "external" definitions and the "easy to prevent" attribute.

### H2. Ocular artifacts: blinks 🔥 (Q32)

**Physics:** the eye is an electrical **dipole**. The **cornea is positively charged** and the **retina negatively charged** (the corneo-retinal potential).

**Bell's phenomenon:** **during a blink the eyes roll up slightly**, so the **cornea (+) moves closer to the frontal electrodes Fp1 and Fp2**. Those electrodes see a **positive** potential change.

**Recognition:**

- **Very high amplitude**, **strong enough to be clearly visible**.
- **Bifrontal** (Fp1 and Fp2 together, symmetric), **maximal at Fp1/Fp2**, **no field posteriorly** (fades quickly with distance).
- **EEG channels near the eyes are most vulnerable.**
- **Low frequency** (a blink lasts ~200–400 ms), so it contaminates **delta/theta**.

**About polarity wording:** the slides say both "very high amplitude **negative** waveforms in bifrontal regions" and "frontal electrodes see a **positive** signal". Both are describing the same event: the true potential at Fp1/Fp2 is **positive**, and in the clinical EEG display convention (**negative up**) a positive wave is drawn **downward**. In a bipolar chain (Fp1–F3) it appears as a large deflection. For the exam, remember: **eyes roll up, cornea closer to Fp1/Fp2, large bifrontal artifact.**

### H3. Ocular artifacts: lateral eye movements 🔥 (Q33)

- Looking **to the right**: the **right eye's cornea (+) moves toward F8** (right lateral frontal), which becomes **positive**. The **left eye's cornea moves away from F7** (its retina side faces F7), so **F7 becomes negative**.
- Looking **left**: F7 positive, F8 negative.
- **Signature: opposite polarities at F7 and F8.** Strongest at **lateral frontal** electrodes near the outer canthi, **not** at Pz/Oz.
- The polarity follows directly from the **cornea–retina charge separation**.

| | Blink | Lateral eye movement |
|---|---|---|
| Electrodes | **Fp1 and Fp2** (bifrontal) | **F7 and F8** (lateral frontal) |
| Polarity | **Same** on both sides | **Opposite** on the two sides |
| Mechanism | Eyes roll **up** (Bell's), cornea toward Fp1/Fp2 | Corneas rotate **sideways** toward one of F7/F8 |

### H4. Muscle (EMG) artifacts 🔥 (Q34)

- **Originate from muscle contractions in various body parts** (jaw, forehead, neck, scalp, tongue).
- **More diverse forms** than ocular artifacts (no single stereotyped waveform).
- **Detected through the electromyogram (EMG).**
- **Widespread sources** make it challenging to identify their true profiles.
- **Spatial distribution is wider and almost uniform over the entire scalp.**
- **Temporal patterns are often associated with tasks** (e.g., speaking, clenching during effort), so removal is challenging: you may remove task-related brain activity too.
- **Spectral properties vary across sources** and **affect both high- and low-frequency EEG components** (not only high frequencies, although they are most obvious as fast activity in beta/gamma).

**Slide example:** EMG bursts at T7/T8/P8 with spectra showing broadband power extending to 120 Hz, far above the beta band.

### H5. Chewing and hypoglossal (tongue) artifacts ⭐

**Chewing artifact:**

- **Hard to miss:** **sudden onset, intermittent bursts of generalized very fast activity**.
- Originates from the **temporalis muscle** (the slide highlights this in red).
- **Do not confuse** with **generalized periodic fast activity** (an EEG pattern), which is **slightly slower (beta frequency) and lower in amplitude**.

**Hypoglossal (tongue) artifact:**

- **Often seen with chewing artifact**, and arises from **tongue movement** (the tongue is also a dipole: tip negative relative to root).
- Shows **organized**, **synchronous slow, diffuse waves** across all tracings, distinct from slow-wave sleep or seizure patterns.
- **Reproducible:** ask the patient to **move the tongue or say "la la la"** to reproduce the pattern and confirm it.

### H6. Cardiac artifacts ⭐

**ECG artifact:**

- Waveforms **time-locked to the QRS complex** on the ECG channel. Check alignment with the ECG strip.
- **More so or entirely on the left side**, because the **heart lies in the left chest**.
- **Relatively low amplitude**, sharp, repeating at the heart rate (~1–1.5 Hz).
- The slide also warns: **check the display speed** (a page shown at 60 mm/s instead of 30 mm/s) and calibrate the screen before reading.

**Cardioballistic (pulse) artifact:**

- **Much less common.** The **electrode sits just above an artery (arteriole)**, and each **pulsation moves the electrode**, a **motion** artifact.
- Appears as a slow wave about **200 ms after each QRS complex** (the pulse wave's travel delay), usually at one or a few electrodes.

| | ECG artifact | Cardioballistic |
|---|---|---|
| Mechanism | Electrical field of the heart | **Mechanical** motion from arterial pulse |
| Timing | **Simultaneous with QRS** | **~200 ms after QRS** |
| Shape | Sharp, spiky | Slower, rounded |
| Location | Left-sided, often widespread | Focal (electrode over artery) |

### H7. Electrode / electrical artifacts ⭐

- **Electrical artifacts** stem from **60 Hz** (US) or **50 Hz** (Europe) activity in wiring.
- Sources: **electrical appliances**, **cell-phone charging**, etc.
- **Proper electrode placement is crucial** to avoid significant interference. A **bad electrode** (e.g., high impedance at **Fp1**) picks up much more hum than its neighbours, showing thick, dense fast activity in **every derivation that includes that electrode** (Fp1–F7 and Fp1–F3 in the slide). **Notch filtering would greatly reduce it.**
- **Recognition tip:** dense uniform "thick band" at exactly 50/60 Hz, restricted to channels sharing one electrode, points to a **bad electrode**. Present in all channels, suspect the **reference or ground**.

### H8. Sweat artifact ⭐

- **Very slow activity, typically < 0.5 Hz**, **relatively low amplitude**, undulating baseline.
- Arises from the **charge carried by sodium chloride (NaCl) in sweat**, picked up by the electrodes (it changes electrode–skin potentials).
- **No specific localization**: can be **bilateral, unilateral, or focal** to a few electrodes.
- Remedy (background): cool the room, high-pass filter (e.g., 0.5 Hz), re-prep electrodes.

### H9. Artifact master table 🔥

| Artifact | Type | Frequency | Amplitude | Location | Key sign |
|---|---|---|---|---|---|
| **Blink** | Internal (eye) | Low (delta) | **Very high** | **Fp1/Fp2**, bifrontal, symmetric | Bell's phenomenon; cornea + moves closer to Fp1/Fp2 |
| **Lateral eye movement** | Internal (eye) | Low | High | **F7 vs F8** | **Opposite polarities** |
| **Muscle (EMG)** | Internal | **Broad** (mostly high, also low) | Variable, often high | **Wide, almost uniform over scalp** | Diverse, task-related |
| **Chewing** | Internal (temporalis) | **Very fast** bursts | High | Generalized (temporal) | Sudden, intermittent bursts |
| **Hypoglossal** | Internal (tongue) | **Slow**, diffuse | Moderate | Diffuse, synchronous | Reproducible with "la la la" |
| **ECG** | Internal (heart) | ~heart rate, sharp | **Low** | **Left** side | **Time-locked to QRS** |
| **Cardioballistic** | Internal (motion) | ~heart rate | Low–moderate | Electrode over artery | **~200 ms after QRS** |
| **Line noise / electrode** | External | **50/60 Hz** (+ harmonics) | Variable, can be huge | Channels sharing a bad electrode | Thick monotone band; notch helps |
| **Sweat** | Internal (skin/NaCl) | **< 0.5 Hz** | **Low** | Any (bi-, uni-lateral, focal) | Slow undulation |

### Part H — Practice MCQs (select all correct)

**H-1.** A patient looks to the left during recording. Which are expected?
- A. F7 becomes relatively positive.
- B. F8 becomes relatively positive.
- C. F7 and F8 show opposite polarities.
- D. The largest deflection is at O1/O2.
- E. The polarity arises from the corneo-retinal potential.

> **Answer: A, C, E.**
> - Looking left brings the left cornea (+) toward F7. F8 goes negative. The effect is frontal, not occipital.

**H-2.** An EEG shows repetitive sharp transients in left posterior channels aligned exactly with QRS complexes in the ECG channel.
- A. This is most consistent with ECG artifact.
- B. Its left-sided predominance reflects the heart's position in the left chest.
- C. It is likely high amplitude compared with blinks.
- D. A cardioballistic artifact would instead appear about 200 ms after the QRS.
- E. It should be classified as an external artifact.

> **Answer: A, B, D.**
> - C ✗: ECG artifact is **relatively low amplitude**.
> - E ✗: it is **internal** (physiological).

**H-3.** Sweat artifact:
- A. Is very slow, typically below 0.5 Hz.
- B. Is caused by NaCl charge in sweat.
- C. Is always strictly unilateral.
- D. Is typically of very high amplitude like blinks.
- E. Can be focal to a few electrodes.

> **Answer: A, B, E.**
> - C ✗: it can be bilateral, unilateral or focal.
> - D ✗: relatively low amplitude.

**H-4.** Chewing and tongue artifacts:
- A. Chewing artifact arises from the temporalis muscle.
- B. Chewing artifact appears as sudden intermittent bursts of generalized very fast activity.
- C. Generalized periodic fast activity is faster and larger than chewing artifact.
- D. Hypoglossal artifact can be reproduced by asking the patient to say "la la la".
- E. Hypoglossal artifact shows synchronous slow diffuse waves.

> **Answer: A, B, D, E.**
> - C ✗: generalized periodic fast activity is **slightly slower (beta)** and **lower amplitude**.

**H-5.** Artifact categories:
- A. Wireless signals are external artifacts.
- B. Poor electrode attachment is an external artifact source.
- C. Eye blinks are internal artifacts.
- D. External artifacts permeate EEG and are harder to prevent than internal ones.
- E. Most artifact removal methods focus on internal artifacts.

> **Answer: A, B, C, E.**
> - D ✗: reversed.

**H-6.** One channel pair Fp1–F7 and Fp1–F3 shows dense 50 Hz activity while other channels look normal.
- A. A bad Fp1 electrode is the most likely cause.
- B. The ground electrode is the most likely cause.
- C. A notch filter would substantially reduce it.
- D. Re-preparing/reattaching Fp1 is a sensible fix.
- E. It is an internal physiological artifact.

> **Answer: A, C, D.**
> - B ✗: a ground or reference problem would affect many channels.
> - E ✗: it is external/electrical.

**H-7.** Muscle artifacts:
- A. Have a wide, nearly uniform scalp distribution.
- B. Affect only frequencies above 30 Hz.
- C. Can be temporally correlated with the task.
- D. Are more diverse in form than ocular artifacts.
- E. Are detected via EMG.

> **Answer: A, C, D, E.**
> - B ✗: they affect both high and low frequencies.

---

## Part I — Brain Rhythms 🔥

### I1. The five bands (exam version) 🔥 (Q35, Q36)

| Band | Frequency (**exam/slide version**) | Table variant | State (slides) | Extra facts |
|---|---|---|---|---|
| **Delta (δ)** | **0.5–4 Hz** | 0.5–4 Hz | **Sleep, dreaming**; strongest in **dreamless, restorative (deep) sleep** | **Slowest** waves; state where **healing and rejuvenation** are stimulated |
| **Theta (θ)** | **4–8 Hz** | 4–8 Hz | **Creativity, insight, dreams, reduced consciousness**; drowsiness; deeply relaxed, inward focused | **Strongly detectable when dreaming**; also **deep meditation**, **daydreaming**, and **automatic tasks** (brushing teeth, showering); more frequent in **highly experienced meditators**; **source probably frontal** (monitoring of other mental processes); positively associated with **memory, creativity, psychological well-being** |
| **Alpha (α)** | **8–13 Hz** | 8–12 Hz | **Physically and mentally relaxed**; reflective, restful; very relaxed, passive attention | **Among the most easily observed** and **first discovered**; **detectable when eyes are closed and mind relaxed**; also in yoga, **just before falling asleep**, being creative/artistic; slide spectrum example at O2 shows a peak slightly below 10 Hz |
| **Beta (β)** | **13–32 Hz** | 12–35 Hz | **Alert, normal alert consciousness, active thinking**; busy, active mind; anxiety dominant, external attention | Examples: **active conversation, making decisions, solving a problem, focusing on a task, learning a new concept** |
| **Gamma (γ)** | **32–100 Hz** | >35 Hz | **Heightened perception, learning, problem-solving**; concentration | **Fastest measurable** EEG waves; "**peak mental state**" when there is **simultaneous processing of information from different brain parts**; **much stronger and more regularly observed in very long-term meditators, including Buddhist monks** |

**Memory aid:** *"**D**eep **T**ired **A**lert? **B**usy **G**enius"*, from slowest to fastest: Delta (deep sleep), Theta (tired/dreamy), Alpha (awake but relaxed, eyes closed), Beta (busy), Gamma (genius/peak). Boundaries **4, 8, 13, 32**. Each boundary is roughly **double** the previous (4, 8, then ~13 and ~32).

**Meditation trap:** both **gamma** ("very long-term meditators, Buddhist monks") **and theta** ("highly experienced meditation practitioners", "deep meditation") are linked to meditation. Alpha is linked to **yoga**.

**Source trap:** theta's source is "probably **frontal**". "Occipital" is a distractor (alpha is classically posterior/occipital).

### I2. Other brain-wave facts ⭐

- Brain waves are oscillating voltages of **just a few millionths of a volt (µV)**.
- **Different brain regions do not emit the same frequency simultaneously.**
- A scalp EEG signal **consists of many waves with different characteristics**. The large amount of data makes interpretation difficult. **Brain-wave patterns are unique for every individual.**
- **EEG's superior temporal resolution** (vs fMRI, PET) lets it capture activity changing over **tens of ms**. Thanks to it, **spectral analysis** yields a lot of information.
- **Clinical biomarkers (slide):**
  - **Reduced frontal gamma (30–50 Hz)** may indicate **declined cognitive function**.
  - **Increased midline beta (13–30 Hz)** may indicate **restless legs syndrome**.
- Spectral analysis also enables **brain–computer interfaces (BCIs)** and **neurofeedback** systems.

### Part I — Practice MCQs (select all correct)

**I-1.** Which pairings are correct according to the course slides?
- A. Delta 0.5–4 Hz: dreamless restorative sleep.
- B. Theta 4–8 Hz: creativity, insight, dreams.
- C. Alpha 8–13 Hz: alert active thinking and problem solving.
- D. Beta 13–32 Hz: active conversation and decision making.
- E. Gamma 32–100 Hz: heightened perception, peak mental state.

> **Answer: A, B, D, E.**
> - C ✗: alert active thinking is **beta**. Alpha is relaxed, eyes closed.

**I-2.** A subject closes their eyes and relaxes; a peak near 10 Hz appears over occipital electrodes.
- A. This is alpha activity.
- B. Alpha was among the first rhythms discovered.
- C. Opening the eyes and doing mental arithmetic would likely shift activity toward beta.
- D. This peak is best explained as a harmonic of delta.
- E. Alpha is described as strongest during dreamless sleep.

> **Answer: A, B, C.**
> - D ✗.
> - E ✗: that is delta.

**I-3.** Theta rhythm:
- A. Is strongly detectable during dreaming.
- B. Is associated with automatic tasks like showering.
- C. Is thought to originate from occipital cortex.
- D. Occurs more in highly experienced meditators.
- E. Is positively associated with memory and psychological well-being.

> **Answer: A, B, D, E.**
> - C ✗: frontal.

**I-4.** Spectral biomarkers and applications:
- A. Reduced frontal gamma may indicate declined cognitive function.
- B. Increased midline beta may indicate restless legs syndrome.
- C. Spectral analysis is used in BCIs and neurofeedback.
- D. EEG spectral analysis is limited by EEG's poor temporal resolution.
- E. All brain regions emit the same dominant frequency at any given time.

> **Answer: A, B, C.**
> - D ✗: EEG has **high** temporal resolution.
> - E ✗.

---

## Part J — Time-Domain Techniques and Digital Filtering (Medium)

### J1. Time-domain analysis techniques ⭐

| Technique | What it does | Typical use |
|---|---|---|
| **Peak detection** | Locates **extrema** (local maxima/minima). Amplitudes between successive maxima and minima give the **amplitude distribution**. For impulse-like signals it yields **intervals between events**. | **Spike detection**; **QRS detection in ECG** (e.g., neonatal heart rate). Two stages: **(1) pretreat the signal to remove artifacts, (2) detect extreme values above a threshold**. |
| **Level and window detection** | Identifies epochs where the signal is **within a certain amplitude range** (level = above a threshold; window = between two thresholds). Analog or digital. | **Extracellular AP recordings**: sorting spikes by amplitude |
| **Cross-correlation** | Quantifies the **relationship between different signals**. Applied to parts of the **same** signal it is **auto-correlation**. | Delay estimation, periodicity detection, connectivity |
| **Template matching** | **Correlates a known template** with the time series to extract features. **Wavelets and scaling signals are special templates.** | Detecting spikes or known waveforms |

**Cross-correlation intuition:** slide one signal past the other and compute a dot product at each lag. The lag of the maximum gives the delay. Auto-correlation of a periodic signal peaks at multiples of its period.

### J2. Digital filtering ⭐

- **Filtering** removes or separates the unwanted part of a mixture. In signal processing, it **removes or extracts part of a signal** (slide: noisy sine in, clean sine out).

| Filter | Passes | Removes | EEG example |
|---|---|---|---|
| **Low-pass** | Below cutoff | Above cutoff | Anti-aliasing; remove EMG/high-frequency noise |
| **High-pass** | Above cutoff | Below cutoff | Remove drifts, **sweat** (<0.5 Hz), late slow EP components |
| **Band-pass** | Between two cutoffs | Outside the band | Extract alpha (8–13 Hz); acquisition band filter (e.g., 0.5–70 Hz) |
| **Band-stop (notch)** | Everything except a band | A narrow band | 50/60 Hz line noise |

- **Ideal** filters have perfectly rectangular (brick-wall) responses.
- **Realistic** filters have **gradual transitions** (roll-off), **ripple**, and imperfect attenuation. The black curves on the slide deviate from the ideal red boxes.
- **Background (helps with trick options):** a brick-wall response in frequency corresponds to an infinitely long sinc in time. Real, finite filters must have transition bands. Sharp filters **ring** in time (the notch transient oscillations of Part G), which follows from the time–frequency duality in D3.

### Part J — Practice MCQs (select all correct)

**J-1.** Time-domain methods:
- A. QRS detection typically pre-processes the signal and then applies a threshold to detect peaks.
- B. Auto-correlation is the cross-correlation of a signal with itself.
- C. Level and window detection identify epochs where the signal lies within an amplitude range.
- D. Wavelets can be considered special templates.
- E. Peak detection is useless for spike trains.

> **Answer: A, B, C, D.**
> - E ✗: it is particularly useful for impulse-like signals.

**J-2.** Filters:
- A. A high-pass filter at 0.5 Hz reduces sweat artifact.
- B. A notch filter is a narrow band-stop filter.
- C. Realistic filters have perfectly sharp transitions.
- D. An anti-aliasing filter is a low-pass filter.
- E. A band-pass filter 8–13 Hz isolates alpha.

> **Answer: A, B, D, E.**
> - C ✗.

---

## Part K — MATLAB Labs: Sine Waves, Complex Numbers, Dot Products, DFT vs FFT (Medium)

> These labs build intuition for Parts C and D. The exam may use them as a scenario ("a signal sampled at...", "the dot product peaks at...").

### K1. Generating sine waves (`SineWaves`, `SinWavesLab2`, `SineWavesInitialLab1`)

$$y(t) = A\sin(2\pi f t + \theta)$$

- `fs = 500; TimeVec = 0:1/fs:1;` gives 501 samples over 1 s (the time step is $1/f_s$).
- Five sines (5, 7, 15, 26, 30 Hz with different amplitudes and phases) are **summed** into a time series. **Gaussian white noise** is added with `10*randn` (little noise) or `100*randn` (a lot of noise). The noise **standard deviation** is 10 or 100, so its power is 100 or 10,000. With the large noise, the sum of sines disappears visually, which motivates spectral analysis and averaging.
- **Lab 1:** a 20 Hz sine sampled at **500, 59, 24 Hz** reproduces the Nyquist slide (clean, distorted-looking, aliased to 4 Hz).

### K2. Complex numbers and Euler (`Lab4ComplexNumbers`, `EulersFormula`, `ComplexSinWaves`)

- Create: `1+1i`, `-1+3*1i`, `-5-3*sqrt(-1)`, `complex(2,3)`. Plot real vs imaginary parts.
- `Point = Amp*exp(1i*Phase)` with Amp = 4, Phase = π/3. Then `abs(Point)` = 4 (magnitude $\sqrt{a^2+b^2}$ or $\sqrt{z\bar z}$), and `angle(Point)` = π/3.
- **Complex sine wave:** $A e^{j(2\pi f t+\theta)}$. The real part is a cosine, the imaginary part a sine. In 3-D (time, real, imag) it is a **helix**.
- ⚠️ **Code trap:** the lab writes `Amp*exp(2*1i*pi*f0*TimeVec + phas)`. Because `phas` is **not multiplied by `1i`**, it does **not** shift the phase. It multiplies the amplitude by $e^{\pi/3}\approx2.85$. The correct form is `Amp*exp(1i*(2*pi*f0*TimeVec + phas))`.

### K3. Dot products as frequency detectors (`DotProductLab`, `ComplexDotProductt`, `Lab3Gaussian`)

- `sum(a.*b)` = `dot(a,b)`. For `a=[2 4 2 1 5 3 1]`, `b=[4 2 2 -3 2 5 0]`: $8+8+4-3+10+15+0=$ **42**.
- **Gaussian-windowed sine:** `exp(-t.^2/delta)` times `sin(2*pi*5*t+pi)`. Dot products with test sines at 1–10 Hz, normalized by length, **peak at 5 Hz** (negative sign here because $\theta=\pi$ inverts the sine).
- **`Lab3Gaussian`:** sines 1–20 Hz under a Gaussian envelope with $\sigma = 0.5$ (a larger $\sigma$ gives a wider envelope). This shows **localization in time** (tapering).
- **Complex dot product:** for complex vectors $\langle a,b\rangle=\sum \bar a\, b$ (`sum(conj(a).*b)`). MATLAB's `dot(a,b)` **conjugates the first argument**.
- Signal $\sin(2\pi\cdot5t+\pi/5)$ tested against $e^{j2\pi f t}$ for $f = 1\ldots10$ Hz: the **magnitude** peaks at **5 Hz** regardless of phase, and the **angle** at 5 Hz reveals the **phase offset** (relative to the complex sine). **This is the Fourier transform in miniature.**

### K4. DFT vs FFT (`FastFourierTransformm`)

- `fs = 1000`, `T = 2` s, `t = 0:1/fs:T-1/fs`, so **N = 2000** and **Δf = 0.5 Hz**.
- Signal: sines at **4, 6, 8, 10 Hz** with amplitudes **2, 3, 8, 3**.
- **DFT by double loop:** $X(k)=\sum_n x(n)e^{-j2\pi(k-1)(n-1)/N}$, which is $N^2$ = 4,000,000 operations (MATLAB indices start at 1, hence $k-1$, $n-1$).
- **FFT:** `fft(x)`. Both are divided by $N$.
- One-sided frequency axis: `f = fs*(0:N/2)/N`. Plot `2*abs(X(1:N/2+1))`. **Peaks of height 2, 3, 8, 3** at 4, 6, 8, 10 Hz, confirming the $\frac{2}{N}\lvert X\rvert$ amplitude normalization.
- **Max difference DFT vs FFT ≈ 0** (numerical precision): **the FFT is exact, just faster**.
- All frequencies fall exactly on bins (multiples of 0.5 Hz) and the epoch holds whole cycles, so there is **no leakage**. A 4.25 Hz component would leak.

### Part K — Practice MCQs (select all correct)

**K-1.** In `FastFourierTransformm`, fs = 1000 Hz and T = 2 s. Which are correct?
- A. N = 2000.
- B. The frequency resolution is 0.5 Hz.
- C. The one-sided amplitude spectrum uses $2\lvert X\rvert/N$ so an 8-amplitude sine shows a peak of 8.
- D. The FFT result differs noticeably from the double-loop DFT.
- E. The frequency axis for plotting is `fs*(0:N/2)/N`.

> **Answer: A, B, C, E.**
> - D ✗: identical up to rounding.

**K-2.** Complex numbers in MATLAB:
- A. `abs(4*exp(1i*pi/3))` returns 4.
- B. `angle(4*exp(1i*pi/3))` returns π/3.
- C. `exp(2*1i*pi*f*t + phas)` correctly adds a phase shift `phas`.
- D. `real(exp(1i*2*pi*f*t))` is a cosine at f Hz.
- E. `dot(a,b)` for complex vectors conjugates `a`.

> **Answer: A, B, D, E.**
> - C ✗: phase must be inside `1i*(...)`. As written it scales the amplitude.

**K-3.** Dot product labs:
- A. The normalized dot product of a 5 Hz signal with test sines peaks at 5 Hz.
- B. Using complex exponentials as templates makes the magnitude insensitive to the signal's phase.
- C. The dot product of orthogonal vectors is maximal.
- D. The dot product of `[2 4 2 1 5 3 1]` and `[4 2 2 -3 2 5 0]` is 42.
- E. A Gaussian envelope localizes a sine wave in time.

> **Answer: A, B, D, E.**
> - C ✗: orthogonal vectors give **zero**.

---

## High-Yield Revision Notes

### Neurophysiology (Section A)

1. **Neurons** do long-distance electrical signalling. **Glia** support, repair, act as stem cells in some areas, prevent regeneration elsewhere, and myelinate.
2. **Dendrites receive** (antenna). **Axons transmit** (telephone wires). **Axon terminals** transmit to dendrites/soma of the next cell (transmitter). **Soma** ~20 µm.
3. **Convergence** = number of inputs. **Divergence** = number of targets. Retinal bipolar: short axon. Amacrine: no axon.
4. **Membrane potential** = charge difference across the membrane. Ions move by **diffusion**, **electrostatics**, and only through **channels**.
5. **Nernst:** $E=\frac{2.303RT}{zF}\log\frac{[out]}{[in]}$, 61.54 mV per decade at 37 °C (30.77 for Ca²⁺). $E_K\approx-80$, $E_{Na}\approx+62$, $E_{Ca}\approx+123$, $E_{Cl}\approx-65$ mV.
6. **Resting $V_m\approx-65$ mV**, not −80, because of **some Na⁺ permeability**. **$P_K = 40\times P_{Na}$**. The **Goldman** equation weights by permeability.
7. **Leak channels:** normally open, ion-selective. **Pump:** ATP, against gradients. **Voltage-gated:** open with voltage change.
8. **AP phases:** rest (VG Na⁺ and K⁺ closed), threshold, rising (Na⁺ in), overshoot (toward $E_{Na}$, never reaching it), falling (Na⁺ inactivation after ~1 ms + delayed K⁺ opening), undershoot (toward $E_K$).
9. **Absolute refractory:** Na⁺ channels **inactivated**, no AP possible. **Relative refractory:** K⁺ still open and membrane hyperpolarized, so a **larger stimulus** is needed.
10. **All-or-none:** AP size is independent of stimulus strength. **Firing rate** increases with current.
11. **Passive** conduction decays within a few mm. **Active** conduction has no decrement, only delay. **Saltatory:** Na⁺ channels at **nodes of Ranvier**. **Oligodendrocytes** (CNS, many axons) vs **Schwann** (PNS, one axon).
12. **Spike-initiation zone:** **axon hillock** (CNS) or **sensory nerve endings** (sensory neurons). Dendrites and soma have **few** VG Na⁺ channels.
13. **Electrical synapse:** gap junction ~3 nm, **6 connexins = connexon**, **2 connexons = channel**, **bidirectional**, **very fast**, synchronization. **Furshpan & Potter (late 1950s)**.
14. **Chemical synapse:** AP, Ca²⁺ influx, vesicle fusion, exocytosis, receptor binding, channels, PSP. **Loewi 1921** (vagus, frog heart). **Katz** (neuromuscular junction).
15. **EPSP = Na⁺ in**, depolarization. **IPSP = Cl⁻ in**, hyperpolarization. **Spatial** summation = different inputs at once. **Temporal** summation = same input repeatedly. An IPSP can veto E1+E2.
16. Glutamate/ACh excitatory. **GABA/glycine inhibitory**. Endocannabinoids "inhibit inhibition". Neuropeptides and NO both.

### EEG origin and acquisition (Section B)

17. **EEG = extracellular currents from synaptic (postsynaptic) activity in dendrites** of cortical **pyramidal** neurons aligned **perpendicular** to the cortex. **Not APs.** Single-neuron dipoles are unmeasurable.
18. **Radial dipole at gyral crown gives the strongest signal. Tangential dipoles in sulcal walls cancel. Deep sources are weaker.**
19. **Synchrony + same orientation + same transmitter type gives summation.** Random orientation or mixed E/I gives cancellation.
20. **Why EEG:** non-invasive (no radiation/magnetic field), **direct** electrical measure, portable, **high temporal resolution** (speed of cognition), rich information (oscillations, synchronization, connectivity), open environment, economical. **Poor spatial resolution.**
21. **Methods:** EEG, MEG (non-invasive); ECoG (semi-invasive); LFP, APs, patch clamp (invasive); fMRI (non-invasive, blood-flow coupling, slow).
22. **Acquisition chain:** electrodes, pre-amp, amp, band filter, notch, **anti-alias**, S/H, MUX, ADC.
23. **Ag/AgCl:** ionic-to-electronic transition, **lower capacitance**, better **low-frequency** recording. Electrode potentials cancel with same-material pairs.
24. **ADC bits:** $2^n$ levels (3 bits = 8 levels).
25. **Nyquist rate = $2f_{max}$** (minimum sampling rate). **Nyquist frequency = $F_s/2$**. 20 Hz needs ≥ 40 Hz. **5× is common** in practice. The **anti-aliasing filter** goes **before** the ADC.
26. **Sampling = multiplication by a Dirac comb**, which **periodizes the spectrum** at $F_s$. Overlap = aliasing.
27. **10–20 system:** Jasper 1958; percentages; **odd = left, even = right, z = midline**; Fp, F, C, P, O, T, A.
28. **Differential amplifier:** $C = V_{AG}-V_{RG}$. Common noise cancels. **Ground** (frontal) location matters less. **No neutral reference.** The reference is usually the ear lobe(s).
29. **Montages:** bipolar (neighbours), unipolar/common reference, biauricular, CAR (subtract mean), Laplacian/LAR. **CAR suffers from outlier channels, so remove bad channels first.** Changing the reference changes waveforms and topography.

### Fourier (Section C)

30. **Real FS:** $P(t)=\frac12a_0+\sum[a_n\cos n\omega t+b_n\sin n\omega t]$. $a_0,a_n,b_n = \frac2T\int f\cdot(1,\cos,\sin)$. DC $=\frac12a_0$. **Even gives $b_n=0$. Odd gives $a_n=0$.**
31. **Orthogonality:** $\int_T\cos n\omega t\cos m\omega t = T/2$ if $m=n$, else 0. Same for sin. sin·cos = 0.
32. **Complex FS:** $\sum c_ne^{jn\omega t}$, $c_n=\frac1T\int_T fe^{-jn\omega t}$. **Start point irrelevant**, equivalent to the real FS via Euler, **contains phase**.
33. **CFT pairs:** $\delta\leftrightarrow1$; $1\leftrightarrow2\pi\delta(\omega)$; $\cos\leftrightarrow\pi[\delta(\omega+\omega_0)+\delta(\omega-\omega_0)]$; $\sin\leftrightarrow j\pi[\delta(\omega+\omega_0)-\delta(\omega-\omega_0)]$.
34. **DFT:** $X(k)=\sum x(n)W_N^{kn}$. Inverse: $x(n)=\frac1N\sum X(k)W_N^{-kn}$. $W_N=e^{-j2\pi/N}$ is **periodic** ($W_N^m=W_N^{m+N}$).
35. **Precision $\Delta f=1/T$. Range $=F_s/2$** (full circle $F_s$). 0.5 s at 1 kHz gives 2 Hz / 500 Hz. 5 s at 200 Hz gives 0.2 Hz / 100 Hz. 10 s gives 0.1 Hz.
36. **Circular frequency scale:** $0\to\pi$ positive, $\pi\to2\pi$ negative. **Power spectrum is even**, so show up to Nyquist.
37. **FFT:** Cooley & Tukey 1965. **$N^2$ vs $N\log_2N$** multiplications. It exploits the twiddle periodicity. It is an exact algorithm, not a filter.
38. **Spectra:** $S=XX^{\ast}/N$. $AS=\frac2N\sqrt{XX^{\ast}}$. $\varphi=\arctan(\mathrm{Im}/\mathrm{Re})$ with **no normalization**.
39. **Finite epoch = rectangular window.** Time multiplication equals frequency convolution, which causes **leakage** with ripples spaced **$1/T$** (T = 1, 2, 4 s gives 1, 0.5, 0.25 Hz).
40. **Windows:** rectangular (1), Bartlett ($1-\lvert t\rvert/T$), **Hann** ($0.5+0.5\cos\pi t/T$), **Hamming** ($0.54+0.46\cos\pi t/T$).
41. **Physiological spectra:** nonstationary, periodic + nonperiodic, low-frequency trends, high-frequency transients, **harmonics from non-sinusoidal waveforms** (respiration 1.5 Hz with a harmonic near 3 Hz). EEG O2 alpha peak just below 10 Hz.

### Random processes and averaging (Section D)

42. **Measurement noise** $M_i = x_i+N_i$ (deterministic process). **Dynamical noise** enters the state, making the process **stochastic** with **correlated values and slower trends**.
43. **PDF** integrates to 1. **CDF** $F(x)=\int_{-\infty}^xp$. **Survival** $=1-F$.
44. **Ensemble** = collection of sample functions. **Stationary** = the distribution does not change over time. **Ergodic** = one sample function represents the ensemble, so time averages work.
45. **SNR** $=ms_s/ms_n$; dB $=10\log_{10}$ (power) $=20\log_{10}$ (rms). Dimensionless; the ratio is a figure of merit.
46. **Hum is enemy #1.** EP < amplifier noise < EEG < EMG/ECG ≈ hum < intracellular.
47. **Averaging assumptions:** uncorrelated signal/noise, known timing, consistent signal, random zero-mean noise. Robust to minor violations.
48. **Noise rms falls as $1/\sqrt N$**, power SNR rises ×N. 256 trials cut noise rms 16×.
49. **Prestimulus:** assumes the signal is only post-trigger; unreliable with overlapping late responses; fix with longer ISI or high-pass.
50. **Bootstrap:** random triggers give a control average; offline; good when signal ≪ noise; signal present but not enhanced.
51. **± average:** invert alternate trials; signal cancels; residual noise rms equals that of the true average.
52. **Hum + 10 Hz stimulation = phase-locked**, so the hum survives. **Noninteger rate (7.7 Hz) or random ISI** avoids it.
53. **Background EEG:** 0.01–100 Hz, ~100 µV, power-law PSD, 5 bands, stochastic, long-term non-stationary, short-term quasi-stationary (seconds–minutes).
54. **EPs:** AEP/VEP/SEP. **P300** (oddball, positive, ~300 ms, central, novelty). **CNV** (warning, then second stimulus with button press; centrofrontal **negative**; Cz; 32 trials).

### Artifacts, preprocessing and rhythms (Sections E–F)

55. **Notch** removes 50/60 Hz but **distorts 50–70 Hz**, causes **transient oscillations**; low-pass <50 Hz can alter temporal structure and create spurious interactions. It is **not "optimal"**.
56. **Multitaper:** multiple tapers, averaged spectra; good for **low SNR, high frequency (>30 Hz), single-trial power**; smoothing blurs nearby frequencies. Line-noise pipeline: sliding window, multitaper, regression, statistical test, subtract, repeat.
57. **Bad channels:** robust z-score amplitude; correlation after low-pass; high/low frequency power ratio. **Interpolation:** spherical splines (accurate, dense), polynomials, nearest neighbour, radial basis (cheap).
58. **Artifacts:** **internal** (heart, eyes, muscles; hard to prevent) vs **external** (environment, electrodes, equipment; can be inhibited).
59. **Blink:** Bell's phenomenon (eyes roll up), cornea (+) closer to **Fp1/Fp2**, very high amplitude, bifrontal.
60. **Lateral eye movement:** **opposite polarities at F7/F8**; looking right makes F8 positive.
61. **Muscle:** diverse, detected by EMG, **wide almost uniform scalp distribution**, task-related, affects **high and low** frequencies.
62. **Chewing:** temporalis, sudden intermittent bursts of generalized very fast activity. **Hypoglossal:** tongue, slow diffuse synchronous waves, reproducible with "la la la".
63. **ECG:** time-locked to QRS, left-sided, low amplitude. **Cardioballistic:** electrode over artery, pulse motion ~200 ms after QRS.
64. **Electrode/line artifact:** 50/60 Hz from appliances and phone charging; a bad electrode shows in its derivations; notch helps. **Sweat:** <0.5 Hz, low amplitude, NaCl, any localization.
65. **Rhythms:** **Delta 0.5–4** (deep sleep, healing); **Theta 4–8** (dreams, creativity, deep meditation, daydreaming, automatic tasks, **frontal**); **Alpha 8–13** (eyes closed relaxed, easiest to see, first discovered, yoga, before sleep); **Beta 13–32** (alert, active thinking); **Gamma 32–100** (fastest, heightened perception/peak state, long-term meditators/monks).
66. **Biomarkers:** reduced frontal gamma suggests cognitive decline; increased midline beta suggests restless legs. Spectral analysis also drives BCI/neurofeedback.

---

## Formula Sheet

### Neurophysiology

| Quantity | Formula | Remember |
|---|---|---|
| Nernst | $E_{ion}=\dfrac{2.303RT}{zF}\log_{10}\dfrac{[ion]_o}{[ion]_i}$ | **out/in**; ≈61.54 mV/decade at 37 °C (z = ±1) |
| $E_K$ | $61.54\log(5/100)=-80$ mV | |
| $E_{Na}$ | $61.54\log(150/15)=+61.5$ mV | |
| $E_{Ca}$ | $30.77\log(2/0.0002)=+123$ mV | z = 2 halves the slope |
| $E_{Cl}$ | $-61.54\log(150/13)=-65$ mV | z = −1 flips the sign |
| Goldman | $V_m=61.54\log\dfrac{P_K[K]_o+P_{Na}[Na]_o}{P_K[K]_i+P_{Na}[Na]_i}$ | $P_K:P_{Na}=40:1$ gives −65 mV |

### Acquisition

| Quantity | Formula |
|---|---|
| Sampling interval | $T_s = 1/F_s$ |
| Nyquist rate (minimum $F_s$) | $F_s \ge 2 f_{max}$ (practice: ~5×) |
| Nyquist frequency | $F_s/2$ |
| Alias frequency | $\lvert f - kF_s\rvert$ folded into $[0, F_s/2]$ |
| ADC levels | $2^n$; step $\approx V_{range}/2^n$ |
| Sampled signal | $x^s(nT_s)=x(t)\sum_n\delta(t-nT_s)$ |
| Differential channel | $C = V_{AG}-V_{RG}$ |
| Biauricular reference | $V'_{RG}=(V_{R1G}+V_{R2G})/2$ |
| CAR | $M=\frac1K\sum_{c} C_c$, $C'_c=C_c-M$ |

### Fourier

| Quantity | Formula |
|---|---|
| Angular frequency | $\omega=2\pi f$, $f=1/T$ |
| Real Fourier series | $P(t)=\tfrac12a_0+\sum_{n\ge1}[a_n\cos n\omega t+b_n\sin n\omega t]$ |
| Coefficients | $a_0=\frac2T\int_Tf\,dt$, $a_n=\frac2T\int_Tf\cos n\omega t\,dt$, $b_n=\frac2T\int_Tf\sin n\omega t\,dt$ |
| Complex FS | $P(t)=\sum_{-\infty}^{\infty}c_ne^{jn\omega t}$, $c_n=\frac1T\int_Tf e^{-jn\omega t}dt$ |
| Real ↔ complex | $c_0=a_0/2$, $c_n=(a_n-jb_n)/2$, $c_{-n}=\overline{c_n}$ |
| Euler | $e^{jx}=\cos x+j\sin x$ |
| CFT / inverse | $F(j\omega)=\int f(t)e^{-j\omega t}dt$; $f(t)=\frac1{2\pi}\int F(j\omega)e^{j\omega t}d\omega$ |
| Triangle wave | $a_n=\dfrac{8A}{n^2\pi^2}$ (odd $n$), 0 for even $n$ |
| Square wave (±1, odd) | $b_n=\dfrac{4}{n\pi}$ (odd $n$) |
| DFT | $X(k)=\sum_{n=0}^{N-1}x(n)W_N^{kn}$, $W_N=e^{-j2\pi/N}$ |
| Inverse DFT | $x(n)=\frac1N\sum_{k=0}^{N-1}X(k)W_N^{-kn}$ |
| Twiddle periodicity | $W_N^{m}=W_N^{m+N}$ |
| Frequency precision | $\Delta f=1/T=1/(N\Delta t)=F_s/N$; $\Delta\omega=2\pi/(N\Delta t)$ |
| Range | full $F_s$ ($\Omega=2\pi/\Delta t$); displayed $F_s/2$ |
| Bin frequency | $f_k=kF_s/N$ |
| FFT cost | $N\log_2N$ (DFT: $N^2$) |
| Power spectrum | $S=XX^{\ast}/N$ |
| Amplitude spectrum | $AS=\frac2N\sqrt{XX^{\ast}}$ |
| Phase spectrum | $\varphi=\arctan[\mathrm{Im}(X)/\mathrm{Re}(X)]$ |
| Rectangular window ripple spacing | $1/T$ |
| Bartlett | $w=1-\lvert t\rvert/T$ |
| Hann | $w=0.5+0.5\cos(\pi t/T)$ |
| Hamming | $w=0.54+0.46\cos(\pi t/T)$ |

### Noise and averaging

| Quantity | Formula |
|---|---|
| Measurement noise model | $M_i=x_i+N_i$, $x_i=0.8x_{i-1}+3.5$ (fixed point 17.5) |
| Dynamical noise model | $x_i=[0.8x_{i-1}+3.5]+D_{i-1}$ |
| PDF normalization | $\int p(x)dx=1$ |
| CDF / survival | $F(x)=\int_{-\infty}^xp(y)dy$; $1-F(x)$ |
| Mean / variance | $\hat x=\frac1N\sum x_i$; $\widehat{Var}=\frac1N\sum(x_i-\hat x)^2$ |
| ms / rms | $ms=\frac1N\sum x_i^2$; $rms=\sqrt{ms}$ |
| SNR | $ms_s/ms_n$; $10\log_{10}(ms_s/ms_n)$ dB $=20\log_{10}(rms_s/rms_n)$ dB |
| Sine power | $ms=A^2/2$, $rms=A/\sqrt2$ |
| Averaging | residual noise rms $=\sigma/\sqrt N$; power SNR ×N; +$10\log_{10}N$ dB |
| ± average | $\frac1N\sum(-1)^iM_i$, residual noise rms $=\sigma/\sqrt N$ |
| Hum phase-lock condition | $f_{hum}/f_{stim}\in\mathbb{Z}$ |

---

## Key Comparisons

| Pair | A | B |
|---|---|---|
| **Dendrite vs axon** | Receives (antenna) | Transmits over distance (wires) |
| **Neuron vs glia** | Long-distance electrical signalling | Support, repair, stem cells, myelin, block regeneration |
| **Convergence vs divergence** | Number of inputs to one neuron | Number of targets of one neuron |
| **Nernst vs Goldman** | One ion, equilibrium, no permeability | Several ions, resting $V_m$, permeability-weighted |
| **Leak channel vs pump** | Always open, passive, down gradient | ATP, against gradient |
| **Absolute vs relative refractory** | Na⁺ inactivated, no AP | K⁺ open/hyperpolarized, a bigger stimulus fires an AP |
| **Passive vs active conduction** | Subthreshold, decays in mm | Suprathreshold AP, no decrement, delay only |
| **Oligodendrocyte vs Schwann** | CNS, many axons | PNS, one axon |
| **Axon hillock vs sensory ending** | Spike-initiation zone in CNS neurons | Spike-initiation zone in sensory neurons |
| **Electrical vs chemical synapse** | Gap junction 3 nm, bidirectional, very fast, synchrony | Cleft, vesicles, Ca²⁺, mostly unidirectional, slower, flexible (excitation/inhibition) |
| **EPSP vs IPSP** | Na⁺ in, depolarize | Cl⁻ in, hyperpolarize |
| **Spatial vs temporal summation** | Different synapses at once | Same synapse repeatedly |
| **EEG vs MEG** | Electric potential, radial sources, skull smears | Magnetic field, tangential sources |
| **EEG vs fMRI** | Direct, ms, poor spatial | Indirect (blood flow), s, better spatial |
| **Radial vs tangential dipole** | Gyral crown, strongest EEG | Sulcal walls, cancel |
| **Nyquist rate vs Nyquist frequency** | $2f_{max}$ (needed $F_s$) | $F_s/2$ (max representable) |
| **Sampling rate vs bit depth** | Time resolution / max frequency | Amplitude resolution / levels |
| **Ground vs reference electrode** | Potential cancels; location less important; frontal | In every channel; no neutral site; ear lobe(s) |
| **Bipolar vs referential vs CAR** | Bipolar: neighbour differences, local | Referential: one common electrode. CAR: mean of all channels; sensitive to bad channels |
| **Fourier series vs Fourier transform** | Periodic signals, discrete harmonics | Non-periodic, continuous spectrum |
| **Real vs complex FS** | sin/cos, $2/T$, $n\ge0$ | $e^{jn\omega t}$, $1/T$, $-\infty..\infty$, equivalent |
| **DFT vs FFT** | Definition, $N^2$ | Algorithm, $N\log_2N$, same result |
| **Precision vs range** | $1/T$ (epoch length) | $F_s/2$ (sampling rate) |
| **Power vs amplitude vs phase spectrum** | Power: $XX^{\ast}/N$ | Amplitude: $\frac2N\sqrt{XX^{\ast}}$. Phase: $\arctan(\mathrm{Im}/\mathrm{Re})$, no normalization |
| **Rectangular vs Hann/Hamming** | Narrow main lobe, big ripples | Tapered, less leakage, wider main lobe |
| **Hann vs Hamming** | 0.5 + 0.5cos, reaches 0 | 0.54 + 0.46cos, edges 0.08 |
| **Measurement vs dynamical noise** | Additive, fast jitter, deterministic process | Enters state, correlated, slow trends, stochastic |
| **Stationary vs ergodic** | Distribution constant in time | One sample function represents the ensemble |
| **Prestimulus vs bootstrap vs ± average** | Pre-trigger epoch | Random triggers, offline | Invert alternate trials |
| **Random vs periodic noise in averaging** | Cancels as $1/\sqrt N$ | Survives if phase-locked to stimulus |
| **P300 vs CNV** | Oddball, positive, 300 ms, novelty | Warning then second stimulus, negative, anticipation |
| **Notch vs multitaper regression** | Removes the whole band, distorts, rings | Subtracts only significant sinusoidal line noise |
| **Internal vs external artifacts** | Heart, eyes, muscle; hard to prevent | Environment, electrodes, equipment; can be inhibited |
| **Blink vs lateral eye movement** | Fp1/Fp2 same polarity | F7/F8 opposite polarity |
| **ECG vs cardioballistic** | Electrical, with QRS, left | Mechanical pulse, ~200 ms after QRS |
| **Chewing vs hypoglossal** | Temporalis, fast bursts | Tongue, slow diffuse, "la la la" |
| **Chewing vs generalized periodic fast activity** | Very fast, high amplitude, bursts | Slightly slower (beta), lower amplitude |
| **Alpha vs beta** | 8–13 Hz relaxed eyes closed | 13–32 Hz alert active thinking |
| **Theta vs delta** | 4–8 Hz dreams/creativity/meditation, frontal | 0.5–4 Hz dreamless deep sleep |
| **Gamma vs theta (meditation)** | Very long-term meditators, peak state | Experienced meditators, deep relaxation |

---

## Common MCQ Traps

**Numbers the professor changes:**

1. $P_K/P_{Na}$ = **40**, not 80.
2. Resting $V_m$ ≈ **−65 mV**; $E_K$ ≈ **−80 mV**; $E_{Na}$ ≈ **+62 mV**.
3. Nernst ratio is **out/in**, not in/out.
4. **Six** connexins per connexon; **two** connexons per channel.
5. Gap junction ≈ **3 nm**.
6. Na⁺ channels inactivate ≈ **1 ms** after opening.
7. Precision $=1/T$: **0.5 s gives 2 Hz**, **5 s gives 0.2 Hz**, **10 s gives 0.1 Hz**.
8. Ripple spacing $=1/T$: **T = 4 gives 0.25 Hz** (not 0.5).
9. Nyquist for 20 Hz = **40 Hz**; 30 Hz is **not** enough.
10. FFT = **$N\log_2N$**; DFT = **$N^2$**; **1965**, Cooley & Tukey.
11. Jasper **1958**; Loewi **1921**; Furshpan & Potter **late 1950s**.
12. Background EEG: **0.01–100 Hz**, **~100 µV**, **five** bands.
13. Bands: **4 / 8 / 13 / 32** Hz boundaries.
14. P300 at **300 ms**, **positive**; CNV **negative**; **32** trials in the CNV example.
15. Cardioballistic ≈ **200 ms after QRS**; sweat **< 0.5 Hz**; notch width e.g., **10 Hz**, distorting **50–70 Hz**.
16. Averaging **256** trials reduces noise rms **16×** (√256).

**Swapped definitions and directions:**

17. Dendrites **receive**, axons **transmit** (not the reverse).
18. Neurotransmitter goes **pre → post**.
19. EPSP = **Na⁺**, IPSP = **Cl⁻** (K⁺ is the decoy).
20. Resting membrane more permeable to **K⁺**.
21. Relative refractory is due to **K⁺ still open** (not Na⁺ permanently disabled).
22. Oligodendrocyte **CNS/many**, Schwann **PNS/one**.
23. Precentral **motor**, postcentral **sensory**; Broca **production**, Wernicke **comprehension**.
24. Deeper dipoles contribute **less**. Sulcal cancellation happens because of **opposite** polarities.
25. Odd electrode numbers are **left**.
26. Fourier **series** for **periodic**; odd function means **$a_n=0$**; even function means **$b_n = 0$**.
27. Complex FS is a sum of **exponentials** and **contains phase**.
28. Positive frequencies **0→π**, negative **π→2π**; power spectrum **even**.
29. Longer epoch **improves** precision; range depends on $F_s$ only.
30. Dynamical noise gives **slower** trends.
31. Stationary = distribution **does not** change.
32. Bootstrap works well when the signal is **small** relative to noise, and **offline**.
33. Noninteger stimulus rate **avoids** hum locking.
34. **External** artifacts can be inhibited; **internal** ones are hard to prevent.
35. Blink: cornea **closer** to Fp1/Fp2; F7/F8 opposite polarity is **lateral eye movement**.
36. Muscle artifacts are **diverse**, **widely distributed**, and affect **both** high and low frequencies.
37. ECG artifact is **low** amplitude and **left**-sided.
38. Theta source **frontal**; alpha **13–32** is wrong (that is beta).
39. CAR is **sensitive** to outlier channels.
40. Ground position is **less** important than the reference.

**Absolute words (almost always false here):** *only, always, never, guarantees, must, cannot, irrelevant, optimal, permanently, zero noise, all noise, completely, no information, unlimited.*

**Plausible-but-wrong reasoning patterns:**

- "APs are the biggest voltages, so EEG records APs." Size is not what matters; **duration, synchrony and alignment** are.
- "More bits fix aliasing / electrode problems." Bits only change amplitude resolution.
- "Higher sampling rate improves frequency resolution." Only a **longer epoch** does.
- "FFT is an approximation / filter / continuous-time method." It is an exact algorithm on sampled data.
- "Random noise breaks averaging." Random noise is **the ideal case**; **periodic phase-locked** noise breaks it.
- "Prestimulus baseline is always clean." Late responses and short ISIs contaminate it.
- "Notch = perfect line-noise removal." It distorts and rings.
- "A neutral reference exists." It does not.

---

## 100 Practice MCQs with Explanations

> **Format:** like the real exam, most are **"select ALL correct statements"** (any number can be correct). Questions marked **(Single best answer)** have exactly one correct option. Try each block before reading its answers. Tag in brackets: [C] conceptual, [N] numerical, [G] graph/figure, [S] scenario, [X] comparison, [T] tricky.

### Block 1 — Neurophysiology (Q1–Q18)

**Q1 [C].** Select all correct.
- A. Axon collaterals allow one neuron to send output to several targets.
- B. Dendrites of different neurons vary in size and branching, contributing to different information-processing capacity.
- C. The axon hillock is where the axon originates from the soma.
- D. Retinal amacrine cells have exceptionally long axons.
- E. The cerebellar Purkinje cell is shown as an example of an extensive dendritic tree.

**Q2 [N] (Single best answer).** At 37 °C, extracellular K⁺ is 4 mM and intracellular K⁺ is 400 mM. $E_K$ is closest to:
- A. −61.5 mV B. −123 mV C. −30.8 mV D. +123 mV

**Q3 [N].** A hypothetical ion X²⁺ has $[X]_o = 10$ mM and $[X]_i = 0.1$ mM at 37 °C. Select all correct.
- A. $E_X \approx +61.5$ mV.
- B. $E_X \approx +123$ mV.
- C. If X were monovalent with the same ratio, $E_X$ would be ≈ +123 mV.
- D. Raising temperature would increase the magnitude of $E_X$.
- E. $E_X$ is negative because the ion is divalent.

**Q4 [S].** A drug blocks all resting Na⁺ leak permeability (resting $P_{Na}\to0$) without changing K⁺. Select all correct.
- A. Resting $V_m$ moves toward $E_K$.
- B. The neuron depolarizes to around 0 mV.
- C. The Goldman equation reduces to the Nernst equation for K⁺.
- D. Resting $V_m$ becomes more negative than −65 mV.
- E. $E_K$ itself changes.

**Q5 [T].** Select all correct about the resting potential.
- A. The discrepancy between −80 mV and −65 mV is explained by Na⁺ permeability.
- B. The resting membrane is roughly equally permeable to Na⁺ and K⁺.
- C. The Goldman equation includes permeability terms.
- D. The Nernst equation includes permeability terms.
- E. The relative permeability of the resting membrane is high to K⁺ and low to Na⁺.

**Q6 [G].** In the slide diagram where a membrane separates 10 mM Na⁺Cl⁻ (left) from 2 mM Na⁺Cl⁻ (right) and is permeable **only to Na⁺**, select all correct.
- A. Na⁺ diffuses from left to right.
- B. Cl⁻ follows Na⁺, keeping both sides neutral.
- C. The left side becomes negatively charged relative to the right.
- D. An electrostatic force eventually opposes further Na⁺ diffusion.
- E. At equilibrium there is still a net Na⁺ current to the right.

**Q7 [C].** Select all correct about the action potential's rising phase and overshoot.
- A. The driving force on Na⁺ is large when the inside is negative.
- B. At threshold, the relative permeability favours Na⁺ over K⁺.
- C. The overshoot means $V_m$ exceeds 0 mV.
- D. $V_m$ reaches exactly $E_{Na}$ at the peak.
- E. Na⁺ flows out of the cell during the rising phase.

**Q8 [G].** In the plot of summed ionic currents during an AP (Bear Fig. 4.12), select all correct.
- A. The summed Na⁺ current is inward and brief.
- B. The summed K⁺ current is outward and longer-lasting.
- C. The net current is outward first, then inward.
- D. Individual Na⁺ channels stay open no more than about 1 ms.
- E. K⁺ currents peak before Na⁺ currents.

**Q9 [S].** A stimulus arrives 0.5 ms after the peak of an AP, while Na⁺ channels are still inactivated. Select all correct.
- A. No AP can be generated, regardless of stimulus strength.
- B. The neuron is in the absolute refractory period.
- C. A very large stimulus will produce a smaller AP.
- D. The Na⁺ channels must be de-inactivated by sufficient repolarization first.
- E. The all-or-none law implies a partial AP.

**Q10 [S].** A stimulus arrives during the undershoot. Select all correct.
- A. The neuron is in the relative refractory period.
- B. Na⁺ channels are responsive again.
- C. A larger than normal depolarizing current is needed to reach threshold.
- D. The undershoot occurs because $g_K\gg g_{Na}$ and $V_m$ approaches $E_K$.
- E. Voltage-gated K⁺ channels are closed during the undershoot.

**Q11 [G].** In the current-injection figure (Purves), select all correct.
- A. Hyperpolarizing pulses produce only passive responses.
- B. Small depolarizing pulses produce only passive responses.
- C. Suprathreshold pulses evoke APs.
- D. Increasing current amplitude above threshold increases the number of APs per pulse.
- E. Increasing current amplitude increases AP height.

**Q12 [C].** Passive vs active signals. Select all correct.
- A. A subthreshold potential recorded 2 mm from the injection site is smaller than at the site.
- B. An AP recorded 2 mm away arrives later but with the same amplitude.
- C. Passive decay occurs because current leaks out of the axon.
- D. Myelin reduces current leakage between nodes.
- E. Active conduction eliminates any conduction delay.

**Q13 [X].** Select all correct comparisons.
- A. Oligodendrocytes: CNS, several axons per cell.
- B. Schwann cells: PNS, one axon per cell.
- C. Nodes of Ranvier: sites where the axon is exposed to extracellular fluid.
- D. Voltage-gated Na⁺ channels: concentrated under the myelin.
- E. Saltatory conduction: current appears to jump from node to node.

**Q14 [C].** Select all correct about the spike-initiation zone.
- A. Only membrane with a high density of voltage-gated Na⁺ channels can generate Na⁺-dependent APs.
- B. Dendrites and cell bodies usually do not generate Na⁺-dependent APs.
- C. In sensory neurons, the zone is near the sensory nerve ending.
- D. In CNS pyramidal cells, the zone is at the apical dendrite tips.
- E. The arrows in the figure indicate the normal direction of AP propagation.

**Q15 [C].** Select all correct about chemical synaptic transmission.
- A. Presynaptic depolarization opens voltage-gated Ca²⁺ channels.
- B. Ca²⁺ causes vesicles to fuse with the presynaptic membrane.
- C. Transmitter is removed from the cleft by glial uptake or enzymatic degradation.
- D. Vesicle membrane is retrieved from the plasma membrane.
- E. Transmitter is released by endocytosis.

**Q16 [T].** Select all correct about gap junctions.
- A. Two connexons, one from each cell, form a gap-junction channel.
- B. A connexon is made of six connexins.
- C. Ions and small molecules can pass through the channel.
- D. Electrical synapses are usually unidirectional like chemical synapses.
- E. An AP in cell 1 produces a small electrical PSP in cell 2 with very little delay.

**Q17 [S].** A neuron receives E1 (subthreshold), E2 (subthreshold) and I (inhibitory). Select all correct.
- A. E1 + E2 simultaneously can exceed threshold.
- B. E1 + I produces a smaller depolarization than E1 alone.
- C. E1 + E2 + I may stay below threshold.
- D. I alone depolarizes the neuron slightly.
- E. This demonstrates spatial summation.

**Q18 [C].** Select all correct about history and transmitters.
- A. Loewi showed that stimulating the vagus nerve released a chemical that slowed a second heart.
- B. Katz showed that neuromuscular transmission is electrically mediated.
- C. Glutamate is excitatory.
- D. Glycine is excitatory.
- E. Serotonin (5-HT) is listed as excitatory.

#### Answers Q1–Q18

**Q1: A, B, C, E.** D ✗: amacrine cells have **no axon**. The short-axon example is the retinal bipolar cell.

**Q2: B.** $61.54\log(4/400)=61.54\times(-2)=-123$ mV. A is one decade; C uses the divalent slope; D has the wrong sign.

**Q3: A, C, D.** Ratio 100 (2 decades) with $z=2$: $30.77\times2=61.5$ mV, so A ✓ and B ✗. Monovalent: $61.54\times2=123$ ✓. Temperature scales $RT/F$ ✓. E ✗: sign comes from the ratio direction and the sign of $z$, and a cation concentrated outside gives positive $E$.

**Q4: A, C, D.** With $P_{Na}=0$ the membrane behaves as K⁺-only, so $V_m=E_K\approx-80$ mV. B ✗: that would need huge Na⁺ permeability. E ✗: $E_K$ depends on K⁺ concentrations only.

**Q5: A, C, E.** B ✗: 40:1 in favour of K⁺. D ✗: Nernst has no permeability term.

**Q6: A, C, D.** B ✗: the membrane is impermeable to Cl⁻. C ✓: the left loses + charge (−3 vs +3 in the slide). E ✗: at equilibrium there is **no net current** for Na⁺.

**Q7: A, B, C.** D ✗: $V_m$ approaches but does not reach $E_{Na}$ (Na⁺ channels inactivate). E ✗: Na⁺ flows **in**.

**Q8: A, B, D.** C ✗: inward (Na⁺) first, then outward (K⁺). E ✗: K⁺ is delayed.

**Q9: A, B, D.** C ✗ and E ✗: during the absolute refractory period no AP occurs, and APs are never partial.

**Q10: A, B, C, D.** E ✗: they are still **open**, which causes the undershoot.

**Q11: A, B, C, D.** E ✗: all-or-none. Firing rate increases, height does not.

**Q12: A, B, C, D.** E ✗: delay remains (arrival time increases with distance).

**Q13: A, B, C, E.** D ✗: channels concentrate **at the nodes**.

**Q14: A, B, C, E.** D ✗: the zone is the **axon hillock**.

**Q15: A, B, C, D.** E ✗: release is by **exocytosis**. Retrieval is the endocytic step.

**Q16: A, B, C, E.** D ✗: electrical synapses are mostly **bidirectional**.

**Q17: A, B, C, E.** D ✗: an IPSP **hyperpolarizes**.

**Q18: A, C, E.** B ✗: Katz showed it was **chemically** mediated. D ✗: glycine is **inhibitory**.

---

### Block 2 — Brain, EEG origin and acquisition (Q19–Q36)

**Q19 [C].** Select all correct.
- A. The temporal lobe lies ventral to the lateral (Sylvian) fissure.
- B. Lobes are named after the skull bones overlying them.
- C. The occipital lobe borders the parietal and temporal lobes.
- D. The insula is visible on the lateral surface without retracting anything.
- E. The superior temporal gyrus is involved in audition.

**Q20 [X].** Match function to location. Select all correct.
- A. Prefrontal cortex: personality, judgment, decision making.
- B. Primary olfactory cortex: temporal lobe.
- C. Posterior association area (parietal): multimodal association and spatial coordination.
- D. Gustatory cortex: occipital lobe.
- E. Visceral sensation of thoracic/abdominal organs: insula.

**Q21 [C].** Select all correct about why pyramidal cells dominate EEG.
- A. Their apical dendrites are parallel to each other.
- B. They are aligned perpendicular to the cortical surface.
- C. They are mostly excitatory.
- D. Their dipoles add when many are synchronously activated.
- E. They are the only neurons in the cortex.

**Q22 [G].** A dipole source is located on the wall of a sulcus, oriented parallel to the scalp, with a mirror-image source on the opposite wall. Select all correct.
- A. This is a tangential configuration.
- B. Scalp EEG will be large directly above it.
- C. The fields from the two walls tend to cancel.
- D. Rotating the source to point radially toward the scalp at a gyral crown would increase EEG amplitude.
- E. MEG is typically more sensitive than EEG to tangential sources. (background knowledge)

**Q23 [S].** In a region, half the pyramidal neurons receive glutamatergic input and the neighbouring half receive GABAergic input at the same moment. Select all correct.
- A. Their dipoles have opposite orientations.
- B. The scalp EEG from this region will be enhanced.
- C. The scalp EEG from this region will be reduced by cancellation.
- D. This illustrates that synchrony alone is not enough; the transmitter type also matters.
- E. EEG measures the transmitter chemicals directly.

**Q24 [X].** Select all correct.
- A. ECoG places electrodes on the cortical surface and is considered semi-invasive.
- B. MEG measures magnetic fields and is non-invasive.
- C. Patch clamp works at the scale of a single cell.
- D. fMRI directly measures neuronal electrical currents.
- E. LFPs are recorded with invasive electrodes.

**Q25 [T].** Select all correct about EEG.
- A. EEG allows analysis of oscillations, synchronization and connectivity.
- B. EEG is economical.
- C. EEG has a temporal resolution in the order of seconds.
- D. EEG can only be recorded inside shielded laboratories.
- E. EEG exposes subjects to a strong magnetic field.

**Q26 [N] (Single best answer).** A 70 Hz component is sampled at 100 Hz without an anti-aliasing filter. It appears at:
- A. 70 Hz B. 50 Hz C. 30 Hz D. 170 Hz

**Q27 [N].** An EEG system samples at 256 Hz. Select all correct.
- A. The Nyquist frequency is 128 Hz.
- B. Line noise at 50 Hz can be represented without aliasing.
- C. A 150 Hz EMG component would alias to 106 Hz if not filtered.
- D. The anti-aliasing filter should attenuate components above 128 Hz before the ADC.
- E. By the 5× rule, activity up to about 51 Hz is comfortably represented in the time domain.

**Q28 [G].** In the figure showing a 20 Hz sine sampled at 500, 59 and 24 Hz, select all correct.
- A. At 500 Hz the sine looks smooth.
- B. At 59 Hz the frequency content is preserved even though the waveform looks distorted.
- C. At 24 Hz the samples trace a wave of about 4 Hz.
- D. At 59 Hz aliasing occurs because 59 < 5 × 20.
- E. Sampling exactly at peaks and valleys at 40 Hz would give a 20 Hz triangular wave.

**Q29 [C].** Select all correct about the Dirac delta and sampling.
- A. The discrete unit impulse sums to 1.
- B. The continuous Dirac delta integrates to 1.
- C. A unit impulse can be approximated by a pulse of duration τ and height 1/τ with τ → 0.
- D. The Fourier transform of a Dirac comb in time is a Dirac comb in frequency.
- E. Multiplying by a Dirac comb in time convolves the spectrum with a comb, making it periodic.

**Q30 [N] (Single best answer).** A 24-bit ADC has how many quantization levels?
- A. 24 B. 48 C. 16,777,216 D. 65,536

**Q31 [C].** Select all correct about the 10–20 system.
- A. Electrodes at the edges are 10% from the nasion/inion landmarks.
- B. O2 is over the right occipital region.
- C. Fp1 is over the left frontal pole.
- D. Pz is over the left parietal region.
- E. The vertex electrode is Cz.

**Q32 [S].** In the slide example (G frontal, R left ear, A at O1), the scalp above O1 is more negative than at the ear. Select all correct.
- A. The channel value $V_{AG}-V_{RG}$ is negative.
- B. Moving the ground to the chin would change the channel value substantially.
- C. If the reference ear were over an active source, the O1 channel would be contaminated.
- D. The channel reflects contributions from both A and R.
- E. Common noise on the ground connection is cancelled.

**Q33 [S].** Five electrodes A1–A5 lie along a line (T3, C3, Cz, C4, T4). A widespread slow wave of equal amplitude appears at all five, plus a focal spike only at C3. Select all correct.
- A. In a bipolar montage, the widespread slow wave is largely cancelled.
- B. In a bipolar montage, the C3 spike appears in the two derivations involving C3 with opposite signs (phase reversal).
- C. In CAR, the widespread wave is subtracted out as part of the mean.
- D. In CAR, the C3 spike slightly contaminates all other channels (with inverted sign).
- E. A unipolar ear reference would remove the widespread slow wave.

**Q34 [T].** Select all correct about referencing.
- A. The average of the two mastoids is a common reference choice.
- B. A reference correlated with task-induced activity biases results.
- C. CAR is immune to single-point failure of a reference electrode.
- D. Robust average referencing reduces contamination by bad channels.
- E. The reference should have amplitude comparable to EEG signals.

**Q35 [C].** Select all correct about electrodes.
- A. Bare metal electrodes in ionic solution create an electrode potential that depends on material and solution.
- B. Using identical electrode material for both electrodes reduces problems from electrode potentials.
- C. AgCl coating increases electrode capacitance to block DC drift.
- D. Ag/AgCl facilitates recording of low-frequency signals.
- E. The electrode interface can be modelled as a resistor in parallel with a capacitor.

**Q36 [C].** Select all correct about the acquisition chain.
- A. Amplification is often done in two stages (pre-amplifier and amplifier).
- B. The notch filter attenuates line frequency interference.
- C. The anti-aliasing filter attenuates frequencies too high to be digitized.
- D. The sample-and-hold keeps the voltage constant during conversion.
- E. The ADC precedes the amplifier to minimize noise.

#### Answers Q19–Q36

**Q19: A, B, C, E.** D ✗: the insula is **buried**. You see it by pulling the lateral fissure margins apart.

**Q20: A, B, C, E.** D ✗: gustatory cortex is in the **insula**.

**Q21: A, B, C, D.** E ✗: there are many interneurons too. Pyramidal cells dominate because of alignment.

**Q22: A, C, D, E.** B ✗: cancellation makes it small.

**Q23: A, C, D.** B ✗. E ✗: EEG measures electrical potentials.

**Q24: A, B, C, E.** D ✗: fMRI is **indirect** (blood-flow coupling).

**Q25: A, B.** C ✗: milliseconds. D ✗: open environments are possible. E ✗: that is MRI.

**Q26: C.** $\lvert70-100\rvert=30$ Hz.

**Q27: A, B, C, D, E.** C ✓: $\lvert150-256\rvert=106$ Hz (below 128). E ✓: $256/5\approx51$ Hz.

**Q28: A, B, C, E.** D ✗: 59 > 40, so there is **no aliasing**. The 5× rule concerns **time-domain appearance**, not aliasing.

**Q29: A, B, C, D, E.** All correct.

**Q30: C.** $2^{24}=16{,}777{,}216$.

**Q31: A, B, C, E.** D ✗: "z" means **midline**.

**Q32: A, C, D, E.** B ✗: ground potential cancels, so its location matters little.

**Q33: A, B, C, D.** A ✓: equal at neighbours cancels. B ✓: C3 appears in (T3–C3) and (C3–Cz) with opposite polarity. C ✓: the widespread wave is common to all channels, so it is in the mean. D ✓: the spike raises the mean, so other channels get −spike/5. E ✗: an ear reference does not see the scalp slow wave, so the wave stays in every channel.

**Q34: A, B, D, E.** C ✗: CAR **reduces** the impact but is not immune, and it has its own weakness (outlier channels).

**Q35: A, B, D, E.** C ✗: AgCl **reduces** capacitance and thereby **helps** low frequencies.

**Q36: A, B, C, D.** E ✗: the amplifier comes before the ADC.

---

### Block 3 — Fourier analysis (Q37–Q56)

**Q37 [C].** Select all correct about the Fourier series.
- A. Coefficients are found by minimizing the squared error between P(t) and f(t) over a period.
- B. There is no $b_0$ coefficient.
- C. $\partial P/\partial a_0 = 1/2$.
- D. The coefficients $a_n$ are obtained by correlating f(t) with $\sin(n\omega t)$.
- E. The approach relies on orthogonal functions.

**Q38 [N] (Single best answer).** A periodic signal has mean value 3. Its real Fourier coefficient $a_0$ equals:
- A. 1.5 B. 3 C. 6 D. 0

**Q39 [N].** $f(t)=5+4\cos(2\omega t)-2\sin(3\omega t)$. Select all correct.
- A. $a_0=10$.
- B. $a_2=4$.
- C. $b_3=-2$.
- D. $a_1=0$.
- E. The function is even.

**Q40 [C].** A square wave (±1) that is an odd function of time. Select all correct.
- A. All $a_n=0$.
- B. Only odd harmonics are present.
- C. Harmonic amplitudes decay like $1/n$.
- D. The fundamental amplitude is $4/\pi$.
- E. The DC component equals 1.

**Q41 [X].** Select all correct comparisons of triangle and square waves.
- A. The triangle's harmonics decay faster ($1/n^2$) than the square's ($1/n$).
- B. Both have only odd harmonics (in their symmetric forms).
- C. The triangle (even form) uses only cosines; the odd square wave uses only sines.
- D. The square wave needs more high-frequency content because of its discontinuities.
- E. Both have a nonzero DC component.

**Q42 [C].** Select all correct about the complex Fourier series.
- A. $c_0$ equals the DC component.
- B. For $n>0$, $c_n = (a_n - j b_n)/2$.
- C. $\lvert c_n\rvert$ equals half the amplitude of the $n$-th harmonic.
- D. The complex series requires integration from exactly $t=0$ to $t=T$.
- E. The complex form uses the normalization $1/T$.

**Q43 [G].** In the polar plot of a Fourier coefficient $c_n$ with real part $a_n$ and imaginary part $b_n$, select all correct.
- A. The length of the vector is $\sqrt{a_n^2+b_n^2}$.
- B. The angle $\phi_n$ represents the phase.
- C. If $b_n=0$, the phase is 0 or π.
- D. The plot shows how amplitude varies with time.
- E. A purely imaginary coefficient has phase ±π/2.

**Q44 [C].** Select all correct about Fourier transform pairs.
- A. $\delta(t)\leftrightarrow 1$.
- B. $1\leftrightarrow 2\pi\delta(\omega)$.
- C. $\cos(\omega_0t)\leftrightarrow\pi[\delta(\omega+\omega_0)+\delta(\omega-\omega_0)]$.
- D. $\sin(\omega_0t)\leftrightarrow\pi[\delta(\omega+\omega_0)+\delta(\omega-\omega_0)]$.
- E. These pairs show that time-domain and frequency-domain descriptions are interchangeable representations.

**Q45 [N].** A recording lasts 20 s at 500 Hz. Select all correct.
- A. $\Delta f=0.05$ Hz.
- B. $N=10{,}000$.
- C. The usable spectrum extends to 250 Hz.
- D. The DFT has 10,000 complex coefficients.
- E. $\Delta\omega = 2\pi\times0.05$ rad/s.

**Q46 [T].** Select all correct about the DFT derivation.
- A. The DFT arises from approximating the CFT integral by a sum over N samples.
- B. $\Delta t$ is factored out ("smuggled out") to give the standard DFT.
- C. The summation index for the inverse runs from −N/2 to N/2 inclusive.
- D. On the circular scale, −N/2 and N/2 are the same point.
- E. The inverse DFT contains a 1/N factor.

**Q47 [N] (Single best answer).** For $N=8$, $W_8^{2}$ equals:
- A. $1$ B. $-1$ C. $-j$ D. $+j$

**Q48 [N].** For $N=4$, select all correct.
- A. $W_4^{5}=-j$.
- B. $W_4^{7}=W_4^{3}=j$.
- C. $W_4^{2}=W_4^{6}=-1$.
- D. $W_4^{8}=1$.
- E. $W_4^{1}=W_4^{3}$.

**Q49 [C].** Select all correct about the FFT.
- A. It combines terms that share the same twiddle-factor values.
- B. It needs about $N\log_2N$ multiplications.
- C. For $N=16$, direct DFT needs 256 multiplications vs 64 for the FFT.
- D. It reduces the frequency resolution in exchange for speed.
- E. Its $N=4$ example splits the sum into even- and odd-indexed samples.

**Q50 [N].** A DFT of a 1 s, 1000-sample signal $x(t)=6\sin(2\pi\cdot 50 t)$ gives $\lvert X(50)\rvert = 3000$. Select all correct.
- A. The amplitude spectrum value is $\frac{2}{1000}\times3000 = 6$.
- B. The power spectrum value at 50 Hz is $3000^2/1000=9000$.
- C. $\lvert X(950)\rvert$ (the negative-frequency bin) is also 3000.
- D. The phase at 50 Hz must be normalized by N before interpretation.
- E. The 50 Hz bin index is k = 50.

**Q51 [G].** In the Ch 6 figure (10 s series, 0.5 s sampling, "Pos Freq | Neg Freq"), select all correct.
- A. The sampling rate is 2 Hz.
- B. The full frequency range around the circle is 2 Hz.
- C. The resolution is 0.1 Hz.
- D. The Nyquist frequency is 1 Hz.
- E. The spectrum's negative-frequency half differs from the positive half.

**Q52 [C].** Select all correct about windowing.
- A. Truncating a signal is equivalent to multiplying it by a rectangular window.
- B. The spectrum of the truncated signal equals the true spectrum convolved with the window spectrum.
- C. A longer rectangular window produces a narrower main lobe.
- D. Tapered windows increase sidelobe leakage.
- E. The spectrum of a finite cosine shows energy adjacent to its true frequency.

**Q53 [N] (Single best answer).** A 0.8 s rectangular window produces spectral ripples spaced by:
- A. 0.8 Hz B. 1.25 Hz C. 2.5 Hz D. 0.4 Hz

**Q54 [X].** Select all correct.
- A. Hann: $0.5+0.5\cos(\pi t/T)$.
- B. Hamming: $0.54+0.46\cos(\pi t/T)$.
- C. Bartlett is also called triangular or Fejér.
- D. The rectangular window gives the least leakage.
- E. The Hann window tapers to zero at the epoch edges.

**Q55 [S].** A heart-rate signal at 1.2 Hz has a spectrum with peaks at 1.2, 2.4 and 3.6 Hz. Select all correct.
- A. The 2.4 and 3.6 Hz peaks are likely harmonics.
- B. The waveform is not purely sinusoidal.
- C. The peaks at 2.4 and 3.6 Hz prove the presence of three independent oscillators.
- D. Harmonics appear at integer multiples of the fundamental.
- E. Removing the DC component would remove the harmonics.

**Q56 [S].** An EEG spectrum shows a large peak near 0 Hz even after subtracting the mean. Select all correct possible reasons.
- A. A slow nonperiodic trend (drift).
- B. Periodic activity with period longer than the analysis window.
- C. Sweat artifact.
- D. Aliasing of 50 Hz line noise when sampling at 1000 Hz.
- E. Physiological signals are rarely stationary.

#### Answers Q37–Q56

**Q37: A, B, C, E.** D ✗: $a_n$ uses **cosine**. $b_n$ uses sine.

**Q38: C.** DC $=\frac12a_0=3$, so $a_0=6$.

**Q39: A, B, C, D.** A ✓: DC $=5=\frac12a_0$. E ✗: the $\sin$ term makes it neither even nor odd.

**Q40: A, B, C, D.** A ✓: odd function. D ✓: $b_1=4/\pi$. E ✗: symmetric ±1 has zero DC.

**Q41: A, B, C, D.** E ✗: both are zero-mean in these forms.

**Q42: A, B, C, E.** C ✓: harmonic amplitude $=2\lvert c_n\rvert$. D ✗: any full period works.

**Q43: A, B, C, E.** D ✗: it is a complex-plane plot, not a time plot.

**Q44: A, B, C, E.** D ✗: sine has $j$ and a minus sign.

**Q45: A, B, C, D, E.** $1/20=0.05$ Hz; $N=20\times500$; Nyquist 250 Hz; one coefficient per sample; $\Delta\omega=2\pi\Delta f$.

**Q46: A, B, D, E.** C ✗: it runs from −N/2 to **N/2 − 1** (N/2 is excluded because it coincides with −N/2).

**Q47: C.** $W_8^2=e^{-j\frac{2\pi}{8}\cdot2}=e^{-j\pi/2}=-j$.

**Q48: A, B, C, D.** A ✓: $W_4^5=W_4^1=-j$. B ✓: $W_4^3=e^{-j3\pi/2}=+j$. E ✗: $-j\neq+j$.

**Q49: A, B, C, E.** C ✓: $16\log_2 16=64$. D ✗: same resolution and result.

**Q50: A, B, C, E.** B ✓: $XX^{\ast}/N$. C ✓: the power spectrum is even. D ✗: phase needs no normalization. E ✓: $f_k = k\cdot1000/1000$.

**Q51: A, B, C, D.** E ✗: the power spectrum is even (mirror).

**Q52: A, B, C, E.** D ✗: tapering **reduces** sidelobes.

**Q53: B.** $1/0.8 = 1.25$ Hz.

**Q54: A, B, C, E.** D ✗: rectangular leaks the most.

**Q55: A, B, D.** C ✗: integer multiples point to harmonics. E ✗: harmonics come from waveform shape, not DC.

**Q56: A, B, C, E.** D ✗: 50 Hz is far below Nyquist (500 Hz), so no aliasing occurs.

---

### Block 4 — Noise, random processes and averaging (Q57–Q74)

**Q57 [X].** Select all correct.
- A. Thermal noise is an example of random noise.
- B. Switching instruments can produce man-made artifacts.
- C. Dynamical noise is an independent additive term in the measurement.
- D. Systematic bias shifts measurements consistently.
- E. Temperature affecting the ion-channel kinetics during recording is dynamical noise.

**Q58 [G].** In Fig 3.1 (A: measurement noise only; B: dynamical + measurement noise), select all correct.
- A. Trace B shows slower wandering trends.
- B. Trace A looks like fast, independent fluctuations.
- C. Trace B's slower trends arise from correlation between sequential values.
- D. Both traces are from deterministic processes.
- E. Trace A's underlying process is deterministic.

**Q59 [T].** Select all correct.
- A. A stochastic process can include a deterministic component.
- B. Dynamical noise terms can act as a statistical proxy for unknown system details.
- C. A process with measurement noise only is called stochastic because the recorded signal is noisy.
- D. Eq. (2) $x_i=[0.8x_{i-1}+3.5]+D_{i-1}$ describes a stochastic process.
- E. Eq. (1) describes a deterministic process whose measurement is noisy.

**Q60 [C].** Select all correct.
- A. An ensemble is a collection of sample functions.
- B. A sample function is one realization of a random process.
- C. Amplitude histograms of sample functions can be compared to judge stationarity.
- D. Ergodicity requires that each sample function has a different mean.
- E. For a stationary ergodic process, the mean can be estimated as $\frac{1}{N}\sum x_i$ over time.

**Q61 [S].** Each trial of a process is a flat line at a random level drawn from N(0, 1) (the level differs by trial but is constant within a trial). Select all correct.
- A. The process is stationary.
- B. The process is ergodic.
- C. The time average of one trial generally does not equal the ensemble mean.
- D. Ensemble averaging across trials gives an estimate near 0.
- E. A single long trial is representative of the ensemble.

**Q62 [N].** A signal has rms 30 µV and noise rms 10 µV. Select all correct.
- A. SNR (power ratio) = 9.
- B. SNR ≈ 9.5 dB.
- C. SNR ≈ 19 dB.
- D. SNR in dB is dimensionless.
- E. If the noise rms doubles, the SNR drops by about 6 dB.

**Q63 [N] (Single best answer).** A sine wave of amplitude 10 µV has a mean-squared value of:
- A. 100 µV² B. 50 µV² C. 7.07 µV² D. 10 µV²

**Q64 [C].** Select all correct about the noise amplitude figure.
- A. Hum is among the largest noise sources (~mV).
- B. Evoked potentials are among the smallest signals.
- C. EEG is an intracellular signal.
- D. Quantization noise is smaller than amplifier noise.
- E. Noise can be comparable in amplitude to biopotentials.

**Q65 [N].** 400 trials are averaged. Single-trial noise rms = 40 µV. Select all correct.
- A. Residual noise rms ≈ 2 µV.
- B. Power SNR improves by a factor of 400.
- C. Amplitude SNR improves by a factor of 20.
- D. SNR improves by 26 dB.
- E. Signal amplitude is reduced by a factor of 20.

**Q66 [N] (Single best answer).** How many trials are needed to improve amplitude SNR by a factor of 8?
- A. 8 B. 16 C. 64 D. 512

**Q67 [S].** An average of 128 trials is split into the average of odd trials and the average of even trials. Select all correct.
- A. If the two sub-averages overlap closely, the response is reproducible.
- B. Their sum (divided appropriately) gives the full average.
- C. Their difference estimates residual noise.
- D. Their difference contains twice the signal.
- E. This is closely related to the ± average.

**Q68 [T].** Select all correct about the ± average.
- A. With an even number of trials, the consistent signal cancels exactly.
- B. It uses different data than the true average.
- C. Its residual noise rms equals that of the true average.
- D. It is invalid if the noise is Gaussian.
- E. It fails if the response changes substantially between odd and even trials.

**Q69 [S].** A spike-triggered average is computed from a continuous recording. Select all correct.
- A. Prestimulus noise estimation is appropriate because nothing happens before a spike.
- B. Prestimulus estimation is problematic because activity surrounds the spike trigger.
- C. Bootstrapping with random triggers is a sensible alternative for a control average.
- D. The ± average can be used to estimate residual noise.
- E. Bootstrapping must be done during online acquisition.

**Q70 [S].** A study uses a 2 Hz stimulus rate, and the auditory response has components lasting 600 ms. Select all correct.
- A. The inter-stimulus interval is 500 ms.
- B. Late components can spill into the next trial's prestimulus epoch.
- C. The prestimulus noise estimate may be inflated by signal.
- D. Increasing the ISI to 1 s would help.
- E. High-pass filtering slow late components could help.

**Q71 [N].** Mains frequency is 60 Hz. Which stimulus rates will phase-lock to the hum? Select all correct.
- A. 10 Hz
- B. 7.5 Hz
- C. 7.7 Hz
- D. 15 Hz
- E. 11 Hz

**Q72 [C].** Select all correct about bootstrapping.
- A. It destroys the time-locked alignment in the control average.
- B. The control average still contains the time-locked signal energy, just not aligned.
- C. Comparing true average statistics with multiple control averages helps validate the result.
- D. It requires that the time-locked component is much larger than the noise.
- E. It can be applied to stored data.

**Q73 [C].** Select all correct about background EEG.
- A. Power decreases with frequency roughly following a power law.
- B. Short EEG segments can be approximately stationary.
- C. Long-term EEG is stationary.
- D. Amplitudes are typically in the millivolt range.
- E. EEG is considered stochastic.

**Q74 [C].** Select all correct about evoked potentials.
- A. AEP, VEP and SEP respond to auditory, visual and somatosensory stimulation.
- B. The oddball P300 is a negative wave at 300 ms.
- C. The CNV is recorded at Cz and is centrofrontal.
- D. The CNV requires averaging because it is weak relative to ongoing EEG.
- E. EPs are a showcase application of signal averaging in clinical diagnosis.

#### Answers Q57–Q74

**Q57: A, B, D, E.** C ✗: dynamical noise **interacts with the process** and is not an independent measurement term.

**Q58: A, B, C, E.** D ✗: B includes dynamical noise, so it is **stochastic**.

**Q59: A, B, D, E.** C ✗: with measurement noise only, the **process** remains deterministic.

**Q60: A, B, C, E.** D ✗: ergodicity means any sample function **represents** the ensemble (same statistics).

**Q61: A, C, D.** Stationary ✓ (the distribution does not change over time). **Not ergodic** (B ✗, E ✗): one trial's time average equals its own random level, not the ensemble mean (C ✓).

**Q62: A, B, D, E.** A ✓: $(30/10)^2=9$. B ✓: $10\log_{10}9=9.54$ dB. C ✗. E ✓: power ratio falls by 4, i.e., −6 dB.

**Q63: B.** $A^2/2=50$.

**Q64: A, B, D, E.** C ✗: EEG is **extracellular**.

**Q65: A, B, C, D.** A ✓: $40/\sqrt{400}=2$. D ✓: $10\log_{10}400=26$ dB. E ✗: the signal is preserved.

**Q66: C.** $\sqrt N=8$, so $N=64$.

**Q67: A, B, C, E.** D ✗: the difference **cancels** the signal.

**Q68: A, C, E.** B ✗: same epochs. D ✗: symmetric noise distributions (like Gaussian) are exactly the ideal case.

**Q69: B, C, D.** A ✗. E ✗: bootstrapping is especially good **offline**.

**Q70: A, B, C, D, E.** 2 Hz gives a 500 ms ISI, shorter than the 600 ms response.

**Q71: A, B, D.** $60/10=6$, $60/7.5=8$ and $60/15=4$ are integers, so they lock. 7.7 (7.79 cycles) and 11 (5.45 cycles) do not. Note B: a **noninteger rate that still locks**.

**Q72: A, B, C, E.** D ✗: it requires the component to be **small** relative to noise.

**Q73: A, B, E.** C ✗: non-stationary. D ✗: ~100 **µV**.

**Q74: A, C, D, E.** B ✗: P300 is **positive**.

---

### Block 5 — Artifacts and preprocessing (Q75–Q90)

**Q75 [C].** Select all correct about line noise removal.
- A. A notch filter has a finite bandwidth (e.g., 10 Hz).
- B. Notch filtering can create transient oscillations in the baseline.
- C. Multitaper regression subtracts line noise only when statistically significant.
- D. A low-pass filter below 50 Hz never affects EEG temporal structure.
- E. Line noise spectra can show harmonics (e.g., 60 and 180 Hz).

**Q76 [G].** In the flowchart for multitaper line-noise removal, select all correct.
- A. The signal is processed in sliding time windows.
- B. Regression estimates the line-noise magnitude.
- C. A statistical test decides whether to reconstruct the line noise.
- D. After subtraction, the procedure is repeated on the noise-reduced EEG.
- E. Noise is subtracted in every window regardless of significance.

**Q77 [X].** Multitaper vs standard short-time FFT with a single taper. Select all correct.
- A. Multitaper averages spectra from several tapers.
- B. Multitaper yields smoother spectral estimates.
- C. Multitaper is better at isolating narrow low-frequency peaks.
- D. Multitaper is useful for single-trial power at high frequencies.
- E. Standard STFFT uses one taper.

**Q78 [S].** Channel T8 has a robust z-score of amplitude of 9 (threshold 5), a very low correlation with its neighbours after low-pass filtering, and a very high ratio of high- to low-frequency power. Select all correct.
- A. T8 should be flagged as bad.
- B. It should be interpolated or removed before CAR.
- C. Spherical spline interpolation could reconstruct it.
- D. It should be included in CAR because averaging will dilute it.
- E. All three detection criteria agree.

**Q79 [C].** Select all correct about ocular artifacts.
- A. The cornea is positive relative to the retina.
- B. EEG channels near the eyes are more vulnerable.
- C. Blinks produce a field that extends strongly to occipital electrodes.
- D. Bell's phenomenon refers to upward eye rolling during blinks.
- E. Blink artifacts are among the lowest-amplitude artifacts.

**Q80 [S].** A patient looks to the right. Select all correct.
- A. F8 becomes positive.
- B. F7 becomes negative.
- C. Fp1 and Fp2 show identical large positive deflections as in a blink.
- D. The polarity pattern would reverse on looking left.
- E. The artifact amplitude is largest at O1/O2.

**Q81 [C].** Select all correct about muscle artifacts.
- A. Their spectral properties vary with source.
- B. They can overlap in time with task execution.
- C. Their true profile is easy to identify because they come from one source.
- D. They are typically localized to a single electrode.
- E. They are more diverse in form than ocular artifacts.

**Q82 [X].** Select all correct.
- A. Chewing artifact: intermittent bursts of generalized very fast activity.
- B. Hypoglossal artifact: organized slow diffuse waves.
- C. Generalized periodic fast activity: faster and higher amplitude than chewing artifact.
- D. Hypoglossal artifact can be confirmed by asking the patient to say "la la la".
- E. Chewing artifact comes from the temporalis muscle.

**Q83 [S].** Sharp transients appear on the left posterior channels exactly aligned with QRS complexes. The page appears to be displayed at 60 mm/s instead of 30 mm/s. Select all correct.
- A. This is ECG artifact.
- B. Display speed should be checked and the screen calibrated before reading.
- C. This is cardioballistic artifact because it follows the QRS by ~200 ms.
- D. It is predominantly left-sided because of heart position.
- E. It is relatively low in amplitude.

**Q84 [S].** One frontal-central electrode shows a slow rounded wave about 200 ms after each QRS, and nowhere else. Select all correct.
- A. This suggests cardioballistic artifact.
- B. The electrode likely sits over an artery.
- C. It is caused by the heart's electrical field reaching the scalp simultaneously with QRS.
- D. It is a motion artifact.
- E. It is an external artifact.

**Q85 [C].** Select all correct about sweat artifact.
- A. Frequency typically below 0.5 Hz.
- B. Arises from the charge carried by NaCl in sweat.
- C. Relatively low amplitude.
- D. Always bilateral and symmetric.
- E. A high-pass filter can reduce it.

**Q86 [C].** Select all correct about artifact classes.
- A. Cell-phone charging near the subject produces an external artifact.
- B. Tongue movement produces an internal artifact.
- C. Internal artifacts can be eliminated by simply switching off equipment.
- D. External artifacts become more important as EEG moves into home healthcare.
- E. Most artifact-removal methods focus on external artifacts.

**Q87 [S].** A single channel shows a thick band of 50 Hz activity. Select all correct.
- A. A high electrode impedance at that electrode is a likely cause.
- B. Proper electrode placement could prevent it.
- C. A notch filter could substantially reduce it.
- D. It is a physiological internal artifact.
- E. If the artifact appeared on all channels referenced to one ear, the reference electrode would be suspect.

**Q88 [T].** Select all correct.
- A. Notch filtering is described in the slides as successful at removing line noise.
- B. Notch filtering can distort components between 50 and 70 Hz.
- C. Notch filtering is described as optimal with no drawbacks.
- D. Low-pass filtering below 50 Hz can cause spurious interactions between channels.
- E. Transient oscillations from notch filtering can affect interpretation.

**Q89 [C].** Select all correct about interpolation of bad channels.
- A. Nearest-neighbour averaging is one scheme.
- B. Higher-order polynomials are one scheme.
- C. Radial basis functions have lower computational load.
- D. Spherical splines are accurate with dense electrode mapping.
- E. Interpolation creates virtual channels to reconstruct global brain responses.

**Q90 [S].** You must choose the order of preprocessing steps. Select all correct.
- A. Detect bad channels before computing the common average reference.
- B. Apply CAR first, then detect bad channels via correlation.
- C. Interpolated channels can then be included in a robust average reference.
- D. An anti-aliasing filter can be applied digitally after sampling to undo aliasing.
- E. Line noise can be removed by notch or multitaper methods.

#### Answers Q75–Q90

**Q75: A, B, C, E.** D ✗: it **can** alter temporal structure.

**Q76: A, B, C, D.** E ✗: only significant noise is reconstructed and subtracted.

**Q77: A, B, D, E.** C ✗: smoothing impedes low-frequency isolation.

**Q78: A, B, C, E.** D ✗: bad channels contaminate the average.

**Q79: A, B, D.** C ✗: "without any field posteriorly". E ✗: very **high** amplitude.

**Q80: A, B, D.** C ✗: that is the blink pattern. E ✗: the effect is frontal (F7/F8).

**Q81: A, B, E.** C ✗: widespread diverse sources make identification **hard**. D ✗: wide, almost uniform distribution.

**Q82: A, B, D, E.** C ✗: it is slightly **slower** (beta) and **lower** amplitude.

**Q83: A, B, D, E.** C ✗: exact alignment with QRS means ECG artifact.

**Q84: A, B, D.** C ✗: that would be simultaneous (ECG artifact). E ✗: it is physiological, i.e., internal.

**Q85: A, B, C, E.** D ✗: bilateral, unilateral or focal.

**Q86: A, B, D.** C ✗: internal artifacts come from the body. E ✗: most methods focus on **internal** artifacts.

**Q87: A, B, C, E.** D ✗: external/electrical.

**Q88: A, B, D, E.** C ✗.

**Q89: A, B, C, D, E.** All correct.

**Q90: A, C, E.** B ✗: CAR spreads the bad channel. D ✗: aliasing cannot be undone digitally.

---

### Block 6 — Brain rhythms, filtering and labs (Q91–Q100)

**Q91 [C].** Select all correct.
- A. Delta is the slowest EEG band.
- B. Gamma is the fastest measurable EEG band.
- C. Beta (13–32 Hz) is associated with focusing on a task and learning a new concept.
- D. Alpha is associated with just before falling asleep.
- E. Delta is strongest during active problem solving.

**Q92 [T].** Select all correct.
- A. Gamma is linked to simultaneous processing of information from different brain parts.
- B. Theta is stated to probably originate in frontal areas monitoring other mental processes.
- C. Alpha is 4–8 Hz.
- D. Theta appears during tasks so automatic that the mind can disengage.
- E. Gamma is stronger in very long-term meditators.

**Q93 [S].** A neurofeedback system rewards increased 8–13 Hz power over occipital areas. Select all correct.
- A. It targets alpha.
- B. Subjects might achieve it by closing their eyes and relaxing.
- C. It targets the band associated with alert active thinking.
- D. Spectral analysis underlies such systems.
- E. It targets the band described as "the first discovered".

**Q94 [X] (Single best answer).** Which band pairing is WRONG per the course?
- A. Theta, 4–8 Hz, creativity/insight/dreams
- B. Beta, 13–32 Hz, alert consciousness
- C. Gamma, 0.5–4 Hz, heightened perception
- D. Alpha, 8–13 Hz, physically and mentally relaxed

**Q95 [C].** Select all correct about filters.
- A. A band-stop filter removes a band and passes frequencies on both sides.
- B. Ideal filters have instantaneous transitions between pass and stop bands.
- C. Realistic low-pass filters gradually attenuate above the cutoff.
- D. A high-pass filter keeps slow drifts.
- E. Filtering can be used to extract part of a signal.

**Q96 [C].** Select all correct about time-domain techniques.
- A. Cross-correlation quantifies relationships between different signals.
- B. Template matching correlates a known template with the signal.
- C. Peak detection helps compute intervals between events such as heartbeats.
- D. Level detection finds epochs where the signal falls within a certain amplitude range.
- E. Auto-correlation compares a signal with a different signal.

**Q97 [N].** In `SinWavesLab2`, fs = 500 Hz and TimeVec = 0:1/fs:1. Select all correct.
- A. There are 501 samples.
- B. The highest frequency in the sum (30 Hz) is below the Nyquist frequency.
- C. `100*randn` noise has a standard deviation of 100.
- D. The noise added with `10*randn` has 100 times less power than `100*randn` noise.
- E. The Nyquist frequency is 1000 Hz.

**Q98 [T].** Select all correct about the lab code.
- A. `Amp*exp(1i*Phase)` creates a complex number of magnitude Amp and angle Phase.
- B. `exp(2*1i*pi*f0*t + phas)` shifts the phase by `phas`.
- C. `sum(conj(a).*b)` computes the complex dot product.
- D. `angle(dotProd)` at the matching frequency gives phase information.
- E. `abs(z)` equals `sqrt(z*conj(z))` for a scalar z.

**Q99 [S].** A signal $x(t)=\sin(2\pi\cdot5t+\pi/2)$ is compared with the real sine templates $\sin(2\pi f t)$ for f = 1…10 Hz over a symmetric window. Select all correct.
- A. The dot product at 5 Hz may be near zero because of the 90° phase difference.
- B. Using complex exponential templates would reveal a strong 5 Hz match regardless of phase.
- C. The real-sine dot product is a reliable frequency detector independent of phase.
- D. The magnitude of a complex dot product measures frequency match.
- E. This is why Fourier analysis uses complex exponentials.

**Q100 [N].** `FastFourierTransformm` is modified so T = 4 s (fs = 1000 Hz), signal frequencies 4, 6, 8, 10.25 Hz. Select all correct.
- A. N = 4000.
- B. Δf = 0.25 Hz.
- C. The 10.25 Hz component falls exactly on a frequency bin.
- D. The 10.25 Hz component must leak strongly because 10.25 is not an integer frequency.
- E. The FFT still gives the same result as the double-loop DFT.

#### Answers Q91–Q100

**Q91: A, B, C, D.** E ✗: delta is deep sleep.

**Q92: A, B, D, E.** C ✗: alpha is 8–13 Hz.

**Q93: A, B, D, E.** C ✗: that is beta.

**Q94: C.** Gamma is 32–100 Hz. 0.5–4 Hz is delta.

**Q95: A, B, C, E.** D ✗: a high-pass filter **removes** slow drifts.

**Q96: A, B, C, D.** E ✗: auto-correlation compares a signal with **itself**.

**Q97: A, B, C, D.** A ✓: 0 to 1 inclusive in 1/500 steps gives 501. D ✓: power ∝ std², so $(10/100)^2=1/100$. E ✗: Nyquist is 250 Hz.

**Q98: A, C, D, E.** B ✗: `phas` is not multiplied by `1i`, so it scales the amplitude by $e^{phas}$.

**Q99: A, B, D, E.** A ✓: $\sin(\cdot+\pi/2)=\cos$, which is orthogonal to $\sin$ over a symmetric window. C ✗.

**Q100: A, B, C, E.** A ✓: $4\times1000$. B ✓: $1/4$ Hz. C ✓: $10.25/0.25=41$, an integer bin index. D ✗: what matters is whether the frequency is an integer multiple of $\Delta f$ (whole cycles in the window), not whether it is an integer in Hz. 10.25 Hz completes exactly 41 cycles in 4 s, so there is no leakage. E ✓: same result, faster.

---

## Full Mock Exam (36 Questions, Previous-Exam Format)

> **Instructions:** For each question, **select all correct statements**. The number of correct options varies. Time yourself: **70 minutes**. Scoring suggestion: 1 point per question only if your selection is exactly right, or (more lenient) +1 per correctly judged option.

### Section A: Neurophysiology basics

**M1.**
- A. Glial cells support signalling functions of nerve cells and can repair nervous system damage.
- B. Dendrites act like radio transmitters sending signals to other neurons.
- C. The number of targets innervated by one neuron represents its divergence.
- D. Some neurons, such as retinal bipolar cells, have very short axons.
- E. The soma contains the nucleus and cytoplasm.

**M2.**
- A. The Nernst equation contains the charge of the ion $z$.
- B. For K⁺ with an out:in ratio of 1:20, $E_K\approx-80$ mV at 37 °C.
- C. For Na⁺ with an out:in ratio of 10:1, $E_{Na}\approx-61.5$ mV.
- D. For Ca²⁺ the prefactor at 37 °C is about 30.77 mV.
- E. The Nernst potential is the membrane potential at which the net flux of that ion is zero.

**M3.**
- A. The Goldman equation weights ion concentrations by membrane permeabilities.
- B. The resting potential is around −65 mV in a typical neuron.
- C. If $P_{Na}$ increased greatly relative to $P_K$, $V_m$ would become more negative.
- D. The resting membrane permeability ratio $P_K:P_{Na}$ is about 40:1.
- E. If the membrane were permeable only to Na⁺, $V_m$ would approach $E_{Na}$.

**M4.**
- A. Voltage-gated channels can be forced to move by changes in membrane potential.
- B. The Na⁺/K⁺ pump moves ions down their concentration gradients without energy.
- C. Leak channels are normally open.
- D. Leak channels have different permeability for different ions.
- E. The voltage-gated channel figure shows a pore closed at −65 mV and open at −40 mV.

**M5.**
- A. During the falling phase, Na⁺ channels inactivate and K⁺ channels open.
- B. K⁺ channels open at the falling phase because they were triggered ~1 ms earlier by depolarization.
- C. The undershoot brings $V_m$ toward $E_{Na}$.
- D. At rest, both voltage-gated Na⁺ and K⁺ channels are closed.
- E. The AP overshoot reaches exactly $E_{Na}$.

**M6.**
- A. The absolute refractory period results from Na⁺ channel inactivation.
- B. During the relative refractory period no stimulus can trigger an AP.
- C. The relative refractory period lasts until voltage-gated K⁺ channels close.
- D. The all-or-none law means a stronger stimulus cannot increase AP amplitude.
- E. Increasing depolarizing current increases the AP firing rate.

**M7.**
- A. Myelin is interrupted by nodes of Ranvier.
- B. Voltage-gated Na⁺ channels are concentrated at nodes of Ranvier.
- C. One oligodendrocyte myelinates only one axon.
- D. Schwann cells are found only in the peripheral nervous system.
- E. In most sensory neurons, the spike-initiation zone is at the axon hillock.

**M8.**
- A. Otto Loewi's 1921 experiment supported chemical synaptic transmission.
- B. EPSP: transmitter-gated channels allow Na⁺ entry, depolarizing the cell.
- C. Temporal summation: EPSPs from the same presynaptic fibre firing in quick succession add together.
- D. Electrical synapses are often found where neighbouring neurons need to be highly synchronized.
- E. At a gap junction, the two membranes are separated by about 20–40 nm.
- F. Neurotransmitter release in chemical synapses depends on Ca²⁺ influx.

### Section B: EEG biophysics & acquisition

**M9.**
- A. The dipole of an individual neuron can be easily measured at the scalp.
- B. EEG is mainly generated by PSPs rather than APs.
- C. When the AP reaches postsynaptic dendrites, current enters through the synapse into the postsynaptic dendrite.
- D. Randomly oriented neurons produce dipoles that tend to cancel.
- E. Synchronized activation of similarly oriented neurons with the same transmitter type produces measurable scalp potentials.

**M10.** *(Figure: radial dipole (a) under the electrode at the gyral crown; tangential dipoles (b, c) on sulcal walls; radial dipole (d) at the bottom of the sulcus.)*
- A. Dipole (d) contributes more than (a) because it is radial.
- B. Dipole (d) contributes less than (a) because it is further from the electrode.
- C. Dipoles (b) and (c) are likely to cancel each other.
- D. EEG is equally sensitive to all orientations.
- E. The strongest EEG contribution comes from dipoles like (a).

**M11.**
- A. EEG is a direct measure of electrical brain activity.
- B. EEG spatial resolution is superior to fMRI.
- C. EEG temporal resolution is superior to fMRI and PET.
- D. EEG devices can be made small and portable.
- E. EEG requires exposure to ionizing radiation.

**M12.**
- A. Sampling a 45 Hz sine at 100 Hz satisfies the Nyquist criterion.
- B. Sampling a 45 Hz sine at 80 Hz produces an alias at 35 Hz.
- C. Sampling at 5× the maximum frequency is common to avoid time-domain distortion.
- D. The Nyquist frequency for a 1 kHz sampling rate is 1 kHz.
- E. The anti-aliasing filter must act before the ADC.

**M13.**
- A. The electrode potential at the metal–solution interface is specific to material and solution.
- B. With Ag/AgCl, low-frequency components are easier to record.
- C. Ag/AgCl electrodes increase interface capacitance.
- D. A 3-bit ADC has 8 levels (000–111).
- E. Increasing ADC bits increases the sampling rate.

**M14.** *(In EEG acquisition)*
- A. Measuring a single scalp electrode against the circuit ground mainly captures static electricity differences larger than neural activity.
- B. The ground electrode location is more important than the reference location.
- C. The EEG channel value is $V_{AG}-V_{RG}$.
- D. Noise common to both measurements relative to ground is eliminated.
- E. The reference electrode is usually placed on one or both ear lobes.
- F. The ground electrode is usually on the frontal bone to minimize muscular noise.

**M15.** *(Referencing and derivations)*
- A. In the unipolar method, all channels share one reference electrode.
- B. In the biauricular method, the reference is the average of two ear electrodes.
- C. In CAR, each channel has the mean of all channels subtracted.
- D. Laplacian and LAR are free-reference spatial filtering methods.
- E. The EEG signal from one channel reflects only the active electrode.

### Section C: Frequency domain fundamentals

**M16.**
- A. The Fourier series coefficients $a_n$ and $b_n$ are computed by integrating over one full period.
- B. $a_n=\frac{2}{T}\int_T f(t)\cos(n\omega t)dt$.
- C. $\int_T \sin(n\omega t)\cos(m\omega t)dt=T/2$ when $m=n$.
- D. For an even function, the sine coefficients vanish.
- E. The decomposition of white light by a prism is used as an analogy for spectral analysis.

**M17.**
- A. $c_n=\frac1T\int_Tf(t)e^{-jn\omega t}dt$.
- B. The complex Fourier series sums over negative and positive $n$.
- C. Euler's relation is $e^{jx}=\cos x - j\sin x$.
- D. The complex coefficients carry both amplitude and phase.
- E. Real and complex Fourier series are different, non-equivalent representations.

**M18.**
- A. A Dirac impulse in time contains all frequencies.
- B. A DC signal transforms to a flat spectrum.
- C. The CFT of $\cos(\omega_0t)$ has peaks at $\pm\omega_0$.
- D. FFT results can be used to compute the power spectrum $S=XX^{\ast}/N$.
- E. The FFT reduces multiplications from $N^2$ to $N\log_2N$.

**M19.**
- A. $W_N=e^{-j2\pi/N}$.
- B. $W_8^{0}=W_8^{8}$.
- C. $W_8^{2}=W_8^{10}$.
- D. The FFT's efficiency does not depend on the twiddle factor.
- E. The inverse DFT is $x(n)=\frac1N\sum_k X(k)W_N^{-kn}$.

**M20.**
- A. A 2-s epoch sampled at 500 Hz has 0.5 Hz precision and 250 Hz range.
- B. A 1-s epoch sampled at 2 kHz has 1 Hz precision and 1000 Hz range.
- C. Doubling the sampling rate halves the frequency precision value (improves resolution).
- D. The amplitude spectrum normalization $2/N$ makes peak heights match sine amplitudes.
- E. The phase spectrum is $\arctan(\mathrm{Im}(X)/\mathrm{Re}(X))$ and needs no normalization.

**M21.**
- A. The discrete spectrum of a pure cosine analysed over a finite epoch can show energy next to the main peak.
- B. Ripples in the rectangular-window spectrum are spaced by $1/T$; for T = 2 s this is 0.5 Hz.
- C. The Hamming window is $0.5+0.5\cos(\pi t/T)$.
- D. Physiological signals often contain both periodic and nonperiodic components.
- E. A respiratory signal with a 1.5 Hz fundamental may show a harmonic near 3 Hz.
- F. Even after DC removal, low-frequency spectral power may remain due to slow trends.

### Section D: Random processes & averaging

**M22.**
- A. In $M_i=x_i+N_i$ with $x_i=0.8x_{i-1}+3.5$, the process $x$ is deterministic.
- B. When noise $D_{i-1}$ is included in the state update, the process becomes stochastic.
- C. Dynamical noise does not interact with the process itself.
- D. Temperature fluctuations influencing membrane processes are an example of dynamical noise.
- E. Additive measurement noise produces correlated slow trends.

**M23.**
- A. A PDF must integrate to 1.
- B. The survival function is the integral of the PDF from $-\infty$ to $x$.
- C. The normal distribution has most values near the mean.
- D. The PDF of a fair die assigns 1/6 to each of the values 1–6.
- E. The cumulative function increases from 0 to 1.

**M24.**
- A. Stationarity and ergodicity are often implicitly assumed in signal processing.
- B. Ergodicity allows statistics to be obtained from averages over time.
- C. If a process is ergodic, any sample function is representative of the ensemble.
- D. Stationarity means that the amplitude distribution is identical at all times.
- E. Techniques assuming stationarity are useless when the assumption is only approximately met.

**M25.** *(Signal averaging)*
- A. The ultimate reason to perform signal averaging is to increase SNR.
- B. Averaging 64 trials reduces random noise rms by a factor of 8.
- C. Averaging 64 trials reduces the signal amplitude by a factor of 8.
- D. The average of odd trials minus the average of even trials estimates the residual noise.
- E. Averaging is robust to minor violations of its assumptions.

**M26.** *(Noise estimation)*
- A. The ± average inverts every other trial, removing the consistent signal.
- B. The ± average's residual noise rms is larger than the standard average's.
- C. The bootstrap control average is produced with random triggers.
- D. Prestimulus estimation fails for spike-triggered averages because activity surrounds the trigger.
- E. High-pass filtering late/slow components can improve prestimulus noise estimates.

**M27.** *(Periodic noise)*
- A. A 50 Hz hum can create a large 50 Hz component in an average obtained with a 10 Hz stimulus rate.
- B. With a 7.7 Hz stimulus rate, the phase of 50 Hz hum relative to stimulus onset changes each trial.
- C. Randomizing inter-stimulus intervals is a remedy.
- D. Hum is a random noise source, so it always averages out.
- E. Hum is described as "enemy #1" in biopotential recordings.

**M28.** *(Evoked potentials)*
- A. The oddball paradigm elicits the P300 in response to the rare stimulus.
- B. The P300 is centrally located and positive.
- C. The CNV is observed between a warning stimulus and a second stimulus.
- D. In the CNV example, 32 trials were enough to show the negative slope.
- E. The CNV signal is strong relative to ongoing EEG and visible in single trials.

**M29.** *(Background EEG)*
- A. Stationary windows typically last several seconds to minutes.
- B. EEG power spectral density follows a power law.
- C. EEG amplitudes are typically around 100 mV.
- D. EEG spans roughly 0.01–100 Hz.
- E. Short-term EEG is always strictly stationary.

### Section E: Artifacts & pattern recognition

**M30.**
- A. Multitaper methods are particularly effective for high-frequency activity and single-trial power estimates.
- B. Multitaper is especially appropriate below 30 Hz where SNR is low.
- C. Multitaper line-noise removal combines regression and statistical testing.
- D. Notch filter width is typically 10 Hz, which may distort activity between 50 and 70 Hz.
- E. Low-pass filtering below 50 Hz after notch filtering has no side effects.

**M31.**
- A. Bad channels can be detected by excessively large amplitudes using a robust z-score.
- B. Normal EEG shows low-frequency correlation across channels.
- C. A channel with a very low ratio of high- to low-frequency power is flagged as bad.
- D. CAR can suffer from outlier channels.
- E. Spherical splines are an interpolation method.

**M32.**
- A. Ocular artifacts are internal artifacts.
- B. The retina is positively charged relative to the cornea.
- C. Blink artifacts are maximal at Fp1 and Fp2.
- D. During a blink, the cornea moves closer to Fp1/Fp2.
- E. Blinks produce a strong field over occipital regions.

**M33.**
- A. Chewing artifact originates from the temporalis muscle.
- B. Hypoglossal artifact results from tongue movement.
- C. ECG artifact is time-locked to the QRS complex.
- D. ECG artifact is typically strongest on the right side.
- E. Cardioballistic artifact arises when an electrode is over an artery.

**M34.**
- A. Sweat artifact has very slow activity (< 0.5 Hz).
- B. Electrical artifacts at 50/60 Hz may stem from appliances or phone charging.
- C. Sweat artifact always localizes to frontal electrodes.
- D. A bad electrode can show large line-noise artifact that would be reduced by a notch filter.
- E. Muscle artifacts affect both high- and low-frequency EEG components.

### Section F: Brain rhythms

**M35.**
- A. Beta (13–32 Hz) is associated with alert, normal consciousness and active thinking.
- B. Delta (0.5–4 Hz) is strongest in dreamless restorative sleep.
- C. Gamma is described as the slowest EEG rhythm.
- D. Alpha can be found during yoga and just before falling asleep.
- E. Theta is associated with memory, creativity and psychological well-being.

**M36.**
- A. Reduced frontal gamma activity may indicate declined cognitive function.
- B. Increased midline beta activity may indicate restless legs syndrome.
- C. Brain wave patterns are identical across individuals.
- D. Various brain regions emit the same frequency simultaneously.
- E. Spectral analysis can be used for BCIs and neurofeedback.

---

## Mock Exam Answer Key and Explanations

### Section A

**M1: A, C, D, E.** B ✗: dendrites are **antennas** (receive). Axon terminals are the transmitters.

**M2: A, B, D, E.** C ✗: $E_{Na}\approx$ **+61.5 mV** (Na⁺ is concentrated outside, so the potential is positive).

**M3: A, B, D, E.** C ✗: more Na⁺ permeability pulls $V_m$ toward $E_{Na}$, i.e., **less negative / positive**.

**M4: A, C, D, E.** B ✗: the pump works **against** gradients using **ATP**.

**M5: A, B, D.** C ✗: toward **$E_K$**. E ✗: it approaches but does not reach $E_{Na}$.

**M6: A, C, D, E.** B ✗: a **larger** stimulus **can** trigger an AP in the relative refractory period.

**M7: A, B, D.** C ✗: an oligodendrocyte myelinates **several** axons. E ✗: sensory neurons initiate spikes near **sensory nerve endings**.

**M8: A, B, C, D, F.** E ✗: gap junctions are **~3 nm**. 20–40 nm is typical of the chemical synaptic cleft.

### Section B

**M9: B, C, D, E.** A ✗: a single neuron's dipole is **impossible** to measure at the scalp.

**M10: B, C, E.** A ✗: depth matters, and (d) is further away. D ✗: orientation matters.

**M11: A, C, D.** B ✗: EEG spatial resolution is **worse** than fMRI. E ✗: no radiation.

**M12: A, B, C, E.** A ✓: 100 > 90. B ✓: $\lvert45-80\rvert=35$. D ✗: Nyquist frequency = **500 Hz**.

**M13: A, B, D.** C ✗: Ag/AgCl **reduces** capacitance. E ✗: bits set amplitude resolution, not sampling rate.

**M14: A, C, D, E, F.** B ✗: the **reference** location is more important (the ground potential cancels).

**M15: A, B, C, D.** E ✗: the channel reflects **both** active and reference electrodes.

### Section C

**M16: A, B, D, E.** C ✗: sin·cos integrates to **0** for all $m,n$. $T/2$ applies to cos·cos and sin·sin when $m=n$.

**M17: A, B, D.** C ✗: $e^{jx}=\cos x+j\sin x$. E ✗: they are **equivalent**.

**M18: A, C, D, E.** B ✗: DC transforms to an **impulse at zero frequency** ($2\pi\delta(\omega)$). The flat spectrum belongs to the impulse.

**M19: A, B, C, E.** D ✗: the FFT's efficiency relies crucially on the **periodicity** of the twiddle factor.

**M20: A, B, D, E.** A ✓: $1/2$ Hz, 250 Hz. B ✓: $1/1$ Hz, 1000 Hz. C ✗: sampling rate does **not** change precision; only $T$ does.

**M21: A, B, D, E, F.** C ✗: that is **Hann**. Hamming is $0.54+0.46\cos(\pi t/T)$.

### Section D

**M22: A, B, D.** C ✗: dynamical noise **interacts** with the process. E ✗: **dynamical** noise produces correlated slow trends.

**M23: A, C, D, E.** B ✗: that is the **cumulative** function. The survival function integrates from $x$ to $\infty$ ($1-F$).

**M24: A, B, C, D.** E ✗: the slides say techniques are often useful even when assumptions are not strictly met.

**M25: A, B, D, E.** B ✓: $\sqrt{64}=8$. C ✗: the signal is **preserved**.

**M26: A, C, D, E.** B ✗: the rms is the **same**.

**M27: A, B, C, E.** D ✗: hum is **nonrandom** and survives averaging when phase-locked.

**M28: A, B, C, D.** E ✗: the CNV is **weak** and **needs averaging**.

**M29: A, B, D.** C ✗: ~100 **µV**. E ✗: "approximately", not "always strictly".

### Section E

**M30: A, C, D.** B ✗: multitaper is **less** appropriate below ~30 Hz (SNR is already high there, and smoothing blurs frequencies). E ✗: it can alter temporal structure or create spurious channel interactions.

**M31: A, B, D, E.** C ✗: a **high** high/low power ratio flags a bad channel.

**M32: A, C, D.** B ✗: the **cornea** is positive and the retina negative. E ✗: there is no posterior field.

**M33: A, B, C, E.** D ✗: ECG artifact is **left**-sided (heart on the left).

**M34: A, B, D, E.** C ✗: sweat artifact has **no specific localization**.

### Section F

**M35: A, B, D, E.** C ✗: gamma is the **fastest**. Delta is the slowest.

**M36: A, B, E.** C ✗: patterns are **unique** to each individual. D ✗: regions do **not** emit the same frequency simultaneously.

---

## Last-Minute Revision: 2 Hours, 1 Hour, 30 Minutes

### If you have 2 hours

| Minutes | Task |
|---|---|
| 0–15 | Re-read **Section 1.4 (slide inconsistencies)** and the **Common MCQ Traps** list. |
| 15–35 | **Part A** essentials: Nernst (out/in, 61.54 mV, −80/+62), Goldman (40:1, −65 mV), AP phases and gates, absolute vs relative refractory, conduction, myelin, spike-initiation zone, synapses (6 connexins, EPSP Na⁺, IPSP Cl⁻, summation). |
| 35–50 | **Part B/C** essentials: EEG = summed PSPs of aligned pyramidal cells; radial vs tangential vs deep; synchrony; why EEG. Nyquist rate vs frequency, aliasing, anti-alias before ADC, 5×, Ag/AgCl, 3-electrode differential amplifier, 10–20 naming, montages, CAR pitfalls. |
| 50–70 | **Part D:** FS coefficients, even/odd rules, complex FS facts, CFT pairs, DFT formula, twiddle $N=4$ table, $1/T$ precision and $F_s/2$ range (practice the 0.5 s and 5 s examples), FFT $N\log_2N$, $S$/$AS$/phase formulas, windows (1/T ripples, T = 4 gives 0.25 Hz), harmonics. |
| 70–90 | **Parts E/F:** measurement vs dynamical noise, stationarity/ergodicity definitions, SNR dB, $\sqrt N$, averaging assumptions, prestimulus/bootstrap/± average, hum and stimulus rate, background EEG facts, P300/CNV. |
| 90–110 | **Parts G/H/I:** notch drawbacks, multitaper pros/cons, bad-channel criteria, artifact master table, blink vs lateral eye movement, ECG vs cardioballistic, chewing/hypoglossal/sweat, band table with 4/8/13/32 and state descriptions. |
| 110–120 | Redo **10 random questions** from the mock exam that you missed earlier. |

### If you have 1 hour

1. **(10 min)** Common MCQ Traps list and Section 1.4.
2. **(10 min)** Formula Sheet: Nernst, Goldman, Nyquist, $1/T$, $F_s/2$, DFT, twiddle, spectra, SNR dB, $\sqrt N$.
3. **(15 min)** High-Yield Revision Notes 1–41 (neuro, EEG, acquisition, Fourier).
4. **(15 min)** High-Yield Revision Notes 42–66 (noise, averaging, artifacts, rhythms).
5. **(10 min)** Skim the Key Comparisons table, focusing on rows you hesitate on.

### If you have 30 minutes: the "must-not-miss" list

**Neuro**

- Nernst uses **out/in**. 61.54 mV per decade. **$E_K=-80$, $E_{Na}=+62$**.
- Resting **−65 mV** because of **some Na⁺ permeability**. **$P_K = 40\,P_{Na}$**.
- Pump = ATP, against the gradient. Leak = always open, selective.
- AP: Na⁺ in (never reaching $E_{Na}$), Na⁺ inactivation ~1 ms, delayed K⁺ out, undershoot toward $E_K$.
- **Absolute refractory** = Na⁺ inactivated. **Relative refractory** = K⁺ open, bigger stimulus needed.
- All-or-none: size fixed, **rate** codes strength.
- Passive decays in mm. Active has no decrement. Na⁺ channels at the nodes. Oligodendrocyte CNS/many, Schwann PNS/one.
- Gap junction **3 nm, 6 connexins/connexon, 2 connexons, bidirectional, fast**. EPSP **Na⁺**, IPSP **Cl⁻**.

**EEG and acquisition**

- EEG = **PSPs**, **pyramidal**, **perpendicular**, **synchronous**. Radial crown strongest; sulcal walls cancel; deep is weaker.
- Why EEG: non-invasive, direct, portable, **ms resolution**, rich, open environment, cheap. **Poor spatial resolution.**
- Nyquist **rate $2f_{max}$** vs **frequency $F_s/2$**. Anti-alias **before** ADC. 5× in practice.
- Ag/AgCl: ionic-to-electronic, **lower capacitance**, **low frequencies**.
- $C=V_{AG}-V_{RG}$. Ground location less important. **No neutral reference.** CAR sensitive to bad channels.
- 10–20: **odd left, even right, z midline**; Jasper 1958.

**Fourier**

- DC $=a_0/2$. Even gives $b_n=0$; odd gives $a_n=0$. The complex series is **equivalent**, uses exponentials, **has phase**, and the start point is irrelevant.
- $\delta\leftrightarrow1$; $1\leftrightarrow2\pi\delta$; cos gives two real lines.
- **Precision $1/T$, range $F_s/2$.** 0.5 s/1 kHz gives **2 Hz/500 Hz**; 5 s/200 Hz gives **0.2 Hz/100 Hz**.
- $W_N=e^{-j2\pi/N}$, periodic with $N$. $W_4$: 1, −j, −1, j.
- FFT **$N\log_2N$** vs $N^2$ (Cooley–Tukey 1965).
- $S=XX^{\ast}/N$; $AS=\frac2N\sqrt{XX^{\ast}}$; phase has no normalization. Power spectrum is even.
- Finite epoch = rectangular window, which convolves the spectrum and causes leakage with ripples at **$1/T$** (T = 4 gives 0.25 Hz). Hann 0.5/0.5, Hamming 0.54/0.46.
- Harmonics come from **non-sinusoidal** periodic activity.

**Noise and averaging**

- Dynamical noise gives **correlated, slow trends** and a **stochastic** process.
- **Stationary** = distribution constant. **Ergodic** = one sample function represents all.
- SNR dB $=10\log$ (power) $=20\log$ (rms).
- Noise **$/\sqrt N$**. Four assumptions: uncorrelated, known timing, consistent signal, random zero-mean noise.
- Prestimulus (late responses contaminate it), bootstrap (random triggers, offline, signal ≪ noise), **± average** (invert alternate trials, same rms).
- **10 Hz + 50 Hz hum locks.** Use a noninteger or random rate.
- Background EEG: **0.01–100 Hz, ~100 µV, power law, 5 bands, stochastic, long-term non-stationary**.
- P300 **positive 300 ms oddball**. CNV **negative** between warning and second stimulus.

**Artifacts and rhythms**

- Notch: 50/60 Hz, **distorts 50–70 Hz**, **ringing**, not optimal. Multitaper: high frequency, low SNR, blurs low frequencies.
- Internal (heart/eyes/muscle, hard to prevent) vs external (environment/electrodes, can be inhibited).
- Blink: **Bell's**, cornea closer to **Fp1/Fp2**, huge. Lateral: **F7/F8 opposite**.
- Muscle: diverse, EMG, **wide uniform**, task-related, high and low frequencies. Chewing: **temporalis**, fast bursts. Tongue: slow, "la la la".
- ECG: QRS-locked, **left**, low amplitude. Cardioballistic: artery, ~200 ms after QRS. Sweat: < 0.5 Hz.
- **δ 0.5–4** deep sleep; **θ 4–8** dreams/creativity/meditation, **frontal**; **α 8–13** eyes closed relaxed, easiest, first discovered; **β 13–32** alert/active; **γ 32–100** fastest, peak state, monks.

> **Final exam-room strategy:** judge every statement on its own. Circle absolute words. Check every number against the must-not-miss list. Watch for swapped pairs (in/out, Na⁺/K⁺/Cl⁻, alpha/beta/theta, internal/external, closer/farther, even/odd). When a statement is a slide sentence with one changed detail, it is false.

**Good luck!**
