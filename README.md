
# Network & System Security — Complete Study Notes
## 100-Mark Written Exam Preparation | All 8 Chapters | Questions + Explanations

---
---

# CHAPTER 0: INTRODUCTION & CRYPTOGRAPHIC RECAP

---

## 1. FOUNDATIONAL DEFINITIONS

### 1.1 Cyber Security
- **Computer Security**: Tools to protect data and thwart hackers
- **Network Security**: Measures to protect data during transmission
- **Internet Security**: Measures over interconnected networks; includes deter, prevent, detect, correct

### 1.2 Privacy, Anonymity, Steganography
- **Privacy**: "Claim of individuals to determine for themselves when, how and to what extent information about them is communicated to others" — Westin (1968)
- **Anonymity**: "State of being not identifiable within a set of subjects, the anonymity set" — Pfitzmann
- **Steganography**: Conceals the *existence* of a message (vs. encryption which conceals *content*)

### 1.3 Safety vs. Security
- **Safety**: System does not pose threat to environment (persons, infrastructure)
- **Security**: System not misused by environment (information, services)
- **Relationship**: Security vulns → safety incidents; Safety bugs → security vulns

### 1.4 Correctness vs. Security
- **Correctness**: System satisfies specification → reasonable input → reasonable output
- **Security**: Properties preserved under attack → unreasonable input → not completely disastrous
- **Key difference**: Interference from adversary
- **Security defined negatively**: Secure as long as no attacks succeed

---

## 2. THE CIA TRIAD

| Goal | Definition |
|------|-----------|
| **Confidentiality** | Only authorized entities obtain information (storage + transmission) |
| **Integrity** | Changes only by authorized persons/processes |
| **Availability** | Information available to authorized entities |

---

## 3. TAXONOMY OF ATTACKS

### Definitions
- **Threat**: Potential event leading to abuse/malfunction
- **Attack**: Implementation of a threat exploiting a vulnerability
- **Exploit**: Program executing the attack
- **Incident**: Executed attack

### Passive Attacks (Threaten Confidentiality)
- Eavesdropping, Traffic Analysis

### Active Attacks (Threaten Integrity/Availability)
- Modification, DoS, Delay, Masquerading, Replaying, Repudiation

---

## 4. PREVENTIVE vs. REACTIVE SECURITY
- **Preventive**: Encryption, authentication, access control, firewalls, hash functions
- **Reactive**: IDS, virus scanners, honeypots

---

## 5. SYMMETRIC ENCRYPTION

### ECB Mode
- `c_i = E_K(m_i)`, `m_i = D_K(c_i)`
- **Problem**: Same plaintext block → same ciphertext; patterns preserved; reordering undetectable

### CBC Mode
- XOR each block with previous ciphertext before encryption
- Eliminates pattern leakage

---

## 6. ASYMMETRIC ENCRYPTION

- **Encryption**: Bob's Public Key; **Decryption**: Bob's Private Key

### Key Size Equivalences (MEMORIZE)

| Symmetric | RSA/DH | ECC |
|-----------|--------|-----|
| 56 bit | 512 bit | — |
| 80 bit | 1024 bit | 160 bit |
| 112 bit | 2048 bit | 224 bit |
| 128 bit | 3072 bit | 256 bit |
| 192 bit | 7680 bit | 384 bit |
| 256 bit | 15360 bit | 512 bit |

**Why RSA needs larger keys**: Security based on integer factorization (easier than brute-force), so ~30× larger keys needed for equivalent security.

---

## 7. DIFFIE-HELLMAN KEY EXCHANGE
- Establishes shared secret over insecure channel
- Based on **discrete logarithm problem**
- **Vulnerable to MITM** → Solution: authenticated key exchange via certificates

---

## 8. HASH FUNCTIONS
- **Compression**: Arbitrary input → fixed-length output
- **Ease of computation**: h(x) easy to compute
- **Collision**: `h(x) = h(x')` — every hash function has collisions (pigeonhole principle)
- Cannot be injective

---

## 9. MESSAGE AUTHENTICATION CODES (MAC)
- Integrity + Authentication using secret key
- `MAC = f(Message, Key)`

---

## 10. PKI & CERTIFICATION AUTHORITIES
- DH vulnerable to MITM → need authenticated public keys
- CA signs certificates binding public keys to identities
- Bob verifies Alice's key via CA's signature

---

## 11. AUTHENTICATION PROTOCOLS

### Objectives
1. Correctness: Honest A, B → A authenticates to B
2. Transferability: B can't reuse exchange to impersonate A to C
3. Impersonation resistance: Negligible probability C causes B to accept A

### Factors: What you know, Where you are, What you are, What you have

### Salting Against Dictionary Attacks
- `hash(salt || password)` instead of `hash(password)`
- Prevents rainbow table attacks; makes each crack independent

---

## EXAM QUESTIONS — CHAPTER 0

**Q1: Prove that ECB mode leaks information about plaintext patterns. Assume an adversary observes ciphertext blocks c₁, c₂, ..., cₙ.**
**Answer:** In ECB, c_i = E_K(m_i). If m_i = m_j, then c_i = c_j (deterministic encryption with same key). Adversary does NOT need the key — identical ciphertext blocks reveal identical plaintext blocks. For a 64-bit block cipher, if the adversary sees c_i = c_j, they know m_i = m_j with probability 1. This breaks semantic security (IND-CPA). Counterexample: CBC with random IV, where c_i = E_K(m_i ⊕ c_{i-1}), produces different ciphertext even for identical plaintext. **Formal**: ECB is deterministic → cannot be semantically secure. Any deterministic encryption scheme is trivially distinguishable: encrypt m₁ twice, get same ciphertext; encrypt m₂, get different ciphertext.

**Q2: Derive the key size equivalence between symmetric, RSA, and ECC. Why does a 128-bit symmetric key require a 3072-bit RSA key?**
**Answer:** Symmetric key brute-force complexity: O(2^n). RSA factoring complexity (GNFS): O(exp((64/9)^(1/3) · (ln N)^(2/3) · (ln ln N)^(1/3))). For RSA modulus N of bit-length L, complexity ≈ O(2^(L·0.075)) for practical ranges. Equating: 2^n ≈ 2^(L·0.075) → L ≈ n/0.075 ≈ 13.3n. For n=128: L ≈ 1700. But with improved estimates and practical considerations, NIST recommends 3072 bits for 128-bit security. ECC: discrete log on elliptic curves has complexity O(√q) where q is group order. For 256-bit ECC group, complexity ≈ O(2^128), matching 128-bit symmetric. **Why RSA needs ~30× larger**: factoring is sub-exponential (GNFS), whereas brute-force on symmetric is fully exponential. ECC groups have no known sub-exponential algorithm, so ECC ≈ 2× symmetric key size.

**Q3: Prove that Diffie-Hellman is insecure against a man-in-the-middle attack. Show the attack steps and explain why certificates fix this.**
**Answer:** Setup: Alice has (a, g^a), Bob has (b, g^b), public p, g. **Without certificates**: MITM Mallory intercepts g^a from Alice and g^b from Bob. Mallory generates own key pair (m, g^m). Mallory sends g^m to Alice (pretending it's g^b) and g^m to Bob (pretending it's g^a). Alice computes K_A = (g^m)^a = g^(ma). Bob computes K_B = (g^m)^b = g^(mb). Mallory computes K_A = (g^a)^m and K_B = (g^b)^m. Mallory decrypts, reads, re-encrypts. **Both parties are unaware**. **With certificates**: Alice has certificate C_A = Sign_CA(A, g^a). Bob has C_B = Sign_CA(B, g^b). Before key exchange, each party verifies the other's certificate via CA's public key. If Mallory substitutes g^m, Alice verifies C_B and finds B's key doesn't match g^m → attack detected. **Critical insight**: DH provides no authentication by itself — it only provides key agreement. Authentication requires an additional mechanism (certificates, signatures, or pre-shared keys).

**Q4: Given a hash function h: {0,1}* → {0,1}^128, what is the probability of finding a collision after 2^64 random hash evaluations? What is the birthday paradox bound?**
**Answer:** By the birthday paradox, the probability of at least one collision after q random evaluations of an n-bit hash function is approximately: P(collision) ≈ 1 - e^(-q²/(2^(n+1))). For n=128, q=2^64: P ≈ 1 - e^(-(2^64)²/(2^129)) = 1 - e^(-2^128/2^129) = 1 - e^(-0.5) ≈ 0.3935 ≈ 39.3%. **Exact formula**: P(collision) = 1 - ∏_{i=0}^{q-1} (1 - i/2^n). For q = 2^(n/2) = 2^64: P ≈ 1 - e^(-1/2) ≈ 39.3%. To reach P ≈ 99%, need q ≈ 2^(n/2) · √(2·ln(100)) ≈ 2^64 · 3.03 ≈ 2^65.6. **For SHA-256**: n=256, collision resistance ≈ 2^128 evaluations (not 2^256). This is why 128-bit hash output gives only 64-bit collision resistance.

**Q5: Explain why a system can be correct but not secure. Give a concrete example where correctness is satisfied but security is violated.**
**Answer:** **Correctness**: For reasonable input, system produces reasonable output per specification. **Security**: Properties preserved under attack (unreasonable input, adversary-controlled). **Example**: A web server correctly processes HTTP requests (correctness) but is vulnerable to SQL injection (security failure). The server follows its specification for well-formed inputs, but an attacker sends `' OR 1=1 --` as input — the system produces output (returns all records) that is "not completely disastrous" per spec, but violates confidentiality. **Formal distinction**: Correctness is a property of the system's behavior on the specification domain. Security is a property of the system's behavior on the union of specification domain and attack domain. A system is correct iff ∀x ∈ Valid_Inputs: Output(x) = Spec(x). A system is secure iff ∀x ∈ Valid_Inputs ∪ Attack_Inputs: Security_Properties(Output(x)) hold.

**Q6: Why must a salt be unique per user in a password hashing scheme? Prove that a global salt provides no security improvement.**
**Answer:** If salt is global (same for all users), attacker precomputes rainbow table: T[h(salt || pwd)] for all common pwd. This table works for ALL users — no improvement over unsalted hashing. **With per-user salt s_i**: Attacker must recompute rainbow table for each user's unique salt. If dictionary has D entries and there are U users, global salt requires D hash computations total (table reusable). Per-user salt requires D × U hash computations. **Formal**: With global salt, attack complexity = O(D). With per-user salt, attack complexity = O(D × U). For U = 10^6 users and D = 10^6 dictionary entries: global = 10^6 hashes, per-user = 10^12 hashes. **Additionally**: per-user salt prevents detecting if two users have the same password (h(s₁||p) ≠ h(s₂||p) even if p is same). Rainbow tables are useless because each user needs a separate table.

**Q7: Derive the relationship between safety and security. Can a system be safe but not secure? Secure but not safe?**
**Answer:** **Safety**: System does not pose threat to environment (persons, infrastructure). **Security**: System not misused by environment (information, services). **Safety-but-not-secure**: A medical device that cannot harm patients (safe) but can be hacked to leak patient data (not secure). **Secure-but-safety**: A nuclear reactor control system that is perfectly encrypted and authenticated (secure) but has a software bug that causes meltdown on specific input (unsafe). **Relationship**: Security vulnerabilities can lead to safety incidents (hackable car brakes → accident). Safety bugs can lead to security vulnerabilities (crash on input → denial of service). **Key insight**: Safety is about the system's output affecting the physical world. Security is about an adversary manipulating the system's behavior. They are orthogonal properties — neither implies the other. Modern safety-critical systems (automotive, medical, industrial) must address BOTH.

**Q8: Prove that the Dining Cryptographers protocol provides information-theoretic anonymity. Why can unlimited computation not break it?**
**Answer:** Three cryptographers: each has coin x_i ∈ {0,1}. Announcement a_i = x_i ⊕ x_{i+1} (mod 3). If nobody pays: XOR of all announcements = 0. If one pays (say C₃): they announce x₂ ⊕ x₃ ⊕ 1 instead of x₂ ⊕ x₃. XOR of all = 1. **Information-theoretic security**: For any observer, the conditional probability Pr(payer = C₃ | announcements) = Pr(payer = C₃). **Proof**: Consider all 8 possible coin assignments (x₁, x₂, x₃). For each assignment, if nobody pays, announcements are deterministic (XOR = 0). If C₃ pays, announcements are deterministic (XOR = 1). Observer sees announcements → knows XOR value → knows someone paid, but for each coin assignment, the payer's announcement is uniformly distributed among all three cryptographers. **More formally**: For N-bit DC-NET, each user generates N random bits. Sender XORs message. XOR of all announcements = message. Random bits cancel (each appears twice). **Information-theoretic**: Even with unlimited computation, adversary cannot determine payer because the conditional distribution of the payer given observations is uniform over all participants. This is analogous to one-time pad security — the random bits provide perfect secrecy.

**Q9: Compare preventive and reactive security measures. Why is reactive security necessary even with perfect prevention?**
**Answer:** **Preventive**: Encryption, authentication, access control, firewalls, hash functions — stop attacks before they succeed. **Reactive**: IDS, virus scanners, honeypots — detect and respond to attacks that bypass prevention. **Why reactive is necessary**: (1) No preventive measure is perfect — zero-day vulnerabilities exist. (2) Insider threats bypass perimeter defenses. (3) Social engineering defeats technical controls. (4) Defense-in-depth: multiple layers reduce single point of failure. **Formal argument**: Let P(attack succeeds | preventive measures) = ε > 0 (non-zero by assumption). Without reactive measures, undetected breaches persist indefinitely. With reactive measures, breach duration = min(detection_time, attacker_duration). **Example**: Firewall blocks 99.9% of intrusions. Remaining 0.1% includes sophisticated APTs. IDS detects anomalous behavior → incident response → containment. **Cost model**: Preventive cost ∝ 1/ε (diminishing returns). Reactive cost ∝ damage × detection_time. Optimal security = minimize total cost.

**Q10: Why is security defined as a negative property? What are the implications for formal verification?**
**Answer:** **Negative definition**: "Secure = no successful attacks" (cannot enumerate all attacks). Unlike correctness: can test against specification (finite input/output pairs). **Implication 1**: Cannot prove security by testing — must use formal models (Dolev-Yao, computational model). **Implication 2**: Security proofs are reductionist: "Breaking scheme X implies breaking underlying assumption Y" (e.g., factoring). If Y is hard, X is secure. **Implication 3**: Side-channel attacks, implementation bugs, protocol interactions — all outside formal model. **Formal verification approaches**: (1) Information-theoretic security (one-time pad, DC-NET) — provably unbreakable regardless of adversary. (2) Computational security (RSA, AES) — secure assuming adversary bounded by polynomial time. (3) Game-based proofs: adversary's advantage in distinguishing/attacking is negligible. **Critical limitation**: Formal proofs assume perfect implementation. Real-world security fails at the gap between model and implementation (padding oracle attacks, timing attacks).

---
---

# CHAPTER 1: ANONYMOUS COMMUNICATION

---

## 1. MOTIVATION
- Encryption protects **content** NOT **relationships**
- Visible to: ISPs, web servers, search engines, governments
- **Sender anonymity**: Contact without revealing identity
- **Receiver anonymity**: Contact without knowing who receiver is
- **Unlinkability**: Hide relationships from third parties

---

## 2. ATTACKER CLASSIFICATION
- **Global Passive Adversary**: Observes ALL traffic (strongest)
- **Local Passive**: Observes single point (ISP, admin)
- **Active**: Can modify/inject/delay/delete messages

---

## 3. MIXNETS (High-Latency) — David Chaum 1981

### Core Idea
1. Send packet over several relays (mixes)
2. Each mix decrypts one layer
3. Mapping incoming ↔ outgoing kept secret
4. Padding: all packets same size

### Mix Types
| Type | Mechanism |
|------|-----------|
| Simple batch | Collect batch, reorder, forward |
| FIFO | Forward in order (weaker) |
| Threshold batch | Forward when ≥ t messages received |
| Continuous batch | Forward with delay |

### Mix Cascades
- Multiple mixes in sequence, different operators
- Attacker must compromise ALL mixes
- Padded to same size at each hop

### Mixnet Attacks
| Attack | Description |
|--------|-------------|
| Tagging | Modify ciphertext to trace path |
| Flooding | Force mix to forward before batch full |
| Intersection | Observe sender-receiver simultaneous online times |
| Timing | Correlate send/receive times |

---

## 4. TOR (Low-Latency) — The Onion Router

### How It Works
- Clients select **3 onion routers**: Entry → Middle → Exit
- **Layered encryption**: Each OR decrypts one layer
- Entry knows Alice, not destination; Exit knows destination, not Alice; Middle knows neither
- Circuits last ~10 minutes, new ones built periodically
- ~6,000 relays, ~2.5M daily users

### Hidden Services (DarkNet)
1. Server selects introduction points
2. Publishes via directory service
3. Client selects rendezvous point
4. Both connect anonymously to rendezvous point
5. **Properties**: Location hidden, censorship resistant

### Tor Limitations
- Exit node sees traffic in clear
- Website fingerprinting possible
- Performance impact

---

## 4. WEBSITE FINGERPRINTING (CRITICAL)

### How It Works
1. Local attacker captures packet sizes/timing via tcpdump
2. Convert to features (sizes, directions, cumulative data)
3. Train ML classifier on labeled dataset
4. Classify website from traffic pattern

### Packet Representation
- `(timestamp, signed_size)` — negative = outgoing, positive = incoming
- Example: `1380829208159: -586`

### Cross-Validation
- k-fold: split data into k parts, train on k-1, test on 1, repeat k times
- Ensures algorithm works across users

### Countermeasures
- Dummy traffic, random bursts, traffic shaping

---

## 5. PREDECESSOR ATTACKS
- Compromise entry + exit nodes → correlate timing → identify sender-receiver pair
- **Intersection attack**: Observe simultaneous online activity over time → statistical narrowing

---

## 6. CROWDS PROTOCOL

### How It Works
- Jondos form a crowd
- Each jondo: coin flip → heads: forward to random jondo; tails: send to destination

### Math
- `p_f` = forwarding probability, `n` = honest jondos, `c` = colluding
- **Expected path length**: `E(X) = p_f/(1-p_f) + 2`
- For `p_f = 0.6` → E(X) = 3.5 hops

### Predecessor Attack on Crowds
- Colluding jondos track who forwards to them
- Poisson process modeling + Chernoff bounds → estimate sending rates → identify initiator

---

## 7. DINING CRYPTOGRAPHERS (DC-NET) — David Chaum 1988

### Protocol
1. Each cryptographer flips coin, shows to left neighbor
2. Each announces "same" or "different" (own coin vs. neighbor's)
3. Payer announces opposite (lies)
4. Odd "same" → NSA paying; Even → one of them paying
5. Non-payer cannot tell which (without hidden coin)

### XOR Proof
- No lies: `x3⊕x1 ⊕ x1⊕x2 ⊕ x2⊕x3 = 0`
- One lie: XOR = 1
- **Information-theoretic security**: Even unlimited computation can't break

### Superposed Sending (Generalization)
- N users, each generates 1 random bit
- Sender XORs message bit
- XOR of all announcements = message bit (random bits cancel)

### Limitations
- O(N) communication per bit
- Requires secure pairwise channels
- Impractical for large scale

---

## 8. SECRET SHARING

### (k,n)-Threshold Scheme
- k-1 or fewer → cannot reconstruct
- k or more → can reconstruct

### XOR Sharing (n,n)
- P_n gets `r_n = r_1 ⊕ ... ⊕ r_{n-1} ⊕ s`
- Reconstruct: `s = r_1 ⊕ ... ⊕ r_n`

### Shamir's Secret Sharing
- Polynomial P(x) over finite field, P(0) = secret
- Share: point (x_i, P(x_i))
- Reconstruct: Lagrange interpolation
- **Perfect**: k-1 parties learn nothing
- **Ideal**: Share length = secret length

---

## EXAM QUESTIONS — CHAPTER 1

**Q1: Derive the expected path length in the Crowds protocol for arbitrary forwarding probability p_f. Show that for p_f = 0.6, E(X) = 3.5.**
**Answer:** Let X = path length. The path has at least 2 hops (jondo → ... → destination). Let Y = number of additional forwards beyond the minimum. P(Y = k) = p_f^k · (1-p_f) for k ≥ 0 (geometric distribution). E[Y] = Σ_{k=0}^∞ k · p_f^k · (1-p_f) = p_f/(1-p_f). Therefore E[X] = E[Y] + 2 = p_f/(1-p_f) + 2. **For p_f = 0.6**: E[X] = 0.6/(1-0.6) + 2 = 0.6/0.4 + 2 = 1.5 + 2 = **3.5 hops**. **For p_f = 0.7**: E[X] = 0.7/0.3 + 2 = 2.33 + 2 = 4.33 hops. **Limit as p_f → 1**: E[X] → ∞ (every request is forwarded indefinitely). **Limit as p_f → 0**: E[X] → 2 (direct to destination). **Security implication**: Higher p_f = longer path = better anonymity but more latency and load on network. Optimal p_f balances security and performance.

**Q2: Formalize the predecessor attack on Crowds. How does the Poisson process model work, and why do Chernoff bounds apply?**
**Answer:** **Setup**: Attacker observes which jondo forwards messages to Bob. Let λ_i = rate at which user i sends messages. **Poisson model**: Message arrivals from each user are independent Poisson processes. If user i is the initiator, the observed rate from i to Bob is higher because i's messages sometimes reach colluding jondos directly. **Rate estimation**: Observed rate from node i: ω_i = p_h · λ_i + (p_l/n) · Σ_{j≠i} λ_j, where p_h = probability node i is predecessor (initiator's messages hit colluder first), p_l = 1 - p_h. **For initiator**: ω_i is significantly higher (dominated by p_h · λ_i term). **Chernoff bounds**: For large t, the Poisson process observation over time t gives estimate ω̂_i. Chernoff bound: P(|ω̂_i - ω_i| > ε · ω_i) < 2e^(-ε² · ω_i · t / 3). As t → ∞, estimation converges. **Decision rule**: User with highest ω̂_i is likely initiator. **Probability of correct identification**: Increases with observation time t, number of colluding jondos c, and message rate λ. **Countermeasure**: Random dummy traffic (padding) → makes ω_i indistinguishable.

**Q3: Prove the binding property of Shamir's (k,n)-threshold secret sharing scheme.**
**Answer:** **Setup**: Polynomial P(x) = a₀ + a₁x + ... + a_{k-1}x^{k-1} over finite field F_q. Secret = a₀. Shares: (x_i, P(x_i)) for i = 1,...,n. **Binding proof (by contradiction)**: Assume k-1 shares can reconstruct. With k-1 points, there exists exactly one polynomial of degree ≤ k-2 passing through them. But the original polynomial has degree k-1. There are infinitely many degree-(k-1) polynomials passing through k-1 points (free parameter: coefficient of x^{k-1}). Therefore, for any candidate secret a₀', there exists a degree-(k-1) polynomial passing through the k-1 shares with P(0) = a₀'. **Formally**: Given shares (x₁, y₁), ..., (x_{k-1}, y_{k-1}), and candidate secret s', define Q(x) such that Q(0) = s' and Q(x_i) = y_i for i = 1,...,k-1. By Lagrange interpolation, Q exists and is unique among degree-(k-1) polynomials. Since s' was arbitrary, all secrets are equally likely. **Information-theoretic**: H(secret | k-1 shares) = H(secret) = log₂(q). Zero information leakage.

**Q4: Explain why Tor uses exactly 3 onion routers. Analyze the security degradation with 2 and 4 hops.**
**Answer:** **2 hops**: Entry OR knows Alice, Exit OR knows destination. If Entry + Exit collude → complete deanonymization. Single point of failure. **3 hops**: Entry knows Alice (not dest), Middle knows neither, Exit knows dest (not Alice). No single node knows both. Collusion requires Entry + Exit (different operators, different jurisdictions). **4 hops**: Adds latency without proportional security gain. Middle nodes add redundancy but don't improve anonymity against global passive adversary (GPA). **Formal analysis**: For GPA observing all traffic, anonymity set = number of possible paths. With 3 hops and R relays: |anonymity set| = R³ (approximately). With 4 hops: R⁴. But latency increases linearly. **GPA attack on Tor**: If GPA observes entry AND exit traffic simultaneously, timing correlation breaks anonymity regardless of hops. More hops = more latency for same vulnerability. **Latency**: Each hop adds ~10-50ms. 3 hops ≈ 30-150ms. 4 hops ≈ 40-200ms. **Conclusion**: 3 hops is optimal trade-off for web browsing. For higher security, use cascades (multiple independent circuits).

**Q5: Design a website fingerprinting attack. Detail the ML pipeline: feature extraction, classifier choice, and cross-validation.**
**Answer:** **Step 1 — Data collection**: Use tcpdump to capture Tor traffic to 100 websites. Record (timestamp, signed_size) pairs. Negative = outgoing, positive = incoming. **Step 2 — Feature extraction**: (a) Cumulative data features: total bytes sent/received per time window. (b) Packet sequence: number of incoming/outgoing packets. (c) Burst features: packets between idle periods. (d) Page load time. (e) Number of unique packet sizes. **Step 3 — Classification**: k-NN (k=1) with Euclidean distance on normalized features. Alternatives: SVM with RBF kernel, Random Forest. **Step 4 — Cross-validation**: k-fold (k=5 or k=10). Split data into k parts. Train on k-1, test on 1, repeat k times. Average accuracy = final metric. **Step 5 — Evaluation**: Confusion matrix, precision, recall per website. **Known results**: 95%+ accuracy with traffic analysis (Sun et al., USENIX 2002). Deep learning (CNN): 96% on 900 websites (Sirinam et al., 2018). **Countermeasures**: Dummy traffic (WebWash), constant-rate padding, website-specific traffic shaping.

**Q6: Compare Chaum's Mix, Crowds, and Tor. For each, identify the threat model, security guarantees, and limitations.**
**Answer:** **Chaum's Mix (1981)**: Threat model: local passive adversary at mix. Security: breaks input-output link via batching, reordering, padding. Limitations: high latency (must wait for batch), vulnerable to tagging attacks, intersection attacks over time. **Crowds**: Threat model: some jondos are honest, some colluding. Security: initiator anonymity as long as at least one honest jondo in path. Predecessor attack breaks anonymity with enough observations. Limitations: path length depends on p_f, vulnerable to long-term statistical attacks, no encryption at destination. **Tor**: Threat model: global passive adversary (partial protection), local active adversary (full protection). Security: layered encryption, circuit rotation, hidden services. Limitations: website fingerprinting, exit node sees plaintext, performance degradation, relay operators can be compelled. **Comparison table**: Mix = strongest security, highest latency. Tor = lowest latency, moderate security. Crowds = simple, distributed, but weakest against persistent adversary. **Key trade-off**: Latency vs. security vs. scalability. No system achieves all three.

**Q7: Analyze the Naive Bayes classifier used in website fingerprinting. Given Pr(valid) = 0.99, Pr(alarm|valid) = 0.05, Pr(alarm|censored) = 0.90, compute Pr(valid|alarm).**
**Answer:** **Bayes' theorem**: Pr(A|B) = Pr(B|A) · Pr(A) / Pr(B). **Given**: Pr(valid) = 0.99, Pr(censored) = 0.01, Pr(alarm|valid) = 0.05 (false positive), Pr(alarm|censored) = 0.90 (true positive). **Total probability**: Pr(alarm) = Pr(alarm|valid) · Pr(valid) + Pr(alarm|censored) · Pr(censored) = 0.05 × 0.99 + 0.90 × 0.01 = 0.0495 + 0.009 = 0.0585. **Posterior**: Pr(valid|alarm) = Pr(alarm|valid) · Pr(valid) / Pr(alarm) = 0.0495 / 0.0585 ≈ **0.846 = 84.6%**. **Interpretation**: Even with alarm triggered, 84.6% chance the user is valid (not censored). The alarm is mostly false positives because Pr(valid) is very high (base rate fallacy). **Implication for fingerprinting**: Prior probabilities (website popularity) heavily influence classification accuracy. Popular websites dominate — classifier biased toward popular classes. **Improvement**: Use discriminative classifiers (SVM, neural nets) that model P(class|features) directly instead of relying on priors.

**Q8: Prove that DC-NET generalization to N users provides information-theoretic sender anonymity. What is the communication cost?**
**Answer:** **Protocol**: N users in a ring. Each user i generates random bit r_i. User i announces a_i = r_i ⊕ r_{i+1} (mod N). Sender (say user S) announces a_S = r_S ⊕ r_{S+1} ⊕ m (m = message bit). **All announcements XOR**: ⊕_{i=1}^N a_i = (r₁⊕r₂) ⊕ (r₂⊕r₃) ⊕ ... ⊕ (r_N⊕r₁) ⊕ m = 0 ⊕ m = m. Random bits cancel because each r_i appears exactly twice. **Information-theoretic security**: For any observer, the view consists of {a₁, ..., a_N}. For each possible sender S, there exists a random bit assignment consistent with the observed announcements and message m. **Formally**: Pr(sender = S | observations) = Pr(sender = S) for all S. The conditional distribution equals the prior — zero information leakage. **Proof**: Fix observations a₁,...,a_N. For any S, the equation a_S = r_S ⊕ r_{S+1} ⊕ m has a solution for any m (just set r_S appropriately). All random bit assignments are equally likely. **Communication cost**: N random bits to transmit 1 message bit. For k-bit message: N·k random bits + N·k announcement bits = 2Nk total bits. **Scalability**: O(N) per bit → impractical for large N. Requires pre-established secure pairwise channels.

**Q9: Explain the tagging attack on mix networks. How does it work, and what are countermeasures?**
**Answer:** **Attack**: Adversary tags a ciphertext (sets specific bits or adds a known pattern). When mix outputs the modified ciphertext, adversary recognizes the tag → traces the packet through the mix. **Step 1**: Adversary intercepts packet destined for mix. **Step 2**: Modify ciphertext (e.g., XOR tag into last byte). **Step 3**: Forward to mix. **Step 4**: Mix decrypts one layer → tag still present (if mix doesn't strip it). **Step 5**: Adversary monitors output → recognizes tagged packet → knows input-output mapping. **Countermeasures**: (1) **MAC verification**: Mix computes MAC on decrypted message, rejects modified packets. (2) **Redundancy checks**: Add padding that mix verifies and strips. (3) **Batch processing**: Mix processes all packets simultaneously → cannot correlate individual inputs to outputs. (4) **End-to-end integrity**: Receiver verifies message integrity → detects modification. **Formal model**: In Dolev-Yao model, adversary can modify messages in transit. Mix must be modeled as a black box that preserves secrecy but may leak ordering. Tagging breaks the "break input-output link" property.

**Q10: Analyze the intersection attack on Tor. Given an adversary observing entry and exit traffic for 6 months, what is the probability of correctly identifying a sender-receiver pair?**
**Answer:** **Attack model**: Adversary observes when Alice sends (entry node) and when Bob receives (exit node). Each observation gives a "simultaneous online" event. **Probability model**: Let p = probability Alice and Bob are simultaneously online (independent). Without adversary: P(Alice sends at time t) · P(Bob receives at time t). With adversary: for each time interval Δt, count co-occurrences. **After n observations**: Let k = number of times Alice and Bob are simultaneously online. If Alice IS communicating with Bob: E[k] = n · p. If Alice is NOT communicating with Bob: E[k] = n · p² (independent events). **Statistical test**: If observed k > threshold → Alice communicates with Bob. **Chernoff bound**: For binomial distribution, P(|k - E[k]| > δ · E[k]) < 2e^(-δ² · E[k] / 3). **After 6 months**: ~180 days × ~8 hours online = ~1440 observations. For p = 0.3: E[k|same] = 432, E[k|diff] = 129.6. Standard deviation ≈ √(np(1-p)) ≈ √(1440 × 0.3 × 0.7) ≈ 17.3. **Detection**: Gap between 432 and 129.6 is ~300 >> 17.3 → reliable identification. **Countermeasure**: Padding/dummy traffic → makes online times independent of actual communication.

---

---
---

# CHAPTER 2: CAPTCHA & ML ATTACKS

---

## 1. WHAT IS CAPTCHA?
- **Completely Automated Public Turing Test To Tell Computers and Humans Apart**
- Coined 2000: von Ahn, Blum, Hopper (CMU), Langford (IBM)
- "Inverse Turing test" / Human Interaction Proof (HIP)

### Why Needed
- Prevent automated posting, fraudulent profiles, bot crawling, fake votes, dictionary attacks, spam

### Performance Target
- Humans solve >80% of time; automated scripts <0.01%
- Average solving time: ~10 seconds

---

## 2. TYPES OF CAPTCHAs
- Text-based, Image-based, Audio-based, Game-based

### reCAPTCHA Evolution
- Old: Two distorted words
- v2: Checkbox + image selection
- v3: Invisible, score-based (behavioral analysis)

### Google Book Scan
- 400M people helped digitize books
- ~160 books/day, 12K hours unpaid work

---

## 3. ATTACKS ON CAPTCHAs

### Attack Types
| Type | Description |
|------|-------------|
| Outsourcing | Mechanical Turk — cheap human labor |
| OCR | Optical Character Recognition |
| ML | Train classifiers |
| Insecure impl | Reuse session IDs |

### Classical ML Pipeline
```
Preprocessing → Segmentation → Feature Extraction → Classification
```

### Segmentation Techniques
- **Vertical projection**: Count pixels, gaps = character boundaries
- **Snake segmentation**: Snake game-inspired path finding
- **Graph-based**: Dijkstra shortest path + KNN classifier

### Protective Measures
- Anti-detection: Multiple fonts, distortion, blurring, rotation
- Anti-segmentation: Complex backgrounds, lines/shapes, collapsing

---

## 4. DEEP LEARNING APPROACHES

### CNN
- No feature engineering needed
- End-to-end learning (no segmentation)
- Needs large training data (2.3M images)

### GAN + Transfer Learning
1. Learn CAPTCHA synthesizer → generate synthetic CAPTCHAs
2. Train base solver on synthetic data
3. Fine-tune on 500 real CAPTCHAs
- **Only 500 real samples needed!**

### Adversarial ML
- Subtle perturbations fool classifiers
- Arms race continues
- Text CAPTCHA not dead (Shi et al., CCS 2020)

---

## EXAM QUESTIONS — CHAPTER 2

**Q1: Formalize the CAPTCHA security-usability trade-off. Define the ideal performance targets and explain why the 80%/0.01% gap exists.**
**Answer:** **Ideal targets**: Human success rate > 80%, automated script success rate < 0.01%. Average human solve time ~10 seconds. **Formal model**: Let S = security (difficulty for machine), U = usability (ease for human). CAPTCHA design maximizes f(S, U) subject to S ≥ S_min, U ≥ U_min. **Why gap exists**: (1) Human perception: pattern recognition, context, world knowledge. (2) ML: requires labeled data, feature engineering, computational resources. (3) Distortion adds noise → humans use top-down processing (context), ML must learn invariances. **Formal**: CAPTCHA is a game between designer and attacker. Designer chooses challenge C from space Ω. Attacker uses classifier f: Ω → {classes}. Security = min_f P(f(C) = correct). Usability = max_human P(human(C) = correct). **Information-theoretic view**: CAPTCHA encodes n-bit challenge. Human extracts O(n) bits (contextual). Machine extracts O(n/2) bits (statistical). Gap = difference in information extraction capability. **Practical limit**: As ML improves, CAPTCHA must use harder problems (3D reasoning, common sense, social intelligence).

**Q2: Analyze the GAN-based CAPTCHA solver pipeline. Why does transfer learning reduce the data requirement from 2.3M to 500 real samples?**
**Answer:** **Pipeline**: (1) Train CAPTCHA synthesizer (GAN) on synthetic data → unlimited training samples. (2) Train base solver on synthetic data (2.3M images). (3) Fine-tune last layers on 500 real CAPTCHAs. **Why transfer learning works**: **Domain adaptation**: Synthetic and real CAPTCHAs share low-level features (edges, curves, textures) but differ in high-level statistics (distortion patterns, noise). Pre-trained network already learns low-level features. Fine-tuning adapts only high-level decision boundaries. **Formal**: Let f_synthetic: input → features → label. Fine-tuning on real data: f_real = f_synthetic + Δw, where Δw << w. The feature extractor (lower layers) is general → transferable. The classifier (upper layers) is domain-specific → needs adaptation. **Data efficiency**: 500 samples sufficient for fine-tuning because: (1) Network already converged on similar distribution. (2) Only small weight adjustment needed. (3) Regularization prevents overfitting. **Comparison**: From scratch: need 2.3M (full distribution coverage). Fine-tuning: need ~500 (distribution shift coverage). **Ye et al. (2018)**: Achieved >95% accuracy on reCAPTCHA with only 500 real samples + synthetic pre-training.

**Q3: Design a complete attack pipeline for text CAPTCHAs with 5 overlapped characters. Detail each stage: preprocessing, segmentation, feature extraction, classification.**
**Answer:** **Stage 1 — Preprocessing**: (a) Denoise: Markov Random Fields to remove background noise. (b) Binarize: Otsu's thresholding → foreground/background separation. (c) Remove background lines/shapes using morphological operations. **Stage 2 — Segmentation**: (a) Graph-based: Create pixel connectivity graph. (b) Use Dijkstra's shortest path to find character boundaries. (c) Alternative: Vertical projection (count pixels per column → valleys = boundaries). **Stage 3 — Feature extraction**: (a) Log Gabor filters at multiple scales and orientations. (b) Extract texture features from each segmented character. (c) Dimensionality reduction (PCA). **Stage 4 — Classification**: (a) CNN trained on synthetic data (2.3M images). (b) Fine-tuned on 500 real CAPTCHAs. (c) Output: 5 characters per CAPTCHA. **Evaluation metrics**: Accuracy per character, accuracy per CAPTCHA (all 5 correct), segmentation success rate. **Known results**: George et al. (2017): 2.3M CNN → 84% per-character accuracy. With segmentation: >90%. **Defenses**: Complex backgrounds, character collapsing, adaptive distortion.

**Q4: Explain why game-based CAPTCHAs are theoretically more secure than text/image CAPTCHAs. What makes them harder for ML?**
**Answer:** **Text CAPTCHA vulnerability**: ML excels at pattern recognition on 2D images. Convolutional networks learn character shapes → solve text CAPTCHAs. **Game-based CAPTCHA**: Requires spatial reasoning, real-world physics understanding, temporal reasoning. **Why harder for ML**: (1) **Temporal reasoning**: Must understand sequence of actions (drag puzzle piece to correct position). (2) **Physics simulation**: Must predict outcomes of physical actions (drop ball, rotate object). (3) **Common sense**: Requires world knowledge (what fits where, what looks "right"). (4) **Multi-modal reasoning**: Combines visual, spatial, and logical reasoning. **Formal**: Text CAPTCHA = function f: image → character. Game CAPTCHA = function g: state × action → reward. g requires planning (NP-hard in general). **ML limitation**: Current ML (CNNs, transformers) excels at supervised pattern matching. Planning and reasoning require different architectures (RL, tree search). **Trade-off**: Higher security but: (a) Higher cognitive load for humans. (b) Accessibility issues (disabled users). (c) Longer solve times. (d) More complex implementation.

**Q5: Analyze the vertical projection segmentation technique. Given a CAPTCHA image with 4 characters, explain the algorithm and its failure modes.**
**Answer:** **Algorithm**: (1) Binarize image → foreground pixels = 1, background = 0. (2) Project onto x-axis: for each column j, count P(j) = Σ_i image(i,j). (3) P(j) = number of foreground pixels in column j. (4) Find valleys (local minima) in P(j) → character boundaries. (5) Extract each character between consecutive valleys. **Example**: Image width 200px, 4 characters. P(j) peaks at character centers, valleys between characters. Valleys at j=50, 100, 150 → 4 segments. **Failure modes**: (1) **Overlapping characters**: Valleys don't reach zero → segments overlap. (2) **Connected characters**: Adjacent characters share pixels → no valley. (3) **Variable width**: Some characters wider (W, M) → misaligned valleys. (4) **Background noise**: Random pixels create false valleys. **Improvement**: Snake segmentation — uses active contour model. Snake (deformable contour) placed on image, moves to minimize energy (avoids foreground pixels, maintains smoothness). Better handles overlaps. **Complexity**: O(W × H) for projection, O(W × H × iterations) for snake. **Accuracy**: ~70% for simple CAPTCHAs, ~40% for overlapped CAPTCHAs.

**Q6: Why did reCAPTCHA evolve from text to v3? Analyze the arms race between CAPTCHA designers and ML attackers.**
**Answer:** **Timeline**: (1) Text CAPTCHA (2000-2010): Distorted text. (2) Image CAPTCHA (2010-2015): "Select all images with...". (3) Invisible/behavioral (2015-present). **Why text failed**: (1) CNNs achieved human-level accuracy on text recognition (2014). (2) Synthetic data generation (GANs) eliminated data bottleneck. (3) Transfer learning reduced real data requirement to 500 samples. **Why images failed**: (1) ML can identify objects in images (ImageNet). (2) Google's own ML can solve image CAPTCHAs. **v3 approach**: No visible challenge. Analyzes: mouse movement patterns, browsing history, browser fingerprint, interaction speed, scroll behavior. **Score**: 0.0 (bot) to 1.0 (human). Website sets threshold. **Arms race dynamics**: Designers add harder challenges → ML improves → designers switch paradigm. **Fundamental problem**: CAPTCHA relies on "hard AI problem." As AI advances, hard problems become easy. **Future**: Continuous authentication (behavioral biometrics) instead of point-in-time challenges.

**Q7: Given a text CAPTCHA with 6 characters from [A-Z, 0-9] (36 possibilities each), what is the entropy? How does this relate to the brute-force attack complexity?**
**Answer:** **Entropy**: H = log₂(36^6) = 6 · log₂(36) = 6 · 5.17 ≈ **31.0 bits**. **Brute-force complexity**: 36^6 = 2,176,782,336 ≈ 2.18 × 10^9 ≈ 2^31 CAPTCHAs to try. **At 10 seconds per CAPTCHA**: 2.18 × 10^9 × 10s ≈ 691 years (sequential). **Parallel**: With 1000 bots: 0.69 years ≈ 252 days. **With ML solver**: If ML accuracy = 90% per character, per-CAPTCHA accuracy = 0.9^6 ≈ 53%. Expected tries: 1/0.53 ≈ 1.9. Time: 19 seconds. **Defenses to increase entropy**: (1) Increase character count. (2) Increase alphabet (add symbols). (3) Increase distortion. **Trade-off**: More characters/distortion → harder for humans too. **Key insight**: CAPTCHA security ≠ entropy. Even high entropy is useless if ML solver has high accuracy. Security = min(entropy, -log₂(P_ML_solver_correct)).

**Q8: Analyze the snake segmentation algorithm for CAPTCHAs. How does it handle overlapping characters, and what are its computational limitations?**
**Answer:** **Algorithm**: (1) Initialize snake (deformable contour) as circle around character region. (2) Snake has internal energy (smoothness constraint) and external energy (image gradients). (3) Iteratively minimize total energy: E = α · E_internal + β · E_external. (4) E_internal penalizes sharp curves. (5) E_external attracts snake to edges. **Handling overlaps**: Snake cannot cross foreground pixels → naturally separates overlapping characters. Internal energy maintains smoothness → prevents snake from collapsing into noise. **Computational complexity**: O(n · m · k) where n = snake points, m = image pixels, k = iterations. Typical: n=50, m=10000, k=100 → 5 × 10^7 operations. **Limitations**: (1) Local minima: Snake may settle on wrong boundary. (2) Initialization-sensitive: Wrong starting point → wrong segmentation. (3) Slow: Must run per character. (4) Cannot handle touching characters (shared boundary). **Comparison**: Graph-based (Dijkstra): O(W · H · log(W·H)) → faster. Snake: more accurate for clean boundaries, slower overall. **Improvement**: Use CNN to predict initial snake positions → reduce iterations.

**Q9: Why is the "inverse Turing test" framing of CAPTCHAs misleading? Discuss the fundamental asymmetry between humans and machines in CAPTCHA solving.**
**Answer:** **Original Turing test**: Machine convinces human it's human. **Inverse (CAPTCHA)**: System convinces human it's human, machine it's not. **Why misleading**: (1) **Asymmetry**: Human recognition is effortless (System 1). Machine recognition requires explicit computation. (2) **No adaptivity**: Standard Turing test allows dialogue. CAPTCHA is single-shot. (3) **Not testing intelligence**: CAPTCHA tests perception, not reasoning. **Fundamental asymmetry**: Humans use top-down processing: context, expectation, world knowledge. ML uses bottom-up processing: pixel statistics, features. **Formal**: Human: P(correct | image, context, world_knowledge) ≈ 0.99. ML: P(correct | image, training_data) → 0.99 as data increases. **Implication**: CAPTCHA security = time advantage of human processing over ML. As ML improves, advantage shrinks → CAPTCHA arms race approaches end. **Alternative framing**: CAPTCHA = "hard problem for current ML." Not a Turing test — a moving target.

**Q10: Compare OCR-based and ML-based attacks on CAPTCHAs. Why does ML dominate, and what are the fundamental limits of each approach?**
**Answer:** **OCR approach**: (1) Preprocessing: binarize, deskew, denoise. (2) Segmentation: vertical projection, connected components. (3) Template matching: compare segments to character templates. **Limitations**: (1) Fails on distorted text. (2) Cannot handle overlapping characters. (3) Template library must cover all font variations. **ML approach**: (1) Feature extraction: learned automatically (CNN). (2) Classification: softmax over character classes. (3) End-to-end: no explicit segmentation needed. **Why ML dominates**: (1) **Representation learning**: CNN learns features from data, no manual feature engineering. (2) **Invariance**: CNN learns rotation/scale/distortion invariance automatically. (3) **Data efficiency**: GANs + transfer learning solve data bottleneck. (4) **End-to-end**: Joint optimization of segmentation + classification. **Fundamental limits**: (1) OCR: cannot handle arbitrary distortion (no learned invariance). (2) ML: requires training data distribution to match test distribution. Adversarial examples exploit distribution mismatch. **Complexity**: OCR: O(W × H × K) where K = template count. ML: O(W × H × F) where F = filter count. Both linear in image size, but ML has higher constant (more computation per pixel). **Conclusion**: ML is strictly more powerful but more resource-intensive.

---
---

# CHAPTER 3: ELECTRONIC PAYMENTS & BANKING

---

## 1. HISTORY OF MONEY
| Form | Period | Property |
|------|--------|----------|
| Barter | Prehistoric | Double coincidence of wants |
| Commodity | Ancient | Gold, salt — portable, divisible |
| Commodity standard | ~19th C | Paper backed by gold/silver |
| Fiat | Modern | Government declaration + trust |
| Electronic | ~end 20th C | Electronic representations |

Cash: ~80% of transactions, no audit trail, no transaction costs

---

## 2. PAYMENT CLASSIFICATION
- **Timing**: Pre-paid, Pay-now, Post-paid
- **Online/Offline**: Bank involved in real-time or not

### Security Requirements
- Authorization, confidentiality, availability, atomicity (all-or-nothing), privacy (anonymity + untraceability)

---

## 3. CREDIT CARDS

### Types
- **Debit**: Real-time
- **Charge**: End of month
- **Credit**: Extended

### Fraud
- **CVV**: 3-digit MAC on magnetic strip (keyed by issuer only)
- **CVV2**: Printed on card, NOT stored by merchants, doesn't prevent phishing
- **Skimming**: Trick cardholder into swiping through attacker's reader

---

## 4. ONLINE PAYMENTS

### SSL/TLS
- Server authenticated, data encrypted
- **No user authentication**, merchant sees CC number, phishing risk

### SET (Secure Electronic Transactions)
- Dual signature: hash of hash of (order info + payment instruction)
- CC number hidden from merchant
- **Failed**: Too costly, merchants want CC numbers, requires PKI + special software

---

## 5. EMV SMART CARDS

| Type | Crypto | Description |
|------|--------|-------------|
| SDA | Symmetric | Static — card sends signature, terminal verifies |
| DDA | Digital signatures | Terminal sends challenge, card signs |
| CDA | Combined | MAC signed with card's private key |

**Relay attack** on contactless: Attacker relays card-terminal communication → mitigation: distance bounding protocols

---

## 6. E-CASH

### DigiCash (Blind RSA Signatures)
1. User blinds coin hash with random r
2. Bank signs blinded value
3. User unblinds → valid signature
4. Bank can't link signed coin to withdrawal

### CAFE (Offline)
- No real-time checking
- Double-spending detected at redemption → identity revealed

---

## 7. MICROPAYMENTS — PayWord

### Three Phases
1. **Registration**: Broker issues certificate for user
2. **Payment**: Hash chain `w_n, w_{n-1}=h(w_n),...,w_0=h^(n)(w_n)`. Commitment signed once. Each payment: send (w_i, i). Vendor checks hash.
3. **Settlement**: Vendor sends last payword to broker. Broker verifies, pays.

**Efficiency**: 1 signature per session, 1 hash per payment.

---

## 8. ATM SECURITY

- Card stores PAN + PIN key
- **Norwegian case study (2001)**: 4 valid cards → crack DES key offline. Each card divides keys by 2^16.
- **DES brute force**: 24h (1999), $10K hardware (2007), 2 days GPUs (2016)
- Most fraud: skimming, social engineering, corrupt staff

---

## 9. HOME BANKING

### Authentication Evolution
PIN/TAN → iTAN → mTAN → ChipTan → PhotoTan → AppTan → HBCI/FinTS

### Phishing on iTAN
User logs into phishing site → site logs into real bank → bank requests iTAN → user enters → attacker uses

### Eurograbber (2012)
Trojan → logs credentials → installs mobile malware → intercepts mTANs

---

## 10. BITCOIN

### Core Concepts
- **Address**: ECDSA key pair, address = RIPEMD-160(pubkey)
- **Transaction**: References previous tx as input, specifies output addresses + amounts
- **Block**: Header (prev hash, Merkle root, nonce, difficulty) + transactions
- **Merkle Root**: Binary hash tree of all transactions → O(log n) verification
- **Mining**: Find nonce so SHA-256(block) has leading zeros
- **Difficulty**: Adjusts every 2,016 blocks → 10 min/block target
- **Supply**: 50 BTC initially, halves every 210K blocks, cap 21M
- **6 confirmations** (~60 min) for safe transaction

### Monero
- Ring signatures, stealth addresses, Pedersen Commitments

---

## EXAM QUESTIONS — CHAPTER 3

**Q1: Prove the correctness of blind RSA signatures. Show that the bank cannot link the signed coin to the withdrawal.**
**Answer:** **Setup**: Bank has RSA key pair (e, d, n). User wants coin (sn, exp, val). **Protocol**: (1) User computes h = H(sn, exp, val). (2) User chooses random r ∈ Z_n*, computes h' = h · r^e mod n. (3) User sends h' to bank. (4) Bank signs: s' = (h')^d = (h · r^e)^d = h^d · r^(ed) = h^d · r mod n (since ed ≡ 1 mod φ(n)). (5) User unblinds: s = s' · r^{-1} = h^d mod n. **Correctness**: s = h^d mod n = bank's signature on h. User has valid signature without bank seeing h. **Unlinkability**: Bank sees h' = h · r^e mod n. Since r is random and uniformly distributed, h' is uniformly distributed in Z_n* (by RSA assumption). Bank cannot determine h from h'. **Formal**: For any h₁, h₂ ∈ Z_n*, there exists r such that h₁ · r^e = h₂. Specifically, r = (h₂/h₁)^(1/e) mod n. Therefore Pr(bank can distinguish h₁ from h₂) = 1/n ≈ 0. **Information-theoretic**: Even with unlimited computation, bank cannot link because the blinding factor r is truly random and never revealed. **Double-spending prevention**: Bank stores h' values. If same h appears twice (after unblinding), user spent twice → identity revealed (if escrowed).

**Q2: Derive the expected total supply of Bitcoin. Prove the 21 million cap.**
**Answer:** **Reward schedule**: Block i reward = 50 / 2^(i/210000) BTC (halves every 210,000 blocks). **Total supply**: S = Σ_{k=0}^∞ 210000 × 50 / 2^k = 210000 × 50 × Σ_{k=0}^∞ (1/2)^k = 210000 × 50 × 2 = **21,000,000 BTC**. **Proof**: Geometric series: Σ_{k=0}^∞ r^k = 1/(1-r) for |r| < 1. Here r = 1/2, so sum = 2. **Detailed**: Phase 0 (blocks 0-209999): 210000 × 50 = 10,500,000. Phase 1 (blocks 210000-419999): 210000 × 25 = 5,250,000. Phase 2: 210000 × 12.5 = 2,625,000. ... Phase k: 210000 × 50/2^k. Total = Σ_{k=0}^∞ 210000 × 50/2^k = 10,500,000 × Σ_{k=0}^∞ 1/2^k = 10,500,000 × 2 = 21,000,000. **Practical**: After 33 halvings (block ~6.93M), reward < 1 satoshi (10^-8 BTC). Supply converges to 21M asymptotically. **April 2023**: ~19.3M mined (92%). Remaining ~1.7M will be mined over ~100+ years.

**Q3: Analyze the PayWord micropayment scheme. Derive the computational cost for user, vendor, and broker. Prove that the hash chain provides security.**
**Answer:** **Setup**: User generates hash chain: w_n random, w_{i-1} = h(w_i) for i = n,...,1. w_0 = h^n(w_n) = commitment. **Registration**: User sends signed commitment M = {V, Cert_U, w_0, date}_{K_U^{-1}} to broker. Broker verifies, issues certificate. **Payment**: User sends (w_i, i) to vendor. Vendor checks: h^i(w_i) = w_0 (hash i times, verify against commitment). **Settlement**: Vendor sends (w_0, last_i) to broker. Broker verifies, pays. **Computational cost**: User: 1 signature (commitment) + n hashes (chain generation) per session. Vendor: 1 signature verification (commitment) + 1 hash per micropayment. Broker: 1 signature verification (commitment) + 1 hash per settlement. **Security proof**: One-way property of h: given w_i, cannot compute w_{i-1} = h(w_i) efficiently. **Double-spending**: If user sends w_i twice, vendor detects (same index). If user sends w_i to two vendors, both claim same coins → broker detects. **Efficiency**: O(1) signatures per session, O(1) hashes per payment. Compared to per-transaction digital signatures: O(n) savings for n micropayments.

**Q4: Explain the Norwegian ATM attack (2001). Show how 4 cards determine a DES key. Calculate the complexity.**
**Answer:** **Setup**: Each ATM card stores PAN and PIN key. PIN = first 4 digits of Enc(PAN) using shared DES key K. **Attack**: Attacker obtains 4 cards with known PANs and PINs. **Key elimination**: For each card, the PIN constraint eliminates 2^40 / 2^16 = 2^24 possible keys (PIN is 4 digits = 2^16 possibilities out of 2^64 DES key space... actually more precisely: each card pair eliminates half the key space). **Detailed**: DES key space = 2^56. Each card: PIN = f_K(PAN). For each possible key K', compute PIN' = f_K'( PAN). If PIN' matches observed PIN → K' is consistent. Probability K' is consistent ≈ 1/2^16 (PIN has 10^4 = ~2^13.3 possibilities, but each key either produces correct PIN or not). After 4 cards: remaining keys ≈ 2^56 / (2^13.3)^4 = 2^56 / 2^53.2 ≈ 2^2.8 ≈ 7 keys. **Brute force remaining**: 7 keys × test time ≈ instant. **DES brute force history**: 1999: 24 hours (distributed.net). 2007: Copacobana ($10K) < 1 week. 2016: GPUs ~2 days. **Lesson**: Symmetric keys too short → offline attack feasible. Mitigation: longer keys (AES-128), hardware security modules.

**Q5: Analyze the Bitcoin Merkle tree. Why does it provide O(log n) verification? Prove the efficiency gain over linear scanning.**
**Answer:** **Structure**: Leaf nodes = transaction hashes. Internal nodes = H(left || right). Root = Merkle root in block header. **Verification (SPV)**: To prove transaction T is in block: provide authentication path (sibling hashes up to root). Path length = log₂(n) for n transactions. **Proof**: For n = 2^k transactions, tree has k levels. To verify T_i: need hashes of log₂(n) siblings. Example: n=8 transactions, T₃ needs 3 hashes: sibling at level 0, parent at level 1, uncle at level 2. **Complexity**: Linear scan: O(n) hash computations. Merkle path: O(log n) hash computations. For n = 1000: linear = 1000, Merkle = 10. **Space**: SPV client stores only block headers (80 bytes each), not full blocks (~1MB). **Formal**: Let H = height of tree = log₂(n). Authentication path: H hashes. Verify: H hash computations. Total: O(H) = O(log n). **Tamper detection**: Changing one transaction → changes leaf hash → changes all ancestors → changes Merkle root → block invalid. **Bitcoin block header**: 80 bytes (prev_hash, merkle_root, timestamp, difficulty, nonce). SPV security: light nodes verify inclusion but cannot verify transaction validity (no script execution).

**Q6: Compare online and offline e-cash. Analyze the double-spending detection mechanism in offline systems.**
**Answer:** **Online e-cash**: Bank verifies every transaction in real-time. Double-spending prevented at spending time. **Drawback**: Requires connectivity, bank availability. **Offline e-cash**: No real-time bank check. Double-spending detected at redemption. **CAFE protocol**: (1) Withdrawal: User gets coin with blind signature. (2) Spending: User shows coin to merchant. Merchant stores coin locally. (3) Redemption: Merchant submits coin to bank. Bank checks if coin spent before. (4) If double-spent: Bank identifies user (escrow mechanism). **Detection mechanism**: Coin contains identity information (encrypted). Single spend: identity stays hidden. Double spend: two different merchants submit same coin → bank decrypts identity from both → user identified. **Formal**: Coin = (serial_number, value, identity_encrypted). Merchant 1 has (sn, val, E(id)). Merchant 2 has (sn, val, E(id')). Bank: if sn matches → compare encrypted identities → decrypt → identify user. **Limitations**: (1) Requires tamper-resistant device for identity escrow. (2) User privacy lost on double-spending. (3) Detection is post-hoc (damage already done). **Blind signatures**: Bank signs coin without seeing content → user privacy during withdrawal.

**Q7: Analyze the SET (Secure Electronic Transactions) protocol. Why did it fail despite superior security?**
**Answer:** **SET design goals**: (1) Confidentiality: merchant never sees credit card number. (2) Authentication: cardholder, merchant, issuer all authenticated. (3) Integrity: all messages signed. **Dual signature**: H(H(order_info) || H(payment_instruction)). Both hashes signed together. Merchant sees order_info, not payment_instruction. Bank sees payment_instruction, not order_info. **Why it failed**: (1) **PKI overhead**: Every cardholder needs digital certificate → CA infrastructure expensive. (2) **Software complexity**: Special SET software required → merchants couldn't integrate easily. (3) **Merchant resistance**: Merchants WANT credit card numbers (for refunds, marketing). (4) **SSL/TLS "good enough"**: 128-bit encryption sufficient for most threats. (5) **User friction**: Extra steps, certificate management → poor UX. (6) **Cost**: Implementation cost >> perceived benefit. **Comparison**: SET: 3-way handshake, dual signatures, certificate per user. SSL/TLS: simple encryption, no user auth. **Lesson**: Security ≠ usability. Over-engineering fails if usability cost is too high. Market chose convenience over perfect security.

**Q8: Calculate the probability of successfully brute-forcing a 4-digit PIN with 3 trial attempts. Compare online and offline attack scenarios.**
**Answer:** **Online attack** (3 attempts): P(success) = 3/10000 = 0.0003 = 0.03%. Account locked after 3 failures → stops attack. **Offline attack** (with stolen hash): PIN space = 10000 = 10^4. Each attempt: hash candidate PIN, compare. P(success) = 1 (given enough time). Complexity: 10000 hash computations. At 10^9 hashes/sec: 10 microseconds. **Enhanced attack**: If PIN structure known (e.g., p1+p4 = p2+p3 check digit): reduced space ≈ 1000 valid PINs. P(crack one attempt) = 1/1000. **Account enumeration**: Given Q accounts, probability of cracking at least one: P(success) = 1 - (1 - p)^Q where p = attempts/10^n. For Q = 220000, p = 3/10000: P ≈ 1 - e^(-220000 × 0.0003) ≈ 1 - e^(-66) ≈ 1. **Real attack (Eurograbber 2012)**: Trojan captures credentials + intercepts mTAN. Bypasses online protection entirely. Steals €36M from 1700 accounts.

**Q9: Explain the Eurograbber attack. How does it combine multiple attack vectors, and why is it devastating?**
**Answer:** **Attack chain**: (1) User clicks malicious link → installs Android trojan. (2) Trojan intercepts SMS → captures mTAN (mobile transaction authentication number). (3) Attacker logs into online banking with stolen credentials + mTAN. (4) Attacker transfers money to mule accounts. **Components**: (a) Social engineering (phishing link). (b) Mobile malware (Android trojan). (c) Real-time credential theft. (d) Transaction manipulation. **Why devastating**: (1) **Bypasses 2FA**: mTAN intercepted in real-time. (2) **User unaware**: Transfers happen silently. (3) **Scale**: Automated → thousands of accounts. (4) **Irreversible**: Bank transfers hard to reverse. **Mitigation**: (1) Out-of-band verification (call back to known number). (2) Transaction data signing (mTAN includes amount + recipient). (3) Device attestation (detect jailbroken phones). (4) Behavioral analysis (detect unusual transfer patterns). **Formal security model**: Attacker has: credentials (what you know) + mTAN (what you have, intercepted). Need: what you ARE (biometric) or where you ARE (location). **Lesson**: Security is only as strong as weakest link. mTAN on same device as credentials = single point of failure.

**Q10: Design a secure micropayment protocol using hash chains. What are the trust assumptions, and how does the protocol prevent double-spending?**
**Answer:** **Protocol**: (1) User U generates hash chain: w_n random, w_{i-1} = h(w_i). w_0 = commitment. (2) U signs commitment: Sig_U(w_0, date, amount). Sends to Broker B. (3) B verifies, creates certificate: Cert_B(w_0, U, amount, expiry). (4) U sends (w_i, i, Cert_B) to Vendor V. (5) V verifies: h^i(w_i) = w_0 (hash i times). (6) V accumulates payments. (7) V sends (w_0, Cert_B, final_i) to B. (8) B pays V. **Trust assumptions**: (a) B is trusted (holds U's funds). (b) h is one-way. (c) U's private key not compromised. **Double-spending prevention**: (1) Same w_i to same V: V stores (w_i, i), detects duplicate. (2) Same w_i to different V: Both submit to B. B pays first claim, rejects second (or investigates). (3) Chain exhaustion: w_n is last valid payword. After n payments, U must re-register. **Security**: Forward security: compromising w_i doesn't reveal w_{i-1} (one-way property). **Efficiency**: O(1) signatures per session, O(1) hashes per payment. Scalable for millions of micropayments.

---
---

# CHAPTER 4: E-MAIL SECURITY

---

## 1. EMAIL ARCHITECTURE

### Protocols
- **SMTP**: Push email (sender → server, server → server)
- **IMAP/POP**: Pull email (receiver ← server)
- **DNS MX records**: Locate SMTP server

---

## 2. TWO SECURITY APPROACHES
- **End-to-end**: PGP, S/MIME — protects content between sender and receiver
- **Hop-by-hop**: SMTPS, POP3s, IMAPs — protects connection to mail server only

---

## 3. PGP (Pretty Good Privacy)

### Operations — Sender
1. Hash message → sign with private key
2. Compress
3. Encrypt compressed + signed hash with symmetric key
4. Encrypt symmetric key with Bob's public key

### Trust Model: Web of Trust
- No CA required; any user can sign keys (introducer)
- Trust levels: Full, Partial, None
- Key legitimacy = sum of weights ≥ 1 → key valid
- Two partially trusted → legitimacy = 1

### Key Rings
- **Public ring**: User ID, Key ID (64 LSBs), Public key, Trust levels, Certificates
- **Private ring**: User ID, Key ID, Public key, Encrypted private key

### Algorithms
- Public key: RSA, ElGamal, DSS, ECDSA
- Symmetric: IDEA, 3DES, CAST-128, Blowfish, AES
- Hash: MD5, SHA-1, RIPE-MD/160

---

## 4. S/MIME

- X.509 v3 certificates (hierarchical trust)
- **Content types**: Signed-data, Enveloped-data, Digested-data, Encrypted-data, Authenticated-data

### PGP vs. S/MIME

| Aspect | PGP | S/MIME |
|--------|-----|--------|
| Trust | Web of Trust | CA-based |
| Certificates | Optional | Required |
| Setup | Easier | Harder |
| Users | Individuals | Enterprises |

---

## EXAM QUESTIONS — CHAPTER 4

**Q1: Compare PGP and S/MIME in terms of trust model, scalability, and security properties. Which would you deploy in a 10,000-employee enterprise and why?**
**Answer:** **PGP — Web of Trust**: Decentralized. Any user signs any key. Trust = sum of weights ≥ 1. No CA required. **Scalability**: O(N²) potential key signatures in worst case. Trust propagation: transitive but limited. **S/MIME — Hierarchical Trust**: CA-based. Single root CA → intermediate CAs → end users. X.509 v3 certificates. **Scalability**: O(N) certificates, O(1) verification (chain to root). **Comparison**: PGP: resilient to CA compromise, harder to manage, subjective trust. S/MIME: centralized management, single point of failure (CA), easier to revoke. **Enterprise choice**: S/MIME. Reasons: (1) Centralized key management (IT controls certificates). (2) Easy revocation (CRL/OCSP). (3) Integration with email clients (Outlook, Thunderbird). (4) Legal compliance (auditable trust chain). (5) PGP trust is subjective → policy enforcement impossible. **PGP advantage**: No CA dependency → resistant to government compulsion. **Formal trust comparison**: PGP: trust = Σ w_i ≥ 1 (additive). S/MIME: trust = root CA ∈ trusted_store (binary). PGP allows gradual trust. S/MIME allows global policy.

**Q2: Prove the PGP trust calculation. If Alice fully trusts Bob (w=1), Bob partially trusts Charlie (w=½), and Charlie partially trusts David (w=½), is David's key usable?**
**Answer:** **Trust chain**: Alice → Bob (fully trusted, w=1) → Charlie (partially trusted by Bob, w=½) → David (partially trusted by Charlie, w=½). **Key legitimacy calculation**: (1) Bob's key: directly signed by Alice → legitimacy = 1 (trusted). (2) Charlie's key: signed by Bob. Bob's trust weight = 1. Legitimacy = 1 × ½ = ½ (partially trusted). Wait — Bob's trust weight is 1 (fully trusted), and Bob's certificate of Charlie has weight ½ (partially trusted). Actually: **PGP formula**: Legitimacy = Σ (trust_weight_of_signer × certificate_weight). If signer is fully trusted: weight = 1. Partially trusted: weight = ½. Certificate weight: full = 1, partial = ½. **Corrected**: Charlie: signed by Bob (fully trusted → weight=1) with partial certificate (weight=½). Legitimacy = 1 × ½ = ½. **David**: signed by Charlie (legitimacy ½, but trust weight from Charlie = ½). Legitimacy = ½ × ½ = ¼. **Threshold**: Legitimacy ≥ 1 → usable. ¼ < 1 → **David's key is NOT usable**. **Edge case**: If Charlie's legitimacy were 1 (e.g., also signed by Alice directly): legitimacy = 1 × ½ = ½. Still not enough. Need either: (a) Two partially trusted signers (½ + ½ = 1), or (b) One fully trusted signer (1).

**Q3: Analyze the PGP hybrid encryption model. Why is compress before encrypt preferred? What are the security implications?**
**Answer:** **PGP operations**: (1) Hash message → sign with private key. (2) Compress. (3) Encrypt compressed + signed hash with symmetric key. (4) Encrypt symmetric key with Bob's public key. **Why compress**: (a) **Reduced size**: Smaller message → faster transmission. (b) **Increased security**: Compression removes redundancy → harder for cryptanalysis. Known-plaintext attacks harder because compressed data has less structure. (c) **Randomization**: Compressed output varies with compression algorithm parameters → same plaintext produces different ciphertext (with different session keys). **Security implication — CRIME attack**: If compression is before encryption, and attacker can inject known plaintext (e.g., in TLS), they can observe ciphertext length changes → infer compressed content → extract secrets (cookies, tokens). **Formal**: Let Comp(m) = compressed m. If Comp(m₁) has different length than Comp(m₂), attacker learns which plaintext is more similar to injected content. **Trade-off**: Compression improves efficiency and potentially security, but introduces side-channel vulnerability (length leak). **PGP mitigates**: Each message uses new session key → length leak per-message only.

**Q4: Explain the S/MIME signed-data content type. Why is non-repudiation important, and how is it achieved?**
**Answer:** **S/MIME signed-data structure**: Version, digest algorithms, encapContentInfo (message), certificates, signerInfos (signature). **Process**: (1) Hash message with digest algorithm. (2) Sign hash with signer's private key. (3) Attach signature + certificates. **Non-repudiation**: Sender cannot later deny sending the message. **How achieved**: Digital signature is bound to signer's identity via certificate. Only signer's private key can produce valid signature. **Legal standing**: Courts accept digital signatures as evidence (e-signature laws). **Attack on non-repudiation**: Private key compromise → attacker can forge signatures. **Countermeasure**: Revocation certificates, HSMs for key storage. **Formal**: Non-repudiation requires: (a) Signature scheme is EUF-CMA (existential unforgeability under chosen message attack). (b) Private key not shared. (c) Certificate chain valid at signing time. **S/MIME content types**: Signed-data (integrity + authentication + non-repudiation). Enveloped-data (confidentiality only). Both (combined). **Critical difference from PGP**: PGP uses web of trust → non-repudiation depends on trust chain validity. S/MIME uses CA → non-repudiation depends on CA integrity.

**Q5: Analyze the hybrid encryption model used in PGP. Why is asymmetric encryption ~1000× slower than symmetric?**
**Answer:** **PGP hybrid**: RSA encrypts 128-bit symmetric key. AES encrypts message. **Complexity comparison**: AES: O(n) where n = message blocks. Each block: 10-14 rounds of SubBytes, ShiftRows, MixColumns, AddRoundKey. Hardware acceleration: AES-NI → ~1 cycle/byte. RSA: O(n³) for modular exponentiation (n = key size bits). For 2048-bit RSA: 2048³ ≈ 8.6 × 10^9 operations. **Speed ratio**: AES: ~1 GB/s (hardware). RSA: ~1000 signatures/sec (sign+verify) → ~1 KB per signature. Ratio: 10^6 × slower. **Practical**: RSA encrypts 256-byte key in ~1ms. AES encrypts 1GB message in ~1s. **Why RSA is slow**: Modular exponentiation requires repeated squaring: m^e mod n = (m^(e/2))² mod n. Each squaring: O(n²) for n-bit numbers. Total: O(n² · log e) ≈ O(n³). **Why AES is fast**: Substitution-permutation network: each operation is O(1) table lookup. Parallelizable. **Hybrid efficiency**: 1 RSA operation + 1 AES operation = encrypt message of any length. Without hybrid: n RSA operations per n-byte message.

**Q6: Design an attack that exploits the PGP key ring structure. How could an attacker forge trust?**
**Answer:** **PGP key ring structure**: Public ring: {User ID, Key ID (64 LSBs), Public key, Trust levels, Certificates}. Private ring: {User ID, Key ID, Public key, Encrypted private key}. **Attack vector 1 — Key ID spoofing**: Key ID = 64 LSBs of fingerprint. Collision: find different key with same 64-bit ID.概率: 2^64 keyspace → birthday attack needs 2^32 keys → feasible for motivated attacker. **Attack vector 2 — Trust escalation**: Attacker creates fake user IDs, signs with own key. If Alice (trusting) imports attacker's key → attacker can forge messages signed by "trusted" keys. **Attack vector 3 — Revocation absence**: PGP has no automatic revocation propagation. If attacker steals key → no way to inform others. Key remains trusted indefinitely. **Attack vector 4 — Meta-data leakage**: Key rings store user IDs, trust levels, certificates → reveals social graph. **Formal threat model**: Dolev-Yao adversary controls network. Can: intercept, modify, inject, drop messages. **Attack**: (1) Generate key pair with victim's User ID. (2) Sign own key (self-signature). (3) Send to victim's contacts. (4) Contacts trust forged key → attacker intercepts encrypted messages. **Defense**: Verify fingerprints out-of-band. **PGP limitation**: No central authority to report/verify key ownership.

**Q7: Explain why SET's dual signature provides separation of concerns. Prove that merchant cannot learn credit card number and bank cannot learn order details.**
**Answer:** **SET dual signature**: DS = Sign_{K_U}(H(H(OI) || H(PI))). OI = order info. PI = payment instruction (contains CC number). **Merchant receives**: OI, H(PI), DS. **Bank receives**: PI, H(OI), DS. **Merchant cannot learn PI**: Merchant only sees H(PI) (hash), not PI itself. Hash is one-way → cannot invert. **Bank cannot learn OI**: Bank only sees H(OI), not OI. **Formal proof**: Merchant's view: (OI, H(PI), DS). To recover PI from H(PI): require inversion of hash → computationally infeasible (preimage resistance). Bank's view: (PI, H(OI), DS). To recover OI from H(OI): same argument. **Binding**: DS commits to both OI and PI. Changing OI or PI → different hash → different DS → invalid signature. **Verification**: Merchant computes H(H(OI) || H(PI)), verifies DS. Bank does same. Both confirm binding. **Security property**: Privacy (separation of information) + Binding (commitment to both). **Why SET failed**: This security came at usability cost: merchants couldn't process refunds without CC number → business reason to reject SET.

**Q8: Analyze the S/MIME algorithm suite (V3.1). Why must receivers implement more algorithms than senders?**
**Answer:** **S/MIME V3.1 requirements**: Receiver MUST: 3DES (content), RSA (session key), SHA-1 (hash), DSS (signature), HMAC-SHA-1 (MAC). Sender MUST: 3DES, RSA, SHA-1, DSS. Receiver SHOULD: AES, ElGamal, MD5, RSA. Sender SHOULD: AES, RC2/40, MD5, RSA. **Why more for receiver**: (1) **Backward compatibility**: Receiver must decrypt messages sent with older algorithms. Sender can use new algorithms. (2) **Interoperability**: Different senders use different algorithms. Receiver must handle all. (3) **Graceful degradation**: If receiver supports only old algorithms, sender should use those. If sender uses new algorithms, receiver must still handle. **Formal**: Receiver's algorithm set ⊇ Sender's algorithm set. This ensures: ∀sender_algorithm ∈ S_sender: receiver_algorithm ∈ S_receiver. **Security implication**: Must support algorithms that may be weak (3DES, MD5). Attacker can force downgrade → use old algorithm. **Mitigation**: Algorithm preference lists, policy enforcement. **Practical**: Support old algorithms for compatibility, prefer new algorithms for security. This creates tension between usability and security.

**Q9: Compare the PGP Web of Trust with the CA model. Which provides better resistance to government compulsion? Analyze the failure modes.**
**Answer:** **Web of Trust (PGP)**: Decentralized. No single entity controls trust. Users decide who to trust. **Failure modes**: (a) Subjective: Trust decisions inconsistent. (b) Scalability: O(N²) signatures. (c) Revocation: No automatic propagation. (d) usability: Complex for non-experts. **CA model (S/MIME)**: Centralized. Root CAs in browser/email client trust stores. **Failure modes**: (a) Single point of failure: CA compromise → all certificates untrusted. (b) Government compulsion: CA can be forced to issue fraudulent certificates. (c) Scale: CAs manage millions of certificates → errors possible. **Government resistance**: PGP: No central authority to compel. Attacker must compromise individual users. Distributed → resistant. S/MIME: CA can be compelled to issue certificate for victim → man-in-middle. One court order compromises all users. **Formal**: PGP: Trust graph G = (V, E). Attack requires compromising edges in trust path. S/MIME: Trust tree T. Attack requires compromising root (1 node). **Hybrid approach**: Certificate Transparency (CT) — publicly logged certificates → detects fraudulent issuance. **Conclusion**: PGP resists compulsion better. S/MIME scales better. Enterprise: S/MIME + CT. Individual: PGP.

**Q10: Analyze the key ID size in PGP (64 bits). Is this sufficient for security? What are the attack vectors?**
**Answer:** **Key ID**: 64 least significant bits of key fingerprint = H(UserID || Public Key). **Collision resistance**: 64 bits → birthday attack needs 2^32 keys. For motivated attacker: feasible. **Preimage resistance**: 2^64 computation → infeasible. **Attack vectors**: (1) **Key ID collision**: Find different key with same 64-bit ID. Attacker generates many keys → one matches victim's ID. When victim imports, attacker's key replaces real one. **Probability**: After generating 2^32 keys, P(at least one collision) ≈ 50%. **Time**: ~1 hour on modern hardware. (2) **Short key ID spoofing**: Display shows only last 8 hex chars (32 bits). Birthday attack: 2^16 keys → trivial. **Defense**: Always verify full fingerprint (160 bits for SHA-1). (3) **Key substitution**: Replace victim's key in key server → distribute forged messages. **Formal security**: Key ID provides identification, not authentication. 64 bits = practical for identification, insufficient for collision resistance. **NIST recommendation**: Minimum 128-bit security level. 64-bit key ID below this. **Better alternative**: Use full fingerprint (160+ bits) or Key ID = full fingerprint.

---
---

# CHAPTER 5: BIOMETRICS

---

## 1. WHAT IS BIOMETRICS?
- Science of establishing identity based on physical, chemical, or behavioral attributes

### Two Modes
- **Authentication (verification)**: Is this Bob? → 1:1 comparison
- **Identification**: Who is this? → 1:N comparison

### vs. Traditional Auth
| Factor | Example |
|--------|---------|
| Know | Password, PIN |
| Have | Smart card, token |
| **IS** | Biometrics |

**Advantages**: Can't be lost, forgotten, easily stolen
**Disadvantages**: Can't be revoked, permanent, privacy concerns

---

## 2. BIOMETRIC SYSTEM COMPONENTS

1. **Sensor module**: Acquires raw biometric data
2. **Feature extraction**: Quality assessment + feature extraction
3. **Matching & decision**: Compare features, return match score, threshold decision
4. **Database**: Stores templates + biographic data

---

## 3. PERFORMANCE MEASUREMENT

### Key Metrics
- **Intra-class variation**: Variability within same individual's samples
- **Inter-class variation**: Variability between different individuals
- **Useful features**: High inter-class, low intra-class variation

### Authentication Metrics
- **Match score**: Two samples from same individual
- **Impostor score**: Two samples from different individuals
- **Threshold t**: ≥ t → accept; < t → reject

| Metric | Definition |
|--------|-----------|
| **FAR** (False Accept Rate) | Impostor accepted |
| **FRR** (False Reject Rate) | Genuine rejected |
| **FTE** (Failure to Enroll) | Users who can't enroll |

FAR and FRR are **trade-off** regulated by threshold t.

### ROC Curve
- Plots FAR vs. FRR for different thresholds
- Used to compare system accuracy

### Doddington's Zoo
| Type | Characteristic | Effect |
|------|---------------|--------|
| **Sheep** | Distinctive features, low variation | Low FRR, low FAR |
| **Goat** | Large intra-class variation | Prone to false rejects |
| **Lamb** | Low inter-class variation | Easy to impersonate |
| **Wolf** | Can manipulate traits | Successful imposture |

---

## 4. BIOMETRIC TRAITS

### Characteristics Required
1. **Universality**: Everyone has it
2. **Uniqueness**: Different across individuals
3. **Permanence**: Stable over time
4. **Measurability**: Acquirable without undue inconvenience
5. **Performance**: Meets accuracy/resource constraints
6. **Acceptability**: Users willing to present
7. **Unfakeability**: Difficult to imitate

### Comparison Table

| Trait | Uniqueness | Universality | Permanence | Measurability | Acceptability |
|-------|-----------|-------------|-----------|--------------|--------------|
| DNA | High | High | High | Low | Low |
| Fingerprint | High | Medium | High | Medium | Medium |
| Iris | High | High | High | Medium | Low |
| Face | Low | High | Medium | High | High |
| Voice | Low | Medium | Low | Medium | High |
| Signature | Low | Medium | Low | High | High |
| Gait | Low | Medium | Low | High | High |

---

## 5. CHARACTERISTICS OF SPECIFIC TRAITS

### Fingerprint
- Unique even for identical twins
- ~4% population unsuitable (genetic, aging, occupational)
- Matching: minutiae points (position + orientation)

### Iris
- Stabilizes first 2 years of life
- Identical twins have different irises
- Low FAR but high FRR

### Face
- Non-intrusive, natural for humans
- 2D: fooled by photos, videos
- 3D: fooled by masks

### Voice
- Physical (vocal tract) + behavioral
- Not very distinctive
- Useful for phone authentication

### Keystroke
- Behavioral, large intra-class variation
- Enables continuous authentication

---

## 6. SECURITY & PRIVACY

### Vulnerabilities
| Attack | Description |
|--------|-------------|
| Circumvention | Replace database, override matcher |
| Covert acquisition | Lift fingerprints, capture voice |
| Collusion/Coercion | Willing or forced cooperation |
| DoS | Enroll many noisy samples → lower threshold |
| Repudiation | Claim data was stolen |

### Privacy Issues
- Biometrics are **not secret** — can be captured without consent
- **Cannot be revoked** if misused
- **Secondary uses**: Cross-application tracking
- **Health info**: Can reveal genetic disease, medication

---

## 7. SPOOF ATTACKS

### Fingerprint Spoofing (CCC 2004)
1. Lift latent print from glass (cyanoacrylate fuming)
2. Photograph/scan the print
3. Print on transparency
4. Apply wood glue → create dummy
5. Theatrical glue attaches to own finger

### Detection Methods
- Measure perspiration, skin absorbance, temperature, pulse
- Challenge-response

### Iris Spoofing
- High-quality photos, printed contact lenses, 3D artificial irises
- Detection: pupil involuntary motion, light response, blink challenge

### Face Spoofing
- 2D: photos, videos → detect head movement, blinking
- 3D: masks → challenge-response (blink, smile)

---

## EXAM QUESTIONS — CHAPTER 5

**Q1: Derive the FAR/FRR trade-off mathematically. Show that lowering threshold t decreases FRR but increases FAR. Prove that no threshold achieves both FAR = 0 and FRR = 0 simultaneously.**
**Answer:** **Definitions**: Let s = match score (similarity between two biometric samples). Genuine scores: distribution f_g(s). Impostor scores: distribution f_i(s). Threshold t: accept if s ≥ t. **FAR(t)** = P(s ≥ t | impostor) = ∫_t^∞ f_i(s) ds. **FRR(t)** = P(s < t | genuine) = ∫_{-∞}^t f_g(s) ds. **Trade-off**: As t decreases: FRR decreases (fewer genuine rejections). FAR increases (more impostor accepts). As t increases: FAR decreases, FRR increases. **Proof no perfect threshold**: Assume FAR = 0 and FRR = 0. FAR = 0 requires t ≥ max{s : f_i(s) > 0} (threshold above all impostor scores). FRR = 0 requires t ≤ min{s : f_g(s) > 0} (threshold below all genuine scores). These require max(impostor scores) ≤ min(genuine scores). **But**: In practice, genuine and impostor distributions overlap (same biometric feature space). Therefore max(impostor) > min(genuine) → impossible. **Formal**: Distributions overlap → ∀t: FAR(t) > 0 AND FRR(t) > 0. **Equal Error Rate (EER)**: t where FAR = FRR. Used to compare systems. Lower EER = better system.

**Q2: Explain the ROC curve. How does it relate to the Neyman-Pearson lemma? What does the area under the ROC curve (AUC) represent?**
**Answer:** **ROC curve**: Plots FAR (x-axis) vs. FRR (y-axis) for all thresholds t. Actually: P(detect | impostor) vs. P(reject | genuine). Or: TPR vs. FPR. **Neyman-Pearson lemma**: For a given significance level α (FAR), the likelihood ratio test maximizes power (1 - FRR). **Test**: Accept if f_g(s)/f_i(s) ≥ λ(t). This gives optimal trade-off. **ROC is the curve of optimal operating points**. Any point on ROC is optimal for some α. **AUC interpretation**: AUC = probability that a randomly chosen genuine score is higher than a randomly chosen impostor score. AUC = ∫₀¹ TPR(FPR) dFPR. **Range**: 0.5 (random guessing) to 1.0 (perfect). AUC = 0.5: no discrimination. AUC = 1.0: perfect separation. **Formal**: AUC = P(S_genuine > S_impostor). **For biometric system**: AUC = 0.99 means 99% chance genuine score exceeds impostor score. **Comparison**: System A (AUC=0.99) better than System B (AUC=0.95) at all operating points.

**Q3: Analyze Doddington's Zoo. How can the classification be used to improve system accuracy? Give concrete threshold adjustments.**
**Answer:** **Sheep**: Distinctive features, low intra-class variation. Genuine scores consistently high. Impostor scores consistently low. → **Threshold**: Lower (don't reject sheep easily). **Goat**: Large intra-class variation. Genuine scores spread widely → many false rejects. → **Threshold**: Lower (accept goat more easily, tolerate higher FAR for goat class). **Lamb**: Low inter-class variation. Impostor scores high → easy to impersonate. → **Threshold**: Higher (reject lambs more aggressively). **Wolf**: Can manipulate traits. Impostor scores very high. → **Threshold**: Much higher (flag for additional verification). **Adaptive threshold**: t_i = t_base + Δ(class_i). Sheep: Δ = -α. Goat: Δ = -β. Lamb: Δ = +γ. Wolf: Δ = +δ. **Formal optimization**: Minimize total error: E = Σ_i w_i · (FAR_i + FRR_i) subject to per-class constraints. **Identification system**: Match sheep first (high confidence), then process goats/lambs separately. **Training phase**: Label users as sheep/goat/lamb/wolf from enrollment data. **Practical**: Reduces EER by 20-30% compared to global threshold.

**Q4: Compare authentication and identification. Analyze the computational complexity of each.**
**Answer:** **Authentication (verification)**: 1:1 comparison. User claims identity → system verifies. **Complexity**: O(1) comparisons per query. Template retrieval: O(log N) (database lookup). **Identification**: 1:N comparison. Unknown user → find in database of N users. **Complexity**: O(N) comparisons per query. For N = 10^6 users: 10^6 comparisons. **Naive Bayes identification**: P(user_i | feature) = P(feature | user_i) · P(user_i) / P(feature). Compute for all i → select max. **Formal**: Authentication: verify (template, sample) → match score → threshold decision. Time: O(1). Identification: for i = 1 to N: score_i = match(template_i, sample); return argmax(score_i). Time: O(N). **Scaling problems**: N = 10^6, matching time = 1ms → 1000 seconds per identification. **Solutions**: (1) Indexing (hash-based pre-filtering). (2) Tiered matching (fast filter → detailed comparison). (3) Parallel processing. **Accuracy**: Identification is harder because: (1) More comparisons → more chances for false matches. (2) Score distributions change with N. (3) Computational cost limits template quality (larger templates needed for accuracy).

**Q5: Prove that biometrics cannot replace passwords entirely. What are the fundamental limitations?**
**Answer:** **Password properties**: (1) Revocable: change when compromised. (2) Secret: known only to user. (3) Transferrable: can be used across systems. **Biometric limitations**: (1) **Non-revocable**: Cannot change fingerprint if compromised. Biometric is permanent. (2) **Non-secret**: Biometric data can be captured without consent (face in photo, fingerprint on glass). (3) **Non-transferable**: Biometric tied to physical person. **Formal security model**: Password: secret s ∈ {0,1}^n. Compromise: s exposed → change to s'. Biometric: feature vector b ∈ ℝ^d. Compromise: b exposed → cannot change. **Cancelable biometrics**: Transform: b' = T(b, secret). If b' compromised: change secret → new transform. But: original b still compromisable. **Biometric cryptosystems**: Bind secret to biometric: s = F(b, helper_data). If helper_data exposed: need new biometric → impossible. **Fundamental**: Biometrics are "what you ARE" not "what you KNOW". Cannot be kept secret like a password. **Best practice**: Multi-factor: biometric (convenience) + password (revocability).

**Q6: Analyze the CCC fingerprint spoofing attack. What are the detection countermeasures, and why are they imperfect?**
**Answer:** **CCC attack steps**: (1) Lift latent print from glass using cyanoacrylate fuming. (2) Photograph/scan print. (3) Print on transparency film. (4) Apply wood glue to create 3D mold. (5) Attach to own finger with theatrical glue. **Why effective**: Fingerprint sensors measure ridge/valley pattern, not liveness. Spoof replicates pattern. **Detection methods**: (1) **Perspiration**: Real fingers perspire → measure conductivity change over time. Spoof doesn't perspire. (2) **Skin absorbance**: IR light absorption differs between real skin and glue. (3) **Temperature**: Real finger ≈ 37°C, spoof ≈ room temperature. (4) **Pulse**: Blood flow detection. (5) **Challenge-response**: Ask user to move finger, press harder. **Why imperfect**: (1) **False accepts**: Sophisticated spoofs (gelatin, silicone) mimic liveness. (2) **False rejects**: Real fingers with dry skin, cold hands fail liveness check. (3) **Cost**: Liveness sensors expensive → not always deployed. (4) **Adversarial adaptation**: Attackers study detection methods → create spoofs that pass. **Formal**: Liveness detection adds second factor. But: each detection method has FAR/FRR. Combined system: FAR_combined = FAR_pattern × FAR_liveness (multiplicative). But: usability decreases.

**Q7: Analyze why iris recognition has the lowest FAR but high FRR. What are the mathematical properties?**
**Answer:** **Iris properties**: (1) High entropy: ~400 unique features (vs. ~30-40 for fingerprint). (2) High uniqueness: Even identical twins have different irises. (3) Stable: Doesn't change after age 2. **Why low FAR**: Feature space is high-dimensional (400+ features). Impostor distribution: very low density in genuine region. P(impostor score > threshold) ≈ 0. **Mathematical**: Iris code: 2048-bit binary vector. Hamming distance: d(x,y) = number of differing bits. For genuine: d ≈ 0.29 (mean). For impostor: d ≈ 0.46 (mean, close to 0.5 random). **Distribution**: Genuine: narrow Gaussian centered at 0.29. Impostor: wide Gaussian centered at 0.46. **Overlap**: Very small → low FAR. **Why high FRR**: (1) Pupil dilation changes iris pattern. (2) Eyelid occlusion. (3) Contact lenses. (4) Surgery (LASIK). **Mathematical**: Genuine distribution has non-negligible spread → some genuine samples score low → false rejects. **Daugman's algorithm**: 2D Gabor wavelets extract phase information → binary iris code. Hamming distance threshold ≈ 0.32. FAR ≈ 1 in 1.2 million. FRR ≈ 0.5-2% depending on conditions.

**Q8: Derive the Bayesian formula for biometric authentication. Given FAR = 0.01, FRR = 0.10, prior P(impostor) = 0.01, compute P(impostor | accept).**
**Answer:** **Bayes' theorem**: P(impostor | accept) = P(accept | impostor) · P(impostor) / P(accept). **Given**: FAR = P(accept | impostor) = 0.01. FRR = P(reject | genuine) = 0.10 → P(accept | genuine) = 0.90. P(impostor) = 0.01 → P(genuine) = 0.99. **Total probability**: P(accept) = P(accept | genuine) · P(genuine) + P(accept | impostor) · P(impostor) = 0.90 × 0.99 + 0.01 × 0.01 = 0.891 + 0.0001 = 0.8911. **Posterior**: P(impostor | accept) = 0.01 × 0.01 / 0.8911 = 0.0001 / 0.8911 ≈ **0.000112 = 0.0112%**. **Interpretation**: Even with FAR = 1%, only 0.011% of accepted users are impostors (because prior P(impostor) is very low). **For identification**: P(impostor | match) increases with database size N. P(match | impostor) ≈ N · FAR. For N = 1000: P(match | impostor) ≈ 10%. **Lesson**: Prior probabilities matter enormously. Low base rate of attacks → low posterior even with moderate FAR.

**Q9: Analyze the privacy implications of biometric systems. Why are biometrics fundamentally different from passwords in terms of privacy?**
**Answer:** **Password privacy**: Stored as hash → even if compromised, doesn't reveal user's physical characteristics. Can be changed. **Biometric privacy**: (1) **Non-revocable**: Once compromised, biometric is permanently compromised. Cannot issue new fingerprint. (2) **Non-secret**: Face captured by CCTV, fingerprint on glass, voice recorded. No consent needed. (3) **Re-identification**: Biometric template can be used across databases → cross-application tracking. (4) **Health information**: Iris patterns can reveal genetic conditions, medications. (5) **Function creep**: Collected for authentication, used for surveillance. **Formal**: Biometric b is public information (can be observed). Password s is private (known only to user). Security model: Biometric system assumes b is secret → fundamentally flawed. **Countermeasures**: (1) **Cancelable biometrics**: T(b, k) → irreversible transform. (2) **Biometric cryptosystems**: Bind secret to biometric. (3) **Template protection**: Store transformed template, not original. **GDPR**: Biometrics are "special category data" → stricter processing rules. **Fundamental difference**: Password = knowledge (can be secret). Biometric = identity (inherently public).

**Q10: Design a multi-modal biometric system combining fingerprint and iris. Analyze the accuracy improvement mathematically.**
**Answer:** **Fusion levels**: (1) Feature-level: concatenate feature vectors. (2) Score-level: combine match scores. (3) Decision-level: combine binary decisions. **Score-level fusion**: s_combined = w₁ · s_fingerprint + w₂ · s_iris. w₁, w₂ = weights (optimize on training data). **Accuracy improvement**: Let FAR_f = 0.01, FRR_f = 0.10 (fingerprint alone). FAR_i = 0.001, FRR_i = 0.05 (iris alone). **Assuming independent errors**: FAR_combined ≈ FAR_f × FAR_i = 0.01 × 0.001 = 10^-5. FRR_combined ≈ FRR_f × FRR_i = 0.10 × 0.05 = 0.005. **Improvement**: FAR reduced from 10^-2 to 10^-5 (1000×). FRR reduced from 0.10 to 0.005 (20×). **Formal**: For independent systems, combined error = product of individual errors. **Correlation**: If errors are correlated (e.g., dry skin affects both), improvement is less. **Naive Bayes fusion**: P(genuine | s_f, s_i) ∝ P(s_f | genuine) · P(s_i | genuine) · P(genuine). **Practical**: NIST tests show multi-modal systems achieve EER < 0.1% vs. 1-5% for single modality. **Trade-off**: Higher cost (two sensors), more complex enrollment, user inconvenience.

---
---

# CHAPTER 6: DIGITAL RIGHTS MANAGEMENT (DRM)

---

## 1. MOTIVATION
- Copyright: Protect rights of content creator
- DRM: Impose limitations on usage of digital content
- Some call it "Digital Restrictions Management"

### DRM Context vs. Classic Crypto
- Classic: Alice & Bob protect messages from third parties
- DRM: Alice sells content to **unreliable** Bob, prevents dissemination
- **Problem**: Content must be clear on Bob's side
- **Solution**: Content only usable on trusted device

---

## 2. DRM FOR SOFTWARE

### Approaches
1. **Dongle**: Hardware device required for software to run
2. **Create uniqueness**: Hide code in bad sectors, require master disk
3. **Use existing uniqueness**: Check PC configuration

### Why Technical Protection Decreased (late 80s)
- Unless expensive tamper-resistant dongle → mechanisms failed
- Protection was a nuisance
- Technical support more important
- Some piracy good for business

### Legal Solutions
- Anti-piracy organizations, prosecution, threatening letters
- Time bombs found illegal (unless user notified)

---

## 3. DRM FOR TV BROADCAST

### Conditional Access Systems
1. Station encrypts video + embeds entitlement messages
2. Set-top box decrypts + decodes entitlements
3. Smartcard controls what can be decrypted

### Key Hierarchy
- **User key**: Shared between station and smartcard
- **Authorization key**: Encrypts control words (in EMM)
- **Control Word** (8-byte): Changes several times per minute, encrypts content (in ECM)

### Attacks
- Control word recording → share on Internet
- Block "kill-command ECMs" → keep watching after cancellation
- User key leakage → fake smartcards

---

## 4. DRM FOR DVDs

### CSS (Content Scrambling System) — 1996
- 40-bit proprietary stream cipher (US export restrictions)
- Reverse engineered 1999 (DeCSS)

### Three Key Types
| Key | Purpose |
|-----|---------|
| Play key (k_p) | Encrypts disk key, shared with players |
| Disk key (k_d) | Encrypts title keys, stored encrypted on disk |
| Title key | Encrypts actual content |

### CSS Vulnerabilities
- 40-bit key → brute forceable (2^40)
- CSS stream cipher weaknesses → complexity reduced to 2^25
- No incentives for manufacturers to use tamper-resistant hardware

### AACS (Advanced Access Content System) — 2005
- AES encryption
- Tree-based media key block (subset difference trees)
- Supports device revocation
- Used on HD-DVD and Blu-ray

### Subset Difference Trees
- Master tree of keys starting from root
- Each device: associated with one leaf, knows set of keys, can compute all except path to root
- Child keys derived via one-way hash
- Revocation: exclude device's leaf key from media key block

---

## 5. DRM FOR AUDIO

### History
- Cassette tax proposed (1960s) → didn't help much
- DRM on audio CDs stopped January 2007: "Cost didn't measure up to result"
- Apple iTunes went DRM-free January 2009

### FairPlay (Apple)
- AES + MD5 encryption of AAC audio
- Master key → encrypted with user key → stored in MP4 container
- Different user key per track
- Max 5 authorized computers
- **Problem**: Vendor lock-in, no interoperability

### Steve Jobs "Thoughts on Music"
- DRM never perfect (hackers always break)
- DRM hurts legal users, not pirates
- Most music sold without DRM (CDs) anyway

---

## 6. WATERMARKS & FINGERPRINTING

### Hidden Watermarks
- Record copyright owner, purchaser, or distribution chain
- Used for ownership proof, tracking leaks

### Hiding Techniques
- Least significant bits (easy to detect/remove)
- Secret key determines mark location (pixel parity)
- Text line shifting (1/300 inch)
- Extra echoes in audio
- Spread spectrum techniques

### Quality Metrics
- **Robustness**: Survives compression, format conversion, manipulation
- **Transparency**: Not noticeable to humans

### Applications
- Currency counterfeit detection (color copier serial numbers)
- Image manipulation proof
- Patient info in X-rays

---

## 7. LEGAL ISSUES

- **WIPO Copyright Treaty (1996)**: Nations adopt anti-circumvention laws
- **DMCA (US)**: Forbids circumvention with intent to violate copyright; exceptions for research/interoperability
- **EU Directive (2001)**: Applies to commercial purposes; French requirement for interoperability

---

## EXAM QUESTIONS — CHAPTER 6

**Q1: Prove that DRM is fundamentally different from classic cryptography. Show why the "untrusted receiver" model breaks standard security assumptions.**
**Answer:** **Classic crypto**: Alice encrypts for Bob. Adversary = eavesdropper (outside). Bob is honest recipient. Security: adversary cannot decrypt. **DRM**: Alice sells content to Bob. Bob is UNTRUSTED recipient. Adversary = Bob himself. Security: Bob cannot redistribute. **Fundamental conflict**: In classic crypto, decryption key = shared secret. In DRM, decryption key must exist on Bob's device → Bob can extract it. **Formal**: Let D_K(c) = decryption. Bob has (c, K, D). Bob can compute D_K(c) himself. To prevent redistribution: Bob's device must be trusted (tamper-resistant). **But**: Any device that can decrypt can also copy the plaintext. **Kerckhoffs' principle**: Security depends on key, not algorithm. DRM requires security through obscurity (device tamper-resistance). **Theoretical impossibility**: Content must be in clear for rendering. Adversary can: (a) Screenshot, (b) Record analog output, (c) Modify device firmware. **Steve Jobs' argument**: DRM never perfect. Most music sold without DRM (CDs). DRM hurts legal users, not pirates. **Formal model**: DRM = game between Alice and Bob where Bob has both c and K. Alice's goal: prevent Bob from creating c' = copy(c). Bob's goal: create c'. **Conclusion**: DRM is provably impossible without hardware trust assumptions.

**Q2: Analyze the CSS (Content Scrambling System) vulnerability. Show how the 40-bit key and stream cipher weaknesses reduced the brute-force complexity from 2^40 to 2^25.**
**Answer:** **CSS design**: 40-bit key (US export restrictions). Stream cipher with two LFSRs. **Key hierarchy**: Play key k_p (per player), Disk key k_d (per disk), Title key (per movie). Disk key encrypted under all 4096 play keys: E_{k_p}(k_d) stored on DVD. **Attack 1 — Key reduction**: CSS stream cipher uses two LFSRs of lengths 17 and 13. Total state space: 2^17 × 2^13 = 2^30 (not 2^40). An attacker only needs to brute-force the LFSR state, not the full key. **Attack 2 — Known plaintext**: DVD content has known structure (headers, patterns). Attacker XORs known plaintext with ciphertext → recovers keystream segment. From keystream: recover LFSR state in O(2^30). **Combined complexity**: 2^30 operations. With optimizations: reduced to **2^25** (as reported). **DeCSS (1999)**: Jon Johansen reverse-engineered CSS. Released DeCSS tool. **Legal fallout**: DMCA lawsuit. Johansen acquitted. **Lesson**: 40-bit key insufficient. Custom crypto (LFSRs) insecure. Export restrictions weakened security.

**Q3: Explain the AACS subset difference tree. How does it achieve device revocation? What is the key derivation algorithm?**
**Answer:** **Tree structure**: Binary tree with root key K. Each device occupies one leaf. Device knows keys on path from leaf to root, EXCEPT its own leaf key. **Key derivation**: Child key = Hash(parent key). One-way: cannot derive parent from child. **Example**: Device D at leaf K_010 knows: K_00 (parent), K_0 (grandparent), K (root). Does NOT know: K_010 (own leaf), K_01 (sibling path). **Media Key Block (MKB)**: Contains encrypted media key under various node keys. Device decrypts: tries all keys it knows → finds media key. **Revocation**: To revoke device D at leaf K_010: Remove all MKB entries encrypted under keys D knows (K_00, K_0, K). New MKB encrypted only under keys D doesn't know. D cannot decrypt → revoked. **Formal**: Let S_D = {keys known to D}. MKB' = {E_K'(media_key) : K' ∉ S_D}. D: ∀K' ∈ S_D: K' ∉ MKB' → cannot decrypt. **Individual revocation**: Remove one leaf. **Group revocation**: Remove set of leaves. **Subset difference**: Encrypt under nodes that partition non-revoked devices. **Complexity**: O(N) MKB entries for N devices. O(log N) keys per device.

**Q4: Analyze the FairPlay DRM system. Why did Apple succeed where others failed?**
**Answer:** **FairPlay architecture**: (1) AAC audio encrypted with AES+MD5. (2) Master key → encrypted with user key → stored in MP4 container. (3) Different user key per track. (4) Max 5 authorized computers. (5) Authorization through Apple servers. **Why succeeded**: (1) **Usability**: iTunes Store — easy purchase, instant download. (2) **Ecosystem**: iPod + iTunes integration. (3) **Perception**: "Fair" — 5 devices, family sharing. (4) **Legal**: Licensed content from major labels. **Why others failed**: (1) **Sony BMG rootkit**: Installed kernel-level rootkit → security disaster. (2) **Interoperability**: Each vendor had own DRM → vendor lock-in. (3) **User rights**: Restricted fair use (backup, format shift). **Steve Jobs' reversal (2007)**: "DRM never perfect. Most music sold without DRM (CDs). DRM hurts legal users." → Apple went DRM-free 2009. **Formal analysis**: DRM cost > benefit for music. Music already available without DRM (CDs). Video: different (no physical media equivalent → DRM persists longer). **Lesson**: Market forces > technical DRM. Usability drives adoption, not security.

**Q5: Compare CSS and AACS. Why is AACS more secure? Analyze the key management and revocation mechanisms.**
**Answer:** **CSS**: 40-bit key, custom stream cipher, no revocation. **AACS**: AES-128, standard algorithms, subset difference tree with revocation. **Key management comparison**: CSS: flat key hierarchy. One disk key → one title key. No revocation → compromised player works forever. AACS: tree-based hierarchy. Multiple key levels. Individual device revocation possible. **Revocation mechanism**: CSS: None. Once compromised (DeCSS), all DVDs accessible. AACS: MKB updated. New discs → new MKB → revoked devices fail. **Complexity**: CSS key: 40 bits → 2^40 brute force (reduced to 2^25). AACS key: 128 bits → 2^128 brute force (infeasible). **Attack resistance**: CSS: Reverse-engineered (DeCSS). AACS: Broken (09/09/09 key), but revocation possible. **Formal**: CSS: Security = obscurity (no formal proof). AACS: Security = AES hardness (well-studied). **Trade-off**: AACS more complex → more implementation bugs possible. CSS simpler → easier to audit. **Conclusion**: AACS is strictly more secure. Revocation capability is the key advantage.

**Q6: Explain why watermarking is fundamentally different from encryption. What are the quality metrics, and how do they conflict?**
**Answer:** **Encryption**: Transform content → ciphertext. Unauthorized access = decrypt. Authorized access = plaintext (no mark). **Watermarking**: Embed mark in content. Mark survives transformations. **Quality metrics**: (1) **Robustness**: Survives compression, format conversion, attacks. (2) **Transparency**: Mark not perceptible to humans. (3) **Capacity**: Amount of information embedded. (4) **Security**: Mark cannot be removed without degrading content. **Conflict**: Robustness vs. Transparency. Strong mark (robust) → more visible (less transparent). Invisible mark (transparent) → easier to remove. **Formal**: Let m = original, w = watermarked, w' = attacked. Robustness: w' still contains mark. Transparency: dist(m, w) < ε (imperceptible). **Attack**: Remove mark → produce w'' with no mark and dist(m, w'') < ε. **Arms race**: Embedder maximizes robustness. Attacker minimizes it. **Applications**: Copyright proof, leak tracking, ownership verification. **Limitation**: Watermarking proves ownership, not prevents copying. **Legal**: Watermark evidence admissible in court (copyright infringement).

**Q7: Analyze the DMCA anti-circumvention law. How does it conflict with security research and fair use?**
**Answer:** **DMCA Section 1201**: Prohibits circumvention of technological measures that control access to copyrighted works. **Exceptions**: (1) Security research. (2) Interoperability. (3) Fair use. (4) Encryption research. **Conflict with security research**: To find vulnerabilities in DRM, must circumvent access control → illegal under DMCA. Example: Researcher finds CSS weakness → must circumvent CSS to demonstrate → DMCA violation. **Conflict with fair use**: DMCA prohibits circumvention even for fair use purposes (backup, accessibility, education). Example: Making accessible copy for blind user → illegal if circumvents DRM. **Legal cases**: (1) **Universal v. Corley**: DeCSS publication blocked. (2) **Chamberlain v. Skylink**: Garage door opener circumvention → not DMCA violation (no copyright link). (3) **Lexmark v. Static**: Printer cartridge chip circumvention → not DMCA (no copyright link). **Formal**: DMCA conflates "access control" with "copy protection." Access control ≠ copyright protection. Circumventing access control ≠ infringing copyright. **Reform**: DMCA exemptions expanded (2015, 2018, 2021) for security research, repair, accessibility.

**Q8: Analyze the conditional access system for TV broadcast. Show the key hierarchy and explain why control words change frequently.**
**Answer:** **Key hierarchy**: (1) **User key** K_u: Shared between station and smartcard. Long-term. (2) **Authorization key** K_a: Encrypts control words. Sent in EMM (Entitlement Management Message). (3) **Control word** CW: Encrypts content. Sent in ECM (Entitlement Control Message). **Why CW changes**: (1) **Anti-piracy**: If CW leaked, only current segment compromised. Next CW: new key. (2) **Segmentation**: Content divided into short segments (few minutes). Each segment encrypted under different CW. **Message flow**: Station → EMM(K_a) → smartcard. Station → ECM(CW) → smartcard. Smartcard: K_a decrypts ECM → gets CW. CW decrypts content. **Attack**: Record CW → share on Internet → anyone can decrypt. **Countermeasure**: CW changes every 5-10 minutes. Leaked CW valid for short window. **Formal security**: If CW interval = T, attacker must distribute CW within T. If distribution time > T → CW expires before use. **Smartcard compromise**: If K_u leaked → fake smartcards possible. **Kill-command ECM**: Send ECM that deactivates card → block stolen cards.

**Q9: Explain the concept of "Self-Protecting Digital Content" for Blu-ray. How does it differ from traditional DRM?**
**Answer:** **Traditional DRM**: Encrypt content → decrypt on authorized device → render. Device trusted. **Blu-ray approach**: Virtual machine (VM) on each player runs content-protection code. **Key idea**: Protection code unique to each title. Code changes per disk. **Mechanism**: (1) BD-J (Blu-ray Disc Java) runs on player. (2) Content includes protection script. (3) Script runs in VM → controls decryption/rendering. (4) Each title: different script. **Advantages**: (1) **No universal key**: Compromising one title doesn't compromise others. (2) **Blacklisting**: Individual player blacklisting possible. (3) **Adaptability**: Protection can evolve per title. **Disadvantages**: (1) **VM complexity**: More code → more bugs. (2) **Performance**: VM overhead. (3) **Compatibility**: Different VM implementations. **Formal**: Traditional DRM: K_shared compromisable → all content exposed. Blu-ray: K_title_i per title → title-specific compromise. **Trade-off**: Complexity vs. security. More moving parts → more attack surface.

**Q10: Compare the three approaches to DRM: CSS, AACS, and Blu-ray self-protection. Analyze the security and practicality of each.**
**Answer:** **CSS (1996)**: 40-bit key, flat hierarchy, no revocation. Security: broken (DeCSS, 1999). Practicality: simple, widely deployed. **AACS (2005)**: AES-128, tree hierarchy, revocation. Security: broken (09/09/09 key), but revocation possible. Practicality: complex, HD-DVD/Blu-ray. **Blu-ray self-protection (2006)**: Per-title VM code, no universal key. Security: not broken universally (title-specific). Practicality: most complex, BD-J required. **Comparison**: Security: CSS < AACS < Blu-ray. Practicality: CSS > AACS > Blu-ray. **Why Blu-ray survived**: (1) No universal break. (2) Title-specific protection limits damage. (3) Player blacklisting possible. **Formal trade-off**: Security ∝ complexity. Complexity ∝ attack surface. Paradox: more complex → more secure but more vulnerable to implementation bugs. **Lesson**: No DRM is permanent. All broken eventually. Market decides based on convenience + content availability.

---
---

# CHAPTER 7: ELECTRONIC VOTING

---

## 1. VOTING FORMS
- Paper (marked in polling station, hand-counted)
- Punch cards
- Optical scanners
- Lever voting machines
- **DRE** (Direct Recording Electronic): electronic display, processes selections, stores in memory

---

## 2. SECURITY REQUIREMENTS
1. **Vote captured correctly?**
2. **Vote counted correctly?**
3. **Tally independently verifiable?**
4. **Vote anonymous?**
5. **Can anyone sell vote?** (should be NO)
6. **Can voters be coerced?** (should be resistant)

---

## 3. THREE-BALLOT (Rivest 2006)

### Basic Idea
- Each voter gets 3 ballots
- Mark each ballot: candidate gets 2 marks on one ballot, 1 mark on others
- All candidates except chosen one get exactly 1 mark per ballot

### Operation
1. Fill all 3 ballots
2. Testing machine checks correctness
3. Voter selects 1 ballot, gets copy to take home
4. All 3 originals go in ballot box
5. All published
6. **Netto-votes** = votes for X - number of voters
7. Each faked vote detected with probability 1/3 (if voter checks)

### Coercion Resistance
- Coercer can demand receipt with pattern → but voter can use other 2 ballots to rectify
- Problem: coercer can demand specific pattern on all 3

### Weaknesses
- Trust in testing machine required
- Confusing for voters (MIT trial)
- Serial numbers forbidden in many countries

---

## 4. COMMITMENT SCHEMES

### Properties
- **Hiding**: No information about m revealed by commitment c
- **Binding**: Cannot open c to different m'

### Pedersen Commitments
- Based on discrete logarithm being hard
- `c = h^m · g^r` (h, g = generators, r = random)
- **Binding**: If c = h^m · g^r = h^m' · g^r', then `logg(h) = (r-r')(m-m')^{-1}` → attacker knows discrete log
- **Hiding**: c is random (r random → g^r random → c random)

### Masking
- `c' = c · g^s` is still commitment on m
- Can prove c, c' commit to same m without opening

---

## 5. BINGO VOTING (Bohli et al. 2007)

### Setup
- N voters, L candidates
- For each candidate: N random numbers, generate commitments C_ki
- Publish all L×N commitments
- Store random numbers as dummy votes in machine

### Voting
1. Voter selects candidate
2. Trusted RNG generates fresh random number → assigned to chosen candidate
3. Other L-1 numbers drawn from dummy votes
4. Machine prints record: pairs of (candidate, random number)
5. Voter checks receipt against RNG display

### Counting
- Published: vote counts, all records, opened commitments on unused dummies
- **For each candidate**: unused dummy votes = vote count
- Must prove each record has L-1 dummies without revealing which is real

### Proofs
- **Before election**: Same number of dummies per candidate (reveal random subset)
- **After election**: Each record has L-1 dummies (Pedersen commitment masking + shuffle + coin flip)

### Why "Bingo"?
- RNG must be trusted by voters → could be a bingo cage
- Machine must be tamper-resistant, booth secured

---

## 6. SCANTENTICITY (Chaum 2008)

### How It Works
- Each ballot: human-readable + machine-readable serial number
- Each candidate randomly assigned a letter on each ballot
- Voter marks candidate, rips off serial, writes down letter
- Ballot fed into scanner

### Verification
- Officials post serial numbers + code letters
- Voter checks: correct letter associated with their serial
- Correct letter → ballot correctly scanned

### Tally Verification
- Circuit switching board shuffles ballots randomly
- Two boards used: prove each ballot belongs to one "Alice" and one "Bob" row
- Random coin flip reveals either link through board 1 or board 2

### Dispute Resolution
- Ballot retrieved by serial (privacy sleeve)
- Dummy ballots with same code letter mixed in
- If mismatch → scan was wrong → vote corrected

### Scantegrity II (2008)
- Invisible ink marking process
- Confirmation codes independent and random for each selection

---

## 7. ATTACKS ON COMMERCIAL SYSTEMS

### Diebold Vulnerabilities
- Install malicious software (buffer overflows, weak access control)
- Viruses propagate between machines
- **Ballot secrecy broken**: Votes recorded in cast order + timestamp → anyone observing order knows votes
- **One password was "diebold"**

### Sequoia Vulnerabilities
- Weak cryptography (hardcoded keys, custom encryption: "secret" → "secretXYZ")
- Access control easily circumvented
- Buffer overflows, format string vulnerabilities
- Same crypto keys in all hardware shipped to different jurisdictions

---

## EXAM QUESTIONS — CHAPTER 7

**Q1: Prove the binding property of Pedersen commitments. Show that if an adversary can open a commitment to two different values, they can compute discrete logarithms.**
**Answer:** **Setup**: G = cyclic group of prime order q. g, h = generators. Commitment: c = h^m · g^r. **Binding**: Cannot find (m, r) and (m', r') such that c = h^m · g^r = h^{m'} · g^{r'} with m ≠ m'. **Proof (by contradiction)**: Assume adversary finds c = h^m · g^r = h^{m'} · g^{r'}, m ≠ m'. Then: h^m · g^r = h^{m'} · g^{r'} → h^{m-m'} = g^{r'-r} → (h^{m-m'})^{(m-m')^{-1}} = g^{(r'-r)(m-m')^{-1}} → h = g^{(r'-r)(m-m')^{-1}}. Therefore: log_g(h) = (r'-r)(m-m')^{-1} mod q. **Adversary now knows log_g(h)**. This contradicts the setup assumption that discrete log is hard. **Formal**: If DLP is hard → binding holds. Binding security = DLP hardness. **Quantitative**: Breaking binding requires computing discrete log. Best algorithms: GNFS for general groups → sub-exponential. For elliptic curve groups: O(√q) → exponential.

**Q2: Prove the hiding property of Pedersen commitments. Show that commitment reveals zero information about m.**
**Answer:** **Hiding**: For any two messages m₁, m₂, the distributions {c | c = h^{m₁} · g^r} and {c | c = h^{m₂} · g^r} are identical (uniform over G). **Proof**: Fix m₁. For any c ∈ G, how many r produce c = h^{m₁} · g^r? Exactly one: r = log_g(c · h^{-m₁}). Since r is uniform in {2, ..., q-1}, c is uniform in G. Same for m₂: c = h^{m₂} · g^{r'} → c is uniform. **Formal**: Pr[c | m] = 1/q for all c ∈ G, independent of m. **Information-theoretic**: Even unlimited computation cannot determine m from c. **Why**: g^r is uniform (random in G). h^m is fixed. c = h^m · g^r is uniform (product of fixed and uniform is uniform). **Perfect hiding**: Unconditional. No computational assumptions needed. **Trade-off**: Pedersen is perfectly hiding but computationally binding. Commitment: c = h^m · g^r. The hiding property holds for ANY group, ANY generators, ANY distribution of r. **Comparison**: Hash commitment: H(m || r). Computationally binding (preimage resistance). Computationally hiding (second preimage resistance). Pedersen: perfectly hiding, computationally binding.

**Q3: Analyze the masking property of Pedersen commitments. Prove that c' = c · g^s commits to the same value as c.**
**Answer:** **Masking**: c = h^m · g^r. c' = c · g^s = h^m · g^r · g^s = h^m · g^{r+s}. **Claim**: c' is a valid commitment on m (with randomness r+s). **Proof**: (1) c' = h^m · g^{r+s}. This is Pedersen commitment with message m and randomness r'. (2) r' = r+s is uniform if r is uniform (s is public, r uniform → r+s uniform). (3) Therefore c' has same hiding property as c. **Zero-knowledge proof**: To prove c and c' commit to same m without revealing m: publish s. Verifier: compute c' / c = g^s. Check if g^s is consistent with group. **Voting application**: (1) Real vote: c = h^m · g^r. (2) Masked vote: c' = c · g^s = h^m · g^{r+s}. (3) Both commit to same m. Publishing s proves equivalence without revealing m. **Formal**: c and c' are in same equivalence class: c ~ c' iff c'/c ∈ ⟨g⟩. This holds iff c' = c · g^s for some s. **Security**: Adversary sees c and c' → learns m? No (hiding property). Adversary learns that c and c' are equivalent → learns nothing about m.

**Q4: Analyze the Three-Ballot voting protocol. Prove that each faked vote is detected with probability 1/3.**
**Answer:** **Protocol**: Each voter gets 3 ballots. Chosen candidate gets 2 marks on one ballot, 1 mark on others. Non-chosen candidates get exactly 1 mark per ballot. **Netto-votes**: Netto(X) = votes(X) - number of voters. For honest voting: Netto(X) = 0 (each voter adds exactly 1 net vote to chosen candidate). **Detection**: Faked vote = voter marks candidate incorrectly. Voter takes home 1 ballot as receipt. **Probability analysis**: Voter takes home ballot uniformly at random (1 of 3). Faked vote: chosen candidate gets 2 marks on one ballot. If voter takes home ballot with 2 marks: Netto reveals inconsistency (2 vs 1). Probability: 1/3. If voter takes home ballot with 1 mark: appears normal (1 on each). Probability: 2/3. **Formal**: Let B₁, B₂, B₃ be the three ballots. Chosen candidate C gets marks: B₁: 2, B₂: 1, B₃: 1 (or permutation). Voter takes home B_i uniformly. If B_i is the "2-mark" ballot: receipt shows 2 → auditor can compare with server record → detects faked vote. P(detect) = 1/3. **With randomization**: If server uses random ballot ordering → voter cannot predict which ballot has 2 marks → P(detect) = 1/3 regardless of voter's strategy. **Weakness**: Voter can mark all 3 ballots identically → P(detect) = 0.

**Q5: Analyze the Bingo voting protocol. Prove that the voter's choice remains hidden among L-1 dummy votes.**
**Answer:** **Setup**: N voters, L candidates. For each candidate: N random numbers with commitments. **Voting**: Voter selects candidate. Trusted RNG generates fresh random number r*. Assigned to chosen candidate. L-1 dummy numbers drawn from pre-generated pool. **Ballot**: Record with L pairs: (candidate_j, random_number_j) for j = 1,...,L. **Hiding**: Voter's choice is the candidate with fresh random number r*. Others have dummy numbers. **Security**: Adversary sees ballot → L pairs. Which is the real vote? **Probability**: Without knowledge of r*, all L candidates equally likely. **Formal**: For any candidate j, P(vote = j | ballot) = 1/L. The real vote is hidden uniformly among L candidates. **Coercion resistance**: Coercer demands specific receipt pattern. But: real vote hidden among dummies → coercer cannot verify. Voter can claim any pattern. **Counting**: Unused dummy votes per candidate = vote count. Must prove each ballot has L-1 dummies without revealing which. **Pedersen masking**: Each ballot proves knowledge of dummies without opening commitments. **Security**: Statistical privacy from dummy votes + cryptographic privacy from commitments.

**Q6: Compare Three-Ballot, Bingo voting, and Scantegrity. Analyze the trade-offs between usability, security, and verifiability.**
**Answer:** **Three-Ballot**: No cryptography. Paper-based. Netto-votes for verification. **Security**: Probabilistic detection (1/3). **Usability**: Confusing (MIT trial). **Verifiability**: Individual (receipt), tally (netto). **Bingo**: Cryptographic. Trusted RNG. Commitments. **Security**: Perfect hiding (Pedersen). **Usability**: Requires trust in RNG. **Verifiability**: Full (individual + tally proofs). **Scantegrity**: Invisible ink. Optical scan compatible. **Security**: Code letters per ballot. **Usibility**: Familiar (optical scan). **Verifiability**: Individual (letter check), tally (switching boards). **Comparison matrix**: | Protocol | Crypto? | Usability | Individual Verif. | Tally Verif. | Coercion Resist. | **Three-Ballot**: No | Low | Probabilistic | Probabilistic | Low. **Bingo**: Yes | Medium | Full | Full | Medium. **Scantegrity**: Minimal | High | Full | Full | Low. **Trade-off**: No system achieves all three: usability, security, verifiability. **Key insight**: Three-Ballot shows cryptography not always needed. Bingo shows crypto enables stronger guarantees. Scantegrity shows practical deployment possible.

**Q7: Analyze the Diebold voting machine vulnerabilities. What specific attacks break ballot secrecy?**
**Answer:** **Vulnerabilities found (Hopkins 2007)**: (1) **Buffer overflows**: Remote code execution via crafted SmartCard. (2) **Weak access control**: Default password "diebold". (3) **Malicious software**: Can be installed via SmartCard → propagate between machines. (4) **Ballot secrecy broken**: Votes stored in cast order with timestamp. **Ballot secrecy attack**: (1) Attacker observes voting order (election official). (2) Records timestamp of each vote. (3) Votes stored in order: vote_1, vote_2, ..., vote_n with timestamps t_1, t_2, ..., t_n. (4) Observer knows: voter_1 cast vote_1 at t_1, voter_2 cast vote_2 at t_2, etc. (5) **Result**: Complete breach of ballot secrecy. **Formal**: Ballot secrecy requires: ∀ voter i: Pr[ vote_i = v | transcript ] = Pr[ vote_i = v ]. Diebold: transcript includes (timestamp, vote) pairs → voter identity linked to vote via timing. **Other attacks**: (1) **Vote flipping**: Modify software → change votes during transmission. (2) **Audit log manipulation**: Delete or alter logs. (3) **Key compromise**: Same key in all machines. **Lesson**: Hardware + software + procedure must all be secure. Single point of failure → system failure.

**Q8: Analyze the Scantegrity verification mechanism. How do the circuit switching boards prove tally correctness?**
**Answer:** **Scantegrity ballot**: Each candidate gets random letter per ballot. Voter marks candidate, records letter, rips off serial number. **Verification**: Officials post serial + letter (without candidate association). Voter checks correct letter. **Tally verification (switching boards)**: (1) Two boards (Board 1, Board 2) used. (2) Each board shuffles ballots randomly. (3) For each intermediate position: randomly reveal link through Board 1 OR Board 2. (4) Multiple instances → statistical certainty. **Formal**: Board 1 proves: each ballot appears in exactly one row. Board 2 proves: each row contains exactly one ballot. Together: each ballot counted exactly once. **Coin flip**: Random bit determines which board to check. After n flips: probability all checks pass honestly = (1/2)^n → negligible. **Dispute resolution**: Ballot retrieved by serial (privacy sleeve). Dummy ballots mixed in. If letter mismatch → scan was wrong → vote corrected. **Security**: Information-theoretic: switching boards provide perfect shuffle proof. **Limitation**: Requires physical boards + manual verification.

**Q9: Analyze the Sequoia voting machine vulnerabilities. Why was custom encryption a catastrophic failure?**
**Answer:** **Sequoia vulnerabilities (2007)**: (1) **Custom encryption**: "secret" encrypts to "secretXYZ". (2) **Hardcoded keys**: Same key in all machines. (3) **Weak access control**: Easily bypassed. (4) **Buffer overflows, format string bugs.** **Custom encryption failure**: (1) **No peer review**: Algorithm not publicly scrutinized. (2) **Kerckhoffs' principle violated**: Security depends on secrecy of algorithm, not key. (3) **Weak algorithm**: Simple substitution → easily broken. **Formal**: Let E_k(m) = custom encryption. If E is not standard: no security proof. Adversary can analyze algorithm → recover key. **Standard algorithms** (AES, RSA): Security proven under well-studied assumptions. **Hardcoded keys**: Same key in all machines → one compromise → all compromised. **Formal**: Security requires key secrecy. Hardcoded key = key public → security = 0. **Lessons**: (1) Never invent custom crypto. (2) Use standard algorithms. (3) Unique keys per device. (4) Public peer review. **Voting-specific**: Election software must be auditable. Closed-source + custom crypto = opaque system → trust without verification.

**Q10: Design a secure electronic voting protocol. What are the minimum requirements, and how do you achieve voter-verifiable audit trail?**
**Answer:** **Minimum requirements**: (1) Correctness: votes counted correctly. (2) Privacy: vote anonymous. (3) Verifiability: voter can check their vote counted. (4) Coercion resistance: voter can lie to coercer. **Protocol design**: (1) **Registration**: Voter gets credential (blind signature on identity). (2) **Voting**: Voter encrypts vote under election public key. Sends encrypted vote + credential. (3) **Receipt**: Voter gets receipt (hash of encrypted vote). (4) **Tallying**: Homomorphic tallying: multiply encrypted votes → encrypted tally. **Voter-verifiable audit trail (VVAT)**: (1) **Individual verification**: Voter checks receipt against bulletin board. (2) **Universal verification**: Anyone checks all receipts against tally. (3) **Paper trail**: DRE prints paper record → voter verifies → deposited in ballot box. **Homomorphic tallying**: Enc(v₁) · Enc(v₂) · ... · Enc(v_n) = Enc(v₁ + v₂ + ... + v_n). No decryption needed during tally. Final tally decrypted once. **Coercion resistance**: Voter can revote (last vote counts). Voter can claim receipt is fake. **Formal security**: IND-CPA encryption + zero-knowledge proofs + mix-nets or homomorphic tallying. **Trade-off**: Complexity vs. security vs. usability. No perfect system.

---
---

# QUICK REVISION: TOP 30 MUST-KNOW FORMULAS & CONCEPTS

1. **ECB**: `c_i = E_K(m_i)` — deterministic → leaks patterns → NOT IND-CPA
2. **CBC**: `c_i = E_K(m_i ⊕ c_{i-1})` — randomized (via IV) → semantically secure
3. **Key equivalence**: 128-bit symmetric = 3072-bit RSA = 256-bit ECC
4. **RSA hardness**: factoring (GNFS): O(exp((64/9)^(1/3) · (ln N)^(2/3) · (ln ln N)^(1/3)))
5. **Crowds E(X)**: `p_f/(1-p_f) + 2` — expected path length
6. **Pedersen commitment**: `c = h^m · g^r` — binding (DLP), hiding (uniform)
7. **Pedersen binding proof**: `log_g(h) = (r'-r)(m-m')^{-1} mod q` → adversary computes discrete log
8. **Pedersen masking**: `c' = c · g^s` — commits to same m, proves equivalence without opening
9. **Shamir**: polynomial degree k-1, Lagrange interpolation, perfect secrecy, ideal scheme
10. **XOR secret sharing**: `s = r_1 ⊕ ... ⊕ r_n` — (n,n)-threshold only
11. **DC-NET**: XOR of all announcements = message bit — information-theoretic sender anonymity
12. **Blind RSA**: `h·r^e` signed → unblind `h^d·r·r^{-1} = h^d` — unlinkable
13. **Bitcoin mining**: SHA-256(block header) with leading zeros — PoW
14. **Bitcoin supply**: Σ 210000 × 50/2^k = 21M (geometric series)
15. **Merkle root**: O(log n) verification — SPV clients
16. **FAR/FRR trade-off**: `FAR(t) = ∫_t^∞ f_i(s)ds`, `FRR(t) = ∫_{-∞}^t f_g(s)ds`
17. **No perfect threshold**: genuine & impostor distributions overlap → ∀t: FAR(t) > 0 AND FRR(t) > 0
18. **Doddington's zoo**: Sheep (easy), Goat (hard to match), Lamb (easy to impersonate), Wolf (manipulator)
19. **PGP trust**: legitimacy = Σ (signer_weight × cert_weight) ≥ 1
20. **SET dual signature**: `Sign(H(H(OI) || H(PI)))` — separation of concerns
21. **CSS**: 40-bit key, three key types (play, disk, title) — broken (DeCSS)
22. **CSS brute force**: 2^40 → 2^25 (LFSR state space reduction)
23. **AACS**: subset difference tree, device revocation via MKB update
24. **Three-ballot**: netto-votes = votes - voters, P(detect faked) = 1/3
25. **Bingo voting**: L-1 dummies hide real vote, Pedersen masking proves correctness
26. **Website fingerprinting**: packet sizes + ML classification (k-NN, CNN)
27. **Salting**: `hash(salt || password)` — prevents rainbow tables, each user independent
28. **Hybrid encryption**: asymmetric for key exchange, symmetric for data
29. **Birthday paradox**: `P(collision) ≈ 1 - e^(-q²/(2^(n+1)))` — for n-bit hash, need ~2^(n/2) evaluations
30. **Bayes' theorem**: `P(A|B) = P(B|A)·P(A)/P(B)` — base rate matters enormously
