# Neural Signal Analysis — One-Day Q&A Revision

> **Purpose:** the most exam-relevant questions and answers from the whole course, condensed so you can finish in **one day (about 7–8 hours)**.
> **Built from:** the lecture slides (Ch 1–9, Signal & Noise deck), the MATLAB labs, and the previous exam (36 "select all correct" questions).
> **How to use:** cover the **Answer** column, answer out loud, then check. Mark every miss with ✗ and repeat those rows in the final session.

---

## Contents

- [Study Plan for the Day](#study-plan-for-the-day)
- [Part 1 — Neurophysiology (80 min)](#part-1--neurophysiology-80-min)
- [Part 2 — Brain Anatomy and Origin of EEG (35 min)](#part-2--brain-anatomy-and-origin-of-eeg-35-min)
- [Part 3 — EEG Acquisition (50 min)](#part-3--eeg-acquisition-50-min)
- [Part 4 — Fourier Analysis (80 min)](#part-4--fourier-analysis-80-min)
- [Part 5 — Noise, Random Processes, SNR (35 min)](#part-5--noise-random-processes-snr-35-min)
- [Part 6 — Signal Averaging and Evoked Potentials (40 min)](#part-6--signal-averaging-and-evoked-potentials-40-min)
- [Part 7 — Preprocessing and Artifacts (45 min)](#part-7--preprocessing-and-artifacts-45-min)
- [Part 8 — Brain Rhythms, Filters, Time-Domain Methods, Labs (25 min)](#part-8--brain-rhythms-filters-time-domain-methods-labs-25-min)
- [Part 9 — Numerical Problems with Worked Answers (40 min)](#part-9--numerical-problems-with-worked-answers-40-min)
- [Part 10 — True/False Trap Drill (30 min)](#part-10--truefalse-trap-drill-30-min)
- [Part 11 — 30 Exam-Style Multi-Select Questions (60 min)](#part-11--30-exam-style-multi-select-questions-60-min)
- [Part 12 — Final 20-Minute Cheat Sheet](#part-12--final-20-minute-cheat-sheet)

---

## Study Plan for the Day

| Session | Time | Content |
|---|---|---|
| 1 | 09:00–11:00 | Parts 1–2 (neuro + EEG origin) |
| Break | 15 min | |
| 2 | 11:15–13:30 | Parts 3–4 (acquisition + Fourier) |
| Lunch | 45 min | |
| 3 | 14:15–16:15 | Parts 5–8 (noise, averaging, artifacts, rhythms) |
| Break | 15 min | |
| 4 | 16:30–17:40 | Parts 9–10 (numericals + trap drill) |
| 5 | 17:45–18:45 | Part 11 (exam-style questions, timed) |
| 6 | 18:45–19:15 | Redo all ✗ rows + Part 12 cheat sheet |

**Exam technique (the exam is "select ALL correct"):** judge each statement on its own. Statements with *only, always, never, guarantees, optimal, irrelevant, permanently, zero noise* are almost always false. A slide sentence with one changed number, ion, direction or band is false.

---

## Part 1 — Neurophysiology (80 min)

### 1A. Cells, neuron parts, synaptic transmission

| # | Question | Answer |
|---|---|---|
| 1 | What are the two cell classes of the nervous system? | **Neurons** (electrical signalling over long distances) and **glial cells** (support). |
| 2 | Four roles of glia (slides)? | Support neuronal signalling; **repair** damage; act as **stem cells** in some areas; **prevent regeneration** in other regions. They also form myelin. |
| 3 | Function of dendrites (and analogy)? | **Receive** signals from neighbouring neurons, like a **radio antenna**. |
| 4 | Function of the axon (and analogy)? | **Transmit** signals over a distance, like **telephone wires**. |
| 5 | Function of the axon terminal? | Transmits signals to other neurons' **dendrites or somata** (or tissues), like a **radio transmitter**. |
| 6 | Soma diameter and content? | About **20 µm**; contains the **nucleus** and cytoplasm. |
| 7 | Convergence vs divergence? | **Convergence** = number of **inputs** to one neuron. **Divergence** = number of **targets** of one neuron. |
| 8 | Which neurons have a very short axon / no axon? | **Retinal bipolar** cell: short axon. **Retinal amacrine** cell: **no axon**. |
| 9 | What gives neurons different information-processing capacity? | Variation in the **size and branching of dendrites**. |
| 10 | Define synaptic transmission. | The process by which information encoded by action potentials is passed on at synaptic contacts to a target cell. |
| 11 | Sequence at a chemical synapse (short)? | AP arrives at **presynaptic** terminal, transmitter released from **vesicles** into the **cleft**, binds **receptor proteins**, generates **electrical or chemical** signals in the postsynaptic cell. |

### 1B. Ions, Nernst, Goldman

| # | Question | Answer |
|---|---|---|
| 12 | Define membrane potential. | The **electrical charge difference across the cell membrane**. |
| 13 | Three rules of ion movement? | High → low **concentration**; away from like / toward opposite **charges**; only through **permeable channels**. |
| 14 | Membrane equally permeable to Na⁺ and Cl⁻ (10 mM vs 2 mM): result? | Both diffuse to 6/6; charges balanced, so **membrane potential = 0**. |
| 15 | Membrane permeable only to Na⁺: result? | Na⁺ diffuses, charge builds up (−3/+3), electrostatic force opposes it, equilibrium with **no net Na⁺ current**. That voltage is $E_{Na}$. |
| 16 | Define the ionic equilibrium potential. | The electrical potential difference that **exactly balances an ionic concentration gradient**. |
| 17 | Write the Nernst equation. | $E_{ion}=\frac{2.303RT}{zF}\log\frac{[ion]_{out}}{[ion]_{in}}$ (**out/in**). |
| 18 | Meaning of R, T, z, F? | Gas constant; **absolute temperature**; **charge of the ion**; Faraday's constant. |
| 19 | Prefactor at 37 °C for K⁺/Na⁺/Cl⁻ and for Ca²⁺? | **61.54 mV** (z = ±1); **30.77 mV** (Ca²⁺, z = 2). |
| 20 | $E_K$ for $[K]_o:[K]_i=5:100$ (1:20)? | **−80 mV**. |
| 21 | $E_{Na}$ for $150:15$ (10:1)? | **+61.5 mV** (≈ +62). |
| 22 | $E_{Ca}$ for $2 : 0.0002$ (10,000:1)? | **+123 mV**. |
| 23 | $E_{Cl}$ for $150:13$? | **−65 mV** (z = −1 flips the sign; the slide prints "65 mV"). |
| 24 | How does temperature affect $E_{ion}$? | Through the **RT/F** term: higher T means larger magnitude. |
| 25 | Does membrane thickness or permeability appear in Nernst? | **No.** Only concentrations, charge and temperature. |
| 26 | Typical resting potential and why it differs from $E_K$? | About **−65 mV**, not −80, because the resting membrane also has **some Na⁺ permeability**. |
| 27 | Resting permeability ratio? | $P_K$ is **40 times** $P_{Na}$ (high to K⁺, low to Na⁺). |
| 28 | Write the Goldman equation (slide form). | $V_m=61.54\log\frac{P_K[K^+]_o+P_{Na}[Na^+]_o}{P_K[K^+]_i+P_{Na}[Na^+]_i}$ |
| 29 | Nernst vs Goldman in one line? | Nernst: **one ion**, equilibrium potential. Goldman: **several ions weighted by permeability**, resting $V_m$. |
| 30 | What happens to $V_m$ if $P_{Na}\to0$? | Goldman reduces to Nernst for K⁺, so $V_m\to E_K$ (−80 mV). |

### 1C. Channels and pump

| # | Question | Answer |
|---|---|---|
| 31 | Leak channels? | **Normally open**; **different permeability for different ions**; passive (no ATP). |
| 32 | Sodium–potassium pump? | Transports ions **against their concentration gradients** using **metabolic energy (ATP)**. |
| 33 | Voltage-gated channels? | Gated by **changes in membrane voltage** (figure: closed at −65 mV, open at −40 mV). |
| 34 | Which one uses ATP directly? | Only the **pump**. Channels are passive. |

### 1D. Action potential

| # | Question | Answer |
|---|---|---|
| 35 | State of voltage-gated channels at rest (−65 mV)? | **Both** voltage-gated Na⁺ and K⁺ channels are **closed**. |
| 36 | Define threshold. | The $V_m$ at which enough voltage-gated Na⁺ channels open that relative permeability **favours Na⁺ over K⁺**. |
| 37 | Rising phase? | Na⁺ **floods in** down its gradient (large driving force when inside is negative); rapid depolarization. |
| 38 | Overshoot? | $V_m$ goes positive, close to $E_{Na}$ (> 0 mV), but **never reaches $E_{Na}$** because Na⁺ channels quickly close. |
| 39 | Two gates of the Na⁺ channel? | **Activation gate** (opens on depolarization) and **inactivation gate** (closes **~1 ms** after activation). |
| 40 | Falling phase (two reasons)? | **Na⁺ channels inactivate** and **voltage-gated K⁺ channels open** (triggered ~1 ms earlier); K⁺ flows out. |
| 41 | Undershoot? | K⁺ channels stay open, little Na⁺ permeability, so $V_m$ goes **toward $E_K$**, hyperpolarized relative to rest. |
| 42 | Direction of summed Na⁺ and K⁺ currents? | Na⁺: brief **inward**. K⁺: slower **outward**. Net: inward then outward. |
| 43 | Absolute refractory period cause? | **Na⁺ channels are inactivated**; no AP until the membrane is negative enough to de-inactivate them. |
| 44 | Relative refractory period cause? | Membrane **hyperpolarized** while **K⁺ channels remain open**; Na⁺ channels are responsive again, but **more depolarizing current** is needed. |
| 45 | All-or-none law? | AP strength does **not** depend on stimulus strength. |
| 46 | How is stimulus strength coded then? | By **firing rate**: rate increases with depolarizing current. |
| 47 | Responses to hyperpolarizing and small depolarizing currents? | Only **passive** responses; APs only when threshold is reached. |

### 1E. Conduction, myelin, spike-initiation zone

| # | Question | Answer |
|---|---|---|
| 48 | Passive conduction? | Subthreshold potential **decays with distance** as current leaks out; small fraction within **a few mm**. |
| 49 | Active conduction? | AP amplitude **constant** ("without decrement"); only **arrival time** is delayed. |
| 50 | What are nodes of Ranvier? | Gaps in the myelin every few mm where the axon is exposed to extracellular fluid. |
| 51 | Where are voltage-gated Na⁺ channels in myelinated axons? | **Concentrated at the nodes.** |
| 52 | Saltatory conduction? | Excitation occurs only at nodes; current **jumps node to node**, faster conduction. |
| 53 | Oligodendrocytes vs Schwann cells? | Oligodendrocytes: **CNS**, one cell myelinates **several axons**. Schwann: **PNS**, **one axon** each. |
| 54 | Why don't dendrites/soma usually fire Na⁺ APs? | They have **very few voltage-gated Na⁺ channels**. |
| 55 | Spike-initiation zone in a CNS pyramidal neuron? | The **axon hillock**. |
| 56 | Spike-initiation zone in a primary sensory neuron? | Near the **sensory nerve endings**. |

### 1F. Synapses and summation

| # | Question | Answer |
|---|---|---|
| 57 | Who supported chemical synapses in 1921 and how? | **Otto Loewi**: stimulated the **vagus** of frog heart A, transferred fluid, heart B slowed. |
| 58 | Who showed neuromuscular transmission is chemical? | **Bernard Katz** (University College London). |
| 59 | Who proved electrical synapses exist? | **Furshpan and Potter**, late **1950s**. |
| 60 | Gap junction spacing? | About **3 nm** (3.5 nm in figure). |
| 61 | Connexin, connexon, gap-junction channel? | **6 connexins** form a connexon; **2 connexons** (one per cell) form a channel. |
| 62 | Direction and speed of electrical synapses? | Mostly **bidirectional**; **very fast**, very little delay. |
| 63 | Where are electrical synapses found? | Where neighbouring neurons must be **highly synchronized**. |
| 64 | Which ion generates the EPSP (slide)? | **Na⁺ entry**, depolarization. |
| 65 | Which ion generates the IPSP (slide)? | **Cl⁻ entry**, hyperpolarization. |
| 66 | Role of Ca²⁺ at chemical synapses? | Presynaptic depolarization opens **voltage-gated Ca²⁺ channels**; Ca²⁺ influx makes vesicles **fuse**; transmitter released by **exocytosis**. |
| 67 | How is transmitter removed? | **Glial uptake** or **enzymatic degradation**. |
| 68 | Spatial vs temporal summation? | **Spatial**: different inputs active **at the same time**. **Temporal**: **same** input firing in quick succession. |
| 69 | E1+E2+I scenario? | E1 or E2 alone subthreshold; E1+E2 suprathreshold (AP); adding I keeps the neuron **below threshold**. |
| 70 | Excitatory vs inhibitory transmitters? | Excitatory: **glutamate, ACh**, catecholamines, serotonin, histamine, ATP. Inhibitory: **GABA, glycine**. Both: neuropeptides, NO. Endocannabinoids: "inhibit inhibition". |

---

## Part 2 — Brain Anatomy and Origin of EEG (35 min)

| # | Question | Answer |
|---|---|---|
| 71 | Three major parts of the brain? | **Cerebrum**, **brain stem**, **cerebellum** (coordination, timing, motor learning). |
| 72 | Gyri, sulci, fissures? | Bumps; grooves; especially deep grooves. |
| 73 | Precentral vs postcentral gyrus? | Precentral (anterior to central sulcus): **voluntary movement**. Postcentral: **somatic sensation**. |
| 74 | What separates frontal and parietal lobes? What lies below the lateral fissure? | The **central sulcus**; the **temporal lobe** lies ventral to the lateral (Sylvian) fissure. |
| 75 | Insula? | Buried cortex, seen by pulling apart the lateral fissure; separates **temporal and frontal** lobes; taste and visceral sensation. |
| 76 | Broca vs Wernicke? | **Broca** (frontal): speech **production**. **Wernicke** (temporal): language **comprehension**. |
| 77 | Occipital lobe? | Primary visual cortex (awareness) and visual association cortex (colour, angle, movement, recognition). |
| 78 | Invasiveness of EEG, MEG, ECoG, LFP, patch clamp, fMRI? | Non-invasive: EEG, MEG, fMRI. **Semi-invasive: ECoG.** Invasive: LFP, APs, patch clamp. |
| 79 | What does fMRI rely on? | Coupling of **cerebral blood flow and neuronal activation** (indirect, slow). |
| 80 | What does EEG mainly record? | **Extracellular currents** from **synaptic activity in dendrites** of cortical neurons. |
| 81 | What mainly generates the extracellular field? | **Postsynaptic potentials** (EPSPs/IPSPs), not action potentials. |
| 82 | Why pyramidal cells? | Mostly excitatory and **spatially aligned perpendicular to the cortex**, so their dipoles add. |
| 83 | Can a single neuron's dipole be measured at the scalp? | **No**; only the sum of many dipoles under specific conditions. |
| 84 | Which dipole orientation gives the strongest EEG? | **Radial** dipoles at the **gyral crown** (case a). |
| 85 | Why are sulcal-wall (tangential) dipoles poorly measured? | Dipoles on **opposing sides of a sulcus** have **opposite polarity** and **cancel**. |
| 86 | Why does a dipole at the bottom of a sulcus contribute less? | It is **further from the electrode**. |
| 87 | Irregular vs synchronized activation of six neurons? | Irregular: **small** summed amplitude. Synchronized: **large** amplitude. |
| 88 | Two cancellation conditions? | **Random orientation**; adjacent neurons receiving **excitatory vs inhibitory** input (opposite dipoles). |
| 89 | Condition for measurable scalp EEG? | Many neurons with **similar orientation**, **same transmitter type**, activated **at about the same moment**. |
| 90 | Seven advantages of EEG? | Non-invasive (no radiation/magnetic field); **direct** electrical measure; small/portable; **high temporal resolution** (matches speed of cognition); rich information (oscillations, synchronization, connectivity); open environment; economical. |
| 91 | Main weakness of EEG? | **Poor spatial resolution.** |

---

## Part 3 — EEG Acquisition (50 min)

| # | Question | Answer |
|---|---|---|
| 92 | Order of the acquisition chain? | Electrodes → pre-amplifier → amplifier → band filter → notch filter → **anti-alias filter** → **S/H** → MUX → ADC. |
| 93 | Role of the anti-aliasing filter? | Attenuates frequencies **too high to be digitized**, **before** the ADC. |
| 94 | Role of sample-and-hold? | Samples the analog signal and **holds it constant during conversion**. |
| 95 | Fundamental problem with metal electrodes? | The **metal–solution interface** creates an **electrode potential** (material- and solution-specific). |
| 96 | When is electrode potential not a problem? | When both electrodes are of the **same material**. |
| 97 | Three benefits of the AgCl coating? | Eases **ionic → electronic** conduction; **reduces electrode capacitance**; makes **low-frequency** signals easier to record. |
| 98 | Electrode equivalent circuit? | **Resistor in parallel with a capacitor**. |
| 99 | Biomedical signals are analog: what two discretizations? | **Time** by sampling; **amplitude** by the ADC (rounding to integers). |
| 100 | Unit of ADC amplitude resolution; levels of 3 bits? | **Bits**; $2^3 =$ **8 levels** (000–111). |
| 101 | Dirac delta properties? | Zero except at 0; integral (or sum) = **1**; derivative of the **unit step**; limit of a pulse of width τ and height 1/τ. |
| 102 | How is sampling modelled? | Multiplying $x(t)$ by a **Dirac comb**: $x^s=x(t)\sum\delta(t-nT_s)$. |
| 103 | What does sampling do to the spectrum? | **Convolves** it with a comb, making it **periodic with period $F_s$**. Overlap = **aliasing**. |
| 104 | Nyquist sampling rate for a 20 Hz sine? | **40 Hz** (minimum = $2f_{max}$). |
| 105 | Nyquist frequency? | **$F_s/2$**, the highest frequency representable. **Not** the same as the Nyquist rate. |
| 106 | 20 Hz sine sampled at 500, 59, 24 Hz? | 500: clean; 59: frequency preserved but waveform looks distorted; 24: **aliased to 4 Hz**. |
| 107 | Sampled exactly at peaks/valleys at 40 Hz? | Looks like a 20 Hz **triangular** wave. |
| 108 | Practical sampling rule? | Sample at **5×** the maximum frequency; always use an anti-alias filter. |
| 109 | Who proposed the 10–20 system and when? | **Herbert Jasper, 1958**. |
| 110 | What do 10 and 20 mean? | **Percentages** of nasion–inion / preauricular distances: edge electrodes 10%, others 20% apart. |
| 111 | Naming rules? | Letter = region (Fp, F, C, P, O, T, A); **odd = left**, **even = right**, **z = midline**. |
| 112 | Why not one electrode vs circuit ground? | It would mainly measure **static electricity** differences, much larger than neural activity. |
| 113 | Three electrodes per EEG channel? | **Active (A)**, **reference (R)**, **ground (G)**. |
| 114 | Differential amplifier output? | $C = V_{AG}-V_{RG}$; noise **common** to both is eliminated. |
| 115 | Where is the ground placed and does its location matter? | Usually **frontal bone** (reduce muscle noise); its potential cancels, so location is **less important than the reference**. |
| 116 | Is there a neutral reference site? | **No.** Each channel reflects **both** active and reference electrodes. Usually on ear lobe(s). |
| 117 | Slide example O1 (G frontal, R left ear): sign? | $V_{AG} < V_{RG}$, so O1 is **negative**. |
| 118 | When does common-mode rejection fail? | When interference is **not identical** at both inputs, e.g., an artifact at only one electrode remains. |
| 119 | Bipolar derivation? | Differences between **neighbouring** electrodes (e.g., $V_{A1G}-V_{A2G}$); removes activity common to both. |
| 120 | Unipolar (common reference)? | Every active electrode minus the **same reference** R. |
| 121 | Biauricular reference? | $V'_{RG}=(V_{R1G}+V_{R2G})/2$, the average of the two ears. |
| 122 | Common average reference (CAR)? | Subtract the **mean of all channels** from each channel. |
| 123 | Other free-reference methods? | **Laplacian** and **local average reference (LAR)** (spatial filters). |
| 124 | Requirements for a good reference? | Stays unchanged relative to EEG, **comparable amplitude**, **no correlation with task-induced activity**. |
| 125 | CAR advantage and weakness? | Reduces **single-point failure** impact; **suffers from outlier (bad) channels**, so remove bad channels first (robust average reference). |
| 126 | Can changing the reference change waveforms/topography? | **Yes**, even with unchanged brain activity. |

---

## Part 4 — Fourier Analysis (80 min)

### 4A. Fourier series

| # | Question | Answer |
|---|---|---|
| 127 | What does the Fourier series represent? | A **periodic** function $f(t)=f(t+T)$ as a **sum of sines and cosines**. |
| 128 | Real Fourier series formula? | $P(t)=\frac12a_0+\sum_{n=1}^{\infty}[a_n\cos n\omega t+b_n\sin n\omega t]$ |
| 129 | Definition of ω? | $\omega=2\pi f$, $f=1/T$. |
| 130 | What is the DC component? | $\frac12 a_0$ (the mean). |
| 131 | What are the AC components? | Sine/cosine terms weighted by $a_n$, $b_n$. |
| 132 | Coefficient formulas? | $a_0=\frac2T\int_Tf\,dt$; $a_n=\frac2T\int_Tf\cos n\omega t\,dt$; $b_n=\frac2T\int_Tf\sin n\omega t\,dt$. |
| 133 | How are the coefficients derived? | Minimize $E^2=\int_T[P-f]^2dt$: set $\partial E^2/\partial a_n=0$ and $\partial E^2/\partial b_n=0$. |
| 134 | Two properties used? | Integral of sin/cos over whole periods is **0**; **orthogonality**. |
| 135 | Orthogonality results? | $\int_T\cos n\omega t\cos m\omega t=T/2$ if $m=n$, else 0 (same for sin·sin); $\int_T\sin\cdot\cos=0$ always. |
| 136 | Is there a $b_0$? | **No.** |
| 137 | Even function consequence? | $f(t)=f(-t)$ gives **$b_n=0$** (cosines only). |
| 138 | Odd function consequence? | $f(t)=-f(-t)$ gives **$a_n=0$** (sines only). |
| 139 | Triangle wave (even, zero mean) coefficients? | $a_0=0$, $b_n=0$, $a_n=\frac{8A}{n^2\pi^2}$ for **odd n**, 0 for even n. |
| 140 | Square wave (±1) spectrum? | Odd harmonics with amplitude $\frac{4}{n\pi}$ (decay 1/n); the sum of 5 sines approximates it. |
| 141 | Analogies for spectral decomposition? | A **prism** splitting white light; sound split into **pure tones**. |

### 4B. Complex series and transforms

| # | Question | Answer |
|---|---|---|
| 142 | Complex Fourier series? | $P(t)=\sum_{-\infty}^{\infty}c_ne^{jn\omega t}$, $c_n=\frac1T\int_Tf e^{-jn\omega t}dt$. |
| 143 | Does the integration start point matter? | **No**, any full period (e.g., −T/2→T/2 or 0→T). |
| 144 | What links real and complex forms? | **Euler's relation** $e^{jx}=\cos x+j\sin x$; the notations are **equivalent**. |
| 145 | Relation between $c_n$ and $a_n,b_n$? | $c_0=a_0/2$; $c_n=(a_n-jb_n)/2$; $c_{-n}=\overline{c_n}$. |
| 146 | Does the complex series contain phase? | **Yes**: the angle of $c_n$. |
| 147 | CFT and inverse? | $F(j\omega)=\int f(t)e^{-j\omega t}dt$; $f(t)=\frac1{2\pi}\int F(j\omega)e^{j\omega t}d\omega$. |
| 148 | FT of $\delta(t)$? | **1**: all frequencies. |
| 149 | FT of a DC signal (1)? | $2\pi\delta(\omega)$: an impulse at **zero** frequency. |
| 150 | FT of $\cos\omega_0t$ and $\sin\omega_0t$? | $\pi[\delta(\omega+\omega_0)+\delta(\omega-\omega_0)]$; $j\pi[\delta(\omega+\omega_0)-\delta(\omega-\omega_0)]$. |
| 151 | Order of Fourier methods on the overview slide? | Real FS → complex FS → CFT → DFT → FFT → power spectrum $S=XX^{\ast}/N$. |

### 4C. DFT, twiddle factor, FFT

| # | Question | Answer |
|---|---|---|
| 152 | Why must DFT scales be finite and related? | We analyse **sampled real-world signals** over a **finite interval**. |
| 153 | Frequency precision? | $\Delta f=1/T$ (T = epoch length). Example: T = 10 s gives **0.1 Hz**. |
| 154 | Frequency range? | Full circle $1/\Delta t=F_s$ (1 ms gives 1000 Hz); displayed up to **$F_s/2$**. |
| 155 | Angular step and range? | $\Delta\omega=2\pi/(N\Delta t)$; $\Omega=2\pi/\Delta t$. |
| 156 | DFT formula? | $X(k)=\sum_{n=0}^{N-1}x(n)W_N^{kn}$ |
| 157 | Inverse DFT? | $x(n)=\frac1N\sum_{k=0}^{N-1}X(k)W_N^{-kn}$ |
| 158 | What is "smuggled out" in the derivation? | **$\Delta t$**, and $f(t_n)\to x(n)$, $F_a(j\omega_k)\to X(k)$. |
| 159 | Why does the inverse sum stop at N/2 − 1? | On the circular scale **−N/2 and N/2 are the same point**. |
| 160 | Twiddle factor? | $W_N=e^{-j2\pi/N}$, a point on the unit circle. |
| 161 | Key property of the twiddle factor? | **Periodic**: $W_N^m=W_N^{m+N}$ (cycle completes in N steps). |
| 162 | $W_4^0 … W_4^4$? | $1, -j, -1, +j, 1$. So $W_4^0=W_4^4$, $W_4^1=W_4^5$, $W_4^2=W_4^6=-1$. |
| 163 | $N=8$ examples on the slide? | $W_8^0=W_8^8$, $W_8^2=W_8^{10}$. |
| 164 | Who introduced the FFT and when? | **Cooley and Tukey, 1965**. |
| 165 | FFT vs DFT cost? | DFT **$N^2$** multiplications; FFT **$N\log_2N$**. |
| 166 | How does the FFT save work? | Uses **twiddle periodicity** to combine terms (split even/odd samples; $W_4^{(2r+1)k}=W_4^{2rk}W_4^k$). |
| 167 | Is the FFT a filter or an approximation? | **Neither**: an exact, faster **algorithm** for the DFT on sampled data. |

### 4D. Spectra, epoch length, windows

| # | Question | Answer |
|---|---|---|
| 168 | Power spectrum? | $S = XX^{\ast}/N$: **power vs frequency**. |
| 169 | Amplitude spectrum? | $AS=\frac2N\sqrt{XX^{\ast}}$ (square root of power; 2/N makes peaks match sine amplitudes). |
| 170 | Phase spectrum and normalization? | $\varphi=\arctan(\mathrm{Im}X/\mathrm{Re}X)$; **no normalization** needed. |
| 171 | Positive and negative frequencies on the circle? | **0→π positive**, **π→2π negative**. |
| 172 | Why show only half the spectrum? | The power spectrum is **even**; show up to **Nyquist**. |
| 173 | 10 s sampled every 0.5 s? | Precision **0.1 Hz**; full range **2 Hz** (shown to 1 Hz). |
| 174 | 0.5 s at 1 kHz? | Precision **2 Hz**; range **500 Hz**. |
| 175 | 5 s at 200 Hz? | Precision **0.2 Hz**; range **100 Hz**. |
| 176 | What improves precision? What improves range? | Longer **epoch** improves precision. Higher **sampling rate** extends range. |
| 177 | What does a finite epoch do implicitly? | Multiplies the signal by a **rectangular window**. |
| 178 | Consequence in frequency? | **Convolution** with the window spectrum: ripples/leakage; energy **adjacent** to a pure tone's peak. |
| 179 | Ripple spacing of rectangular windows? | **1/T**: T = 4 → **0.25 Hz**, T = 2 → 0.5 Hz, T = 1 → 1 Hz. |
| 180 | Window formulas? | Rectangular 1; Bartlett $1-\lvert t\rvert/T$; **Hann** $0.5+0.5\cos(\pi t/T)$; **Hamming** $0.54+0.46\cos(\pi t/T)$. |
| 181 | EEG O2 spectrum example? | Strong **alpha**, peak **slightly below 10 Hz** (smoothed with a 1.5 Hz window). |
| 182 | Why are physiological spectra tricky? | Rarely **stationary**; periodic + nonperiodic components; low-frequency power from **trends** or periods longer than the window; high-frequency contamination from **sudden events**; **harmonics**. |
| 183 | Why do harmonics appear? | Periodic activity is **not purely sinusoidal** (e.g., respiration peak 1.5 Hz, harmonic ≈ 3 Hz). |

---

## Part 5 — Noise, Random Processes, SNR (35 min)

| # | Question | Answer |
|---|---|---|
| 184 | Examples of man-made noise? | **Switching instruments**; **50–60 Hz hum** from power lines. |
| 185 | Example of random noise? | **Thermal noise** from resistors. |
| 186 | Two kinds of measurement-procedure noise? | **Systematic bias** (appetite after dinner) and **random measurement noise**. |
| 187 | Measurement noise model? | $M_i=x_i+N_i$, $x_i=0.8x_{i-1}+3.5$: **deterministic** process, noisy measurement. |
| 188 | Dynamical noise model? | $x_i=[0.8x_{i-1}+3.5]+D_{i-1}$: noise enters the process, so it is **stochastic**. |
| 189 | Example of dynamical noise? | **Temperature fluctuations** that physically influence membrane-potential processes. |
| 190 | Visual difference between the two noise types? | Dynamical noise gives **correlated sequential values**, so **slower trends**. |
| 191 | Why use dynamical noise terms? | As a **statistical proxy** for unknown details of complex systems. |
| 192 | PDF properties? | Describes the probability of values; $\int p(x)dx=1$. |
| 193 | Cumulative and survival functions? | $F(x)=\int_{-\infty}^xp$; survival $=1-F(x)=\int_x^{\infty}p$. |
| 194 | Three PDF examples? | Fair die (1/6 each); uniform continuous 0–6; **normal** (values cluster near the mean). |
| 195 | Sample function and ensemble? | One realization of a random process; a **collection** of sample functions. |
| 196 | Stationary? | The **distribution** generating x(t) **does not change over time**. |
| 197 | Ergodic? | **Any sample function represents the whole ensemble**, so statistics can come from **time averages**. |
| 198 | Estimators for a stationary ergodic process? | $\hat x=\frac1N\sum x_i$; $\widehat{Var}=\frac1N\sum(x_i-\hat x)^2$. |
| 199 | Are these assumptions strictly needed in practice? | No: often implicitly assumed; techniques remain **useful when not strictly met**. |
| 200 | ms and rms? | $ms=\frac1N\sum x_i^2$; $rms=\sqrt{ms}$. |
| 201 | SNR and SNR in dB? | $ms_{signal}/ms_{noise}$; $10\log_{10}(ms_s/ms_n)$ dB ($=20\log_{10}$ of rms ratio). |
| 202 | Units of dB SNR; what is FOM? | **Dimensionless**; SNR without log is used as a **figure of merit** by manufacturers. |
| 203 | Amplitude order: EP, EEG, EMG/ECG, intracellular? | EP (~µV and below) < **EEG** (tens of µV) < EMG/ECG (~mV) < intracellular (tens of mV). |
| 204 | Noise order? | Quantization < amplifier < giga-seal < **hum** (largest). |
| 205 | "Enemy #1" in biopotential recording? | **Hum** (nonrandom; can spoil averaging). |

---

## Part 6 — Signal Averaging and Evoked Potentials (40 min)

| # | Question | Answer |
|---|---|---|
| 206 | Four assumptions of signal averaging? | (1) Signal and noise **uncorrelated**; (2) **timing known**; (3) signal **consistent** across trials; (4) noise **random, zero mean**. |
| 207 | Is averaging robust? | Yes, to **minor violations**. |
| 208 | Ultimate reason to average? | To **increase SNR**. |
| 209 | How does residual noise scale with N trials? | rms falls as **$1/\sqrt N$**; signal preserved; power SNR ×N. |
| 210 | 256 trials reduce noise rms by? | **16×**. |
| 211 | What do odd and even sub-averages show? | If they overlap, the response is reproducible; their **sum** = average, **difference** = residual noise estimate. |
| 212 | Three residual-noise estimation methods? | **Prestimulus noise**, **bootstrap**, **± average**. |
| 213 | Prestimulus assumption? | The time-locked signal occurs **only after the trigger**. |
| 214 | When does prestimulus estimation fail? | **Spike-triggered averages** (activity surrounds the trigger); EPs where **late components** overlap the next prestimulus epoch. |
| 215 | Mitigations for prestimulus problems? | **Longer inter-stimulus intervals**; **high-pass** filtering of late/slow components; another estimator. |
| 216 | Bootstrap method? | Control average with **random triggers**; time-locking destroyed so the signal is **not enhanced** (but still present). |
| 217 | When does bootstrap work well? | **Offline** (stored data) and when time-locked power is **small** relative to noise. |
| 218 | How is bootstrap used for validation? | Repeat many times; compare control-average statistics with the true average. |
| 219 | ± average? | **Invert every other trial** then average; consistent signal cancels, noise remains. |
| 220 | Residual noise rms of ± average vs true average? | **The same** (inverted random noise has the same distribution). |
| 221 | 50 Hz hum with 10 Hz stimulus rate? | Onsets hit the **same hum phase**, so a **large 50 Hz** artifact survives. |
| 222 | 7.7 Hz rate? | Relative hum phase **changes** every stimulus, so hum averages out. |
| 223 | Remedies for hum phase-locking? | **Randomize the stimulus interval** or use a **noninteger stimulus rate**. |
| 224 | Precise locking condition? | $f_{hum}/f_{stim}$ is an **integer** (e.g., 50/12.5 = 4 locks despite a noninteger rate). |
| 225 | Background EEG facts? | **0.01–100 Hz**; **~100 µV**; **power-law** PSD; **5 bands**; **stochastic**; long-term **non-stationary**; short-term approximately stationary (**seconds–minutes**). |
| 226 | Most common physiological EEG contaminants? | **Ocular**, **muscular**, **cardiac**. |
| 227 | Common clinical EPs? | **AEP** (auditory), **VEP** (visual), **SEP** (somatosensory): primary perception. |
| 228 | Oddball paradigm and P300? | Frequent stimuli with occasional **rare** stimulus; **central positive wave at ~300 ms**; reflects **novelty**. |
| 229 | CNV paradigm? | **Warning stimulus** (tone burst) then **second stimulus** turned off by **button press**; **centrofrontal negative** wave between them, recorded at **Cz**. |
| 230 | Why must the CNV be averaged? | It is **weak relative to ongoing EEG**; **32 trials** revealed it; ± average estimates residual noise. |

---

## Part 7 — Preprocessing and Artifacts (45 min)

### 7A. Line noise, multitaper, bad channels

| # | Question | Answer |
|---|---|---|
| 231 | Notch filter use and width? | Removes **50/60 Hz** line noise; width e.g. **10 Hz**. |
| 232 | Notch filter drawbacks? | May **distort 50–70 Hz** components; **transient oscillations** in baseline. |
| 233 | Drawback of follow-up low-pass below 50 Hz? | Can **alter EEG temporal structure** or cause **spurious inter-channel interactions**. |
| 234 | Multitaper line-noise removal pipeline? | Sliding window → multitaper transform → **regression** → **statistical test** → subtract if significant → repeat. |
| 235 | What is a multitaper spectrum? | Data multiplied by **several tapers**; power spectra **averaged** (STFFT uses one taper). |
| 236 | When is multitaper useful? | **Low SNR**, **higher frequencies**, **single-trial** power. |
| 237 | When is multitaper less appropriate? | Below **~30 Hz**: SNR already high, and **spectral smoothing** merges nearby bands. |
| 238 | Three bad-channel detection criteria? | **Robust z-score** of amplitude; **low correlation** with other channels (after low-pass); high **high/low frequency power ratio**. |
| 239 | Why does correlation work? | Normal EEG shows **low-frequency correlations** across channels. |
| 240 | Interpolation schemes? | **Spherical splines** (accurate, dense electrodes), higher-order polynomials, nearest-neighbour averaging, **radial basis functions** (cheap). |

### 7B. Artifacts

| # | Question | Answer |
|---|---|---|
| 241 | Two classes of artifact source? | **Internal** (heart, eyes, muscles) and **external** (environment/wireless, electrode attachment, recording equipment). |
| 242 | Which class can be inhibited once identified? | **External.** Internal artifacts permeate EEG and are hard to prevent. |
| 243 | Why handle external artifacts? | EEG is moving toward **in-home healthcare**. |
| 244 | Which class do most removal methods target? | **Internal.** |
| 245 | Charge of cornea and retina? | Cornea **positive**, retina **negative**. |
| 246 | Bell's phenomenon? | During blinking the eyes **roll up slightly**. |
| 247 | Blink artifact location and mechanism? | Cornea moves **closer to Fp1/Fp2**; **very high amplitude**, bifrontal, no posterior field. |
| 248 | Lateral eye movement signature? | **Opposite polarities at F7 and F8**; looking right moves the right cornea toward **F8**. |
| 249 | Muscle artifact features? | From muscle contractions; **diverse forms**; detected by **EMG**; **wide, almost uniform scalp distribution**; task-related timing; affects **high and low** frequencies. |
| 250 | Chewing artifact? | **Temporalis muscle**; sudden, intermittent bursts of **generalized very fast** activity. |
| 251 | How does it differ from generalized periodic fast activity? | GPFA is **slightly slower (beta)** and **lower amplitude**. |
| 252 | Hypoglossal artifact? | **Tongue** movement; synchronous **slow diffuse** waves; reproducible by saying **"la la la"**. |
| 253 | ECG artifact? | **Time-locked to QRS**; mostly **left side**; **relatively low amplitude**. |
| 254 | Cardioballistic artifact? | Electrode **over an artery**; pulse-induced **motion** wave ~**200 ms after QRS**. |
| 255 | Electrode/electrical artifact? | **50/60 Hz** from wiring, appliances, phone charging; bad electrode shows in its derivations; **notch** reduces it. |
| 256 | Sweat artifact? | **< 0.5 Hz**, **low amplitude**, from **NaCl** charge; any localization (bilateral, unilateral, focal). |

---

## Part 8 — Brain Rhythms, Filters, Time-Domain Methods, Labs (25 min)

| # | Question | Answer |
|---|---|---|
| 257 | Delta band and state? | **0.5–4 Hz**; **dreamless restorative sleep**; slowest; healing and rejuvenation. |
| 258 | Theta band and state? | **4–8 Hz**; creativity, insight, **dreams**, reduced consciousness; deep meditation, daydreaming, automatic tasks. |
| 259 | Theta source? | Probably **frontal** (monitoring other mental processes). |
| 260 | Alpha band and state? | **8–13 Hz**; physically/mentally **relaxed**; detectable with **eyes closed**; yoga, before sleep. |
| 261 | Special fact about alpha? | Among the **most easily observed** and **first discovered**. |
| 262 | Beta band and state? | **13–32 Hz**; **alert**, active thinking: conversation, decisions, problem solving, focusing, learning. |
| 263 | Gamma band and state? | **32–100 Hz**; **fastest**; heightened perception, **peak mental state** with simultaneous processing across brain parts. |
| 264 | Who shows strong gamma? | **Very long-term meditators** (Buddhist monks). |
| 265 | Clinical spectral biomarkers? | Reduced **frontal gamma** (30–50 Hz): cognitive decline. Increased **midline beta** (13–30 Hz): **restless legs syndrome**. |
| 266 | Other spectral applications? | **BCIs** and **neurofeedback**. |
| 267 | Four filter types? | Low-pass, high-pass, band-pass, band-stop; ideal = sharp edges, realistic = gradual. |
| 268 | Peak detection use? | Extrema, amplitude distributions, **intervals between events**; spikes, **QRS** detection (pretreat, then threshold). |
| 269 | Level/window detection? | Epochs within an amplitude range (e.g., extracellular spikes). |
| 270 | Cross- vs auto-correlation; template matching? | Between different signals vs a signal with itself; correlate a known **template** (wavelets are special templates). |
| 271 | Why use complex exponentials as templates (lab)? | The dot-product **magnitude** detects frequency **regardless of phase**; the **angle** gives phase. |
| 272 | Lab FFT: fs = 1000 Hz, T = 2 s, N and Δf? | **N = 2000**, **Δf = 0.5 Hz**; peaks at 4, 6, 8, 10 Hz with heights 2, 3, 8, 3 using $2\lvert X\rvert/N$; DFT = FFT. |
| 273 | Bug in `ComplexSinWaves`? | `exp(2*1i*pi*f0*t + phas)`: phase not multiplied by `1i`, so it scales amplitude instead of shifting phase. |

---

## Part 9 — Numerical Problems with Worked Answers (40 min)

**N1.** $[K^+]_o=10$ mM, $[K^+]_i=100$ mM, 37 °C. Find $E_K$.
→ $61.54\log(0.1)=$ **−61.5 mV** (less negative than −80: raising extracellular K⁺ depolarizes).

**N2.** $[Na^+]_o=140$, $[Na^+]_i=14$. Find $E_{Na}$.
→ Ratio 10, so **+61.5 mV**.

**N3.** A divalent cation has out/in ratio 100. Find $E$.
→ $30.77\times2=$ **+61.5 mV**.

**N4.** Goldman with $P_K:P_{Na}=40:1$, K 5/100, Na 150/15.
→ $61.54\log\frac{40(5)+150}{40(100)+15}=61.54\log(350/4015)=$ **−65 mV**.

**N5.** A 35 Hz signal sampled at 50 Hz. Alias?
→ $\lvert35-50\rvert=$ **15 Hz**. Minimum sampling rate: **70 Hz**; recommended ≈ **175 Hz** (5×).

**N6.** 70 Hz sampled at 100 Hz; 120 Hz sampled at 100 Hz?
→ **30 Hz**; **20 Hz**.

**N7.** Levels of a 16-bit ADC; step for a 10 mV range?
→ $2^{16}=65{,}536$ levels; $10\text{ mV}/65536\approx$ **0.15 µV**.

**N8.** 4 s epoch at 250 Hz: N, precision, range, number of bins to Nyquist.
→ N = **1000**; Δf = **0.25 Hz**; range **125 Hz**; **500** bins.

**N9.** To resolve 9.5 Hz and 10 Hz, minimum epoch?
→ Need Δf ≤ 0.5 Hz, so **T ≥ 2 s** (sampling rate is irrelevant for this).

**N10.** Ripple spacing for a 0.8 s rectangular window?
→ $1/0.8=$ **1.25 Hz**.

**N11.** $W_4^{7}$ and $W_8^{2}$?
→ $W_4^7=W_4^3=$ **+j**; $W_8^2=e^{-j\pi/2}=$ **−j**.

**N12.** Multiplications for N = 1024: DFT vs FFT.
→ $1024^2=1{,}048{,}576$ vs $1024\times10=10{,}240$: about **100× fewer**.

**N13.** A 1 s, 1000-sample record of $6\sin(2\pi50t)$ gives $\lvert X(50)\rvert=3000$. Amplitude spectrum and power spectrum at 50 Hz?
→ $AS=\frac{2}{1000}\cdot3000=$ **6**; $S=3000^2/1000=$ **9000**.

**N14.** A periodic signal has mean 3. What is $a_0$?
→ DC $=a_0/2=3$, so **$a_0=6$**.

**N15.** Triangle wave: ratio $a_3/a_1$?
→ $a_n\propto1/n^2$, so **1/9**.

**N16.** Fixed point of $x_i=0.8x_{i-1}+3.5$?
→ $x^\ast=3.5/0.2=$ **17.5**.

**N17.** Signal rms 20 µV, noise rms 10 µV. SNR (power) and dB?
→ $(20/10)^2=$ **4**; $10\log_{10}4\approx$ **6 dB**.

**N18.** Sine of amplitude 10 µV: ms and rms?
→ ms = $A^2/2=$ **50 µV²**; rms = $10/\sqrt2\approx$ **7.07 µV**.

**N19.** Single-trial noise rms 40 µV, 400 trials. Residual noise; dB gain?
→ $40/\sqrt{400}=$ **2 µV**; $10\log_{10}400\approx$ **26 dB**.

**N20.** How many trials to improve amplitude SNR by 8? To halve residual noise again?
→ $\sqrt N=8$, so **64**; halving again needs **4×** trials, so **256**.

**N21.** EP of 2 µV in 20 µV noise: trials for amplitude SNR = 1?
→ Need noise 2 µV: $20/\sqrt N=2$, so **N = 100**.

**N22.** 50 Hz hum: which stimulus rates lock? 10, 12.5, 20, 25, 7.7 Hz.
→ 50/rate = 5, 4, 2.5, 2, 6.49 → **10, 12.5, 25 Hz lock**; 20 Hz alternates phase (cancels); 7.7 Hz drifts (cancels).

**N23.** 60 Hz hum: do 7.5 Hz and 11 Hz lock?
→ 60/7.5 = 8 (**locks**); 60/11 = 5.45 (does not).

**N24.** Dot product of $a=[2,4,2,1,5,3,1]$ and $b=[4,2,2,-3,2,5,0]$?
→ $8+8+4-3+10+15+0=$ **42**.

---

## Part 10 — True/False Trap Drill (30 min)

> Say T or F, then the correction. Every item is modelled on an old-exam distractor.

| # | Statement | T/F | Why / correction |
|---|---|---|---|
| 1 | The Nernst ratio is $[ion]_{inside}/[ion]_{outside}$. | F | **Outside/inside.** |
| 2 | Resting K⁺ permeability is ~80× that of Na⁺. | F | **40×.** |
| 3 | The resting membrane is more permeable to Na⁺ than K⁺. | F | K⁺ ≫ Na⁺. |
| 4 | Leak channels need ATP for each ion passing. | F | Only the **pump** uses ATP. |
| 5 | All-or-none: AP strength depends on stimulus strength. | F | It is **independent** of stimulus strength. |
| 6 | Relative refractory period: Na⁺ channels are permanently disabled. | F | They are **responsive again**; hyperpolarization (open K⁺) raises the threshold current. |
| 7 | Undershoot: $V_m$ moves toward $E_K$ because K⁺ permeability is increased. | T | Voltage-gated K⁺ channels still open. |
| 8 | In passive conduction, distant responses have the same amplitude. | F | They **decay** with distance. |
| 9 | A connexon has eight connexins. | F | **Six.** |
| 10 | EPSPs arise from K⁺ entry. | F | **Na⁺ entry.** |
| 11 | Electrical synapses are slow but flexible. | F | **Very fast.** |
| 12 | An IPSP added to suprathreshold E1+E2 can prevent an AP. | T | Slide summation figure. |
| 13 | EEG mainly records single-neuron APs because they are ~100 mV. | F | EEG = summed **PSPs**. |
| 14 | Dipoles further from the electrode contribute more. | F | They contribute **less**. |
| 15 | Sulcal cancellation happens because both walls produce identical polarity. | F | **Opposite** polarity. |
| 16 | EEG has the highest spatial resolution among imaging methods. | F | Spatial resolution is poor. |
| 17 | "Nyquist rate" and "Nyquist frequency" are the same value. | F | $2f_{max}$ vs $F_s/2$. |
| 18 | Sampling a 20 Hz sine at 30 Hz avoids aliasing. | F | Need ≥ 40 Hz. |
| 19 | Electrode choice is irrelevant with a high-bit ADC. | F | Bits cannot fix the interface. |
| 20 | Ag/AgCl guarantees zero noise. | F | Nothing guarantees zero noise. |
| 21 | Differential recording always cancels all noise. | F | Only **common-mode** noise cancels. |
| 22 | An artifact at only one electrode can remain in the channel. | T | Not common-mode. |
| 23 | A neutral reference is guaranteed to be silent. | F | **No neutral site** exists. |
| 24 | CAR can be affected if many electrodes share an artifact. | T | The artifact enters the mean. |
| 25 | The Fourier series applies only to non-periodic signals. | F | Series: **periodic**; transform: non-periodic. |
| 26 | A power spectrum is amplitude vs time. | F | Power vs **frequency**. |
| 27 | The complex Fourier series is written as a sum of sines and cosines. | F | Sum of **complex exponentials**. |
| 28 | The complex Fourier series has no phase information. | F | The angle of $c_n$ is phase. |
| 29 | The FFT is a hardware filter that removes noise. | F | It is an **algorithm**. |
| 30 | The FFT works on continuous-time signals directly. | F | On **sampled** data. |
| 31 | For N = 4, $W_4^3=W_4^4$. | F | $W_4^3=+j$, $W_4^4=1$. |
| 32 | The twiddle factor is used only in the inverse DFT. | F | In **both** DFT and inverse. |
| 33 | 0.5 s epoch at 1 kHz: precision 1 Hz. | F | **2 Hz** (range 500 Hz is correct). |
| 34 | 5 s epoch at 200 Hz: precision 0.1 Hz. | F | **0.2 Hz**. |
| 35 | Longer epochs worsen precision while improving range. | F | Longer epochs **improve precision**; range depends on $F_s$. |
| 36 | Rectangular window, T = 4 s: ripples at 0.5 Hz. | F | **0.25 Hz**. |
| 37 | Harmonics occur only with a DC offset. | F | They come from **non-sinusoidal** waveforms. |
| 38 | Additive noise creates slower trends than dynamical noise. | F | **Dynamical** noise creates slower trends. |
| 39 | Stationary means the distribution changes over time. | F | It **does not** change. |
| 40 | Ergodicity implies zero variance. | F | It means one sample function represents the ensemble. |
| 41 | Averaging assumes signal and noise are correlated. | F | **Uncorrelated.** |
| 42 | Prestimulus noise is always reliable for EPs. | F | Late components can contaminate it. |
| 43 | Bootstrapping requires online stimulation. | F | Works well **offline**. |
| 44 | Bootstrapping works only when the time-locked component dominates. | F | Works well when it is **small** relative to noise. |
| 45 | Bootstrapping guarantees no trace of time-locked activity in the control. | F | Signal is present, just **not enhanced**. |
| 46 | A noninteger stimulus rate makes onsets hit the same hum phase. | F | That is what an **integer relation (10 Hz)** does. |
| 47 | Averaging fails if the noise is random white noise. | F | Random noise is the **ideal** case. |
| 48 | Long-term EEG is stationary if the subject is relaxed. | F | Long-term EEG is **non-stationary**. |
| 49 | EEG is deterministic because measurements are unlimited. | F | **Stochastic**; measurements are **limited**. |
| 50 | Notch filters are the optimal option for line noise. | F | They distort and ring. |
| 51 | Internal artifacts are easy to prevent once identified. | F | **External** ones can be inhibited. |
| 52 | During blinking the cornea moves farther from frontal electrodes. | F | **Closer** (Bell's phenomenon). |
| 53 | Blinks create opposing polarities at F7 and F8. | F | That is **lateral eye movement**. |
| 54 | Lateral eye movements are strongest at Pz and Oz. | F | At **F7/F8**. |
| 55 | Muscle artifacts have a single stereotyped waveform. | F | **Diverse** forms. |
| 56 | Muscle artifacts affect only high frequencies. | F | **Both** high and low. |
| 57 | ECG artifact is mainly right-sided. | F | **Left**-sided. |
| 58 | Alpha is 13–32 Hz and linked to active thinking. | F | That is **beta**; alpha is 8–13 Hz, relaxed. |
| 59 | Theta is 8–13 Hz. | F | Theta is **4–8 Hz**. |
| 60 | Theta comes from occipital parts of the brain. | F | Probably **frontal**. |

---

## Part 11 — 30 Exam-Style Multi-Select Questions (60 min)

> Select **all** correct statements. Aim for 2 minutes per question. Answers follow each block of 10.

### Block A (Q1–Q10)

**Q1.**
- A. Axons transmit signals over distance.
- B. Glial cells are the primary cells for long-distance electrical signalling.
- C. The number of inputs to a neuron reflects its convergence.
- D. Axon terminals form synapses with dendrites or somata of other neurons.
- E. Retinal amacrine cells have no axon.

**Q2.**
- A. $E_{ion}$ exactly balances the ion's concentration gradient.
- B. For Ca²⁺ the Nernst prefactor at 37 °C is 30.77 mV.
- C. $E_{ion}$ depends on membrane thickness.
- D. Raising temperature changes $E_{ion}$.
- E. If the membrane were permeable only to K⁺, $V_m$ would equal $E_K$.

**Q3.**
- A. During the absolute refractory period Na⁺ channels are inactivated.
- B. The inactivation gate closes about 1 ms after the activation gate opens.
- C. AP overshoot reaches exactly $E_{Na}$.
- D. Firing rate increases with depolarizing current.
- E. Voltage-gated K⁺ channels cause the rising phase.

**Q4.**
- A. Voltage-gated Na⁺ channels are concentrated at nodes of Ranvier.
- B. One Schwann cell myelinates several CNS axons.
- C. The axon hillock is the spike-initiation zone of CNS pyramidal neurons.
- D. AP amplitude remains constant during active conduction.
- E. Passive potentials can travel centimetres without decay.

**Q5.**
- A. Gap junctions allow direct ionic current flow between cells.
- B. Most gap junctions are bidirectional.
- C. IPSPs result from Cl⁻ entry producing hyperpolarization.
- D. Temporal summation requires several different presynaptic fibres.
- E. Chemical synaptic release is triggered by Ca²⁺ influx.

**Q6.**
- A. EEG mainly records extracellular currents from synaptic activity in cortical dendrites.
- B. Pyramidal cells contribute strongly because they are aligned perpendicular to the cortex.
- C. Radial dipoles at the gyral crown give the strongest EEG signal.
- D. Adjacent neurons receiving excitatory and inhibitory input enhance the scalp signal.
- E. EEG is a direct measure of magnetic fields.

**Q7.**
- A. EEG is non-invasive and involves no radiation.
- B. EEG temporal resolution matches the speed of cognition.
- C. EEG devices generate no noise.
- D. EEG can be recorded in open environments.
- E. ECoG is non-invasive.

**Q8.**
- A. The Nyquist frequency is $F_s/2$.
- B. Aliasing appears as overlap of periodic spectral copies.
- C. The anti-aliasing filter comes after the ADC.
- D. A 3-bit ADC has 8 levels.
- E. Sampling at 5× the maximum frequency is common in practice.

**Q9.**
- A. The Ag/AgCl layer supports ionic-to-electronic conduction.
- B. Ag/AgCl reduces electrode capacitance, easing low-frequency recording.
- C. The ground electrode location is more important than the reference location.
- D. An EEG channel is computed as $V_{AG}-V_{RG}$.
- E. The reference electrode is usually placed on one or both ear lobes.

**Q10.**
- A. Changing the reference can change the waveforms even if brain activity is unchanged.
- B. Referencing cannot affect topography.
- C. CAR subtracts the mean of all channels.
- D. Bad channels should be removed before CAR.
- E. Bipolar derivations reduce widespread activity common to both electrodes.

#### Answers Q1–Q10

- **Q1: A, C, D, E.** B ✗ neurons do long-distance signalling.
- **Q2: A, B, D, E.** C ✗ thickness is not in Nernst.
- **Q3: A, B, D.** C ✗ never reaches $E_{Na}$; E ✗ K⁺ causes the falling phase.
- **Q4: A, C, D.** B ✗ Schwann cells are PNS, one axon; E ✗ passive decays within mm.
- **Q5: A, B, C, E.** D ✗ temporal summation = same fibre repeatedly.
- **Q6: A, B, C.** D ✗ opposite dipoles cancel; E ✗ that is MEG.
- **Q7: A, B, D.** C ✗ all equipment adds noise; E ✗ ECoG is semi-invasive.
- **Q8: A, B, D, E.** C ✗ anti-alias filter precedes the ADC.
- **Q9: A, B, D, E.** C ✗ reference location matters more.
- **Q10: A, C, D, E.** B ✗ referencing changes topography.

### Block B (Q11–Q20)

**Q11.**
- A. The DC component of the real Fourier series is $a_0/2$.
- B. For an odd function all $b_n$ are zero.
- C. Orthogonality makes cross-product integrals vanish over a full period.
- D. $b_n=\frac2T\int_Tf(t)\sin(n\omega t)dt$.
- E. The angular frequency is $\omega=2\pi f$.

**Q12.**
- A. Complex coefficients are evaluated over a full period and the start point does not matter.
- B. Real and complex Fourier series are equivalent.
- C. The complex series contains no phase information.
- D. $c_n=\frac1T\int_Tf(t)e^{-jn\omega t}dt$.
- E. Euler's relation links complex exponentials to sines and cosines.

**Q13.**
- A. A Dirac impulse in time contains all frequencies.
- B. A DC component transforms to an impulse at zero frequency.
- C. The FFT reduces computations from $N^2$ to $N\log_2N$.
- D. The FFT gives a less accurate result than the DFT.
- E. Power spectra can be computed from FFT results.

**Q14.**
- A. The twiddle factor is periodic and this supports FFT efficiency.
- B. $W_4^2=W_4^6$.
- C. $\theta=0$ and $\theta=2\pi$ give the same complex value.
- D. $W_N^k$ equals 1 only for k = 0.
- E. The inverse DFT includes a factor 1/N.

**Q15.**
- A. A 2 s epoch at 500 Hz gives 0.5 Hz precision and 250 Hz range.
- B. Positive frequencies are 0→π on the circular scale.
- C. The power spectrum is odd.
- D. The amplitude spectrum is normalized by 2/N.
- E. The phase spectrum needs normalization by N.

**Q16.**
- A. A finite epoch is equivalent to multiplication by a rectangular window.
- B. Multiplication in time corresponds to convolution in frequency.
- C. For T = 2 s, rectangular-window ripples are spaced 0.5 Hz.
- D. The Hann window is $0.54+0.46\cos(\pi t/T)$.
- E. Non-sinusoidal periodic activity produces harmonics.

**Q17.**
- A. Dynamical noise produces slower trends due to correlated sequential values.
- B. A process with dynamical noise is stochastic.
- C. Stationarity means $x(t)$ is constant.
- D. If stationary and ergodic, statistics can be obtained from time averages of one sample function.
- E. Similar amplitude histograms across sample functions support stationarity.

**Q18.**
- A. SNR in dB equals $10\log_{10}(ms_s/ms_n)$.
- B. SNR in dB has units of volts.
- C. Hum is described as enemy #1.
- D. Evoked potentials are among the smallest biopotentials.
- E. EEG is an intracellular signal.

**Q19.**
- A. Averaging assumes known signal timing.
- B. Averaging assumes noise is random with zero mean.
- C. Averaging reduces random noise rms by $\sqrt N$.
- D. The ± average inverts every other trial.
- E. The ± average's residual noise rms is larger than the true average's.

**Q20.**
- A. Bootstrapping uses random triggers.
- B. Random triggers enhance time-locked components.
- C. Prestimulus estimation assumes the signal occurs only after the trigger.
- D. Longer inter-stimulus intervals can reduce prestimulus contamination.
- E. A 10 Hz stimulus rate can phase-lock to 50 Hz hum.

#### Answers Q11–Q20

- **Q11: A, C, D, E.** B ✗ odd functions have $a_n=0$.
- **Q12: A, B, D, E.** C ✗ phase is in the angle of $c_n$.
- **Q13: A, B, C, E.** D ✗ identical result.
- **Q14: A, B, C, E.** D ✗ also for k = N, 2N, ….
- **Q15: A, B, D.** C ✗ even; E ✗ phase needs no normalization.
- **Q16: A, B, C, E.** D ✗ that is Hamming; Hann is 0.5 + 0.5cos.
- **Q17: A, B, D, E.** C ✗ the distribution, not the values, is constant.
- **Q18: A, C, D.** B ✗ dimensionless; E ✗ extracellular.
- **Q19: A, B, C, D.** E ✗ same rms.
- **Q20: A, C, D, E.** B ✗ random triggers destroy alignment.

### Block C (Q21–Q30)

**Q21.**
- A. Background EEG spans about 0.01–100 Hz.
- B. EEG amplitudes are typically around 100 µV.
- C. EEG is divided into four bands.
- D. Short-term EEG can be approximately stationary.
- E. EEG PSD follows a power law.

**Q22.**
- A. The P300 is a positive wave at ~300 ms in the oddball paradigm.
- B. The CNV is a negative wave between a warning and a second stimulus.
- C. The CNV is strong enough to see in single trials.
- D. AEP, VEP and SEP reflect primary perception.
- E. The P300 is interpreted as a response to novelty.

**Q23.**
- A. Notch filtering can distort components between 50 and 70 Hz.
- B. Notch filtering can introduce transient oscillations.
- C. Multitaper is most appropriate for separating narrow low-frequency peaks below 30 Hz.
- D. Multitaper is useful for low-SNR, high-frequency, single-trial power estimation.
- E. Multitaper line-noise removal subtracts noise only if statistically significant.

**Q24.**
- A. Bad channels can be flagged by a robust z-score of amplitude.
- B. A high ratio of high- to low-frequency power suggests a bad channel.
- C. Normal EEG channels are uncorrelated at low frequencies.
- D. Spherical splines give accurate interpolation with dense electrodes.
- E. Radial basis functions have lower computational load.

**Q25.**
- A. Internal artifact sources include heart, eyes and muscles.
- B. External sources include electrode attachment and recording equipment.
- C. External artifacts can be inhibited once identified.
- D. Most removal methods focus on external artifacts.
- E. Internal artifacts originate only from equipment malfunction.

**Q26.**
- A. During blinks the eyes roll up (Bell's phenomenon).
- B. The cornea moves closer to Fp1/Fp2 during blinks.
- C. Blink artifacts are low amplitude.
- D. Looking right moves the right cornea closer to F8.
- E. Lateral eye movements produce opposite polarities at F7 and F8.

**Q27.**
- A. Muscle artifacts are detected through EMG.
- B. Muscle artifacts have a wide, almost uniform scalp distribution.
- C. Muscle artifact spectra affect both high- and low-frequency EEG.
- D. Chewing artifact arises from the temporalis muscle.
- E. Hypoglossal artifact cannot be reproduced voluntarily.

**Q28.**
- A. ECG artifact is time-locked to the QRS complex.
- B. Cardioballistic artifact appears about 200 ms after the QRS.
- C. Sweat artifact is very slow (< 0.5 Hz).
- D. Sweat artifact always appears bilaterally.
- E. Electrical artifacts at 50/60 Hz can come from phone charging.

**Q29.**
- A. Gamma (32–100 Hz) is the fastest measurable EEG rhythm.
- B. Gamma is stronger in very long-term meditators.
- C. Alpha is detectable when eyes are closed and the mind is relaxed.
- D. Beta (13–32 Hz) is linked to alert active thinking.
- E. Delta is linked to active problem solving.

**Q30.**
- A. Theta (4–8 Hz) is linked to creativity, insight and dreams.
- B. Theta can appear during daydreaming and deep meditation.
- C. Alpha is among the first rhythms discovered.
- D. Theta is thought to come from occipital cortex.
- E. Reduced frontal gamma may indicate declined cognitive function.

#### Answers Q21–Q30

- **Q21: A, B, D, E.** C ✗ five bands.
- **Q22: A, B, D, E.** C ✗ the CNV is weak and requires averaging.
- **Q23: A, B, D, E.** C ✗ multitaper smoothing blurs low frequencies.
- **Q24: A, B, D, E.** C ✗ normal EEG **is** correlated at low frequencies.
- **Q25: A, B, C.** D ✗ internal; E ✗ internal = physiological.
- **Q26: A, B, D, E.** C ✗ very high amplitude.
- **Q27: A, B, C, D.** E ✗ reproducible by saying "la la la".
- **Q28: A, B, C, E.** D ✗ bilateral, unilateral or focal.
- **Q29: A, B, C, D.** E ✗ delta = deep sleep.
- **Q30: A, B, C, E.** D ✗ frontal.

---

## Part 12 — Final 20-Minute Cheat Sheet

**Numbers to know by heart**

| Item | Value |
|---|---|
| $E_K$ / $E_{Na}$ / $E_{Ca}$ / $E_{Cl}$ | −80 / +62 / +123 / −65 mV |
| Resting $V_m$ | −65 mV |
| $P_K : P_{Na}$ | 40 : 1 |
| Nernst prefactor (37 °C) | 61.54 mV (z = 1), 30.77 mV (z = 2) |
| Na⁺ inactivation | ~1 ms |
| Soma / gap junction | 20 µm / 3 nm |
| Connexins per connexon | 6 (two connexons per channel) |
| Loewi / Furshpan–Potter / Jasper / Cooley–Tukey | 1921 / late 1950s / 1958 / 1965 |
| Nyquist rate / frequency / practice | $2f_{max}$ / $F_s/2$ / 5× |
| ADC levels | $2^n$ |
| Precision / range | $1/T$ / $F_s/2$ |
| FFT / DFT cost | $N\log_2N$ / $N^2$ |
| Ripple spacing | $1/T$ |
| Hann / Hamming | 0.5 + 0.5cos / 0.54 + 0.46cos |
| Averaging | noise rms ÷ $\sqrt N$ |
| SNR dB | 10 log (power) = 20 log (rms) |
| Background EEG | 0.01–100 Hz, ~100 µV, 5 bands |
| P300 | positive, 300 ms, oddball |
| CNV | negative, warning→second stimulus, Cz, 32 trials |
| Cardioballistic delay | ~200 ms after QRS |
| Sweat | < 0.5 Hz |
| Notch | width ~10 Hz, distorts 50–70 Hz |
| Multitaper | good > 30 Hz |
| Bands | δ 0.5–4, θ 4–8, α 8–13, β 13–32, γ 32–100 Hz |

**Swaps the examiner loves**

- out/in (Nernst) • K⁺ ≫ Na⁺ at rest • EPSP Na⁺ / IPSP Cl⁻ • dendrites receive / axons transmit
- absolute (Na⁺ inactivated) vs relative (K⁺ open) refractory • oligodendrocyte CNS-many / Schwann PNS-one
- PSPs not APs • radial strongest / tangential cancel / deep weaker • poor spatial, high temporal
- Nyquist rate ≠ Nyquist frequency • anti-alias before ADC • ground matters less than reference • no neutral reference
- series = periodic • even → $b_n=0$ / odd → $a_n=0$ • complex FS = exponentials + phase • FFT = exact algorithm
- longer T → better precision • power spectrum even • T = 4 → 0.25 Hz
- dynamical noise → slow trends • stationary = distribution constant • ergodic = one sample represents all
- bootstrap offline, signal small • ± average same rms • 10 Hz locks 50 Hz hum
- external artifacts preventable • blink Fp1/Fp2 closer • F7/F8 opposite = lateral gaze • ECG left, low amplitude
- alpha 8–13 relaxed / beta 13–32 alert • theta frontal • gamma meditators

**Good luck!**
