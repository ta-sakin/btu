# Information Retrieval — Complete Master's Exam Preparation Guide

**Course:** Information Retrieval (Prof. Dr.-Ing. Ingo Schmitt, BTU Cottbus–Senftenberg)  
**Based on:** Lecture slides IR-1 … IR-8, exercise sheets EX01–EX04, and Henrich-aligned formulas  
**Purpose:** Self-contained one-day exam prep — this document is your only study material  
**Math notation:** `$...$` inline, `$$...$$` display (GitHub / Glow / VS Code)

---

## How to Use This Guide (1 Day)

| Block | Time | What to do |
|------|------|------------|
| Morning | 3–4 h | Chapters 1–5 (fundamentals → Boolean/signatures → evaluation → NLP → VSM). Do every worked example. |
| Afternoon | 3–4 h | Chapters 6–9 (LM, probabilistic/BM25, clustering, modern IR). Memorize formula sheet. |
| Evening | 3–4 h | Extended practice bank (§23) + one timed sprint (§24) + Mock Exam 1 or 2 under timed conditions. |
| Night | 30–60 min | Final 2-hour / 30-minute revision checklists only. |

**Priority legend**

- 🔥 **Very High Priority** — almost certainly tested; practice until automatic  
- ⭐ **High Priority** — frequently tested conceptually or with calculations  
- ○ **Medium Priority** — know definitions, comparisons, and one example  

**Memorize vs Understand** appears at the end of each major topic.

---

# Table of Contents

1. [What IR Is — Foundations](#1-what-ir-is--foundations-)  
2. [Boolean Retrieval & Inverted Indexes](#2-boolean-retrieval--inverted-indexes-)  
3. [Signatures, Zipf, Storage](#3-signatures-zipf--storage-)  
4. [Extended Boolean, Coordination Level, Fuzzy Sets](#4-extended-boolean-coordination-level--fuzzy-sets-)  
5. [Evaluation of IR Systems](#5-evaluation-of-ir-systems-)  
6. [Language Processing for IR](#6-language-processing-for-ir-)  
7. [Vector Space Model](#7-vector-space-model-)  
8. [Language Models for IR](#8-language-models-for-ir-)  
9. [Probabilistic Retrieval (BIR & BM25)](#9-probabilistic-retrieval-bir--bm25-)  
10. [Alternatives to Global Search](#10-alternatives-to-global-search-)  
11. [Deep Learning, Embeddings & RAG](#11-deep-learning-embeddings--rag-)  
12. [PageRank & Quality Signals](#12-pagerank--quality-signals-)  
13. [High-Yield Revision Notes](#13-high-yield-revision-notes)  
14. [Important Definitions](#14-important-definitions)  
15. [Formula Sheet](#15-formula-sheet)  
16. [Algorithms and Procedures I Must Know](#16-algorithms-and-procedures-i-must-know)  
17. [Important Comparisons](#17-important-comparisons)  
18. [Common Exam Traps](#18-common-exam-traps)  
19. [50+ Mixed Practice Questions with Solutions](#19-50-mixed-practice-questions-with-complete-solutions)  
20. [Full Mixed Mock Exam](#20-full-mixed-mock-exam)  
21. [Final 2-Hour Revision](#21-final-2-hour-revision)  
22. [Final 30-Minute Revision](#22-final-30-minute-revision)  
23. [Extended Practice Bank (Q61–Q140)](#23-extended-practice-bank-q61q140)  
24. [Timed Sprint Sets (40 min each)](#24-timed-sprint-sets-40-min-each)  
25. [Mock Exam 2 (120 min / 100 marks)](#25-mock-exam-2-120-min--100-marks)


---

# 1. What IR Is — Foundations 🔥

## 1.1 Intuition

A **search engine** does not answer database-style exact questions like "salary of employee 42." It helps a **human with a vague information need** find **documents** that are *about* something. Documents are unstructured (or semi-structured) text, web pages, images, etc. Relevance is subjective and graded; the system must **rank** candidates, not only accept/reject them.

Think of Google vs SQL: SQL returns exact tuples matching a schema predicate; Google returns a ranked list of pages that might satisfy "best espresso machine under 200 euros."

## 1.2 Core Definitions

**Information Retrieval (IR)**  
The field that studies systems whose role is to support **knowledge transfer** from producers of information to people who need it — mainly by searching document collections against an information need.

**Information need**  
What the user actually wants to know (often incompletely verbalized).

**Query**  
The formal expression of the need given to the system (keywords, Boolean expression, natural language, …).

**Document**  
Unit of retrieval (page, article, PDF, image, …).

**Relevance**  
Whether a document helps satisfy the information need. Classical evaluation assumes binary relevance for a fixed query; reality is graded and user-dependent.

### Data, Knowledge, Information (Kuhlen — exam favorite)

| Concept | Meaning in IR context |
|--------|------------------------|
| **Data** | Raw symbols / signals without interpretation (bits, characters, sensor readings). |
| **Knowledge** | Structured, organized content that a human (or knowledge base) "has" — what is known. |
| **Information** | Knowledge **in action for a purpose** — the subset/aspect of knowledge that reduces uncertainty for a specific information need. |

**Relationship:** Data can be interpreted into knowledge; when knowledge is selected and used to answer a need, it becomes information. IR systems mediate this transition: they retrieve documents that *contain* knowledge so the user can extract information.

**Memorize:** one crisp sentence for each of data / knowledge / information and their relationship.  
**Understand:** why IR is about *information for a need*, not about storing facts.

## 1.3 Tasks of IR Systems ⭐

1. **Ad-hoc retrieval / query processing** — classic search for a topic.  
2. **Classification / cataloguing** — assign documents to classes (library, patents).  
3. **Browsing / exploratory search** — navigate structures instead of typing keywords.  
4. **Filtering** — standing query over a stream (alerts, spam).  
5. **Question answering, recommendation, …** — related applications.

## 1.4 IR vs Fact Retrieval (Databases) 🔥

| Aspect | Fact retrieval (DB) | Information retrieval |
|--------|---------------------|------------------------|
| User | Often application / expert | End user |
| Query | Precise, schema-based | Vague, free text |
| Matching | Exact | Partial / ranked |
| Result | Complete set of matching facts | Ranked list; incomplete by design |
| Relevance | Well-defined by query semantics | Subjective, graded |
| Evaluation | Correctness + efficiency | **Effectiveness** (quality) + efficiency |

**Exam trap:** "IR systems don't need correctness" is wrong — they need a different notion of quality (precision/recall), and they still need efficient indexes.

## 1.5 Anatomy of a Retrieval Model 🔥

Every IR model specifies four things:

1. **Document representation** (bag of words, vector, language model, binary vector, …)  
2. **Query representation**  
3. **Matching / ranking function** $\mathrm{sim}(Q,D)$  
4. **Implementation** (inverted lists, signatures, …)

**Basic search process**

1. Preprocess collection (tokenize, stopwords, stem, index).  
2. Preprocess query the same way.  
3. Retrieve candidates (index lookup).  
4. Score and rank.  
5. Present results; optionally take relevance feedback and re-rank.

## 1.6 The Three Classical Model Families (preview) 🔥

| Model | Core idea | Result type |
|-------|-----------|-------------|
| **Boolean** | Documents as sets of terms; query as Boolean expression | Unranked set |
| **Vector space** | Documents/queries as weighted vectors; angle/similarity | Continuous ranking |
| **Probabilistic** | Rank by $P(\text{relevant}\mid D,Q)$ or odds | Continuous ranking |

You will study each deeply below. For now, memorize: Boolean = set logic (no ranking); VSM = geometry/heuristics; Probabilistic = odds of relevance (theory + BM25 practice).

### Memorize vs Understand

- **Memorize:** IR definition; data/knowledge/information; IR vs DB table; four aspects of a model.  
- **Understand:** why ranking and vagueness are central.

---

# 2. Boolean Retrieval & Inverted Indexes 🔥

## 2.1 Intuition

Boolean search treats each document as a **set of terms**. A query like `motorcycle AND quality` means: return documents that contain both terms. There is **no score** — a document matches or it doesn't. This is exact, predictable in logic, and terrible for end users (empty results or huge result dumps).

## 2.2 Document & Query Representation

- Document $D$: set of terms (after optional stopword removal / stemming).  
- Variants: multiset (term frequency), or pairs (term, position) for `NEAR`.  
- Query: Boolean expression with `AND`, `OR`, `NOT` / `AND NOT` (`BUT`), optionally `NEAR[k]`, `IN TITLE`.

Examples:

- `eagle bear` often interpreted as `eagle AND bear`  
- `eagle AND (bear OR lion)`  
- `eagle AND NOT lion`

## 2.3 Inverted Lists (Inverted Index) 🔥

**Intuition:** Searching starts from **words**, not from documents. So store, for each term, the list of documents containing it.

**Forward index:** document → list of terms  
**Inverted index:** term → list of document IDs (postings list)

```
quality    → [2, 5, 9, 17, ...]
motorcycle → [5, 9, 12, ...]
```

Postings are kept **sorted by document ID**. That is the key to efficient Boolean operations.

### AND query (intersection)

`motorcycle AND quality`:

1. Load both sorted postings lists.  
2. Walk them in parallel with two pointers.  
3. Emit IDs present in **both**.

**Why sorting helps:** merge/intersection is $O(|L_1| + |L_2|)$, not $O(|L_1|\cdot|L_2|)$.

### OR query (union)

Emit IDs in **either** list (merge, skip duplicates).

### AND NOT

Keep IDs in $L_1$ that are not in $L_2$ (also a linear merge).

### Unary NOT

Usually disastrous (almost the whole collection). Prefer binary `q1 AND NOT q2`.

### NEAR[k]

Requires **positions** in postings. Scan lists in parallel and test whether occurrence positions differ by at most $k$.

## 2.4 Memory Estimate (exam calculation) ⭐

Exercise-style estimate:

- $N$ documents, average $V$ distinct terms per document, $B$ bytes per doc ID.  
- Postings storage ≈ $N \cdot V \cdot B$ (ignoring term dictionary overhead, frequencies, positions).

**Example (lecture):** 210,158 articles × 150 distinct words × 4 bytes ≈ 120 MB for IDs alone; collection was 564 MB → index easily ~20% of collection size → typically on disk.

**Example (EX03):** 500,000 docs, 100 distinct words/doc, 8-byte IDs:

$$
500{,}000 \times 100 \times 8 = 4 \times 10^8 \text{ bytes} \approx 381\ \text{MiB}
$$

(plus dictionary). Collection 1.5 GB → index is a large fraction.

## 2.5 Disadvantages of Classical Boolean 🔥

1. No stemming / linguistic flexibility by default.  
2. No term weighting (title vs body, frequency).  
3. No compound handling.  
4. Hard to formulate for end users.  
5. Unpredictable result **size**.  
6. **No ranking**.

### Memorize vs Understand

- **Memorize:** inverted list definition; AND/OR as intersect/union; sorting → linear merge.  
- **Understand:** why Boolean fails for web search UX; when Boolean is still useful (legal, patents, expert search).

---

# 3. Signatures, Zipf & Storage ⭐

## 3.1 Zipf's Law 🔥

**Intuition:** In natural language, a few words are extremely common; most words are rare. Rank words by frequency: if $r(w)$ is rank and $h(w)$ is frequency,

$$
r(w) \cdot h(w) \approx c \quad \text{(constant)}
$$

English folklore from lectures: top 2 words ≈ 10% of tokens; top 6 ≈ 20%; top 50 ≈ 50%.

**Consequence for inverted indexes**

- Few **very long** postings lists (even after stopword removal).  
- Many **very short** lists.  
- Need a dictionary structure (B+-tree, trie) mapping terms → list addresses.  
- Store several short lists per disk page; long lists span pages.

## 3.2 Signature Files — Intuition 🔥

Signatures are a **fast inexact filter**: hash each word to a bitstring; combine bits for a block; use bitwise tests to eliminate most documents cheaply; then do exact string matching on survivors.

Architecture:

1. Hash query word(s) → query signature.  
2. Signature match → candidate document IDs (**may include false alarms**).  
3. Exact pattern match on candidates → final result.

## 3.3 Superimposed Coding 🔥

- Word signature length $F$ bits; weight $m$ bits set (signature weight).  
- Number of distinct word signatures: $\binom{F}{m}$.  
- **Block signature:** OR together the signatures of the $D$ words in a block.  
- Query match (necessary condition): for every bit set in the query signature, the block signature must also have that bit set  
  (equivalently: `(block_sig AND query_sig) == query_sig`).

**False drops / false alarms:** block signature matches but the word is **not** in the block. Causes:

1. Hash collisions (different words → same signature).  
2. Superposition (OR of several words "accidentally" covers the query bits).

**Exam wording:** "false drop" = necessary condition satisfied ∧ pattern not present.

## 3.4 False-Drop Probability ⭐

For one-word query, under uniformity assumptions:

$$
F_d = \left(1 - \left(1 - \frac{m}{F}\right)^{D}\right)^{m}
$$

Approximation for large $D$:

$$
F_d \approx \left(1 - e^{-mD/F}\right)^{m}
$$

Optimal weight:

$$
m_{\mathrm{opt}} = \frac{F}{D}\ln 2
$$

Then roughly half the bits in a block signature are ones, and

$$
F_d = \left(\tfrac{1}{2}\right)^{F\ln 2 / D}
$$

**Monotonicity:** larger $F$ ↓ $F_d$; larger $D$ ↑ $F_d$; $m$ has a sweet spot.

**Storage ratio example:** if signatures cost $\alpha$ times document text and average word length $c_w$ characters:

$$
\frac{F}{D} = \alpha \cdot c_w \cdot 8
$$

E.g. $\alpha=0.1$, $c_w=10$ ⇒ $F/D=8$ ⇒ $F_d\approx 2.14\%$.

## 3.5 Signature Storage Structures ⭐

| Structure | Idea | Search | Update | When preferred |
|-----------|------|--------|--------|----------------|
| **SSF** (sequential) | Store row-by-row $N\times F$ bit matrix | Linear in $N$ | Easy | Inserts dominate |
| **BSSF** (bit-sliced) | Each bit position = separate file; read only $m$ slices | Much less I/O for search | Expensive ($F$ accesses) | Search-heavy, rare updates |
| **S-tree** | B-tree-like; inner node signature = OR of children | Sublinear; multi-path | Split like B-tree | Balanced search + update |

### S-tree search algorithm

1. Start at root.  
2. Descend into **every** child whose signature AND-matches the query signature.  
3. Multiple paths possible.  
4. At leaves, get document/block pointers; verify exactly.

**Insert:** navigate to leaf needing **minimal expansion** of signatures; on overflow, split: pick two maximally different seed signatures, then alternately assign remaining signatures to the more similar seed; propagate OR upward.

**S-tree trap:** near-root nodes become dense with 1-bits → pruning weakens.

### Conjunctive queries on signatures

OR-ing query word signatures finds blocks that may contain **all** words **in the same block**. If words sit in different blocks of one document, that document may be missed — alternative: candidate sets per word, then intersect.

### Memorize vs Understand

- **Memorize:** Zipf $r\cdot h\approx c$; superimposed coding; $m_{\mathrm{opt}}=\frac{F}{D}\ln 2$; false drop definition; SSF vs BSSF vs S-tree table.  
- **Understand:** signatures as filters, not exact indexes; why bit-slicing helps search.

---

# 4. Extended Boolean, Coordination Level & Fuzzy Sets 🔥

## 4.1 Coordination Level Match ⭐

**Intuition:** Soften Boolean AND. Score = number of desired query terms present minus undesired terms.

Query: desired terms + optional NOT terms.  
Score contribution: $+1$ per desired term in $D$, $-1$ per undesired term.  
Rank by score; drop score $\le 0$.

**Example:** query `House, Garden, NOT France`; doc "Garden in France" → $+1-1=0$ (discard).

**vs Boolean:** partial matches appear; still crude (no weights, all terms equal).  
**Complexity:** with inverted lists, parallel scan over postings touched.

## 4.2 Extended Boolean / Waller–Kraft ⭐

Parameterized soft AND/OR:

$$
(1-\gamma)\min(w_{t_1},\ldots,w_{t_n}) + \gamma\max(w_{t_1},\ldots,w_{t_n})
$$

- Conjunction-like: $0\le\gamma\le 0.5$  
- Disjunction-like: $0.5\le\gamma\le 1$

## 4.3 $p$-Norm Model (Salton) 🔥

Weights $x_i\in[0,1]$ = similarity of document to term $t_i$. Parameter $1\le p\le\infty$.

$$
\mathrm{sim}(q_{\mathrm{or}},d_j)=\left(\frac{\sum_{i=1}^{n} x_i^{p}}{n}\right)^{1/p}
$$

$$
\mathrm{sim}(q_{\mathrm{and}},d_j)=1-\left(\frac{\sum_{i=1}^{n}(1-x_i)^{p}}{n}\right)^{1/p}
$$

**Special cases (memorize!):**

| $p$ | OR | AND |
|-----|----|-----|
| $p=1$ | average of $x_i$ | same average |
| $p=\infty$ | $\max x_i$ | $\min x_i$ |

**Role of $p$:**  
- Small $p$ → soft aggregation (AND and OR behave similarly toward averages).  
- Large $p$ → approaches classical Boolean min/max sharpness.  
Choose $p$ to trade strictness vs partial matching.

**Advantage over Boolean:** ranking + partial match + tunable softness.

## 4.4 Fuzzy Set Model 🔥

**Intuition:** Membership of document $D_j$ in the "set of documents about term $t_i$" is $\mu_i(D_j)\in[0,1]$, not just $\{0,1\}$. Boolean connectives become Zadeh operations:

$$
\mu_{\neg S}(u)=1-\mu_S(u),\quad
\mu_{A\cup B}=\max(\mu_A,\mu_B),\quad
\mu_{A\cap B}=\min(\mu_A,\mu_B)
$$

**Example query:** `House AND (Italy OR France) AND NOT Garden`

$$
\min\bigl(\min(\mu_1(D_j),\max(\mu_3(D_j),\mu_4(D_j))),\,1-\mu_2(D_j)\bigr)
$$

### Term–term correlation (Ogawa et al.) 🔥

$$
c_{i,l}=\frac{n_{i,l}}{n_i+n_l-n_{i,l}}
$$

($n_i$ = docs with $t_i$; $n_{i,l}$ = docs with both; $c_{i,i}=1$.)

**Example:** house in 7, roof in 6, both in 5 → $c=5/(7+6-5)=5/8$.

### Term–document membership

$$
\mu_i(D_j)=1-\prod_{t_l\in D_j}(1-c_{i,l})
$$

(Equivalent to fuzzy OR of correlations of $t_i$ with terms occurring in $D_j$.)

### Dominance trap of min/max 🔥

Query `House AND Italy`:

| Term | D1 | D2 |
|------|----|----|
| House | 0.3 | 0.9 |
| Italy | 0.3 | 0.2 |
| min | **0.3** | **0.2** |

System ranks D1 > D2 even though D2 is strongly about "House". **min is dominated by the weakest term.**

### Pros / cons

- **+** Models language vagueness via correlations; produces ranking.  
- **−** min/max dominance; complex queries; long inverted lists; expensive term–term matrix on dynamic collections.

### Memorize vs Understand

- **Memorize:** $p$-norm formulas + $p=1,\infty$ cases; fuzzy ops; $c_{i,l}$ and $\mu_i(D_j)$; coordination scoring rule.  
- **Understand:** why softening Boolean helps users; why min/max is a problem.


---

# 5. Evaluation of IR Systems 🔥

## 5.1 Efficiency vs Effectiveness ⭐

| | Meaning | Question |
|--|---------|----------|
| **Efficiency** | Use few resources (CPU, RAM, disk, latency) | "Are we doing things right?" |
| **Effectiveness** | Quality of results relative to the information need | "Are we doing the right things?" |

DB evaluation often emphasizes efficiency under correct results. IR evaluation emphasizes **effectiveness** because "correct" is graded/subjective.

## 5.2 Binary Relevance Contingency Table 🔥

For query $q$:

|  | Relevant | Not relevant |
|--|----------|--------------|
| **In result** | $a$ (hits) | $b$ (noise) |
| **Not in result** | $c$ (misses) | $d$ (rejected) |

$$
\mathrm{Recall}=\frac{a}{a+c}=\frac{|R_q\cap\mathrm{Res}|}{|R_q|}
$$

$$
\mathrm{Precision}=\frac{a}{a+b}=\frac{|R_q\cap\mathrm{Res}|}{|\mathrm{Res}|}
$$

- **Recall:** how complete?  
- **Precision:** how accurate / pure?

**Problems of binary relevance (exam):** depends on user prior knowledge; documents can be conditionally relevant (B only after A); graded relevance is more realistic.

## 5.3 F-Measure 🔥

Harmonic mean of precision and recall (weighted):

$$
F=\frac{\mathrm{Precision}\cdot\mathrm{Recall}}{(1-\alpha)\mathrm{Recall}+\alpha\mathrm{Precision}}
$$

Often $\alpha=0.5$ → balanced $F_1$:

$$
F_1=\frac{2PR}{P+R}
$$

**Why harmonic?** Arithmetic mean lets one extreme dominate; harmonic mean stays low if either $P$ or $R$ is low.

## 5.4 Estimating Recall (hard!) ○

Relevant docs are rare → full labeling expensive. Methods:

1. **Large sample** — still costly.  
2. **Document source method** — pick a random doc, invent a query for which it is relevant, see if retrieved (queries unnatural).  
3. **Query expansion / pooling-like supersets** — recall estimate **biased high**.  
4. **External sources / experts**.  
5. **Pooling (TREC):** merge top-$k$ from many systems; judge the pool; treat unjudged outside pool as non-relevant (approximate).

## 5.5 Macro vs Micro Averaging 🔥

Over $m$ queries:

**Macro (user-oriented):** average per-query metrics equally

$$
\mathrm{Recall}_{\varphi,u}=\frac{1}{m}\sum_{i=1}^{m}\frac{a_i}{a_i+c_i},\quad
\mathrm{Precision}_{\varphi,u}=\frac{1}{m}\sum_{i=1}^{m}\frac{a_i}{a_i+b_i}
$$

Problem: empty results ($a_i+b_i=0$).

**Micro (system-oriented):** pool counts as one big experiment

$$
\mathrm{Recall}_{\varphi,s}=\frac{\sum a_i}{\sum(a_i+c_i)},\quad
\mathrm{Precision}_{\varphi,s}=\frac{\sum a_i}{\sum(a_i+b_i)}
$$

Large result sets dominate.

**Lecture numerical sketch:** macro recall ≈ 0.35, precision ≈ 0.34; micro recall 125/167≈0.75, precision 125/226≈0.55 — one fat query dominates micro.

## 5.6 Ranked Retrieval: Precision at Recall Points & AP / MAP 🔥

For a ranked list, compute precision **every time a new relevant document appears**.

If $|R_q|=10$ and the 1st relevant is at rank 1: $P@R=0.1$ means precision when recall first hits 0.1.

**Average Precision (AP)** for one query:

$$
\mathrm{AP}(q)=\frac{1}{|R_q|}\sum_{k=1}^{|R_q|} P@\text{(rank of $k$-th relevant doc)}
$$

Equivalently: average of precision values at each relevant hit; **unretrieved relevant documents contribute 0**.

**Mean Average Precision (MAP):**

$$
\mathrm{MAP}=\frac{1}{|Q|}\sum_{q\in Q}\mathrm{AP}(q)
$$

MAP is **system-oriented** and not a direct UX story; users often care about **P@5 / P@10** (first page).

### Worked example (from EX02 style)

System 1 ranking (`+` relevant, `−` not), $|R|=10$:

`+ − + − − − + + + − − − − + +`

Relevant at ranks: 1,3,7,8,9,14,15 (7 of 10 found in top 15).

| Recall | Rank | Precision |
|--------|------|-----------|
| 0.1 | 1 | $1/1=1.00$ |
| 0.2 | 3 | $2/3\approx0.667$ |
| 0.3 | 7 | $3/7\approx0.429$ |
| 0.4 | 8 | $4/8=0.500$ |
| 0.5 | 9 | $5/9\approx0.556$ |
| 0.6 | 14 | $6/14\approx0.429$ |
| 0.7 | 15 | $7/15\approx0.467$ |

$$
\mathrm{AP}=\frac{1}{10}(1+0.667+0.429+0.5+0.556+0.429+0.467+0+0+0)\approx 0.405
$$

**If $|R|$ were 15 instead of 10:** same $P$ at each *found* relevant, but recall levels become $k/15$ (P@0.1 means after finding $0.1\cdot 15$ relevants — exam trap!).

System 2: `− − − + − − − + − + − + + + −`

AP ≈ 0.195 (worse early precision).

### Tiny AP drill (memorize method)

Ranking of 5 docs, 2 relevant: `− + − + −`

- 1st relevant at rank 2: $P=1/2$  
- 2nd at rank 4: $P=2/4$  
- $\mathrm{AP}=\frac{1}{2}(0.5+0.5)=0.5$

## 5.7 DCG / IDCG / nDCG 🔥

Graded relevance $\mathrm{rel}_i\in\{0,1,2,3,\ldots\}$. Front ranks matter more → logarithmic discount:

$$
\mathrm{DCG}_p=\mathrm{rel}_1+\sum_{i=2}^{p}\frac{\mathrm{rel}_i}{\log_2 i}
$$

($\log_2 1=0$ would break the sum — hence $\mathrm{rel}_1$ separate.)

**Ideal DCG:** sort relevance grades descending, recompute DCG → $\mathrm{IDCG}_p$.

$$
\mathrm{nDCG}_p=\frac{\mathrm{DCG}_p}{\mathrm{IDCG}_p}
$$

Average nDCG over queries.

### Worked example (EX02)

Relevance by rank: $2,1,0,4,3,0$ for $p=6$.

$$
\begin{align*}
\mathrm{DCG}_6&=2+\frac{1}{\log_2 2}+\frac{0}{\log_2 3}+\frac{4}{\log_2 4}+\frac{3}{\log_2 5}+\frac{0}{\log_2 6}\\
&=2+1+0+2+\frac{3}{\log_2 5}+0\approx 6.292
\end{align*}
$$

Ideal order: $4,3,2,1,0,0$

$$
\mathrm{IDCG}_6=4+\frac{3}{1}+\frac{2}{\log_2 3}+\frac{1}{2}+0+0\approx 8.762
$$

$$
\mathrm{nDCG}_6\approx\frac{6.292}{8.762}\approx 0.718
$$

## 5.8 Query Types & Evaluation Initiatives ○

- **Navigational:** find a specific page (homepage of X) — early precision critical.  
- **Informational:** learn about a topic — recall and diversity matter.  
- **TREC:** NIST evaluation; topics + pools + judgments; many tracks (web, QA, filtering, …).  
- Observation: **variance across topics ≫ variance across systems**.  
- **GMAP:** geometric mean of AP — rewards **robustness** across hard queries, not only high average.

**Cranfield criteria (6):** recall, precision, time lag, effort, form of presentation, coverage.

### Memorize vs Understand

- **Memorize:** $P$, $R$, $F$, AP, MAP, DCG, nDCG formulas; macro vs micro.  
- **Understand:** why recall is hard; why MAP ≠ user happiness; pooling bias.

---

# 6. Language Processing for IR 🔥

## 6.1 Why Language Is Hard ○

Synonymy, polysemy/homonymy, inflection, compounding, spelling variation, multilinguality, anaphora, negation, … IR systems usually use **shallow** NLP that improves matching without full understanding.

## 6.2 Stop Words ⭐

**Stop word list:** frequent function words (`the`, `and`, `of`, …) removed from index/query.

**Effects (classic exam answer):**

- Index smaller; matching focuses on content words.  
- Often **precision ↑** (less noise) and sometimes **recall ↑** in vector models (less dilution).  
- **Danger:** queries like "to be or not to be", song titles, names — stopwords can destroy meaning. Domain stopwords ("computer" in a CS collection) may be useful.

**Alternatives:** keep stopwords but downweight via IDF; language-model smoothing; phrase indexes; don't remove for exact phrase search.

**Implementation:** static list lookup during tokenization; or dynamic by collection frequency threshold.

## 6.3 Inflection, Stemming, Lemmatization 🔥

**Inflection:** grammatical word-form variation (run/runs/ran; Haus/Häuser). Blocks exact string match → **hurts recall** if untreated.

**Base-form reduction (lemmatization):** map to a real dictionary base form (`lief → laufen`). Needs morphology/dictionary; better linguistic quality; costly to maintain for technical vocab.

**Stemming:** strip affixes to a stem that need **not** be a word (`connection → connect`). Cheaper; language-specific rules (Porter for English) or dictionaries for rich morphology (German).

**Effects on P/R:** stemming/lemmatization usually **↑ recall** (more matches) and can **↓ precision** (over-conflation).

### Overstemming vs Understemming 🔥

| Error | Meaning | Effect |
|-------|---------|--------|
| **Overstemming** | Different concepts mapped to same stem (`universal`/`university` → `univers`) | Precision ↓ |
| **Understemming** | Same concept kept as different stems | Recall ↓ |

### Methods (Kuhlen / lectures)

1. **Affix removal / rules** (Porter): good for weakly inflected languages (English).  
2. **Dictionary lookup:** needed for strong inflection.  
3. **Stem tables / n-gram methods** as alternatives.

**Porter algorithm (idea):** ordered rule lists removing suffixes under measure constraints (stem length); multi-step. Know *what it does*, not every rule.

## 6.4 Compound Words ⭐

**German:** compounds written as one word (`Bundeskanzlerwahl`). Options:

- Ignore → search for `Wahl` misses inside compound → recall ↓.  
- Decompose → recall ↑ but query for full compound harder / noisier.

**English:** open compounds (`information retrieval`) — treating as independent words can hurt **precision**; phrase/`NEAR` helps.

**Precombination / precoordination / postcoordination** (terminology control):

- Precombination: compound already in indexing language.  
- Precoordination: indexer links terms when indexing.  
- Postcoordination: user links at query time (`Europe AND single market`).

## 6.5 Terminological Control & Thesauri ○

Library tradition: controlled vocabulary with **preferred terms** to reduce synonymy/homonymy. Manual indexing: (1) understand essence, (2) express in indexing language.

## 6.6 $n$-Grams ○

Index character $n$-grams (or word $n$-grams) instead of/in addition to words.

- **+** Language-independent; robust to spelling; fuzzy match.  
- **−** Larger index; hard to explain results; may hurt precision.

## 6.7 RDF (metadata) ○

**RDF:** Resource Description Framework — triples **(subject, predicate, object)** for metadata graphs. Why three? Binary relations between resources, named by predicates; graph of statements. URIs identify nodes/edges. **RDFS** adds classes/properties (type system). Used to attach structured descriptions for retrieval/integration — not a ranking model by itself.

### Memorize vs Understand

- **Memorize:** stopword effects; stemming vs lemma; over/understemming; Zipf already covered; RDF triple.  
- **Understand:** P/R tradeoffs of each NLP choice; compounds differ by language.

---

# 7. Vector Space Model 🔥

## 7.1 Intuition

Represent each document and the query as a vector in $\mathbb{R}^{t}$ ($t$ = vocabulary size). Each axis is a term; coordinate = how important that term is. Documents pointing in a similar **direction** to the query are relevant (**cluster hypothesis**). Ranking uses a similarity (dot product or cosine).

**Assumptions:** term independence (false but useful); non-negative weights.

## 7.2 Notation

- $N$ = #documents  
- $n_k$ = #documents containing term $k$  
- $tf_{dk}$ = frequency of $k$ in $D$  
- $\mathbf{V}_D=(w_{d1},\ldots,w_{dt})$, $\mathbf{V}_Q=(w_{q1},\ldots,w_{qt})$

## 7.3 Why Raw TF Fails 🔥

Docs: D1 "Houses in Italy" → $(1,1,0,0)$; D2 "Houses in Italy and around Italy" → $(1,2,0,0)$; Q same as D1.

Dot products: D2 scores **higher only because it is longer / repeats**. Long documents are unfairly favored.

## 7.4 Length-Normalized TF 🔥

$$
w_{dk}=\frac{tf_{dk}}{\sqrt{\sum_{i} tf_{di}^{2}}}
$$

Now short focused docs can beat long diffuse ones for the right query.

## 7.5 IDF and TF–IDF 🔥

Rare terms discriminate better than common terms. Raw factor $N/n_k$ over-amplifies ultra-rare terms → use log:

$$
\mathrm{idf}_k=\log\frac{N}{n_k}
$$

**Document TF–IDF with cosine-style normalization (slide form):**

$$
w_{dk}=\frac{tf_{dk}\cdot\log\frac{N}{n_k}}{\sqrt{\sum_{i=1}^{t}\left(tf_{di}\cdot\log\frac{N}{n_i}\right)^{2}}}
$$

This is a **heuristic**, not a probability theorem — but extremely effective.

## 7.6 Query Weighting (Salton & Buckley) 🔥

Do **not** use the same formula for queries. User-chosen terms get a base weight:

$$
w_{qk}=\begin{cases}
\left(0.5+0.5\dfrac{tf_{qk}}{\max_i tf_{qi}}\right)\log\dfrac{N}{n_k} & tf_{qk}>0\\
0 & \text{otherwise}
\end{cases}
$$

Query vectors are typically **not** length-normalized (common factor wouldn't change ranking).

**Trap:** document formula ≠ query formula.

## 7.7 Cosine Similarity 🔥

$$
\mathrm{sim}_{\cos}(\mathbf{V}_Q,\mathbf{V}_D)=\frac{\sum_k w_{qk}w_{dk}}{\|\mathbf{V}_Q\|\,\|\mathbf{V}_D\|}
$$

If document vectors are already unit-normalized and query norm is constant across $D$, **ranking by cosine = ranking by dot product**.

## 7.8 Slope / Pivoted Length Normalization ⭐

Full cosine normalization **over-penalizes long docs** and **over-rewards very short docs**. Compensate with:

$$
k_{fd}=(1-\mathrm{slope})+\mathrm{slope}\cdot\frac{\mathrm{old\_norm}_d}{\mathrm{avg\_old\_norm}}
$$

Use $k_{fd}$ when normalizing. TREC: optimal slope ≈ **0.75**. Same idea reappears as BM25's $b$.

After slope, weights need not stay $\le 1$.

## 7.9 Relevance Feedback 🔥

User labels retrieved docs as relevant $F^+$ / non-relevant $F^-$. Move the query vector.

**Ide (dec hi)** — often best empirically:

$$
\mathbf{V}_Q^{\mathrm{new}}=\mathbf{V}_Q^{\mathrm{old}}+\sum_{D\in F^+}D - D_{\mathrm{top}}^{-}
$$

(subtract only the highest-ranked non-relevant)

**Ide (regular):**

$$
\mathbf{V}_Q^{\mathrm{new}}=\mathbf{V}_Q^{\mathrm{old}}+\sum_{D\in F^+}D-\sum_{D\in F^-}D
$$

**Rocchio** ($\alpha+\beta=1$, typically $\alpha=0.25$, $\beta=0.75$ — relevant weighted more):

$$
\mathbf{V}_Q^{\mathrm{new}}=\mathbf{V}_Q^{\mathrm{old}}+\beta\cdot\frac{1}{|F^+|}\sum_{D\in F^+}D-\alpha\cdot\frac{1}{|F^-|}\sum_{D\in F^-}D
$$

**Why Ide dec hi wins:** $F^-$ is heterogeneous; subtracting *all* scatters the query; subtracting the top false positive gives a clear direction away from the worst mistake.

**Pseudo relevance feedback:** treat top-$n$ as $F^+$ automatically → helps recall if early precision is already good; harmful if early ranking is bad.

**Impact:** RF gains (tens of percent) dwarf small TF–IDF tweaks (~10%).

## 7.10 Implementation Sketch ○

Process inverted lists in decreasing order of query term weights; accumulate scores; early exit when docs below rank $\gamma$ cannot catch up (**MaxRemainingWeight**), assuming $w_{dk}\le 1$.

### VSM summary

| Advantages | Disadvantages |
|------------|---------------|
| Simple, strong baseline | Independence assumption |
| Efficient with inverted lists | Heuristic theory |
| Natural RF (Rocchio/Ide) | Structured docs awkward |

### Memorize vs Understand

- **Memorize:** TF–IDF, query weight formula, cosine, Rocchio/Ide, slope idea.  
- **Understand:** long-doc bias; why log IDF; why RF moves the query.


---

# 8. Language Models for IR 🔥

## 8.1 Intuition

Imagine each document was written by sampling words from a little "author model" $M_d$. Given a query $q$, ask: **how likely is $M_d$ to generate $q$?** Rank documents by $P(q\mid M_d)$.

This is the **query-likelihood** approach. By Bayes, if document prior $P(d)$ is uniform,

$$
P(d\mid q)\propto P(q\mid d)\,P(d)\quad\Rightarrow\quad\text{rank by }P(q\mid d).
$$

Non-uniform priors can encode PageRank, freshness, popularity, etc.

## 8.2 Unigram LM

Full chain rule needs context probabilities. **Unigram** assumes independence:

$$
P(t_1\ldots t_n\mid M_d)=\prod_{i=1}^{n}P(t_i\mid M_d),\quad\sum_{t\in V}P(t\mid M_d)=1.
$$

Same independence fiction as VSM — still works.

## 8.3 MLE and the Zero Problem 🔥

$$
\hat P(t\mid M_d)=\frac{tf_{t,d}}{|d|}
$$

If any query term is missing → whole product is **0**. Long queries make this worse. Seen terms are also overestimated.

**Fix: smoothing** — steal probability mass from seen terms and give some to unseen terms via a background (collection) model $M_c$.

## 8.4 Linear / Jelinek–Mercer Smoothing 🔥

$$
\hat P(t\mid M_d)=\omega\cdot\frac{tf_{t,d}}{|d|}+(1-\omega)\cdot\frac{cf_t}{|c|}
$$

- High $\omega$: more conjunctive (need query terms in the doc).  
- Low $\omega$: more disjunctive; better for long queries.  
- Same $\omega$ for all document lengths.

## 8.5 Dirichlet Smoothing 🔥

Make mixing depend on length. With prior mass $\varepsilon$ (often called $\mu$ in textbooks):

$$
\omega=\frac{\varepsilon}{\varepsilon+|d|}
$$

$$
\hat P(t\mid M_d)=\frac{|d|}{\varepsilon+|d|}\cdot\frac{tf_{t,d}}{|d|}+\frac{\varepsilon}{\varepsilon+|d|}\cdot\frac{cf_t}{|c|}
$$

**Intuition:** long documents → trust MLE more; short documents → trust collection more.

Query likelihood:

$$
P(q\mid d)=\prod_{t\in q}\hat P(t\mid M_d)
$$

**Always compute in log space** to avoid underflow:

$$
\log P(q\mid d)=\sum_{t\in q}\log\hat P(t\mid M_d)
$$

## 8.6 Tiny Numerical Example

Query: "frog said that toad likes frog"

| Term | $M_1$ | $M_2$ |
|------|-------|-------|
| frog | 0.01 | 0.0002 |
| toad | 0.01 | 0.0001 |
| said | 0.03 | 0.03 |
| that | 0.04 | 0.04 |
| likes | 0.02 | 0.04 |

$P(q\mid M_1)$ multiplies frog twice etc. → $M_1$ wins by orders of magnitude because frog/toad are more probable under $M_1$.

## 8.7 Naive Bayes Classification (same family) ⭐

Supervised cousin: classify doc into class $c$ by

$$
c_{\mathrm{map}}=\arg\max_c \hat P(c)\prod_{k=1}^{|d|}\hat P(t_k\mid c)
$$

Add-one (Laplace) smoothing:

$$
\hat P(t\mid c)=\frac{T_{ct}+1}{|text_c|+|V|}
$$

Training $O(|D|L_{\mathrm{ave}}+|C||V|)$; testing $O(|C|M_a)$ — linear, strong baseline.

### LM pros/cons

| Pros | Cons |
|------|------|
| Principled generative story | No built-in RF |
| TF/IDF-like effects emerge | Terms are still symbols |
| Efficient | More complex models → more params |

### Memorize vs Understand

- **Memorize:** query likelihood; MLE; JM & Dirichlet formulas; log trick.  
- **Understand:** zero problem; high vs low $\omega$; why Dirichlet is length-adaptive.

---

# 9. Probabilistic Retrieval (BIR & BM25) 🔥

## 9.1 Intuition & Ranking by Odds

Rank documents by probability of relevance, or equivalently by **chance (odds)**:

$$
\mathrm{chance}(D)=\frac{P(D\in R^+(Q))}{P(D\in R^-(Q))}
$$

Odds preserve ranking order vs probability. This is the spirit of the **Probability Ranking Principle** (rank by decreasing $P(\mathrm{rel}\mid d,q)$).

## 9.2 Binary Independence Retrieval (BIR) 🔥

Robertson / Sparck Jones (1976).

**Assumptions:**

1. Binary weights $w_{dk}\in\{0,1\}$.  
2. Term independence given relevance class.  
3. Ideal relevant set exists (estimated via feedback).

After Bayes + independence + dropping query-only factors, score reduces to a sum over terms present in **both** query and document:

$$
\mathrm{sim}(D,Q)\approx\sum_{\{i:w_{qi}=w_{di}=1\}}\left(
\log\frac{p_i}{1-p_i}+\log\frac{1-q_i}{q_i}\right)
$$

where $p_i=P(w_{d'i}=1\mid R^+)$, $q_i=P(w_{d'i}=1\mid R^-)$.

### Initial estimate (no feedback)

$$
p_i=0.5,\qquad q_i=\frac{n_i}{N}
$$

$$
\mathrm{sim}(D,Q)\approx\sum_{\{i:w_{qi}=w_{di}=1\}}\log\frac{N-n_i}{n_i}
$$

≈ sum of log-IDF over matching terms — **TF–IDF cousin with tf=1**.

### Worked example

$N=500$, $Q$ has terms 1,4,5 with $n_1=87,n_4=23,n_5=100$. Document matches terms 1 and 5 only:

$$
\mathrm{sim}=\log\frac{413}{87}+\log\frac{400}{100}\approx 1.56+1.39=2.95
$$

(using natural log; any base preserves ranking).

### Relevance feedback updates

With judged/pseudo set $V$ of size $r$:

$$
p_i=\frac{|\{D'\in V:w_{d'i}=1\}|}{|V|},\quad
q_i=\frac{n_i-|\{D'\in V:w_{d'i}=1\}|}{N-|V|}
$$

Smoothing for small $V$ (add 0.5):

$$
p_i=\frac{r_i+0.5}{|V|+1},\quad
q_i=\frac{n_i-r_i+0.5}{N-|V|+1}
$$

**Criticism:** binary weights; rough initial ranking; independence; improvements not transferable across queries.

## 9.3 BM25 / Okapi 🔥

State-of-the-art classical baseline. Combines RSJ probabilistic IDF with **saturating TF** and **pivoted length normalization** (the slope idea).

$$
\mathrm{sim}(D,Q)=\sum_{i=1}^{t}\mathrm{IDF}(n_i)\cdot
\frac{(k_1+1)\,tf_{di}}{k_1\bigl((1-b)+b\frac{dl}{avdl}\bigr)+tf_{di}}\cdot
\frac{(k_3+1)\,tf_{qi}}{k_3+tf_{qi}}
$$

$$
\mathrm{IDF}(n_i)=\log\frac{N-n_i+0.5}{n_i+0.5}
$$

| Parameter | Typical | Role |
|-----------|---------|------|
| $k_1$ | 1.2–2.0 | TF saturation speed |
| $b$ | ≈0.75 | Length normalization strength |
| $k_3$ | 0–1000 | Query TF normalization |
| $dl,avdl$ | — | Doc length / average |

**Negative IDF trap:** if $n_i>N/2$, IDF $<0$ → usually clip to 0 (stopword-like terms).

**Connection to VSM slope:** factor $(1-b)+b\frac{dl}{avdl}$ is exactly pivoted length normalization.

### BM25 vs VSM vs BIR

| | VSM | BIR | BM25 |
|--|-----|-----|------|
| Weights | continuous TF–IDF | binary | saturating TF |
| Theory | heuristic | probabilistic | probabilistic + engineering |
| Length | cosine / slope | none | $b$ |
| Practice | strong | weak alone | **default strong baseline** |

### Memorize vs Understand

- **Memorize:** BIR initial sum $\sum\log\frac{N-n_i}{n_i}$; full BM25; IDF with +0.5; $k_1,b$.  
- **Understand:** odds ranking; why RF needed for BIR; TF saturation & length pivot.

---

# 10. Alternatives to Global Search ⭐

## 10.1 Classification (manual) ⭐

Organize collections with human schemes: Dewey/UDC, ACM CCS, **IPC** (patents), web catalogs.

- **Monoclassification:** tree (one parent).  
- **Polyclassification:** DAG (multiple parents).  
- Catalogs allow multiple entries (unlike a single shelf location).

**UDC faceting symbols (know meanings):** `(430)` place; `:` relation; `+` enumeration; `/` range; `=` language; `"..."` time.

**Problems:** cost, aging (IPC ~5 years), interdisciplinary topics, revision mismatches.

## 10.2 Clustering 🔥

Automatic groups: high intra-similarity, low inter-similarity.

**Similarities (length-safe):**

- Cosine (as in VSM)  
- **Dice:**
$$
\mathrm{sim}(D_i,D_j)=\frac{2\sum_k w_{ik}w_{jk}}{\sum_k w_{ik}^2+\sum_k w_{jk}^2}
$$
- **Jaccard:**
$$
\mathrm{sim}(D_i,D_j)=\frac{\sum_k w_{ik}w_{jk}}{\sum_k w_{ik}^2+\sum_k w_{jk}^2-\sum_k w_{ik}w_{jk}}
$$

### Non-hierarchical

- **Clique / Star:** threshold graphs; elements may belong to multiple clusters; expensive.  
- **Reallocation (k-means-like):** assign to nearest centroid; recompute; iterate. Threshold/k choice hard.

### Hierarchical agglomerative 🔥

1. Start with $N$ singletons.  
2. Merge most similar pair.  
3. Update similarities; repeat $N-1$ times → **dendrogram**.  
**Irreversible** decisions.

| Linkage | Inter-cluster sim | Behavior |
|---------|-------------------|----------|
| **Single** | max pairwise | **Chaining** — large sprawling clusters |
| **Complete** | min pairwise | Compact, small clusters |
| **Average** | mean pairwise | Compromise |
| **Centroid** | sim of centroids | |
| **Ward** | minimize SSE increase | Homogeneous; costly |

**Automatic thesaurus:** term–term similarities + star clustering → synonym candidates.

**Clustering results vs collection:** often cluster the *result set* to structure Boolean dumps; labels are implicit (show centroid doc) unlike classification.

## 10.3 Browsing & Visualization ○

Navigational access needs structure: classifications, hypertext, cluster trees, maps.

**Shneiderman's mantra:** *"Overview first, zoom and filter, then details on demand."*

### Memorize vs Understand

- **Memorize:** Dice/Jaccard; single vs complete link; classification ≠ clustering.  
- **Understand:** when to browse vs search; chaining problem.

---

# 11. Deep Learning, Embeddings & RAG ○⭐

## 11.1 From One-Hot to Embeddings

One-hot vectors: no notion of similarity. Embeddings (Word2Vec, GloVe, …): dense vectors where similar words are nearby; geometric analogies sometimes work (`king-man+woman≈queen`). Dimensions not human-interpretable.

## 11.2 Neural Sequence Models (exam-level)

- Feedforward window models (POS).  
- **RNN/LSTM:** sequential state; LSTM gates fight vanishing gradients.  
- **Attention / Transformers:** query/key/value; scaled dot-product
$$
r_{ij}=\frac{q_i\cdot k_j}{\sqrt{d}},\quad a_{ij}=\mathrm{softmax}_j(r_{ij}),\quad c_i=\sum_j a_{ij}v_j
$$
- Decoding: greedy vs **beam search**.

## 11.3 LLMs & RAG ⭐

LLMs hallucinate and lack private/fresh knowledge. **Retrieval-Augmented Generation:**

1. Retrieve relevant chunks with IR (BM25 and/or dense embeddings).  
2. Concatenate evidence with the user query.  
3. Let the LLM generate an answer **grounded** in retrieved text.

Sparse vs dense retrieval both appear in RAG. Chunk size matters. Augmentation can be at input / intermediate / output layers.

**Exam point:** RAG improves grounding; it does **not** magically eliminate all hallucinations if retrieval fails.

---

# 12. PageRank & Quality Signals ⭐

Content relevance ≠ page quality. Link analysis estimates authority.

Lecture form (iterative, $\varepsilon\in[0.1,0.2]$):

$$
R(p)=\varepsilon+(1-\varepsilon)\sum_{(q,p)}\frac{R(q)}{\mathrm{outlinks}(q)}
$$

Classic form with damping $d\approx 0.85$:

$$
PR(A)=(1-d)+d\sum_{i}\frac{PR(T_i)}{C(T_i)}
$$

**Problems:** no topical weighting of links; age bias; link spam; dangling nodes.

Combine quality with content score by addition, multiplication, or result mixing.

Other quality cues: freshness, availability, popularity, authority, cohesion.

### CBIR (awareness ○)

Images as vectors of color/texture/shape; or CNN object tags — same VSM idea, different features.


---

# 13. High-Yield Revision Notes

1. IR ≠ databases: vague need, ranked results, effectiveness metrics.  
2. Every model = representation + matching + implementation.  
3. Inverted lists + sorted merge → AND/OR in linear time.  
4. Zipf → few long lists, many short; signatures filter with false drops.  
5. Soft Boolean: coordination, $p$-norm ($p=1$ avg, $p=\infty$ min/max), fuzzy min/max.  
6. Fuzzy membership from term correlations $c_{i,l}=n_{i,l}/(n_i+n_l-n_{i,l})$.  
7. $P$ = purity of result; $R$ = completeness; $F$ = harmonic; AP averages $P$ at each relevant; MAP averages AP.  
8. nDCG for graded relevance with log discount.  
9. Stemming ↑R, risk ↓P; overstem vs understem.  
10. VSM: TF–IDF + cosine; query uses $0.5+0.5\,tf/\max$; RF moves query (Ide dec hi best).  
11. LM: rank $P(q\mid d)$; smooth or die; Dirichlet length-adaptive.  
12. BIR: $\sum\log\frac{N-n_i}{n_i}$ initially; BM25 = industrial probabilistic retrieval.  
13. Clustering: single-link chains; complete-link compacts.  
14. PageRank: recursive authority via in-links.  
15. RAG: retrieve then generate — grounding, not magic.

**If you only drill calculations:** AP/MAP, nDCG, TF–IDF/cosine, BIR init score, BM25 one term, fuzzy $c$ and $\mu$, $p$-norm special cases, inverted-list memory, signature $m_{\mathrm{opt}}$.

---

# 14. Important Definitions

| Term | Definition |
|------|------------|
| Information need | User's underlying desire for knowledge |
| Relevance | Utility of a doc w.r.t. a need/query |
| Inverted list | Term → sorted postings of doc IDs |
| False drop | Signature match without actual term occurrence |
| Stop word | High-frequency low-content word often removed |
| Stemming | Heuristic reduction to stem (may be non-word) |
| Lemmatization | Reduction to dictionary base form |
| Overstemming | Distinct concepts conflated |
| Understemming | Same concept not conflated |
| TF | Term frequency in a document |
| IDF | Inverse document frequency $\log N/n_k$ |
| Cluster hypothesis | Relevant docs cluster in representation space |
| Query likelihood | Rank by $P(q\mid d)$ |
| Smoothing | Reallocate probability to unseen terms |
| PRP | Rank by decreasing $P(\mathrm{rel}\mid d,q)$ |
| Pooling | Judge union of top results from many systems |
| Dendrogram | Tree from hierarchical clustering |
| RDF triple | (subject, predicate, object) metadata statement |
| RAG | LLM generation conditioned on retrieved evidence |

---

# 15. Formula Sheet

**Contingency**

$$
P=\frac{a}{a+b},\quad R=\frac{a}{a+c},\quad F=\frac{PR}{(1-\alpha)R+\alpha P},\quad F_1=\frac{2PR}{P+R}
$$

**AP / MAP**

$$
\mathrm{AP}=\frac{1}{|R|}\sum_{\text{rel ranks }r}P@r,\quad\mathrm{MAP}=\frac{1}{|Q|}\sum_q\mathrm{AP}(q)
$$

**DCG / nDCG**

$$
\mathrm{DCG}_p=\mathrm{rel}_1+\sum_{i=2}^{p}\frac{\mathrm{rel}_i}{\log_2 i},\quad
\mathrm{nDCG}_p=\frac{\mathrm{DCG}_p}{\mathrm{IDCG}_p}
$$

**Zipf**

$$
r(w)\cdot h(w)\approx c
$$

**Signatures**

$$
F_d=\bigl(1-(1-m/F)^D\bigr)^m,\quad m_{\mathrm{opt}}=\frac{F}{D}\ln 2
$$

**$p$-norm**

$$
\mathrm{sim}_{\vee}=\Bigl(\frac{\sum x_i^p}{n}\Bigr)^{1/p},\quad
\mathrm{sim}_{\wedge}=1-\Bigl(\frac{\sum(1-x_i)^p}{n}\Bigr)^{1/p}
$$

**Fuzzy**

$$
c_{i,l}=\frac{n_{i,l}}{n_i+n_l-n_{i,l}},\quad
\mu_i(D_j)=1-\prod_{t_l\in D_j}(1-c_{i,l})
$$

$$
\mu_{\neg}=1-\mu,\ \mu_{\vee}=\max,\ \mu_{\wedge}=\min
$$

**TF–IDF (docs)**

$$
w_{dk}=\frac{tf_{dk}\log(N/n_k)}{\sqrt{\sum_i(tf_{di}\log(N/n_i))^2}}
$$

**Query weights**

$$
w_{qk}=\bigl(0.5+0.5\tfrac{tf_{qk}}{\max tf_{qi}}\bigr)\log\frac{N}{n_k}
$$

**Cosine**

$$
\cos=\frac{\sum w_{qk}w_{dk}}{\|\mathbf{V}_Q\|\|\mathbf{V}_D\|}
$$

**Rocchio**

$$
Q' = Q+\beta\mathrm{avg}(F^+)-\alpha\mathrm{avg}(F^-),\quad\alpha+\beta=1
$$

**LM**

$$
\hat P_{\mathrm{JM}}=\omega\frac{tf}{|d|}+(1-\omega)\frac{cf}{|c|}
$$

$$
\hat P_{\mathrm{Dir}}=\frac{tf+\varepsilon\,cf/|c|}{|d|+\varepsilon}
$$

(equivalent form of Dirichlet)

**BIR init**

$$
\mathrm{sim}=\sum_{i\in Q\cap D}\log\frac{N-n_i}{n_i}
$$

**BM25**

$$
\sum_i\log\frac{N-n_i+0.5}{n_i+0.5}\cdot\frac{(k_1+1)tf_{di}}{k_1((1-b)+b\,dl/avdl)+tf_{di}}\cdot\frac{(k_3+1)tf_{qi}}{k_3+tf_{qi}}
$$

**PageRank**

$$
R(p)=\varepsilon+(1-\varepsilon)\sum_{(q\to p)}\frac{R(q)}{\mathrm{out}(q)}
$$

**Dice / Jaccard**

$$
\mathrm{Dice}=\frac{2\sum w_{ik}w_{jk}}{\sum w_{ik}^2+\sum w_{jk}^2},\quad
\mathrm{Jaccard}=\frac{\sum w_{ik}w_{jk}}{\sum w_{ik}^2+\sum w_{jk}^2-\sum w_{ik}w_{jk}}
$$

---

# 16. Algorithms and Procedures I Must Know

1. **Boolean AND/OR on sorted postings** — two-pointer merge.  
2. **Signature query** — hash → AND-match → exact verify.  
3. **S-tree search** — multi-path AND-match descent; insert with minimal expansion + split seeds.  
4. **AP calculation** — at each relevant hit, $P=\#rel\_found/rank$; average over $|R|$.  
5. **nDCG** — DCG; sort grades for IDCG; divide.  
6. **Porter-style stemming** — rule-based suffix stripping (concept).  
7. **Build TF–IDF vectors + cosine rank**.  
8. **Rocchio / Ide feedback update**.  
9. **LM score with Dirichlet in log space**.  
10. **BIR initial score; update $p_i,q_i$ after feedback**.  
11. **BM25 score for a doc**.  
12. **Agglomerative clustering** — merge loop + linkage choice.  
13. **Naive Bayes classify with add-one**.  
14. **Fuzzy:** build $C$ matrix → $\mu_i(D_j)$ → evaluate Boolean query with min/max/¬.  
15. **PageRank iteration** — update until convergence.

---

# 17. Important Comparisons

| Pair | Key distinction |
|------|-----------------|
| Efficiency vs effectiveness | Resources vs result quality |
| Macro vs micro avg | Equal queries vs equal documents/hits |
| MAP vs P@10 | Full ranked quality vs first-page UX |
| DCG vs AP | Graded vs binary |
| Stemming vs lemmatization | Stem may be non-word; lemma is base word |
| Over- vs understemming | P↓ vs R↓ |
| Inverted lists vs signatures | Exact postings vs probabilistic filter |
| SSF vs BSSF vs S-tree | Scan-all vs bit I/O vs tree prune |
| Boolean vs coordination vs $p$-norm vs fuzzy | Hard set → count → soft $p$ → graded membership |
| VSM vs LM vs BM25 | Geometric heuristic vs generative vs probabilistic engineered |
| Ide dec hi vs Rocchio | Subtract top nonrel vs weighted centroids |
| JM vs Dirichlet | Fixed $\omega$ vs length-adaptive |
| Classification vs clustering | Labeled manual vs automatic unlabeled |
| Single vs complete link | Chain vs compact |
| Sparse vs dense retrieval | BM25/TFIDF vs embeddings |
| Search vs browse | Lookup vs navigate |

---

# 18. Common Exam Traps

1. Confusing **precision** and **recall**.  
2. Computing AP with denominator = #found relevants instead of **$|R|$**.  
3. For P@$r$ when $|R|$ changes: recall levels shift ($k/|R|$).  
4. Forgetting $\mathrm{rel}_1$ is **not** divided by $\log_2 1$ in DCG.  
5. IDCG = DCG of **sorted grades**, not of an arbitrary ranking.  
6. Claiming Boolean has ranking.  
7. Signature match ⇒ document contains term (**false** — false drops).  
8. For conjunctive signatures: OR of query signatures requires terms in **same block**.  
9. Fuzzy: wrong correlation formula (use $n_{i,l}$ in **numerator**).  
10. Believing min/max uses "average strength" — **dominance problem**.  
11. Using document TF–IDF formula for **queries**.  
12. Thinking cosine and dot product always give different rankings (often identical order).  
13. Rocchio: mixing up which of $\alpha,\beta$ weights relevant (relevant gets **larger** weight $\beta\approx0.75$).  
14. LM: ranking by $P(d\mid q)$ without prior — usually rank $P(q\mid d)$.  
15. Forgetting smoothing → zeros.  
16. BIR: summing over all vocabulary instead of **$Q\cap D$**.  
17. BM25: confusing $k_1$ (doc TF) with $b$ (length) with $k_3$ (query TF).  
18. Negative BM25 IDF when $n_i>N/2$.  
19. Single-link "best" without mentioning chaining.  
20. Stemming always improves both P and R (**no**).  
21. Stopwords always safe to remove (**no** — "to be or not to be").  
22. PageRank measures topical relevance (**no** — popularity/authority via links).  
23. Macro/micro mix-up.  
24. Pooling = complete relevance judgments (**no**).  
25. Pseudo RF always helps (**only if top results good**).


---

# 19. 50+ Mixed Practice Questions with Complete Solutions

> **Also do §23 (Q61–Q180), §24 timed sprints, and Mock Exam 2 (§25).** For a 120 min / 100 mark exam, practice > re-reading.

---

### Q1 [SA] 🔥 Define IR and contrast it with fact retrieval.
**Solution:** IR finds documents relevant to a vague information need and ranks them. Fact retrieval (DB) answers exact queries over structured data with complete result sets. IR: end users, partial match, effectiveness metrics. DB: schema predicates, exact match, correctness+efficiency.

### Q2 [SA] Distinguish data, knowledge, and information (Kuhlen).
**Solution:** Data = raw symbols; knowledge = organized known content; information = knowledge activated for a purpose/need. IR delivers documents embodying knowledge so users obtain information.

### Q3 [Why] Why must postings lists be sorted?
**Solution:** AND/OR/AND-NOT become linear merges $O(|L_1|+|L_2|)$. Unsorted lists require nested scans or hashing with worse constants / more memory.

### Q4 [Algo] Postings: `cat→[1,3,5,8]`, `dog→[3,4,8,9]`. Compute `cat AND dog` and `cat OR dog`.
**Solution:** AND: intersect → `[3,8]`. OR: union → `[1,3,4,5,8,9]`.

### Q5 [Calc] 🔥 Collection 200k docs, avg 120 distinct terms/doc, 4-byte IDs. Estimate postings size.
**Solution:** $200000\times120\times4=96\times10^6$ bytes ≈ 91.6 MiB (IDs only).

### Q6 [SA] State Zipf's law and one index consequence.
**Solution:** $r(w)h(w)\approx c$. Consequence: highly skewed list lengths → careful paging; stopword/IDF effects; dictionary needed.

### Q7 [SA] 🔥 What is a false drop in signature files?
**Solution:** Block signature satisfies the necessary bit condition for the query, but the block/document does not contain the search pattern (collision or superposition).

### Q8 [Calc] $F=64$, $D=8$. Optimal $m$? Approximate $F_d$?
**Solution:** $m_{\mathrm{opt}}=\frac{F}{D}\ln2=\frac{64}{8}\ln2=8\ln2\approx5.545$ (≈6).  
$F_d=(1/2)^{F\ln2/D}=(1/2)^{\ln2\cdot8}\approx(1/2)^{5.545}\approx0.021$.

### Q9 [Compare] SSF vs bit-sliced signatures.
**Solution:** SSF reads full signatures (simple updates, search ∝ $N$). BSSF reads only $m$ bit slices (fast search, updates touch $F$ files). Prefer BSSF when search-heavy.

### Q10 [Algo] How does S-tree search work?
**Solution:** From root, follow every child whose signature AND-matches the query signature; multiple paths; verify documents at leaves.

### Q11 [Calc] 🔥 Coordination: query `{house, garden, NOT france}`. Scores for docs: A{house,garden}, B{house,france}, C{garden}, D{house,garden,france}?
**Solution:** A: +1+1=2; B: +1−1=0 (drop); C: +1=1; D: +1+1−1=1. Rank A > C=D.

### Q12 [Calc] 🔥 $p$-norm OR with $x=(0.8,0.2)$, $p=\infty$ and $p=1$.
**Solution:** $p=\infty$: $\max=0.8$. $p=1$: average $(0.8+0.2)/2=0.5$.

### Q13 [Calc] $p$-norm AND with same $x$, $p=\infty$ and $p=1$.
**Solution:** $p=\infty$: $\min=0.2$. $p=1$: also $0.5$ (same as OR when $p=1$).

### Q14 [Why] Why increase $p$ in $p$-norm?
**Solution:** Larger $p$ makes OR→max and AND→min, recovering strict Boolean-like behavior; small $p$ softens toward averages / partial match.

### Q15 [Calc] 🔥 Fuzzy correlation: $n_i=10$, $n_l=6$, $n_{i,l}=4$. Compute $c_{i,l}$.
**Solution:** $c=4/(10+6-4)=4/12=1/3$.

### Q16 [Calc] Doc terms $\{t_2,t_3\}$ with $c_{1,2}=0.5$, $c_{1,3}=0.2$, $c_{1,1}=1$ unused. $\mu_1(D)$?
**Solution:** $\mu_1=1-(1-0.5)(1-0.2)=1-0.5\cdot0.8=0.6$.

### Q17 [Why] Fuzzy min/max dominance with House∧Italy: D1(0.3,0.3) vs D2(0.9,0.2).
**Solution:** Scores $\min=0.3$ vs $0.2$ → D1 wins despite D2's strong House membership — weakest term dominates.

### Q18 [Calc] 🔥 $(P,R)=(0.75,0.25)$ after finding 3 relevants. Docs observed? Total relevant?
**Solution:** $P=3/(3+b)=0.75\Rightarrow b=1$ → observed **4**. $R=3/(3+c)=0.25\Rightarrow c=9$ → $|R|=$ **12**.

### Q19 [SA] Explain F-measure.
**Solution:** Weighted harmonic mean of $P$ and $R$; balances the two; $F_1$ uses equal weight.

### Q20 [Calc] 🔥 Ranking `+ − + − − − + + + − − − − + +`, $|R|=10$. Give $P$ at recall 0.1,0.2,0.3 and AP (approx).
**Solution:** Ranks of rel: 1,3,7,… → $P$: 1.0, 0.667, 0.429. AP≈0.405 (include all 7 found + 3 zeros)/10.

### Q21 [Calc] Same ranking but $|R|=15$. What is "P@0.2"?
**Solution:** Recall 0.2 means $0.2\times15=3$ relevants found → still at rank 7 → $P=3/7\approx0.429$ (same P, different recall label meaning).

### Q22 [SA] What is MAP?
**Solution:** Mean of per-query Average Precisions — system-oriented summary of ranked quality over a query set.

### Q23 [Calc] 🔥 Grades `[2,1,0,4,3,0]`. Compute DCG₆, IDCG₆, nDCG₆.
**Solution:** DCG≈6.292; ideal `[4,3,2,1,0,0]` IDCG≈8.762; nDCG≈0.718.

### Q24 [Why] Why is recall hard to measure?
**Solution:** Relevant docs are rare; full judgments expensive; pooling incomplete; expansion methods bias recall high.

### Q25 [Compare] Macro vs micro averaging.
**Solution:** Macro: unweighted mean over queries (user view). Micro: pool counts (large queries dominate).

### Q26 [SA] Effect of stopword removal on P and R?
**Solution:** Typically improves focus (P↑, index↓); can raise R in VSM by removing noise; can destroy phrase queries → R/P↓ in those cases.

### Q27 [SA] Overstemming vs understemming.
**Solution:** Over: different meanings → same stem → P↓. Under: same meaning → different stems → R↓.

### Q28 [Compare] Stemming vs base-form (lemma) reduction.
**Solution:** Stemming: cheap rules, stem may be non-word, verb/noun share stem. Lemma: dictionary base word, better linguistically, costly for rich morphology.

### Q29 [SA] What is terminological control?
**Solution:** Use of controlled indexing language / preferred terms to reduce ambiguity (library tradition).

### Q30 [SA] RDF subject, predicate, object — why triples?
**Solution:** Statement links two resources (subj,obj) via a named relation (pred); builds a metadata graph; URIs identify components.

### Q31 [Calc] 🔥 Docs: D1 tf=(1,1,0), D2=(1,2,0), Q=(1,1,0) raw. Dot products? Who wins unfairly?
**Solution:** $\langle Q,D1\rangle=2$, $\langle Q,D2\rangle=3$ → longer D2 wins unfairly.

### Q32 [Calc] Normalize D1=(1,1,0), D2=(1,2,0) by $\|tf\|_2$. New dots with Q=(1,1,0)?
**Solution:** D1 unit: $(1/\sqrt2,1/\sqrt2,0)$; D2: $(1/\sqrt5,2/\sqrt5,0)$.  
Dots: D1: $2/\sqrt2=\sqrt2\approx1.41$; D2: $3/\sqrt5\approx1.34$ → D1 wins.

### Q33 [Calc] $N=1000$, $n_t=10$, $tf=4$ in doc with only that term. Unnormalized tf-idf weight?
**Solution:** $4\log(1000/10)=4\log100$. (If $\ln$: $4\cdot4.605\approx18.4$; if $\log_{10}$: $8$. State base.)

### Q34 [SA] Write Salton query weight formula and justify 0.5.
**Solution:** $(0.5+0.5 tf/\max tf)\log(N/n)$. Base 0.5: term was explicitly chosen by user even if $tf=1$.

### Q35 [Why] Why log in IDF?
**Solution:** Raw $N/n$ overpowers rare terms; log dampens while preserving rarity order.

### Q36 [Algo] State Rocchio update; typical $\alpha,\beta$.
**Solution:** $Q'=Q+\beta\mathrm{avg}(F^+)-\alpha\mathrm{avg}(F^-)$ with $\alpha+\beta=1$, e.g. $\alpha=0.25,\beta=0.75$.

### Q37 [Why] Why is Ide (dec hi) often best?
**Solution:** Nonrelevant set is diverse; subtracting all pulls query in conflicting directions; subtracting the top nonrelevant corrects the most damaging error.

### Q38 [SA] Pseudo relevance feedback — risk?
**Solution:** Assumes top-$n$ are relevant; if not, query drifts to wrong topic (query drift).

### Q39 [Calc] 🔥 Unigram MLE: doc "aaab". $P(a),P(b)$? $P($"ab"$)$? $P($"ac"$)$?
**Solution:** $P(a)=3/4$, $P(b)=1/4$; $P(ab)=3/16$; $P(ac)=0$ without smoothing.

### Q40 [Calc] JM: $|d|=4$, $tf(a)=3$, $cf(a)/|c|=0.1$, $\omega=0.7$. $\hat P(a\mid d)$?
**Solution:** $0.7\cdot(3/4)+0.3\cdot0.1=0.525+0.03=0.555$.

### Q41 [Why] Dirichlet vs JM?
**Solution:** Dirichlet's mix weight $\varepsilon/(\varepsilon+|d|)$ depends on length — short docs smoothed more; generally better for IR.

### Q42 [Calc] 🔥 BIR init: $N=1000$, matching terms with $n=50$ and $n=200$. Score?
**Solution:** $\log\frac{950}{50}+\log\frac{800}{200}=\log19+\log4$. ($\ln$: ≈2.944+1.386=4.33)

### Q43 [SA] Role of $k_1$ and $b$ in BM25.
**Solution:** $k_1$: how fast TF saturates. $b$: strength of length normalization (pivot by $dl/avdl$).

### Q44 [Calc] BM25 IDF for $N=1000$, $n=10$ and $n=600$.
**Solution:** $n=10$: $\log\frac{1000-10+0.5}{10+0.5}=\log\frac{990.5}{10.5}>0$.  
$n=600$: $\log\frac{400.5}{600.5}<0$ → typically set to 0.

### Q45 [Compare] VSM vs BM25.
**Solution:** VSM: cosine TF–IDF heuristic. BM25: probabilistic IDF + saturating TF + pivoted length; usually stronger ad-hoc baseline; both use inverted indexes.

### Q46 [Compare] Single-link vs complete-link clustering.
**Solution:** Single: max inter-sim → chaining/sprawl. Complete: min inter-sim → tight clusters.

### Q47 [Calc] Binary sets A={1,2,3}, B={2,3,4}. Jaccard and Dice (set forms).
**Solution:** $|A\cap B|=2$, $|A\cup B|=4$. Jaccard=$2/4=0.5$. Dice=$2\cdot2/(3+3)=2/3$.

### Q48 [Scenario] Legal search needs every statute mentioning both terms, exact Boolean. Which model first?
**Solution:** Boolean over inverted lists (possibly with NEAR); ranking optional secondary. Effectiveness = completeness under expert query language.

### Q49 [Scenario] Web search: short queries, need good first page + authority.
**Solution:** BM25/LM for content + PageRank/quality prior; evaluate with P@10 / nDCG; not pure Boolean.

### Q50 [Long] Explain RAG pipeline and why it helps QA.
**Solution:** Index chunks → embed/search → retrieve top evidence → augment prompt → LLM generates. Helps by grounding answers in retrieved docs, reducing hallucination and enabling domain knowledge without full fine-tuning. Failure if retrieval misses.

### Q51 [MCQ] Harmonic mean of P and R is used because:
A) It equals arithmetic mean  
B) It heavily penalizes if either is low  
C) It ignores precision  
**Answer:** B.

### Q52 [MCQ] In Dirichlet smoothing, as $|d|\to\infty$, $\hat P(t\mid d)$ approaches:
A) collection probability  
B) MLE $tf/|d|$  
C) 0  
**Answer:** B.

### Q53 [MCQ] Coordination level match vs Boolean AND:
A) identical results always  
B) allows partial matches with ranking  
C) uses PageRank  
**Answer:** B.

### Q54 [Algo] Sketch agglomerative clustering.
**Solution:** Start singletons; while >1 cluster: merge pair with highest linkage similarity; update matrix; record merge → dendrogram.

### Q55 [Why] Why does length normalization matter in VSM/BM25?
**Solution:** Raw TF favors long docs; full cosine can over-penalize long docs; pivoted/$b$ balances so verbose and concise relevant docs compete fairly.

### Q56 [Calc] Fuzzy query $\mu$: House=0.7, Italy=0.4, Garden=0.2. Score `(House OR Italy) AND NOT Garden`.
**Solution:** $\min(\max(0.7,0.4),1-0.2)=\min(0.7,0.8)=0.7$.

### Q57 [SA] GMAP purpose?
**Solution:** Geometric mean of APs — emphasizes robustness on hard queries, not only high mean AP.

### Q58 [Compare] Navigational vs informational queries for evaluation.
**Solution:** Navigational: success if right page early (MRR/P@1). Informational: broader relevance, AP/nDCG/recall matter.

### Q59 [Long] Derive why BIR initial ranking resembles IDF.
**Solution:** With $p_i=0.5$, $q_i=n_i/N$, RSV term becomes $\log\frac{N-n_i}{n_i}\approx\log\frac{N}{n_i}$ for small $n_i/N$. Summing over matched query terms ≈ IDF retrieval with binary TF.

### Q60 [Scenario] Build automatic thesaurus from a corpus — steps?
**Solution:** Term–doc matrix → term–term similarities (Dice/Jaccard) → star/clique clustering with threshold → groups as synonym candidates; human check preferred.


---

# 20. Full Mixed Mock Exam

**Time allowed:** 120 minutes  
**Instructions:** No lecture slides. Show formulas before plugging numbers. Approximate logs OK if you state the base.  
**Suggested points:** 100 total.

---

## Part A — Short answers (20 pts)

**A1 (4)** Name the four components every retrieval model must specify.

**A2 (4)** Give Zipf's law and one consequence for inverted indexes.

**A3 (4)** Define overstemming and understemming; state the typical effect of each on P/R.

**A4 (4)** What is pooling in TREC-style evaluation? One limitation?

**A5 (4)** State Shneiderman's information-seeking mantra.

---

## Part B — Calculations (40 pts)

**B1 (10) Evaluation.**  
For a query with 8 relevant documents, a system returns the ranking (first 12):  
`+ − − + + − + − − − + −`  
(a) Fill precision at each relevant hit and the corresponding recall.  
(b) Compute AP.  
(c) Compute P@5 and P@10.

**B2 (8) nDCG.** Relevance grades for top-5: `3, 0, 2, 1, 0`.  
Compute DCG₅, IDCG₅, nDCG₅.

**B3 (10) VSM.** Vocabulary `{alpha, beta, gamma}`.  
D1 tfs $(2,1,0)$, D2 $(0,1,1)$, Q tfs $(1,1,0)$.  
$N=1000$, $n=(100,200,50)$. Use $\mathrm{idf}=\ln(N/n)$ (no length norm).  
(a) Compute raw tf-idf vectors for D1, D2, Q (for Q use Salton formula with max tf = 1).  
(b) Rank D1 vs D2 by dot product with Q.

**B4 (6) BIR.** $N=500$. Query terms with $n_i\in\{20,50,100\}$. Document contains the first and third only. Initial BIR score?

**B5 (6) Fuzzy.** Terms $t_1,t_2,t_3$. Correlations: $c_{1,1}=1,c_{2,2}=1,c_{3,3}=1,c_{1,2}=0.4,c_{1,3}=0.1,c_{2,3}=0.5$.  
Document $D=\{t_2,t_3\}$. Compute $\mu_1(D)$. Then score query $t_1 \wedge \neg t_2$ using $\mu_1(D)$ and $\mu_2(D)=1-\prod_{t\in D}(1-c_{2,t})$.

---

## Part C — Algorithms & design (20 pts)

**C1 (8)** Describe processing of `A AND (B OR C)` with inverted lists. Complexity in terms of list lengths?

**C2 (6)** Explain superimposed coding and how false drops arise. When prefer bit-sliced files over sequential signature files?

**C3 (6)** Give the BM25 formula and explain $k_1$ and $b$ with one sentence each.

---

## Part D — Essays (20 pts)

**D1 (10)** Compare Boolean, Vector Space, Language Model, and BM25 along: document representation, ranking, theoretical status, relevance feedback, typical use.

**D2 (10)** A startup builds enterprise search. They currently use Boolean. Users complain about empty results and no ranking. Propose a migration path (NLP preprocessing → ranking model → evaluation plan → optional RF/RAG). Justify each step.

---

## Mock Exam Solutions

### Part A
**A1:** Document representation; query representation; matching/ranking function; implementation/index.  
**A2:** $r\cdot h\approx c$; skewed postings lengths / need dictionary & paging strategy.  
**A3:** Over: distinct concepts same stem → P↓. Under: same concept different stems → R↓.  
**A4:** Merge top-k from many systems; judge pool; unjudged ≈ nonrel — incomplete, bias toward systems like those pooled.  
**A5:** Overview first, zoom and filter, then details on demand.

### Part B
**B1** Relevant ranks: 1,4,5,7,11 (5 of 8).  
| k | rank | R=k/8 | P=k/rank |  
|---|------|-------|----------|  
|1|1|0.125|1.000|  
|2|4|0.250|0.500|  
|3|5|0.375|0.600|  
|4|7|0.500|0.571|  
|5|11|0.625|0.455|  
AP $=(1+0.5+0.6+0.571+0.455)/8\approx0.391$ (3 missing → 0).  
P@5 $=3/5=0.6$; P@10 $=4/10=0.4$.

**B2** DCG $=3+0/\log_2 2+2/\log_2 3+1/\log_2 4+0/\log_2 5=3+0+2/1.585+0.5\approx4.762$.  
Ideal `[3,2,1,0,0]`: IDCG $=3+2/1+1/\log_2 3\approx3+2+0.631=5.631$.  
nDCG≈$4.762/5.631\approx0.846$.

**B3** idf: $\ln10\approx2.303$, $\ln5\approx1.609$, $\ln20\approx2.996$.  
D1: $(2\cdot2.303,\ 1\cdot1.609,\ 0)=(4.606,1.609,0)$  
D2: $(0,\ 1.609,\ 2.996)$  
Q Salton: each present term $(0.5+0.5\cdot1)\cdot\mathrm{idf}=\mathrm{idf}$ → $(2.303,1.609,0)$  
Dots: D1: $4.606\cdot2.303+1.609\cdot1.609\approx10.61+2.59=13.20$  
D2: $1.609\cdot1.609\approx2.59$ → **D1 ≫ D2**.

**B4** $\log\frac{480}{20}+\log\frac{400}{100}=\log24+\log4$. ($\ln$: $3.178+1.386=4.564$)

**B5** $\mu_1(D)=1-(1-0.4)(1-0.1)=1-0.6\cdot0.9=0.46$.  
$\mu_2(D)=1-(1-1)(1-0.5)$ wait: terms in D are $t_2,t_3$; $c_{2,2}=1$, $c_{2,3}=0.5$ →  
$\mu_2=1-(1-1)(1-0.5)=1-0=1$.  
Score $\min(\mu_1,1-\mu_2)=\min(0.46,0)=0$.

### Part C
**C1:** Compute $L_B\cup L_C$ then intersect with $L_A$ (or distribute: $(L_A\cap L_B)\cup(L_A\cap L_C)$). Sorted merges; time linear in sizes of lists touched.  
**C2:** Hash words to $m$-of-$F$ bits; OR into block signature; match is necessary only. False drops via collision/superposition. Prefer BSSF when searches dominate updates.  
**C3:** Full BM25 as in formula sheet. $k_1$: TF saturation. $b$: doc length normalization strength.

### Part D (sketch of full-credit answer)
**D1:** Table comparing bag/binary/tf vectors vs multinomial LM vs BM25 features; Boolean unranked vs others ranked; theory heuristic vs generative vs probabilistic; RF natural in VSM/BIR, weaker native in LM; BM25 default ad-hoc.  
**D2:** Add tokenization+stemming+stopwords carefully → inverted index already there → introduce BM25 ranking on same index → evaluate with AP/P@10 on labeled queries → add pseudo/real RF → optional semantic rerank/RAG for natural-language answers; keep Boolean mode for expert power users.

**Self-score guide:** 90+ ready; 75–89 review weak calc areas; <75 restudy Ch.5,7,9 formula drills.

---

# 21. Final 2-Hour Revision

**Hour 1 — Formulas on blank paper (no peeking)**

Write from memory: $P,R,F_1$, AP/MAP, DCG/nDCG, TF–IDF, Salton query weights, cosine, Rocchio, JM, Dirichlet, BIR init, BM25, fuzzy $c$ & $\mu$, $p$-norm limits, Zipf, $m_{\mathrm{opt}}$, PageRank.  
Check against §15. Redrill misses.

**Hour 2 — Procedures + comparisons**

- Re-solve: one AP, one nDCG, one TF–IDF rank, one BIR, one BM25 IDF sign check, one fuzzy $\mu$.  
- Speak aloud (2 min each): Boolean vs VSM vs LM vs BM25; Ide vs Rocchio; single vs complete link; signatures vs inverted lists; stemming P/R effects.  
- Skim §18 traps once.

---

# 22. Final 30-Minute Revision

1. **AP:** average $P$ at each relevant / $|R|$.  
2. **nDCG:** discount by $\log_2 i$; normalize by ideal.  
3. **TF–IDF + cosine**; query uses $0.5+0.5 tf/\max$.  
4. **BM25:** IDF$(N-n+0.5)/(n+0.5)$; $k_1$ TF; $b$ length.  
5. **LM:** $P(q\mid d)$ + Dirichlet smoothing + logs.  
6. **BIR init:** $\sum_{Q\cap D}\log\frac{N-n}{n}$.  
7. **Fuzzy:** $c=n_{i,l}/(n_i+n_l-n_{i,l})$; $\mu=1-\prod(1-c)$; min/max/¬.  
8. **$p$-norm:** $p=1$ average; $p=\infty$ max/min.  
9. **False drop** ≠ miss; signatures need verification.  
10. **RF:** Ide dec hi; Rocchio $\beta>\alpha$; pseudo RF risky.  
11. **Traps:** macro/micro; negative IDF; stopword edge cases; PageRank ≠ topical relevance.  
12. Breathe. Read each exam question twice. Write the formula first.

---



---

# Appendix A — Extra Calculation Drills (Formula Variations)

> Do these blind. Solutions at the end of the appendix.

**D1.** Ranking `− + + − +`, $|R|=4$. Compute AP and P@3.

**D2.** Ranking `+ + − − +`, $|R|=3$. Compute AP. Then recompute AP if $|R|=5$ (two relevants missing).

**D3.** Grades `[4,0,3,0,2]`. nDCG₅?

**D4.** Grades `[1,1,1,1]`. Show DCG₄ = $1+1/\log_2 2+1/\log_2 3+1/2$. Numeric ≈?

**D5.** $N=10^6$, $n=10^3$. Compare $\log(N/n)$ vs BM25 $\log\frac{N-n+0.5}{n+0.5}$.

**D6.** Doc length $dl=2\cdot avdl$, $tf=5$, $k_1=1.2$, $b=0.75$. BM25 TF factor $\frac{(k_1+1)tf}{k_1((1-b)+b dl/avdl)+tf}$?

**D7.** Same as D6 but $dl=0.5 avdl$. Compare — which doc gets higher TF factor?

**D8.** JM: $\omega=0.2$, $tf/|d|=0$, $cf/|c|=0.001$. Unseen term probability?

**D9.** Dirichlet $\varepsilon=2000$, $|d|=500$, $tf=0$, $cf/|c|=0.001$. Unseen term probability?

**D10.** Fuzzy: $n_1=8,n_2=5,n_{12}=3$. $c_{1,2}$? If $D=\{t_2\}$ only, $\mu_1(D)$?

**D11.** $p$-norm AND, $x=(1,0.5,0)$, $p\to\infty$ and $p=1$.

**D12.** Signature: $F=128,D=16$. $m_{\mathrm{opt}}$ and $F_d=(1/2)^{F\ln 2/D}$.

**D13.** BIR: three matched terms $n=(5,50,250)$, $N=1000$. Which term contributes most/least?

**D14.** VSM slope: old norms 10,40,80; avg=40; slope=0.75. Compute each $k_{fd}$.

**D15.** Rocchio: $Q=(1,0)$, one relevant $(1,1)$, one nonrel $(1,0)$, $\alpha=0.25,\beta=0.75$. $Q'$?

### Appendix A Solutions

**D1.** Rel ranks 2,3,5 → P: 1/2,2/3,3/5. AP=$(0.5+0.667+0.6)/4=0.442$. P@3=$2/3$.  
**D2.** Ranks 1,2,5 → P:1,1,0.6. AP=$(1+1+0.6)/3=0.867$. If $|R|=5$: divide by 5 → AP=0.52.  
**D3.** DCG=$4+0+3/\log_2 3+0+2/\log_2 5\approx4+1.892+0.861=6.753$. Ideal `[4,3,2,0,0]`: IDCG=$4+3+2/\log_2 3\approx8.262$. nDCG≈0.817.  
**D4.** $1+1+0.631+0.5=3.131$.  
**D5.** $\ln(1000)\approx6.907$; BM25 $\ln(999000.5/1000.5)\approx6.906$ — nearly equal for rare terms.  
**D6.** Denom factor $(1-0.75)+0.75\cdot2=0.25+1.5=1.75$; denom=$1.2\cdot1.75+5=7.1$; num=$2.2\cdot5=11$; TF fac=$11/7.1\approx1.549$.  
**D7.** $(1-b)+b\cdot0.5=0.25+0.375=0.625$; denom=$1.2\cdot0.625+5=5.75$; fac=$11/5.75\approx1.913$ — **short doc higher TF factor**.  
**D8.** $0.2\cdot0+0.8\cdot0.001=0.0008$.  
**D9.** $\frac{0+2000\cdot0.001}{500+2000}=2/2500=0.0008$.  
**D10.** $c=3/(8+5-3)=3/10=0.3$; $\mu_1=1-(1-0.3)=0.3$.  
**D11.** $p=\infty$: $\min=0$; $p=1$: avg $(1+0.5+0)/3=0.5$.  
**D12.** $m=8\ln2\approx5.55$; $F_d=(1/2)^{8\ln2}=(1/2)^{5.545}\approx0.021$.  
**D13.** Contrib $\log\frac{995}{5}$, $\log\frac{950}{50}$, $\log\frac{750}{250}$ — rarest ($n=5$) largest; $n=250$ smallest.  
**D14.** $k=(1-0.75)+0.75\cdot(\mathrm{norm}/40)$ → $0.25+0.75\cdot0.25=0.4375$; $1.0$; $0.25+0.75\cdot2=1.75$.  
**D15.** $Q'= (1,0)+0.75(1,1)-0.25(1,0)=(1,0)+(0.75,0.75)-(0.25,0)=(1.5,0.75)$.

---

# Appendix B — Lecture → Guide Map

| Lecture | Guide chapters |
|---------|----------------|
| IR-1 Intro | §1, §2, §12 (PageRank preview) |
| IR-2 Evaluation | §5 |
| IR-3 Language | §6 |
| IR-4 Simple models | §2–§4 |
| IR-5 VSM | §7 |
| IR-6a Language models | §8 |
| IR-6b DL / RAG | §11 |
| IR-7 Alternatives | §10 |
| IR-8 Probabilistic | §9 |
| EX01–EX04 | Embedded as worked examples + Q-bank |




---

# Exam Pacing (120 min / 100 marks)

Use this whenever you practice under time:

| Block | Minutes | Marks (typical) | Strategy |
|-------|---------|-----------------|----------|
| Short answers / MCQ / definitions | 20–25 | ~20 | 1–2 min each; no essays yet |
| Calculations | 45–50 | ~40 | Formula first, then numbers; skip & return if stuck >4 min |
| Algorithms / compare | 20–25 | ~20 | Bullet steps + complexity / trade-off table |
| Long / scenario | 20–25 | ~20 | Structured paragraphs; name models & metrics |
| Buffer / check | 5–10 | — | Recheck AP denominators, nDCG ideal sort, BM25 IDF sign |

**Mark-efficiency rule:** a correct 6-pt calculation beats a vague 10-pt essay. Secure all 🔥 calc patterns first (AP, nDCG, TF–IDF/cosine, BIR, BM25 piece, fuzzy $c$/$\mu$, $p$-norm limits).

---

# 23. Extended Practice Bank (Q61–Q140)

> 80 new questions with solutions. Prefer these over re-reading theory. Tags match exam styles.

---

## Block A — Foundations & Boolean (Q61–Q75)

### Q61 [MCQ] IR systems primarily optimize:
A) Schema normalization  
B) Effectiveness for an information need  
C) ACID transactions  
**Answer:** B.

### Q62 [SA] List three disadvantages of pure Boolean retrieval.
**Solution:** No ranking; unpredictable result size; hard for end users; no term weights; often no stemming/compounds.

### Q63 [Algo] Lists: `A=[1,4,7,9]`, `B=[2,4,9,11]`, `C=[4,5,9]`. Evaluate `(A OR B) AND C` and `A AND NOT B`.
**Solution:** $A\cup B=[1,2,4,7,9,11]$; ∩C → `[4,9]`. $A\setminus B=[1,7]$.

### Q64 [Why] Why is unary NOT usually avoided?
**Solution:** Result ≈ entire collection minus a short list → huge, useless; prefer `q1 AND NOT q2`.

### Q65 [Calc] 800,000 docs × 90 distinct terms/doc × 8-byte IDs. Postings bytes? GiB?
**Solution:** $800000\times90\times8=5.76\times10^8$ bytes ≈ 0.536 GiB (≈549 MiB).

### Q66 [SA] What must postings store to support `NEAR[3]`?
**Solution:** Term occurrence **positions** (and usually doc IDs); scan pairs of positions within distance 3.

### Q67 [MCQ] Sorted postings AND is typically:
A) $O(|L_1||L_2|)$  
B) $O(|L_1|+|L_2|)$  
C) $O(\log N)$ always  
**Answer:** B.

### Q68 [Compare] Forward index vs inverted index — which starts a keyword search?
**Solution:** Search starts from terms → **inverted** index. Forward is doc→terms (useful for display/snippets).

### Q69 [SA] State the four aspects of a retrieval model.
**Solution:** Document representation; query representation; matching/ranking; implementation.

### Q70 [Why] Empty Boolean AND results frustrate users — name two soft alternatives from the course.
**Solution:** Coordination level match; $p$-norm / extended Boolean; (also VSM/BM25 ranking).

### Q71 [Calc] Coordination query `{ai, search, NOT spam}`. Doc has `{ai, spam}`. Score? Keep?
**Solution:** $+1-1=0$ → discard (≤0).

### Q72 [Calc] Same query; doc `{ai, search}`. Score?
**Solution:** $+1+1=2$.

### Q73 [MCQ] Zipf says if rank-1 frequency is $f$, rank-3 frequency is about:
A) $f$  
B) $f/3$  
C) $3f$  
**Answer:** B ($r\cdot h\approx c$).

### Q74 [SA] Why do inverted indexes need a dictionary (e.g. B+-tree)?
**Solution:** Map term string → start address of its (variable-length) postings list quickly.

### Q75 [Scenario] Patent lawyers need reproducible exact Boolean. Keep Boolean? Add what?
**Solution:** Keep Boolean (+proximity/fields). Optionally add a **ranked mode** for exploration, but legal workflow stays Boolean.

---

## Block B — Signatures & Soft Boolean (Q76–Q90)

### Q76 [SA] Superimposed coding in one sentence.
**Solution:** Each word sets $m$ of $F$ bits; block signature is bitwise OR of its word signatures.

### Q77 [Calc] $F=96$, $D=12$. $m_{\mathrm{opt}}$? Rough $F_d$?
**Solution:** $m=\frac{96}{12}\ln2=8\ln2\approx5.55$. $F_d=(1/2)^{8\ln2}\approx0.021$.

### Q78 [Calc] $F=200$, $D=10$. $m_{\mathrm{opt}}$ and $F_d$.
**Solution:** $m=20\ln2\approx13.86$. $F_d=(1/2)^{20\ln2}=(1/2)^{13.86}\approx6.8\times10^{-5}$.

### Q79 [Why] Increasing block size $D$ (more words/block) does what to false drops?
**Solution:** Increases $F_d$ (more superposition) unless $F$ grows accordingly.

### Q80 [Compare] When are sequential signature files preferred over bit-sliced?
**Solution:** When **inserts/updates dominate** and search is rare (SSF updates easy; BSSF update touches $F$ slices).

### Q81 [Algo] S-tree insert overflow: what are seed signatures?
**Solution:** Two maximally different signatures in the overflowing node; then assign remaining signatures alternately to the closer seed.

### Q82 [MCQ] Signature match without the term is called:
A) false drop  
B) miss  
C) understemming  
**Answer:** A.

### Q83 [Calc] $p$-norm OR, $x=(0.9,0.6,0.3)$, $p=2$.
**Solution:** $\bigl((0.81+0.36+0.09)/3\bigr)^{1/2}=(1.26/3)^{1/2}=\sqrt{0.42}\approx0.648$.

### Q84 [Calc] Same $x$, $p$-norm AND, $p=2$.
**Solution:** $1-\bigl(((0.1)^2+(0.4)^2+(0.7)^2)/3\bigr)^{1/2}=1-\sqrt{0.66/3}=1-\sqrt{0.22}\approx0.531$.

### Q85 [Calc] Same $x$, $p=\infty$: OR and AND?
**Solution:** OR $\max=0.9$; AND $\min=0.3$.

### Q86 [Why] At $p=1$, AND and OR scores coincide — problem for users?
**Solution:** Soft operators become identical averages → cannot express strict conjunction vs disjunction; raise $p$ to sharpen.

### Q87 [Calc] Fuzzy: $n_i=12$, $n_l=9$, $n_{i,l}=6$. $c_{i,l}$?
**Solution:** $6/(12+9-6)=6/15=0.4$.

### Q88 [Calc] $c_{1,2}=0.6$, $c_{1,3}=0.25$, $D=\{t_2,t_3\}$. $\mu_1(D)$?
**Solution:** $1-(1-0.6)(1-0.25)=1-0.4\cdot0.75=0.7$.

### Q89 [Calc] Memberships: A=0.8, B=0.5, C=0.3. Score `(A AND B) OR C` and `A AND (B OR C)`.
**Solution:** $\max(\min(0.8,0.5),0.3)=\max(0.5,0.3)=0.5$.  
$\min(0.8,\max(0.5,0.3))=\min(0.8,0.5)=0.5$.

### Q90 [Why] Why is the term–term matrix awkward on a highly dynamic collection?
**Solution:** $c_{i,l}$ needs co-occurrence counts; updates are expensive — better estimate on a representative snapshot / thesaurus.

---

## Block C — Evaluation Heavy (Q91–Q110)

### Q91 [Calc] 🔥 Ranking `+ − − + + − − + − +`, $|R|=6$. AP? P@5? P@10?
**Solution:** Rel ranks 1,4,5,8,10 (5 found; 1 missing → contributes 0).  
P: $1/1,2/4,3/5,4/8,5/10$ = 1, 0.5, 0.6, 0.5, 0.5.  
AP=$(1+0.5+0.6+0.5+0.5+0)/6=3.1/6\approx0.517$.  
P@5=$3/5=0.6$; P@10=$5/10=0.5$.

### Q92 [Calc] Ranking `− + − + + + − −`, $|R|=5$. AP?
**Solution:** Ranks 2,4,5,6 → P: 0.5, 0.5, 0.6, 0.667. Sum≈2.267; /5 ≈0.453 (1 missing →0).

### Q93 [Calc] $(P,R)=(0.4,0.5)$ after 4 relevants found. Observed docs? $|R|$?
**Solution:** $4/(4+b)=0.4\Rightarrow4=0.4(4+b)\Rightarrow10=4+b\Rightarrow b=6$ → observed **10**.  
$4/(4+c)=0.5\Rightarrow8=4+c\Rightarrow c=4$ → $|R|=$ **8**.

### Q94 [Calc] $P=0.6$, $R=0.4$. $F_1$? Lecture $F$ with $\alpha=0.5$?
**Solution:** $F_1=2\cdot0.6\cdot0.4/(1.0)=0.48$. Same for $\alpha=0.5$: $PR/(0.5R+0.5P)=0.24/0.5=0.48$.

### Q95 [Calc] $P=0.8$, $R=0.2$, $\alpha=0.25$ in $F=\frac{PR}{(1-\alpha)R+\alpha P}$.
**Solution:** Denom=$(0.75)(0.2)+(0.25)(0.8)=0.15+0.2=0.35$; $F=0.16/0.35\approx0.457$.

### Q96 [Calc] Macro/micro: Q1 $a=2,b=8,c=8$; Q2 $a=8,b=2,c=2$. Macro P, Micro P?
**Solution:** P1=$2/10=0.2$, P2=$8/10=0.8$; macro $P=0.5$. Micro $P=(2+8)/(10+10)=0.5$ (here equal; not always).

### Q97 [Calc] Same, Macro R and Micro R.
**Solution:** R1=$2/10=0.2$, R2=$8/10=0.8$; macro R=0.5; micro R=$(2+8)/(10+10)=0.5$.

### Q98 [Calc] Change Q2 to $a=20,b=5,c=5$ (larger). Macro P vs Micro P?
**Solution:** P1=0.2, P2=$20/25=0.8$; macro=0.5. Micro=$(2+20)/(10+25)=22/35\approx0.629$ — **micro pulled up**.

### Q99 [Calc] 🔥 Grades `[3,1,2,0,4]`. DCG₅, IDCG₅, nDCG₅.
**Solution:** DCG=$3+1/\log_2 2+2/\log_2 3+0+4/\log_2 5=3+1+1.262+0+1.723\approx6.985$.  
Ideal `[4,3,2,1,0]`: IDCG=$4+3/\log_2 2+2/\log_2 3+1/2\approx4+3+1.262+0.5=8.762$.  
nDCG≈$6.985/8.762\approx0.797$.

### Q100 [Calc] Grades `[2,2,2,2]`. DCG₄?
**Solution:** $2+2/1+2/\log_2 3+2/2=2+2+1.262+1=6.262$.

### Q101 [Calc] Only first doc relevant grade 3, rest 0 for $p=4$. nDCG₄ if ideal is `[3,0,0,0]`?
**Solution:** DCG=IDCG=3 → nDCG=1.

### Q102 [SA] Why start DCG with $\mathrm{rel}_1$ outside the sum?
**Solution:** $\log_2 1=0$ would make $i=1$ term undefined/infinite; convention puts full credit at rank 1.

### Q103 [MCQ] MAP is closest to:
A) user looking only at first hit  
B) system-oriented average of APs  
C) efficiency metric  
**Answer:** B.

### Q104 [SA] Name two user-oriented alternatives to MAP mentioned in lectures.
**Solution:** P@5 / P@10; metrics emphasizing early precision; (graded) nDCG; stopping at first irrelevant, etc.

### Q105 [Why] Query expansion method for estimating recall tends to **overestimate** recall — why?
**Solution:** Expanded answer is still usually a **subset** of all relevants, but you treat it as denominator proxy → estimated $|R|$ too small → recall too high.

### Q106 [SA] What is GMAP and when prefer it over MAP?
**Solution:** Geometric mean of per-query APs; prefer when you care about **robustness** on hard queries (penalizes near-zero APs).

### Q107 [Compare] Navigational vs ad-hoc informational — pick one primary metric each.
**Solution:** Navigational: MRR or P@1. Informational ad-hoc: AP/MAP or nDCG.

### Q108 [Calc] Two systems' AP on 3 queries: S1 $(0.5,0.4,0.6)$, S2 $(0.9,0.9,0.1)$. MAP and which GMAP wins qualitatively?
**Solution:** MAP1=0.5, MAP2=$1.9/3\approx0.633$ — S2 higher MAP. GMAP2 hurt by 0.1 → S1 more robust.

### Q109 [MCQ] Pooling judges:
A) every document in the collection  
B) union of top results from many systems  
C) only random sample of non-hits  
**Answer:** B.

### Q110 [Scenario] Boss wants “one number” for a ranked search tool used on phones (small screen). Recommend metric + why.
**Solution:** **P@5** or **nDCG@5** — users rarely scroll; early precision / graded early gain matters more than full AP.

---

## Block D — NLP (Q111–Q118)

### Q111 [SA] Inflection hurdle for IR in one sentence.
**Solution:** Morphological variants of the same lemma fail exact string match → missed documents (recall↓) unless normalized.

### Q112 [MCQ] Porter stemmer is primarily:
A) dictionary lemmatization  
B) rule-based affix stripping  
C) neural seq2seq  
**Answer:** B.

### Q113 [Compare] German compounds vs English open compounds — main IR risk each?
**Solution:** German: undecomposed compounds → recall↓ for parts. English: splitting phrases → precision↓ (lose phrasal meaning).

### Q114 [SA] Precoordination vs postcoordination.
**Solution:** Pre: indexer combines concepts when indexing. Post: user combines at query time with operators.

### Q115 [SA] One pro and one con of character $n$-gram indexing.
**Solution:** Pro: language-independent / typo-robust. Con: larger index; hard to explain hits; possible precision loss.

### Q116 [MCQ] Removing stopwords on query "The Who":
A) always improves precision  
B) can destroy the query  
C) has no effect  
**Answer:** B.

### Q117 [SA] RDF triple example for “BTU locatedIn Cottbus”.
**Solution:** subject=`BTU`, predicate=`locatedIn`, object=`Cottbus` (as URIs ideally).

### Q118 [Why] Stemming usually raises recall — when can precision fall?
**Solution:** Overstemming merges unrelated words → spurious matches.

---

## Block E — VSM & Feedback (Q119–Q130)

### Q119 [Calc] 🔥 D1=$(1,0,1)$, D2=$(1,1,0)$, Q=$(1,1,0)$ raw dots?
**Solution:** $\langle Q,D1\rangle=1$, $\langle Q,D2\rangle=2$ → D2 higher.

### Q120 [Calc] L2-normalize D1,D2 from Q119; dots with raw Q=$(1,1,0)$?
**Solution:** $\|D1\|=\sqrt2$, unit D1=$(1/\sqrt2,0,1/\sqrt2)$; $\|D2\|=\sqrt2$, unit=$(1/\sqrt2,1/\sqrt2,0)$.  
Dots: D1: $1/\sqrt2\approx0.707$; D2: $2/\sqrt2=\sqrt2\approx1.414$ → D2 still wins.

### Q121 [Calc] $N=10000$. idf for $n=10,100,1000$ using $\ln$.
**Solution:** $\ln1000\approx6.91$; $\ln100\approx4.61$; $\ln10\approx2.30$.

### Q122 [Calc] Query terms with $tf=(1,2)$, max=2, idfs $(3.0,1.0)$. Salton $w_q$?
**Solution:** $w_1=(0.5+0.5\cdot1/2)\cdot3=(0.5+0.25)\cdot3=2.25$; $w_2=(0.5+0.5\cdot1)\cdot1=1.0$.

### Q123 [Algo] Ide regular vs Ide dec hi — formulas.
**Solution:** Regular: $Q+\sum F^+-\sum F^-$. Dec hi: $Q+\sum F^+ - D^{-}_{\mathrm{top\ ranked\ nonrel}}$.

### Q124 [Calc] $Q=(1,0,0)$, $D^+=(1,1,0)$, $D^-=(0,1,1)$, Rocchio $\beta=0.75,\alpha=0.25$ (one each). $Q'$?
**Solution:** $(1,0,0)+0.75(1,1,0)-0.25(0,1,1)=(1.75,\ 0.5,\ -0.25)$.

### Q125 [Why] Negative query coordinates after RF — meaning?
**Solution:** Query points away from that term's axis (downweight/avoid docs strong in that dimension).

### Q126 [MCQ] Cluster hypothesis says:
A) random docs are relevant  
B) similar docs tend to be relevant to the same requests  
C) PageRank equals TF–IDF  
**Answer:** B.

### Q127 [SA] Slope/pivoted normalization fixes what cosine side-effect?
**Solution:** Over-penalizing long documents / over-rewarding very short ones after full vector normalization.

### Q128 [Calc] old_norm=30, avg=50, slope=0.75 → $k_{fd}$?
**Solution:** $0.25+0.75\cdot(30/50)=0.25+0.45=0.70$.

### Q129 [Compare] Cosine vs dot product for ranking with fixed Q and unit doc vectors?
**Solution:** Same ranking (query norm constant; docs already length 1).

### Q130 [Scenario] First search mediocre; user ticks 3 good and 1 bad on page 1. What do you run?
**Solution:** Relevance feedback — preferably Ide dec hi or Rocchio; rebuild query; re-rank.

---

## Block F — LM, Probabilistic, BM25 (Q131–Q150)

### Q131 [Calc] Doc "to be or not to be" (6 tokens). MLE of "to"? of "be"? of "hamster"?
**Solution:** to=$2/6$; be=$2/6$; hamster=$0$.

### Q132 [Calc] JM $\omega=0.5$, $tf/|d|=0$, $P(t|c)=0.002$. $\hat P$?
**Solution:** $0.5\cdot0+0.5\cdot0.002=0.001$.

### Q133 [Calc] Dirichlet $\varepsilon=1000$, $|d|=1000$, $tf=2$, $cf/|c|=0.01$. $\hat P$?
**Solution:** $\frac{1000}{2000}\cdot\frac{2}{1000}+\frac{1000}{2000}\cdot0.01=0.001+0.005=0.006$.  
Or $\frac{2+1000\cdot0.01}{1000+1000}=\frac{12}{2000}=0.006$.

### Q134 [Why] Must we use $\sum\log\hat P$ instead of $\prod\hat P$?
**Solution:** Avoid floating-point **underflow**; logs turn products into sums; ranking preserved (monotonic).

### Q135 [MCQ] Query-likelihood ranks documents by:
A) $P(d\mid q)$ always  
B) $P(q\mid d)$ (with prior if used)  
C) cosine only  
**Answer:** B (or $P(q\mid d)P(d)$).

### Q136 [Calc] 🔥 BIR init $N=1000$, matched $n=10$ and $n=100$. Score ($\ln$)?
**Solution:** $\ln(990/10)+\ln(900/100)=\ln99+\ln9\approx4.595+2.197=6.792$.

### Q137 [Calc] After RF: $|V|=10$, term in 7 of V, $n_i=40$, $N=1000$. Unsmoothed $p_i,q_i$?
**Solution:** $p_i=7/10=0.7$; $q_i=(40-7)/(1000-10)=33/990\approx0.0333$.

### Q138 [Calc] Same with +0.5 smoothing.
**Solution:** $p=(7+0.5)/(10+1)=7.5/11\approx0.682$; $q=(33+0.5)/(990+1)=33.5/991\approx0.0338$.

### Q139 [Calc] BM25 TF factor: $tf=3$, $k_1=1.2$, $b=0.75$, $dl=avdl$. Value?
**Solution:** Denom=$1.2\cdot1+3=4.2$; num=$2.2\cdot3=6.6$; factor=$6.6/4.2\approx1.571$.

### Q140 [Calc] Same but $dl=2\cdot avdl$. Factor?
**Solution:** Length pivot $(1-0.75)+0.75\cdot2=1.75$; denom=$1.2\cdot1.75+3=5.1$; fac=$6.6/5.1\approx1.294$ (lower than short/avg).

### Q141 [Calc] $tf=10$, $k_1=1.2$, $dl=avdl$. TF factor? Compare to Q139.
**Solution:** Denom=$1.2+10=11.2$; num=$2.2\cdot10=22$; fac=$22/11.2\approx1.964$ — saturates; not 10/3× larger than tf=3.

### Q142 [Calc] BM25 IDF $N=5000$, $n=10$; and $n=3000$.
**Solution:** $\log\frac{5000-10+0.5}{10+0.5}=\log\frac{4990.5}{10.5}>0$.  
$n=3000$: $\log\frac{2000.5}{3000.5}<0$ → clip to 0 typically.

### Q143 [SA] Role of $k_3$ in BM25?
**Solution:** Saturating normalization of **query** term frequency (important for long queries).

### Q144 [Compare] BIR vs BM25 in one line each.
**Solution:** BIR: binary RSJ log-odds, needs RF to shine. BM25: TF saturation + length + RSJ-style IDF — strong default ranking.

### Q145 [MCQ] If $b=0$ in BM25:
A) no length normalization  
B) no IDF  
C) binary TF  
**Answer:** A.

### Q146 [Calc] Naive Bayes add-one: term count 0, $|text_c|=100$, $|V|=1000$. $\hat P(t|c)$?
**Solution:** $(0+1)/(100+1000)=1/1100$.

### Q147 [Why] LM has no built-in relevance feedback like Rocchio — implication?
**Solution:** Need separate mechanisms (expansion, mixture models, etc.); can't just subtract vectors.

### Q148 [Scenario] Short web queries, need strong baseline tomorrow — choose?
**Solution:** **BM25** (or LM+Dirichlet); evaluate P@10 / nDCG.

### Q149 [Long] Derive in 5–7 lines why unsmoothed query likelihood fails for long queries.
**Solution:** Product over query terms; any term missing in $d$ ⇒ MLE factor 0 ⇒ entire $P(q|d)=0$; longer queries raise chance of ≥1 unseen term ⇒ many docs incorrectly score 0; smoothing gives unseen terms background mass.

### Q150 [Calc] Three query terms with smoothed probs 0.1, 0.05, 0.02. $\log P(q|d)$ natural log sum?
**Solution:** $\ln0.1+\ln0.05+\ln0.02\approx -2.303-2.996-3.912=-9.211$.

---

## Block G — Clustering, PageRank, Modern (Q151–Q165)

### Q151 [Calc] Vectors $A=(1,1,0)$, $B=(1,0,1)$. Dice and Jaccard (weighted formulas)?
**Solution:** Dot=1; $\|A\|^2=2$, $\|B\|^2=2$. Dice=$2\cdot1/(2+2)=0.5$. Jaccard=$1/(2+2-1)=1/3$.

### Q152 [SA] Single-link chaining problem in one sentence.
**Solution:** Clusters merge via a single close pair, forming elongated chains that absorb dissimilar points.

### Q153 [MCQ] Complete-link uses inter-cluster similarity:
A) max  
B) min  
C) PageRank  
**Answer:** B.

### Q154 [Algo] One iteration of reallocation clustering.
**Solution:** Assign each doc to nearest centroid; recompute centroids; repeat until stable.

### Q155 [Compare] Classification vs clustering for library access.
**Solution:** Classification: labeled schemes (UDC/IPC), browsable names. Clustering: automatic, cheaper labels implicit (centroid doc), no standard codes.

### Q156 [SA] UDC symbol `:` means?
**Solution:** Relation between concepts (symmetric relation facet).

### Q157 [Calc] Tiny PageRank step: pages X→Y, X→Z, Y→Z. Equal start $R=1$ each, $\varepsilon=0.15$, one simplified update for Z receiving from X and Y...  
(Illustrative) $R'(Z)=0.15+(0.85)(R(X)/2+R(Y)/1)$. If $R=1$: $0.15+0.85(0.5+1)=0.15+1.275=1.425$.
**Solution:** As above (course uses $\varepsilon$ form equivalently).

### Q158 [Why] PageRank is not topical relevance.
**Solution:** It estimates link-based popularity/authority independent of the query topic (unless topic-biased variants).

### Q159 [SA] RAG: sparse vs dense retrieval examples.
**Solution:** Sparse: BM25/TF–IDF. Dense: embedding similarity (bi-encoders).

### Q160 [MCQ] Main RAG benefit for QA:
A) smaller GPUs only  
B) grounds generation in retrieved evidence  
C) removes need for an index  
**Answer:** B.

### Q161 [SA] Shneiderman mantra.
**Solution:** Overview first, zoom and filter, then details on demand.

### Q162 [Why] Hypertext browsing alone fails for large webs.
**Solution:** Easy to get lost; no global ranked relevance; need search + structure.

### Q163 [Compare] Dice vs cosine — when similar?
**Solution:** Both normalize overlapping mass; Dice uses sum of squares in denom differently from cosine's product of norms — related but not identical rankings always.

### Q164 [Scenario] Result set of 500 Boolean hits — how help user?
**Solution:** Cluster the **result set**; show representative docs per cluster; or facet/classify.

### Q165 [SA] Name two quality signals besides PageRank.
**Solution:** Freshness, availability, popularity/clicks, authority labels, cohesion/density, spam scores.

---

## Block H — Mixed “Exam Style” Quickfire (Q166–Q180)

### Q166 [MCQ] Harmonic mean of 1 and 0 is:
A) 0.5  
B) 0  
C) 1  
**Answer:** B — why $F$ collapses if $P$ or $R$ is 0.

### Q167 [Calc] AP for ranking where all 4 relevants are at ranks 1–4. $|R|=4$?
**Solution:** P always 1 → AP=1.

### Q168 [Calc] All 4 relevants at ranks 97–100, $|R|=4$. AP?
**Solution:** $P=1/97+2/98+3/99+4/100$ all /4 ≈ $(0.0103+0.0204+0.0303+0.04)/4\approx0.0253$.

### Q169 [SA] False drop vs miss (Boolean).
**Solution:** False drop: retrieved but irrelevant / signature false alarm. Miss: relevant not retrieved ($c$ in contingency).

### Q170 [Calc] Contingency $a=5,b=5,c=15$. $P$, $R$, $F_1$?
**Solution:** $P=0.5$, $R=5/20=0.25$, $F_1=2\cdot0.5\cdot0.25/0.75=0.333$.

### Q171 [Why] Micro averaging can disagree with users' average experience.
**Solution:** Queries with huge result sets dominate micro; a user cares equally about each query (macro).

### Q172 [Algo] Steps to compute nDCG@p for one query.
**Solution:** Take top-$p$ grades → DCG; sort those grades desc → IDCG; divide; (sometimes ideal uses all known relevants — follow statement).

### Q173 [Calc] $p$-norm OR $x=(1,0)$, $p=1$ and $p=\infty$.
**Solution:** Both: $p=1$ → $0.5$; $p=\infty$ → $1$.

### Q174 [SA] What does BM25 do when $tf\to\infty$?
**Solution:** TF component → $k_1+1$ (saturation ceiling).

### Q175 [MCQ] Ide dec hi subtracts:
A) all nonrelevants  
B) centroid of nonrelevants  
C) the highest-ranked nonrelevant  
**Answer:** C.

### Q176 [Calc] Fuzzy score $t_1\wedge t_2$ with $\mu=(0.9,0.1)$ vs $(0.6,0.6)$ — which doc wins?
**Solution:** $\min$ → 0.1 vs 0.6 → **second wins** (dominance: first weak on $t_2$).

### Q177 [SA] List Cranfield's six evaluation criteria (keywords enough).
**Solution:** Recall, precision, time lag, effort, form of presentation, coverage.

### Q178 [Compare] Efficiency vs effectiveness with one IR example.
**Solution:** Faster index (efficiency) that returns worse AP (effectiveness) is not “better” for search quality goals.

### Q179 [Long] 8–10 lines: design an exam answer comparing VSM, LM, BM25.
**Solution:** Cover representation (tf-idf vectors / unigram LM / TF+IDF BM25); ranking (cosine / $P(q|d)$ / BM25 sum); theory (heuristic / generative / probabilistic-eng); RF (Rocchio native / weak / BIR-style); practice (all strong; BM25 default). Use a table if allowed.

### Q180 [Scenario] You have 90 minutes left in a 120-min exam, 55 marks undone, half are calculations. Plan.
**Solution:** Sweep all remaining 🔥 calcs first (≈40 min); then short definitions (15); one structured long answer (20); 5–10 min check AP/$|R|$ and IDCG sorts; leave lowest-value fluff.

---

# 24. Timed Sprint Sets (40 min each)

Do **closed-book**. Score roughly: Calc 2 pts, SA 2, MCQ 1, Long 8. Target ≥70% before Mock 2.

## Sprint 1 — Evaluation + Fuzzy (40 min)

Do: Q91, Q92, Q93, Q94, Q99, Q87, Q88, Q89, Q18, Q23, Q95, Q98, Q170, Q176, plus write AP definition from memory.

## Sprint 2 — VSM + BM25 + BIR (40 min)

Do: Q119–Q124, Q128, Q136–Q142, Q33, Q42, Q44, Q139–Q141, D6–D7 from Appendix A.

## Sprint 3 — Models & Algorithms (40 min)

Do: Q63, Q76–Q81, Q83–Q86, Q123, Q154, Q4, Q10, write Boolean AND merge + S-tree search steps + BM25 formula from memory.

## Sprint 4 — Mixed Exam Simulation Lite (40 min ≈ 35 marks)

1. AP calc (new): ranking `+ − + + − − +`, $|R|=5$ (8 marks)  
2. nDCG grades `[1,4,0,3]` @4 (8)  
3. BIR init $N=2000$, $n\in\{25,200\}$ matched both (6)  
4. Fuzzy $c$ with 5,8,3 co-occ. + $\mu$ for singleton doc (6)  
5. Compare BM25 vs VSM (7)

**Sprint 4 quick solutions:**  
1. Ranks 1,3,4,7 → P:1, 2/3, 3/4, 4/7 → AP=$(1+0.667+0.75+0.571)/5\approx0.598$.  
2. DCG=$1+4/1+0/\log_2 3+3/2=1+4+0+1.5=6.5$; ideal `[4,3,1,0]`: $4+3+1/\log_2 3\approx7.631$; nDCG≈0.852.  
3. $\ln\frac{1975}{25}+\ln\frac{1800}{200}=\ln79+\ln9$.  
4. $c=3/(5+8-3)=3/10$; $\mu=0.3$ if only other term.  
5. See comparison tables in §17.

---

# 25. Mock Exam 2 (120 min / 100 marks)

**Closed book. Write formulas before numbers.**

### Section A — Short (20 marks)

**A1 (4)** Data vs knowledge vs information.  
**A2 (4)** False drop: definition + two causes.  
**A3 (4)** Overstemming vs understemming.  
**A4 (4)** Dirichlet vs Jelinek–Mercer (one key difference).  
**A5 (4)** Single-link vs complete-link.

### Section B — Calculations (40 marks)

**B1 (10)** Ranking `− + + − + − + +`, $|R|=7$.  
(a) Precision at each relevant hit + recall. (b) AP. (c) P@5.

**B2 (8)** Grades `[0,3,3,1,2,0]`, $p=6$: DCG, IDCG, nDCG.

**B3 (8)** $N=2000$, vocab terms idf via $\ln(N/n)$ with $n=(20,200,400)$.  
D has tfs $(2,0,1)$, Q tfs $(1,1,0)$.  
Raw tf–idf dot product of D and Salton-weighted Q (max q-tf=1). Document **not** length-normalized.

**B4 (7)** BM25: only one query term, $tf_{qi}=1$ so query factor=1.  
$N=10000$, $n=50$, $tf_d=4$, $k_1=1.2$, $b=0.75$, $dl=avdl$. Numeric score using $\ln$ for IDF.

**B5 (7)** Fuzzy: $c_{12}=0.5$, $c_{13}=0.5$, $c_{23}=0.2$ (diags 1).  
$D=\{t_1,t_3\}$. Compute $\mu_2(D)$. Score query $t_2 \vee (t_1 \wedge t_3)$ using also $\mu_1(D)$ and $\mu_3(D)$ (compute all three).

### Section C — Algorithms (20 marks)

**C1 (7)** Pseudocode: intersect three sorted postings for `A AND B AND C` efficiently.  
**C2 (7)** Explain bit-sliced signature query for one word with weight $m$. Pros/cons vs SSF.  
**C3 (6)** Rocchio + when to prefer Ide dec hi.

### Section D — Essays (20 marks)

**D1 (10)** Effectiveness evaluation toolkit: P/R/F, AP/MAP, nDCG, P@k — when each.  
**D2 (10)** From Boolean enterprise search to modern stack (NLP → BM25/LM → feedback → optional RAG). Risks.

---

## Mock Exam 2 — Solutions

### A
**A1:** Data raw symbols; knowledge organized content; information = knowledge for a need.  
**A2:** Signature condition holds but term absent; collisions; superposition OR.  
**A3:** Over→same stem different concepts (P↓); under→missed conflation (R↓).  
**A4:** Dirichlet mixing depends on $|d|$; JM uses fixed $\omega$.  
**A5:** Single=max link (chains); complete=min link (compact).

### B
**B1** Ranks: 2,3,5,7,8 (5 of 7).  
P: $1/2,2/3,3/5,4/7,5/8$ = 0.5, 0.667, 0.6, 0.571, 0.625.  
R: $1/7\ldots5/7$.  
AP=$(0.5+0.667+0.6+0.571+0.625)/7\approx2.963/7\approx0.423$.  
P@5=$3/5=0.6$.

**B2** DCG=$0+3/\log_2 2+3/\log_2 3+1/2+2/\log_2 5+0=0+3+1.893+0.5+0.861\approx6.254$.  
Ideal `[3,3,2,1,0,0]`: $3+3+2/\log_2 3+0.5\approx3+3+1.262+0.5=7.762$.  
nDCG≈$6.254/7.762\approx0.806$.

**B3** idf≈$(\ln100,\ln10,\ln5)\approx(4.605,2.303,1.609)$.  
D tf-idf≈$(2\cdot4.605,\ 0,\ 1\cdot1.609)=(9.21,0,1.609)$.  
Q Salton: $(1\cdot4.605,\ 1\cdot2.303,\ 0)=(4.605,2.303,0)$.  
Dot≈$9.21\cdot4.605\approx42.41$.

**B4** IDF=$\ln\frac{10000-50+0.5}{50+0.5}=\ln\frac{9950.5}{50.5}\approx\ln197.04\approx5.283$.  
TF fac: denom=$1.2+4=5.2$; num=$2.2\cdot4=8.8$; fac=$8.8/5.2\approx1.692$.  
Score≈$5.283\cdot1.692\approx8.94$.

**B5** $\mu_2=1-(1-c_{21})(1-c_{23})=1-(1-0.5)(1-0.2)=1-0.5\cdot0.8=0.6$.  
$\mu_1=1-(1-1)(1-0.5)=1$ (has $t_1$).  
$\mu_3=1-(1-0.5)(1-1)=1$.  
$t_1\wedge t_3=\min(1,1)=1$; $t_2\vee\ldots=\max(0.6,1)=1$.

### C
**C1:** Multi-pointer merge: advance the list with smallest head; emit when all heads equal; or intersect pairwise smallest-first. $O(|L_A|+|L_B|+|L_C|)$.  
**C2:** Read $m$ bit files for set positions; AND bitvectors; candidates → verify. Less read vs SSF on search; updates expensive.  
**C3:** Rocchio weighted centroids; Ide dec hi if nonrel heterogeneous / Salton evidence.

### D (outline)
**D1:** Set retrieval→P/R/F; ranked binary→AP/MAP; graded→nDCG; UI→P@k.  
**D2:** Tokenize/stem carefully→BM25 on inverted index→label queries for P@10/AP→RF→RAG for NL answers; keep Boolean expert mode; watch overstemming & hallucination if retrieval fails.

**Scoring:** 85+ excellent; 70–84 solid; <70 drill Sprints 1–2 again same day.

---


*End of guide. Built from BTU IR lectures (Schmitt), exercises EX01–EX04, and Henrich-aligned formulations. Good luck.*
