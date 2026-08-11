# GATE CSE — Discrete Mathematics Handbook
## PART 1 of 8: Logic, Sets, Relations

---

## 0. COMPLETE SYLLABUS CHECKLIST (all 8 parts of this handbook)

**Part 1 (this file): Logic + Sets + Relations**
- [ ] Propositions, operators, truth tables
- [ ] Tautology / contradiction / contingency
- [ ] Logical equivalence, laws of logic, De Morgan's
- [ ] Implication, converse, inverse, contrapositive
- [ ] Necessary/sufficient conditions
- [ ] Normal forms: DNF, CNF, PDNF, PCNF
- [ ] Rules of inference
- [ ] Predicates, quantifiers, nested quantifiers, negation
- [ ] First order logic basics
- [ ] Set notation, subset, power set, cardinality, Cartesian product
- [ ] Set operations, identities, De Morgan's (sets), inclusion-exclusion
- [ ] Binary relations, domain/range
- [ ] Reflexive, irreflexive, symmetric, antisymmetric, asymmetric, transitive
- [ ] Equivalence relation, equivalence classes
- [ ] Partial order, relation matrix, relation graph
- [ ] Composition, inverse relation, transitive closure, Warshall's algorithm

**Part 2 (next file): Functions + Posets/Lattices + Groups/Monoids**
**Part 3: Graph Theory + Combinatorics**
**Part 4: Recurrence Relations + Generating Functions + Formula Sheet + Must-Remember Theorems**
**Part 5: Verified GATE PYQ analysis (topic-wise)**
**Part 6: Practice Sets A–D (120 Qs) + Answer Keys + Solutions**
**Part 7: 50-Question Mixed Mock Test + Solutions**
**Part 8: Traps Sheet + One-Page Revisions (7 topics) + 14-Day Study Plan + 7-Day Emergency Plan**

Priority tags used throughout: 🔴 HIGH PRIORITY (almost every GATE year) · 🟡 MEDIUM · 🟢 LOW (occasional)

---

# PART A — MATHEMATICAL LOGIC

## A.1 Propositions

**Concept:** A proposition is a declarative sentence that is either **True (T) or False (F)**, never both.

**Intuition:** "Is it a factual claim I can judge True/False?" If yes → proposition. Questions, commands, opinions ("Maths is fun") are NOT propositions.

**Formal definition:** A proposition $p$ is a statement with a fixed truth value $\in \{T, F\}$.

**Examples:**
- "5 is a prime number" → proposition (T)
- "Close the door" → NOT a proposition (command)
- "x + 1 = 5" → NOT a proposition (depends on x, unless x is fixed) — this becomes a **predicate**

**GATE trap 🔴:** Statements with variables (open sentences) are not propositions until quantified/bound. "x > 3" is a predicate, not a proposition.

**Quick revision:** Proposition = declarative + has a definite truth value.

---

## A.2 Logical Operators & Truth Tables 🔴

| Operator | Symbol | Name | Read as |
|---|---|---|---|
| NOT | ¬p | Negation | "not p" |
| AND | p∧q | Conjunction | "p and q" |
| OR | p∨q | Disjunction | "p or q" |
| XOR | p⊕q | Exclusive OR | "exactly one" |
| IMPLIES | p→q | Conditional | "if p then q" |
| IFF | p↔q | Biconditional | "p iff q" |

**Truth table (master table — memorize this):**

```
p   q   ¬p  p∧q  p∨q  p⊕q  p→q  p↔q
T   T   F    T    T    F    T    T
T   F   F    F    T    T    F    F
F   T   T    F    T    T    T    F
F   F   T    F    F    F    T    T
```

**Key intuition for p→q:** "False implies anything" — p→q is **only False** when p=T and q=F. It's a very common GATE trap: p→q is TRUE whenever p is FALSE (vacuously true).

**Common trap 🔴:** Students think p→q means "p causes q." It doesn't — it's just a truth-table rule. `F → F = T` and `F → T = T` confuse most beginners.

**Practice:**
1. Construct truth table for (p∧¬q) → r
2. Is p⊕q the same as ¬(p↔q)? (Yes — prove using truth table)

---

## A.3 Tautology, Contradiction, Contingency

| Term | Meaning | Example |
|---|---|---|
| Tautology | Always TRUE regardless of inputs | p∨¬p |
| Contradiction | Always FALSE regardless of inputs | p∧¬p |
| Contingency | Sometimes T, sometimes F | p→q |

**GATE-level example:** Show `(p→q)∧(q→r) → (p→r)` is a tautology (this is the **Hypothetical Syllogism** law — very frequently tested).

**Trap 🔴:** A formula being "true for the row you tried" doesn't make it a tautology — you must check ALL rows (2ⁿ rows for n variables).

---

## A.4 Logical Equivalence & Laws of Logic 🔴

**Concept:** p ≡ q means p and q have identical truth tables (p↔q is a tautology).

**Laws of Logic (memorize all — GATE loves simplification questions):**

| Law | Form |
|---|---|
| Identity | p∧T ≡ p, p∨F ≡ p |
| Domination | p∨T ≡ T, p∧F ≡ F |
| Idempotent | p∨p ≡ p, p∧p ≡ p |
| Double negation | ¬¬p ≡ p |
| Commutative | p∨q ≡ q∨p |
| Associative | (p∨q)∨r ≡ p∨(q∨r) |
| Distributive | p∨(q∧r) ≡ (p∨q)∧(p∨r) |
| De Morgan's | ¬(p∧q) ≡ ¬p∨¬q ; ¬(p∨q) ≡ ¬p∧¬q |
| Absorption | p∨(p∧q) ≡ p ; p∧(p∨q) ≡ p |
| Negation | p∨¬p ≡ T ; p∧¬p ≡ F |
| Conditional identity | p→q ≡ ¬p∨q |
| Biconditional identity | p↔q ≡ (p→q)∧(q→p) ≡ (p∧q)∨(¬p∧¬q) |

**GATE-level example:** Simplify `¬(p∨q)∨(¬p∧q)`
= (¬p∧¬q)∨(¬p∧q) [De Morgan's]
= ¬p∧(¬q∨q) [Distributive]
= ¬p∧T = ¬p

**Trap 🔴:** `p→q ≡ ¬p∨q` is THE most useful identity for simplification questions — always convert → into ∨ form first when simplifying.

---

## A.5 Implication, Converse, Inverse, Contrapositive 🔴

Given `p → q`:

| Name | Form | Logically equivalent to original? |
|---|---|---|
| Original | p→q | — |
| Converse | q→p | NO |
| Inverse | ¬p→¬q | NO |
| Contrapositive | ¬q→¬p | **YES** (always ≡ p→q) |

**Trap 🔴 (very frequently tested):** Converse ≡ Inverse (they're contrapositives of each other), but neither equals the original. Only **Contrapositive ≡ Original**.

**Example:** "If it rains, the ground is wet" (p→q)
- Converse: "If ground is wet, it rains" (not necessarily true — sprinkler could wet it)
- Contrapositive: "If ground is not wet, it didn't rain" (logically same as original)

---

## A.6 Necessary & Sufficient Conditions

- p→q: **p is sufficient for q**, **q is necessary for p**.
- p↔q: p is necessary AND sufficient for q.

**Trap:** "q is necessary for p" is written as p→q, NOT q→p. Students frequently flip this.

---

## A.7 Normal Forms: DNF, CNF, PDNF, PCNF 🔴

| Form | Full name | Structure |
|---|---|---|
| DNF | Disjunctive Normal Form | OR of AND terms: (p∧q)∨(¬p∧r) |
| CNF | Conjunctive Normal Form | AND of OR terms: (p∨q)∧(¬p∨r) |
| PDNF | Principal DNF | DNF where every term (minterm) contains ALL variables |
| PCNF | Principal CNF | CNF where every term (maxterm) contains ALL variables |

**How to find PDNF (step-by-step):**
1. Build the truth table.
2. For every row where output = T, write a minterm (AND of all variables, using variable if T, negation if F).
3. OR all minterms together.

**How to find PCNF:**
1. For every row where output = F, write a maxterm (OR of all variables, using variable if F, negation if T).
2. AND all maxterms together.

**GATE-level example:** Find PDNF of p→q.
Truth table: (T,T)=T, (T,F)=F, (F,T)=T, (F,F)=T
Minterms for T rows: (p∧q), (¬p∧q), (¬p∧¬q)
PDNF = (p∧q)∨(¬p∧q)∨(¬p∧¬q)

**Trap 🔴:** PDNF/PCNF of the SAME formula, for the SAME variable order, is **unique**. Number of terms in PDNF = number of T's in the truth table (2ⁿ rows total).

---

## A.8 Rules of Inference 🔴

| Rule | Form |
|---|---|
| Modus Ponens | p, p→q ⊢ q |
| Modus Tollens | ¬q, p→q ⊢ ¬p |
| Hypothetical Syllogism | p→q, q→r ⊢ p→r |
| Disjunctive Syllogism | p∨q, ¬p ⊢ q |
| Addition | p ⊢ p∨q |
| Simplification | p∧q ⊢ p |
| Conjunction | p, q ⊢ p∧q |
| Resolution | p∨q, ¬p∨r ⊢ q∨r |

**Trap 🔴:** Confusing Modus Ponens (p, p→q ⊢ q) with the **fallacy** "affirming the consequent" (q, p→q ⊢ p — this is INVALID).

---

## A.9 Predicates & Quantifiers 🔴

**Concept:** A predicate P(x) becomes a proposition only after quantifying x over a domain.

| Symbol | Name | Meaning |
|---|---|---|
| ∀x P(x) | Universal | P(x) true for ALL x in domain |
| ∃x P(x) | Existential | P(x) true for AT LEAST ONE x |

**Negation rules (very frequently tested) 🔴:**

```
¬(∀x P(x))  ≡  ∃x ¬P(x)
¬(∃x P(x))  ≡  ∀x ¬P(x)
```

**Nested quantifiers — order MATTERS:**
- `∀x ∃y P(x,y)` — for every x, SOME y exists (y can depend on x)
- `∃y ∀x P(x,y)` — SOME single y works for every x (much stronger claim)

**GATE trap 🔴:** `∀x∃y` and `∃y∀x` are NOT equivalent. Example: P(x,y) = "y > x" over integers.
- ∀x∃y (y>x): TRUE (for any x, pick y=x+1)
- ∃y∀x (y>x): FALSE (no single y is bigger than all integers)

**Negating nested quantifiers:**
`¬(∀x∃y P(x,y)) ≡ ∃x∀y ¬P(x,y)` — flip every quantifier AND negate the predicate.

**Quick revision:** To negate a fully quantified statement: flip ∀↔∃ at every position, then negate the innermost predicate.

---

# PART B — SETS

## B.1 Notation, Subsets, Power Set

**Concept:** A set is an unordered collection of distinct elements.

| Notation | Meaning |
|---|---|
| x ∈ A | x is an element of A |
| A ⊆ B | A is a subset of B (every element of A is in B) |
| A ⊂ B | A is a proper subset (A⊆B and A≠B) |
| ∅ | empty set |
| P(A) | power set = set of ALL subsets of A |
| \|A\| | cardinality (number of elements) |

**Key formula 🔴:** If \|A\| = n, then \|P(A)\| = 2ⁿ.

**Why (derivation):** Each element has 2 choices — "include" or "exclude" — from the subset being formed. n independent binary choices → 2ⁿ total subsets.

**Trap:** ∅ ∈ P(A) always (empty set is a subset of every set), and A ∈ P(A) always. Students often forget these two are always subsets.

## B.2 Cardinality & Cartesian Product

**Cartesian product:** A×B = {(a,b) : a∈A, b∈B}. **|A×B| = |A|·|B|**.

**Trap:** A×B ≠ B×A (order matters — it's a set of ordered pairs).

## B.3 Set Operations & Identities

| Operation | Symbol | Meaning |
|---|---|---|
| Union | A∪B | elements in A or B |
| Intersection | A∩B | elements in both |
| Difference | A−B | in A but not B |
| Complement | A' or Aᶜ | not in A (w.r.t. universal set U) |
| Symmetric difference | A⊕B | (A−B)∪(B−A) |

**De Morgan's Laws (sets) 🔴:**
```
(A∪B)' = A' ∩ B'
(A∩B)' = A' ∪ B'
```

**Identities (same skeleton as logic laws — sets and logic are isomorphic):**
Identity, Domination, Idempotent, Complement, Distributive, Associative, Commutative, Absorption — all hold exactly like Part A.4 (∪↔∨, ∩↔∧, complement↔¬).

## B.4 Inclusion-Exclusion Principle 🔴

**2-set formula:** |A∪B| = |A| + |B| − |A∩B|

**3-set formula:** |A∪B∪C| = |A|+|B|+|C| − |A∩B|−|B∩C|−|A∩C| + |A∩B∩C|

**Why it works (intuition):** When you add |A|+|B|+|C|, the pairwise-overlap regions get counted twice, so subtract them once; but the triple-overlap region gets added 3 times then subtracted 3 times (net zero), so add it back once.

**GATE-level example:** In a class of 100, 60 like Maths, 50 like Physics, 30 like both. How many like neither?
|M∪P| = 60+50−30 = 80 → Neither = 100−80 = **20**

**Trap 🔴:** "At least one" → use union directly. "Exactly one" → |A|+|B|−2|A∩B| (for 2 sets). "Neither" → total − |union|.

### B.5 — 20 Practice Questions (Sets)

1. If |A|=5, find |P(A)|.
2. If A⊆B, simplify A∪B and A∩B.
3. Prove (A−B)∪(A∩B) = A.
4. If |A|=3, |B|=4, |A∩B|=2, find |A∪B|.
5. Is (A∪B)−C = (A−C)∪(B−C)? Prove or disprove.
6. Find |A×B| if |A|=3, |B|=5.
7. How many subsets of {1,2,3,4,5} contain exactly 2 elements?
8. Prove A−(B∪C) = (A−B)∩(A−C).
9. If A∩B=∅, what is |A∪B|?
10. In a survey of 200 people: 120 read newspaper X, 90 read Y, 40 read both. How many read neither?
11. Prove A⊕B = (A∪B)−(A∩B).
12. Is the power set operation distributive over union? P(A∪B) vs P(A)∪P(B) — check with example.
13. If |A|=4, how many proper subsets does A have?
14. Prove De Morgan's law (A∪B)'=A'∩B' using element-chasing method.
15. Three sets A,B,C with |A|=50,|B|=40,|C|=30,|A∩B|=10,|B∩C|=8,|A∩C|=5,|A∩B∩C|=2. Find |A∪B∪C|.
16. Show A∩(B∪C) = (A∩B)∪(A∩C).
17. If A has n elements, how many ordered pairs (X,Y) exist with X,Y⊆A and X∩Y=∅?
18. Prove: A⊆B ⟺ A∪B=B ⟺ A∩B=A.
19. Find the number of relations possible from set A(|A|=3) to set B(|B|=4). (Hint: subsets of A×B)
20. If U has 10 elements and A has 4, find |A'|.

---

# PART C — RELATIONS

## C.1 Binary Relations, Domain & Range

**Concept:** A relation R from A to B is any subset of A×B. If A=B, it's a relation ON A.

**Notation:** aRb means (a,b)∈R.

**Domain** = set of first elements actually appearing; **Range** = set of second elements actually appearing.

## C.2 Properties of Relations (on a set A) 🔴

| Property | Definition | Example (A={1,2,3}) | Counterexample |
|---|---|---|---|
| Reflexive | ∀a∈A, (a,a)∈R | R={(1,1),(2,2),(3,3),(1,2)} | R missing (2,2) is NOT reflexive |
| Irreflexive | ∀a∈A, (a,a)∉R | R={(1,2),(2,3)} | R with even one (a,a) fails |
| Symmetric | (a,b)∈R ⟹ (b,a)∈R | R={(1,2),(2,1)} | R={(1,2)} only — not symmetric |
| Antisymmetric | (a,b)∈R ∧ (b,a)∈R ⟹ a=b | R={(1,1),(1,2)} (no (2,1)) | R={(1,2),(2,1)}, 1≠2 — fails |
| Asymmetric | (a,b)∈R ⟹ (b,a)∉R (and no (a,a) allowed) | R={(1,2)} | R={(1,1)} fails (asymmetric forbids (a,a)) |
| Transitive | (a,b)∈R ∧ (b,c)∈R ⟹ (a,c)∈R | R={(1,2),(2,3),(1,3)} | R={(1,2),(2,3)} missing (1,3) — fails |

**Traps 🔴 (extremely high-frequency GATE traps):**
- **Symmetric vs Antisymmetric are NOT opposites.** A relation can be BOTH (e.g., R={(1,1),(2,2)}) or NEITHER (e.g., R={(1,2),(2,3)}).
- **Asymmetric ⟹ Irreflexive**, but irreflexive does NOT imply asymmetric.
- Empty relation ∅ is vacuously symmetric, antisymmetric, AND transitive (no pairs to violate any condition) — but NOT reflexive (unless A=∅).

**Relation matrix trick:** Reflexive → diagonal all 1s. Symmetric → matrix = its transpose. Antisymmetric → for i≠j, not both M[i][j]=1 and M[j][i]=1.

## C.3 Equivalence Relations & Equivalence Classes 🔴

**Concept:** R is an equivalence relation if it is Reflexive + Symmetric + Transitive.

**Equivalence class of a:** [a] = {x∈A : xRa}

**Key theorem:** Equivalence classes **partition** the set A — they are pairwise disjoint and their union is A.

**Example:** "Same remainder mod 3" on integers → 3 equivalence classes: [0],[1],[2].

**GATE trap 🔴:** Number of equivalence relations on an n-set = number of **partitions** of the set = Bell number B(n). For n=3, B(3)=5.

## C.4 Partial Order Relations

**Concept:** R is a partial order if Reflexive + Antisymmetric + Transitive. (Detailed treatment with Hasse diagrams comes in Part 2 — Posets & Lattices.)

## C.5 Composition & Inverse

**Composition:** R∘S (or S;R depending on convention — GATE usually uses: if R:A→B, S:B→C, then S∘R:A→C, (a,c)∈S∘R iff ∃b: (a,b)∈R ∧ (b,c)∈S).

**Inverse:** R⁻¹ = {(b,a) : (a,b)∈R}. Domain/range swap.

**Trap:** Composition order convention varies by textbook — GATE questions usually spell it out explicitly; always check which "applies first."

## C.6 Transitive Closure & Warshall's Algorithm 🔴

**Concept:** Transitive closure R⁺ = smallest transitive relation containing R (add all "indirectly reachable" pairs).

**Warshall's Algorithm (matrix-based, GATE favorite):**
Start with adjacency matrix M. For k=1 to n:
```
for i = 1 to n:
  for j = 1 to n:
    M[i][j] = M[i][j] OR (M[i][k] AND M[k][j])
```
This means: "can I reach j from i by passing through k?"

**GATE-level example:** R = {(1,2),(2,3),(3,1)} on {1,2,3}. This is a 3-cycle → transitive closure connects EVERY pair, i.e., R⁺ = A×A (full relation), since you can reach any node from any node by going around the cycle.

**Trap 🔴:** Transitive closure is about **reachability** in the relation-graph — equivalent to asking "is there a path (of any length ≥1) from a to b?"

### C.7 — Matrix & Graph-Based Practice Questions

1. Given R={(1,1),(1,2),(2,3),(3,3)} on {1,2,3}, check reflexive/symmetric/antisymmetric/transitive.
2. Draw the relation graph for R={(a,b),(b,c),(c,a)} and find its transitive closure.
3. Write the relation matrix for R = "divides" on {1,2,3,4,6}.
4. How many symmetric relations are possible on a set of size n? (Hint: 2^(n(n+1)/2))
5. How many reflexive relations are possible on a set of size n? (Hint: 2^(n²−n))
6. How many relations are BOTH reflexive and symmetric on an n-set?
7. Find equivalence classes of "same parity" on {1,2,...,10}.
8. Apply Warshall's algorithm step-by-step for R={(1,2),(2,3),(3,4)} on {1,2,3,4}.
9. Is "≤" on integers a partial order? Justify each property.
10. If R is symmetric and transitive but NOT reflexive on all of A, can R still be called an equivalence relation on some subset of A? Explain with example.

---

**End of Part 1.** This covers Logic (complete) + Sets (complete) + Relations (complete) at GATE depth.

Next file (Part 2) will cover: **Functions, Posets & Lattices, Monoids & Groups** — same teaching structure, with Hasse diagram problems and group-theory counterexample tables.

Bata jab ready ho Part 2 ke liye, ya agar is Part 1 me kahin aur depth/examples chahiye to bhi bata sakta hai.
