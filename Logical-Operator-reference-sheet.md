# Logical Operators — Reference Sheet

**Boolean Algebra & Digital Logic — GATE CS Preparation**

---

## 1. Basic & Derived Logical Operators

Boolean algebra ke saare operators ko do categories mein baata ja sakta hai — **basic** (AND, OR, NOT) aur inse **derive** kiye gaye operators (NAND, NOR, XOR, XNOR, Implication, Biconditional).

| Operator | Symbol | Name | Type | Expression | Truth Condition |
|---|---|---|---|---|---|
| AND | `·` / `∧` | Conjunction | Basic | `A · B` | 1 only if both A, B = 1 |
| OR | `+` / `∨` | Disjunction | Basic | `A + B` | 0 only if both A, B = 0 |
| NOT | `'` / `¬` / `~` | Negation | Basic | `A'` | Inverts the input |
| NAND | `↑` | NOT-AND | Derived | `(A · B)'` | 0 only if both A, B = 1 |
| NOR | `↓` | NOT-OR | Derived | `(A + B)'` | 1 only if both A, B = 0 |
| XOR | `⊕` | Exclusive OR | Derived | `AB' + A'B` | 1 if A ≠ B |
| XNOR | `⊙` | Exclusive NOR | Derived | `AB + A'B'` | 1 if A = B |
| Implication | `→` | Conditional | Derived | `A' + B` | 0 only if A = 1, B = 0 |
| Biconditional | `↔` | Double Implication | Derived | `(A→B)·(B→A)` | Same as XNOR |

> **📌 Universal Gates**
> NAND aur NOR ko **"universal gates"** kaha jaata hai kyunki inn dono se akele hi AND, OR, aur NOT ban sakte hain.
> `{AND, OR, NOT}` aur `{NAND}` akele — dono **functionally complete sets** hain.

---

## 2. Properties of Basic Operators (AND, OR, NOT)

| Property | AND / OR Statement | Remarks |
|---|---|---|
| Commutative | `A·B = B·A`  \|  `A+B = B+A` | Order matters nahi karta |
| Associative | `(A·B)·C = A·(B·C)`  \|  `(A+B)+C = A+(B+C)` | Grouping matters nahi karta |
| Distributive | `A·(B+C) = A·B + A·C`  \|  `A+(B·C) = (A+B)·(A+C)` | Dono directions valid hain |
| Identity | `A·1 = A`  \|  `A+0 = A` | 1 is AND-identity, 0 is OR-identity |
| Null / Dominance | `A·0 = 0`  \|  `A+1 = 1` | Dominant element result fix kar deta hai |
| Idempotent | `A·A = A`  \|  `A+A = A` | Same variable repeat karne se koi effect nahi |
| Complement | `A·A' = 0`  \|  `A+A' = 1` | Variable + apna complement |
| Involution | `(A')' = A` | Double negation cancel ho jaata hai |
| Absorption | `A+(A·B) = A`  \|  `A·(A+B) = A` | Redundant term absorb ho jaata hai |
| De Morgan's | `(A·B)' = A'+B'`  \|  `(A+B)' = A'·B'` | NAND/NOR duality ka base |

---

## 3. NAND & NOR — Special Case

NAND aur NOR **commutative** to hote hain, lekin **associative NAHI** hote — yeh ek common GATE trap hai.

| Operator | Commutative? | Associative? |
|---|---|---|
| NAND (↑) | ✅ Yes — `A↑B = B↑A` | ❌ No — `(A↑B)↑C ≠ A↑(B↑C)` |
| NOR (↓) | ✅ Yes — `A↓B = B↓A` | ❌ No — `(A↓B)↓C ≠ A↓(B↓C)` |

---

## 4. XOR & XNOR — Extra Properties

| Property | XOR (⊕) | XNOR (⊙) |
|---|---|---|
| Identity | `A⊕0 = A` | `A⊙1 = A` |
| Complement Rule | `A⊕1 = A'` | `A⊙0 = A'` |
| Self-Inverse | `A⊕A = 0` | `A⊙A = 1` |
| With Complement | `A⊕A' = 1` | `A⊙A' = 0` |
| Commutative | `A⊕B = B⊕A` | `A⊙B = B⊙A` |
| Associative | `(A⊕B)⊕C = A⊕(B⊕C)` | Associative hai |

> **📌 Distributive Trap (GATE Favourite)**
> XOR AND ke saath distribute hota hai: `A·(B⊕C) = (A·B) ⊕ (A·C)` — yeh **valid** hai.
> Lekin `A+(B·C)` jaisa simple OR-distribution pattern XOR ke saath directly assume mat karo — hamesha derive karke check karo.

---

## 5. Quick Memory Trick

- **AND, OR** → Commutative + Associative + Distributive over each other — full "nice" algebra structure.
- **NAND, NOR** → Commutative hai, par Associative **NAHI** — common trap question.
- **XOR** → Commutative + Associative + AND ke saath distribute karta hai: `A·(B⊕C) = (A·B)⊕(A·C)`.
- **Universal Gates**: NAND aur NOR — dono se akele AND, OR, NOT ban sakte hain.

---

*Prepared for GATE CS — Digital Logic Revision*
