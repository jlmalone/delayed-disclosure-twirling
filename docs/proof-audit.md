# Static proof audit

This document rederives the manuscript's central claims independently of its exposition.
It is not an external review.

## Normalization

Let `F` have order `Q`, and let `Fhat` be its additive character group. For a
finite-output channel `W_i`, define

```text
q_i(z) = E_[x uniform in F] W_i(z | x),
g_i(x,z) = W_i(z | x) / q_i(z) - 1.
```

For a character `gamma`, use the coefficient

```text
c_i(gamma,z) = E_x gamma(x) g_i(x,z).
```

The conjugate convention would only relabel characters. Since `E_x g_i(x,z) = 0`,
the trivial coefficient vanishes. Parseval gives

```text
e_i = E_z E_x |g_i(x,z)|^2
    = sum_[gamma nontrivial] E_z |c_i(gamma,z)|^2.
```

The first equality is exactly the definition of chi-square divergence for the joint
law of a uniform input and its channel output.

## Likelihood-ratio calculation

Relative to independent uniform `u_1, ..., u_d`, the density of additive shares of
`s` is

```text
Q 1[u_1 + ... + u_d = s]
  = sum_[gamma in Fhat] gamma(u_1 + ... + u_d - s).
```

For fixed capsule `r = (b,a_2,...,a_d)`, substitute

```text
u_1 = x_1 - b,
u_i = a_i^(-1) x_i.
```

Dividing the leakage probability by `prod_i q_i(z_i)` and integrating over
independent uniform `x_i` yields a likelihood ratio of the form

```text
L_(s,r)(z) - 1
 = sum_[gamma nontrivial]
     gamma(-s-b) c_1(gamma,z_1)
     prod_[i=2..d] c_i(gamma after multiplication by a_i^(-1), z_i).
```

All terms in which one local factor contributes its constant `1` vanish for a
nontrivial character. This is why only the product of all local centered responses
survives.

## Squaring and averaging

In `|L-1|^2`, the average over uniform `B` contains

```text
E_B gamma(-B) conjugate(psi(-B)),
```

which is one when `gamma = psi` and zero otherwise. Thus:

- every cross-character term disappears;
- the phase containing the fixed secret has modulus one and disappears;
- no average over the secret is being taken.

For a fixed nontrivial `gamma` and a uniform `A_i in F*`, multiplication sends
`gamma` uniformly over all `Q-1` nontrivial characters. Therefore

```text
E_[A_i,Z_i] |c_i(gamma after A_i^(-1),Z_i)|^2 = e_i/(Q-1).
```

Summing the first coordinate's spectral energy gives

```text
chi2 = e_1 prod_[i=2..d] e_i/(Q-1)
     = prod_i e_i / (Q-1)^(d-1).
```

This establishes the exact identity for every fixed secret.

## Pairwise statistical distance

Let `M` be the common reference distribution. If the exact value is `C` for both
secrets, then

```text
TV(P_s,P_t)
 <= TV(P_s,M) + TV(P_t,M)
 <= (1/2)sqrt(C) + (1/2)sqrt(C)
 = sqrt(C).
```

No unproved conversion between chi-square divergence and pairwise divergence is used.

## Leakage-alphabet lemma

For the joint law of `(X,Z)`, form the normalized matrix

```text
M[x,z] = P[X=x,Z=z] / sqrt(P[X=x] P[Z=z]).
```

The associated conditional-expectation operator is an `L2` contraction. Hence all
singular values of `M` are at most one. One singular value is the constant component,
and

```text
sum_j sigma_j^2 = 1 + chi2(P_(X,Z) || P_X P_Z).
```

Since `rank(M) <= |Z|`, the remaining squared singular values sum to at most
`|Z|-1`. Consequently `e_i <= |Z_i|-1`.

For deterministic `f` with exactly `r` nonempty fibers, a direct sum over each fiber
gives equality `e = r-1`; balanced fibers are not required.

## Finite-abelian orbit calculation

For a finite abelian group `G` and `H <= Aut(G)`, let `O` range over nontrivial
`H`-orbits in the dual group. A uniform element of `H` maps any fixed character
uniformly over its orbit by orbit-stabilizer. Define

```text
e_i(O) = sum_[gamma in O] E_z |c_i(gamma,z)|^2.
```

After the translation removes cross terms, grouping the diagonal terms by orbit gives

```text
chi2 = sum_O prod_i e_i(O) / |O|^(d-1).
```

No transitivity assumption is needed for this formula. Field multiplication is the
single-nontrivial-orbit specialization.

## Minimax witness over characteristic two

Let `F = GF(2^n)`, let `D` be any distribution on the relative multiplier tuple,
and let `0 <= epsilon_i <= 1`. Additive characters take values in `{+1,-1}`.
For a nontrivial character `chi_beta`, define

```text
W_i(z | x) = (1 + z sqrt(epsilon_i) chi_beta(x))/2,
z in {+1,-1}.
```

This is a valid channel precisely in the stated parameter range, and its nonconstant
spectral energy is `epsilon_i` at one character. Frequencies can be selected so that
all local terms align at any chosen relative multiplier tuple `y`. Its transcript
chi-square divergence is

```text
prod_i epsilon_i times D(y).
```

Choosing a largest atom proves the lower bound

```text
prod_i epsilon_i / (Q-1)^(d-1).
```

Uniform relative multipliers attain the same value for every admissible collection of
channels by the exact identity. If every `epsilon_i` is positive, equality forces every
atom of `D` to equal `1/(Q-1)^(d-1)`. The multiplier tuple therefore requires at least
`(d-1) log_2(Q-1)` bits of seed min-entropy within this design class. No lower bound on
the translation randomness, or on arbitrary nonlocal encodings, has been proved.

## Edge cases

- `e_i = 0` for one party: the exact divergence is zero. This agrees with the fact that
  the additive constraint cannot survive centering unless every local factor contributes.
- Identity leakage: `e_i = Q-1` for every party, giving `chi2 = Q-1`, consistent with
  complete recovery of a uniform `Q`-ary secret relative to its marginal.
- `Q = 2`: the nontrivial character orbit has size one, so multiplier randomization gives
  no gain.
- `d = 1`: the algebraic identity still degenerates to `e_1`, but the manuscript excludes
  this non-sharing case.
- Nonuniform or disclosed `B`: cross-character cancellation is no longer justified.
- Metadata-aware leakage: local bijections can be inverted and the security gain vanishes.
- Correlated stochastic channels: the product likelihood-ratio factorization is absent.

## Open proof risks

1. The exact identity should be independently checked with the manuscript's conjugation
   convention rather than relying on the convention-invariant energy calculation.
2. A shared-public-coins extension needs conditional-energy notation and should not claim a
   product of unconditional energies.
3. The minimax theorem is only for local chi-square budgets at most one. Extending it to
   larger budgets requires a different extremal-channel argument.
4. Publication significance depends on whether the temporal leakage experiment has a
   compelling cryptographic realization.
