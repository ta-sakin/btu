# Neural Signal Analysis — Previous Exam: Answers and Explanations

> Source: the 8 photographed pages in `prev-q/` (36 questions, "select **all** correct statements", number of correct options varies).
> Answers are based on the lecture slides (Chapters 1–9 and the Signal & Noise deck). Two items (Q11-D, Q18-B) are ambiguous in wording; the most likely intended answer is given with reasoning.
> Full theory for every question is in `Neural_Signal_Analysis_Exam_Guide.md`.

## Quick Answer Key

| Q | Section | Correct options |
|---|---|---|
| Q1 | A. Neurophysiology basics | A, B, D |
| Q2 | A. Neurophysiology basics | A, B, C |
| Q3 | A. Neurophysiology basics | A, D |
| Q4 | A. Neurophysiology basics | A, B |
| Q5 | A. Neurophysiology basics | A, B, C |
| Q6 | A. Neurophysiology basics | A, B, E |
| Q7 | A. Neurophysiology basics | A, B, D |
| Q8 | A. Neurophysiology basics | A, B, E, F |
| Q9 | B. EEG biophysics & acquisition | A, C, D |
| Q10 | B. EEG biophysics & acquisition | A, B |
| Q11 | B. EEG biophysics & acquisition | B, F, and most likely D |
| Q12 | B. EEG biophysics & acquisition | A, B |
| Q13 | B. EEG biophysics & acquisition | A, C |
| Q14 | B. EEG biophysics & acquisition | A, D, E |
| Q15 | B. EEG biophysics & acquisition | A, D, E |
| Q16 | C. Frequency domain fundamentals | A, B, C, E |
| Q17 | C. Frequency domain fundamentals | B, C, E |
| Q18 | C. Frequency domain fundamentals | A, C, F, and probably B |
| Q19 | C. Frequency domain fundamentals | A, E |
| Q20 | C. Frequency domain fundamentals | D, F |
| Q21 | C. Frequency domain fundamentals | A, B |
| Q22 | D. Random processes & averaging | A |
| Q23 | D. Random processes & averaging | C, D |
| Q24 | D. Random processes & averaging | A, E |
| Q25 | D. Random processes & averaging | C, E, F |
| Q26 | D. Random processes & averaging | A, E, F |
| Q27 | D. Random processes & averaging | A, C |
| Q28 | D. Random processes & averaging | C, F |
| Q29 | D. Random processes & averaging | A, B, F |
| Q30 | E. Artifacts & pattern recognition | A, C, E |
| Q31 | E. Artifacts & pattern recognition | A, C, E |
| Q32 | E. Artifacts & pattern recognition | A, C, D |
| Q33 | E. Artifacts & pattern recognition | A, B |
| Q34 | E. Artifacts & pattern recognition | A, C, E, F |
| Q35 | F. Brain rhythms | A, B, D, E |
| Q36 | F. Brain rhythms | B, C, D |

---

## Detailed Solutions

> Do this section actively. Cover the answer, decide T/F for each option, then check. Every explanation points to the concept you need (see the main guide for full theory).

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
