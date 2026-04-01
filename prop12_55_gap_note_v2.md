# Revised note on the gap in Proposition 12.55

## Correction to an earlier version of this note

An earlier version of this note said that for a cuspidal cubic, the reduced total transform in an embedded resolution has **three** components. That was **not accurate** if one insists, as Proposition 12.55 does, that

$$
E := \bigl(f^{-1}(C)\bigr)_{\mathrm{red}}
$$

is a **simple normal crossings** divisor.

After the second blowup, one indeed sees three reduced components, but they still meet at a **triple point**, so the divisor is not yet SNC. One more blowup is needed. After that third blowup, the reduced total transform has **four** irreducible components.

This correction does **not** change the mathematical point: for the cuspidal cubic, the SNC reduced total transform still has arithmetic genus

$$
p_a(E)=0,
$$

whereas

$$
p_a(C)=1.
$$

So the proof of Proposition 12.55, as written, still does **not** justify the claimed conclusion in this generality.

---

## What Proposition 12.55 claims to do

Proposition 12.55 starts from an **irreducible singular plane cubic**

$$
C \subset \mathbf P^2,
$$

and after resolving the birational map and total transform, takes a morphism

$$
f:Y \to \mathbf P^2
$$

and the reduced total transform

$$
E := \bigl(f^{-1}(C)\bigr)_{\mathrm{red}}.
$$

The proof then argues that the fibers of $E \to C$ are connected trees of rational curves, and concludes

$$
f_*\mathcal O_E = \mathcal O_C,
\qquad
R^1 f_*\mathcal O_E = 0,
$$

hence

$$
p_a(E)=p_a(C)=1.
$$

The computation below shows that this argument, **as written**, does not justify the proposition for all irreducible singular plane cubics.

---

## Explicit test case: the cuspidal cubic

Take the cuspidal cubic

$$
C: y^2 z = x^3 \subset \mathbf P^2.
$$

On the affine chart $z=1$, this is

$$
C: y^2 = x^3.
$$

It is an irreducible singular plane cubic, so

$$
p_a(C)=1.
$$

Let

$$
f:Y \to \mathbf P^2
$$

be an embedded resolution of the cusp, and set

$$
E := \bigl(f^{-1}(C)\bigr)_{\mathrm{red}}.
$$

We now compute the reduced total transform explicitly.

---

## Step 1: first blowup

Blow up the origin. On the $x$-chart, write

$$
y=xv.
$$

Then

$$
y^2-x^3 = x^2(v^2-x).
$$

So after the first blowup, the reduced total transform has two components:

- the exceptional curve $E_1: x=0$,
- the strict transform $C_1: v^2=x$.

The strict transform $C_1$ is smooth, but it is tangent to $E_1$ at $(x,v)=(0,0)$, so the divisor is **not** SNC.

---

## Step 2: second blowup

Blow up the point $(0,0)$ again. In the chart adapted to the tangent direction, write

$$
x=uv, \qquad v=v.
$$

Substituting into the total transform gives

$$
x^2(v^2-x)=(uv)^2(v^2-uv)=u^2v^3(v-u).
$$

The reduced total transform now has three visible components:

- the strict transform $E_1': u=0$ of the first exceptional curve,
- the new exceptional curve $E_2: v=0$,
- the strict transform $C_2: v=u$ of the cubic.

However, these three curves all pass through the point $(u,v)=(0,0)$. So after the second blowup the divisor is still **not** SNC: it has a triple point.

This is exactly the place where the earlier version of this note was too quick.

---

## Step 3: third blowup

Blow up the triple point $(0,0)$. Let $E_3$ be the new exceptional curve. Then the reduced total transform becomes an SNC divisor with **four** irreducible components:

$$
E = \widetilde E_1 \cup \widetilde E_2 \cup \widetilde C \cup E_3.
$$

Its dual graph is a tree: $E_3$ is the central component, and each of

$$
\widetilde E_1,\ \widetilde E_2,\ \widetilde C
$$

meets $E_3$ transversely in one point and does not meet the other two.

So the final SNC reduced total transform has:

- **4 components**, all smooth rational curves,
- **3 intersection points**,
- a **tree** as dual graph.

---

## Direct arithmetic-genus computation

For a connected reduced SNC divisor

$$
E = \sum_{i=1}^r E_i
$$

with smooth rational components, one has

$$
p_a(E)
= \sum_{i=1}^r p_a(E_i)
  + \sum_{i<j} E_i\cdot E_j
  - r + 1.
$$

In the present example:

- $r=4$,
- each $p_a(E_i)=0$,
- there are exactly $3$ intersection points.

Hence

$$
p_a(E)=0+3-4+1=0.
$$

Therefore

$$
p_a(E)=0 \neq 1 = p_a(C).
$$

So even after correcting the component count from 3 to 4, the main conclusion remains the same:

> the proof of Proposition 12.55 does not justify the equality $p_a(E)=p_a(C)$ for an arbitrary irreducible singular plane cubic.

---

## Where the proof breaks

The problematic implication is

$$
\text{“the fibers of }E\to C\text{ are connected trees of rational curves”}
\quad \Longrightarrow \quad
f_*\mathcal O_E = \mathcal O_C.
$$

This is not automatic when $C$ is **non-normal**. The cuspidal cubic is precisely such a case.

Indeed, if one really had

$$
f_*\mathcal O_E = \mathcal O_C,
\qquad
R^1 f_*\mathcal O_E = 0,
$$

then Leray would give

$$
\chi(\mathcal O_E)=\chi(\mathcal O_C),
$$

hence

$$
p_a(E)=p_a(C)=1.
$$

But the explicit calculation above gives

$$
p_a(E)=0.
$$

So the cohomological step used in the proof fails on this basic example.

---

## Comparison with the nodal case

If $C$ is a **nodal** cubic, then after resolving the node the reduced total transform can have the form

$$
E = R + F,
\qquad
R\cdot F = 2,
$$

with both $R$ and $F$ rational. In that case,

$$
p_a(E)=0+0+2-2+1=1.
$$

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

At present, Proposition 12.55 is **not justified as written**.
