# GATE CSE — Discrete Mathematics Handbook
## PART 2 of 8: Functions, Posets & Lattices, Monoids & Groups

Priority tags: 🔴 HIGH PRIORITY · 🟡 MEDIUM · 🟢 LOW

---

# PART D — FUNCTIONS

## D.1 Function Basics

**Concept:** A function f: A→B assigns EVERY element of A to EXACTLY ONE element of B.

**Terms:**
- **Domain** = A (full input set)
- **Codomain** = B (declared output set)
- **Range** = actual set of outputs = f(A) ⊆ B

**Trap 🔴:** Range ⊆ Codomain always, but Range = Codomain only for onto (surjective) functions.

## D.2 Types of Functions 🔴

| Type | Definition | Diagram intuition |
|---|---|---|
| Injective (one-one) | a₁≠a₂ ⟹ f(a₁)≠f(a₂) | No two arrows hit the same target |
| Surjective (onto) | ∀b∈B, ∃a∈A: f(a)=b | Every target is hit at least once |
| Bijective | Injective AND Surjective | Perfect 1-to-1 matching |
| Many-one | NOT injective | At least two inputs share an output |
| Into | NOT surjective | Some codomain element is unhit |

```
Injective (not onto)      Surjective (not 1-1)      Bijective
A       B                 A       B                 A       B
1 ----> a                 1 --\                      1 ----> a
2 ----> b                 2 ----> a                  2 ----> b
        c (unhit)         3 --/                       (all matched)
```

**GATE trap 🔴:** If |A| = |B| = n (finite, equal size), then f injective ⟺ f surjective ⟺ f bijective. This shortcut ONLY works when domain and codomain have the SAME finite size.

## D.3 Composition, Identity, Inverse

- **Composition:** (g∘f)(x) = g(f(x)). Apply f first, then g.
- **Identity function:** I(x) = x.
- **Inverse f⁻¹ exists ⟺ f is bijective.**

**Trap:** (g∘f)⁻¹ = f⁻¹∘g⁻¹ (order reverses) — commonly tested.

## D.4 Counting Functions 🔴 (GATE favorite — derive, don't memorize blindly)

Let |A| = m, |B| = n.

| Count | Formula | Why |
|---|---|---|
| Total functions A→B | nᵐ | each of m inputs has n independent choices |
| One-one (injective) functions | n!/(n−m)! = P(n,m), valid only if m≤n | 1st input: n choices, 2nd: n−1, ... |
| Onto (surjective) functions | Σₖ₌₀ⁿ (−1)ᵏ C(n,k)(n−k)ᵐ, valid if m≥n | Inclusion-exclusion: total − (miss at least one codomain elt) |
| Bijections | n! (only if m=n) | permutation of B |

**Derivation intuition for onto-count (why inclusion-exclusion):**
Total functions = nᵐ. Subtract functions that MISS at least one B-element, add back double-subtracted cases, etc. — classic inclusion-exclusion over "bad events" (each bad event = "element i of B is never hit").

**GATE-level example:** Number of onto functions from a 4-element set to a 2-element set:
= 2⁴ − C(2,1)·1⁴ = 16 − 2 = **14**

**Trap 🔴:** For onto-function-count formula, if m<n (fewer inputs than outputs), answer is always 0 — impossible to hit every output.

### D.5 — Practice Questions (Functions)

1. How many functions exist from a 3-element set to a 5-element set?
2. How many injective functions from a 5-element set to a 3-element set? (Trick question — think before formula.)
3. Find number of onto functions from {1,2,3,4,5} to {a,b,c}.
4. If f:R→R, f(x)=x², is it injective? Surjective? Bijective? Justify.
5. If f:A→B and g:B→C are both bijections, prove g∘f is a bijection.
6. How many bijections exist from a 4-element set to itself?
7. If |A|=n, how many distinct functions A→A are bijections? Injections but not bijections?

---

# PART E — PARTIAL ORDERS & LATTICES

## E.1 Poset Basics 🔴

**Concept:** A partially ordered set (poset) = (A, ≤) where ≤ is Reflexive + Antisymmetric + Transitive.

**Comparable/Incomparable:** a,b are comparable if a≤b or b≤a. If neither holds, they're incomparable — this is WHY it's called "partial" (not every pair needs to be comparable, unlike total/linear order).

## E.2 Hasse Diagrams 🔴

**Concept:** A simplified diagram of a poset — remove reflexive loops, remove edges implied by transitivity, draw "greater" elements higher up, connect only immediate ("covering") relations.

**Example — divisibility poset on {1,2,3,4,6,12}:**

```
        12
       /  \
      4    6
      |   / \
      2  3   
       \ |
        1
```
(1 divides everything → at bottom; 12 is divided by nothing further → top; edge 2—4 exists since 2|4 directly; NO edge drawn 1—4 directly since it's implied via 1—2—4)

## E.3 Minimal, Maximal, Least, Greatest, Bounds 🔴

| Term | Definition | Uniqueness |
|---|---|---|
| Minimal element | Nothing below it (no x with x<a) | Can have MULTIPLE minimal elements |
| Maximal element | Nothing above it | Can have MULTIPLE maximal elements |
| Least element | Below ALL other elements | If exists, UNIQUE |
| Greatest element | Above ALL other elements | If exists, UNIQUE |
| Upper bound of subset S | Element ≥ every element of S | May not be in S |
| Lower bound of subset S | Element ≤ every element of S | May not be in S |
| LUB (supremum) | SMALLEST upper bound | If exists, UNIQUE |
| GLB (infimum) | LARGEST lower bound | If exists, UNIQUE |

**Trap 🔴🔴🔴 (single most-tested poset trap):** Minimal ≠ Least, Maximal ≠ Greatest!
- A poset can have several minimal elements but zero or one least element.
- **Least element (if it exists) is always the unique minimal element** — but having a unique minimal element does NOT guarantee it's the least element (in infinite/weird posets), though for FINITE posets, unique minimal ⟹ least. Always double check by testing comparability with every other element.

**GATE-level example:** In poset {2,3,4,6,12} under divisibility:
- Minimal elements: 2, 3 (nothing below either)
- Maximal element: 12
- No least element (2 and 3 both minimal, incomparable)
- LUB(2,3) = 6 (smallest number both divide)
- GLB(4,6) = 2

## E.4 Lattices 🔴

**Concept:** A poset is a **lattice** if EVERY pair of elements has both a LUB (called **join**, a∨b) and a GLB (called **meet**, a∧b).

**How to check if a Hasse diagram is a lattice:** For every pair, check join and meet exist and are unique. If even ONE pair fails, it's not a lattice.

| Type | Extra condition |
|---|---|
| Bounded lattice | Has both least (0) and greatest (1) element |
| Complemented lattice | Every element a has a complement a' with a∨a'=1, a∧a'=0 |
| Distributive lattice | a∧(b∨c) = (a∧b)∨(a∧c) holds for all a,b,c |
| Boolean algebra | Complemented + Distributive lattice |

**Trap 🔴:** The "diamond" poset (pentagon N5 or diamond M3 shapes) are classic **non-distributive lattice** examples tested in GATE — memorize that pentagon (N5) and diamond (M3) lattices are the standard counterexamples to distributivity.

### E.5 — Hasse Diagram Practice Questions

1. Draw Hasse diagram for divisors of 30 under "divides."
2. In the poset ({1,2,3,4,6,12}, |), find all minimal, maximal, least, greatest elements.
3. Is the divisibility poset on {1,2,3,4,6,12} a lattice? Verify with 2 pair examples.
4. For power set P({a,b,c}) under ⊆, draw the Hasse diagram (cube shape) and identify least/greatest elements.
5. Find LUB and GLB of {4,6} in divisor-poset of 24.
6. Give an example of a poset with 2 maximal elements and no greatest element.
7. Is every chain (totally ordered set) automatically a lattice? Justify.
8. In a finite lattice, is the greatest element always unique? Prove.

---

# PART F — MONOIDS & GROUPS

## F.1 The Hierarchy 🔴

```
Algebraic structure (S, *) — S is a set, * is a binary operation

Semigroup:  Closure + Associativity
    ↓ (add identity element)
Monoid:     Semigroup + Identity element
    ↓ (add inverse for every element)
Group:      Monoid + Inverse for every element
    ↓ (add commutativity)
Abelian Group: Group + Commutativity
```

**Properties table (each row builds on the one above):**

| Structure | Closure | Associative | Identity | Inverse | Commutative |
|---|---|---|---|---|---|
| Semigroup | ✓ | ✓ | ✗ | ✗ | ✗ |
| Monoid | ✓ | ✓ | ✓ | ✗ | ✗ |
| Group | ✓ | ✓ | ✓ | ✓ | ✗ |
| Abelian Group | ✓ | ✓ | ✓ | ✓ | ✓ |

## F.2 Definitions & Counterexamples 🔴

- **Closure:** a,b∈S ⟹ a*b∈S. *Counterexample:* (Naturals, subtraction) — 2−5=−3 ∉ Naturals → not closed.
- **Associativity:** (a*b)*c = a*(b*c). *Counterexample:* subtraction is NOT associative: (5−3)−1=1 but 5−(3−1)=3.
- **Identity e:** a*e = e*a = a for all a. *Counterexample:* (Naturals excluding 0, addition) has no identity (0 isn't in the set).
- **Inverse:** for each a, ∃a⁻¹ with a*a⁻¹=a⁻¹*a=e. *Counterexample:* (Integers, multiplication) is a monoid (identity=1) but NOT a group — 2 has no integer inverse (1/2 ∉ Z).
- **Commutative:** a*b = b*a. *Counterexample:* matrix multiplication (n×n, n≥2) is a group under multiplication for invertible matrices but generally NOT commutative.

**Quick classification examples (memorize this table):**

| Structure | Group? | Why |
|---|---|---|
| (Z, +) | Abelian group | ✓ all 5 properties |
| (Z, ×) | Monoid only | no inverses (except ±1) |
| (N, +) | Semigroup only | no identity in N (if 0∉N), no inverses |
| (Z⁺, +) | Semigroup only | no identity, no inverses |
| (R−{0}, ×) | Abelian group | every nonzero real has a multiplicative inverse |
| (Matrices n×n, +) | Abelian group | |
| (n×n invertible matrices, ×) | Group (non-abelian) | inverse exists but not commutative |
| (Zₙ, +ₙ) mod-n addition | Abelian group | classic GATE example |

## F.3 Subgroup, Cyclic Group, Order 🔴

- **Subgroup:** A subset H of group G that is itself a group under the same operation.
- **Cyclic group:** A group generated by a single element g (called **generator**): every element = gᵏ for some integer k.
- **Order of an element a:** smallest positive integer n such that aⁿ = e (identity). If no such n exists, order is infinite.
- **Order of a group:** number of elements, |G|.

**Key theorem (Lagrange's theorem) 🔴:** Order of any subgroup H divides the order of group G. (|H| divides |G|)

**GATE-level example:** In (Z₆, +₆), find the order of element 2.
2, 2+2=4, 2+2+2=6≡0 → order of 2 is 3 (since 2·3=6≡0 mod 6).
Check: 6/gcd(6,2) = 6/2 = 3 ✓ (shortcut formula: order of k in Zₙ = n/gcd(n,k))

**Trap 🔴:** Every cyclic group is Abelian, but NOT every Abelian group is cyclic (e.g., Z₂×Z₂ is Abelian but not cyclic — no single generator produces all 4 elements).

### F.4 — Practice Questions (Monoids & Groups)

1. Is (Z, −) [integers under subtraction] a semigroup? Justify with closure/associativity check.
2. Prove (Zₙ, +ₙ) is always an Abelian group for any n≥1.
3. Is (Q, ×) [rationals under multiplication] a group? What about (Q−{0}, ×)?
4. Find the order of every element in (Z₄, +₄).
5. List all subgroups of (Z₆, +₆). Verify Lagrange's theorem holds for each.
6. Is the set of even integers under addition a subgroup of (Z,+)? Justify.
7. Give an example of a monoid that is NOT a group, with proof of which property fails.
8. Is (P(A), ⊕) [power set under symmetric difference] a group? Identify identity and each element's inverse.
9. Prove that in a group, the identity element is unique.
10. Prove that in a group, each element's inverse is unique.

---

**End of Part 2.** Functions (complete, with counting derivations) + Posets & Lattices (complete, with Hasse diagram method) + Monoids & Groups (complete hierarchy + Lagrange's theorem) — all at GATE depth.

Next file (Part 3): **Graph Theory + Combinatorics** — heaviest-weightage section in GATE DM, will include lots of graph diagrams, Handshaking lemma, matching/colouring, and the full counting decision-table ("if question says X → think Y").
