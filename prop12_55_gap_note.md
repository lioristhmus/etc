# A concrete calculation showing the gap in Proposition 12.55

## What Proposition 12.55 claims to do

Proposition 12.55 considers an **irreducible singular plane cubic**
\[
C \subset \mathbf P^2,
\]
and after resolving the birational map and the total transform, it takes a morphism
\[
f:Y \to \mathbf P^2
\]
and the reduced total transform
\[
E := \bigl(f^{-1}(C)\bigr)_{\mathrm{red}}.
\]

The proof then argues that the fibers of \(E \to C\) are connected trees of rational curves, and concludes
\[
f_*\mathcal O_E = \mathcal O_C,
\qquad
R^1 f_*\mathcal O_E = 0,
\]
so that
\[
p_a(E)=p_a(C)=1.
\]

The calculation below shows that **this argument, as written, does not justify the proposition in this generality**.

---

## Explicit test case: the cuspidal cubic

Take the cuspidal cubic
\[
C:\ y^2 z = x^3 \subset \mathbf P^2.
\]

This is an irreducible singular plane cubic, so
\[
p_a(C)=1.
\]
Its normalization is \(\mathbf P^1\), so \(C\) is rational.

Let
\[
f:Y \to \mathbf P^2
\]
be an embedded resolution of the cusp, and set
\[
E := \bigl(f^{-1}(C)\bigr)_{\mathrm{red}}.
\]

For the cusp, the reduced total transform is a chain of three smooth rational curves:
\[
E_1 - E_2 - R,
\]
where

- \(R\) is the strict transform of \(C\),
- \(E_1,E_2\) are exceptional curves.

Thus every irreducible component of \(E\) is rational, and the dual graph of \(E\) is a **tree**.

---

## Direct arithmetic-genus computation

For a connected reduced SNC divisor
\[
E = \sum_{i=1}^r E_i
\]
with smooth rational components, one has
\[
p_a(E)
= \sum_{i=1}^r p_a(E_i)
  + \sum_{i<j} E_i\cdot E_j
  - r + 1.
\]

In the present example:

- \(r=3\),
- each \(p_a(E_i)=0\),
- there are exactly two intersection points: \(E_1\cdot E_2=1\) and \(E_2\cdot R=1\).

Hence
\[
p_a(E)
= 0+0+0 + 2 - 3 + 1 = 0.
\]
So here
\[
p_a(E)=0 \neq 1 = p_a(C).
\]

This shows that the proof of Proposition 12.55 cannot deduce \(p_a(E)=p_a(C)\) in full generality from the argument given.

---

## Where the proof breaks

The problematic step is the implication
\[
\text{“the fibers of }E\to C\text{ are connected trees of rational curves”}
\quad \Longrightarrow \quad
f_*\mathcal O_E = \mathcal O_C.
\]

This is not automatic when \(C\) is **non-normal**. The cuspidal cubic is precisely such a case.

Indeed, if one really had
\[
f_*\mathcal O_E = \mathcal O_C,
\qquad
R^1 f_*\mathcal O_E = 0,
\]
then Leray would give
\[
\chi(\mathcal O_E)=\chi(\mathcal O_C),
\]
and therefore
\[
p_a(E)=p_a(C)=1.
\]
But the explicit calculation above gives
\[
p_a(E)=0.
\]
So **the cohomological argument used in the proof fails on this basic example**.

---

## Comparison with the nodal case

If \(C\) is a **nodal** cubic, then after resolving the node the reduced total transform has the form
\[
E = R + F,
\qquad
R\cdot F = 2,
\]
with both \(R\) and \(F\) rational. Then
\[
p_a(E)=0+0+2-2+1=1.
\]

So in the nodal case the **genus obstruction disappears**: the reduced total transform can indeed have arithmetic genus one. What fails is the uniform passage from “irreducible singular cubic” to the conclusion used in Proposition 12.55.

---

## Consequence for the paper

Proposition 12.55 is used later at least in:

- **Theorem 12.56**,
- **Theorem 12.61**,
- **Theorem 12.70**.

Therefore, unless Proposition 12.55 is repaired, those later closures are not established **in the form currently written**.

---

## Possible repair directions

Two natural repair strategies would be:

1. **Restrict Proposition 12.55 to a nodal-cubic statement**, and then prove that every application produces a nodal cubic rather than a cuspidal one.
2. **Avoid Proposition 12.55 entirely** by constructing directly a reduced genus-one boundary on the resolved model, as is done elsewhere in the paper for the conic-line endpoint.

At present, the statement proved in Proposition 12.55 is **not justified as written**.
