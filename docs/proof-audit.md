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

## Standard-game embedding

Treat `R` as one additional share. If `R` is present but `X_j` is missing, the
known local bijections reduce the view to at most `d-1` original additive shares,
which are independent of the secret. If `R` is absent, `(U_2, ..., U_d)` is
independent uniform for every fixed secret, the uniform translation makes `X_1`
independent uniform, and the independent nonzero multipliers preserve uniformity.
Thus the entire `X` tuple is independent uniform in this case. Every proper subset
of `(R, X_1, ..., X_d)` is therefore private, while the full tuple reconstructs.

When the leakage functions are fixed independently of the designated corrupted
share `R`, returning `R` together with the already evaluated local leakages is
distributionally identical to the standard nonadaptive local-leakage view for that
unauthorized set. This checks the embedding but not full LRSS security, which would
quantify over every unauthorized set.

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

## Arbitrary-prior mutual information

Let `P_s` be the transcript distribution at fixed secret `s`, let `pi` be any
secret prior, let `P_T = sum_s pi(s) P_s`, and let `M` be the common product
reference. Relative entropy satisfies the exact barycenter identity

```text
sum_s pi(s) D(P_s || M) = I(S;T) + D(P_T || M).
```

Also, Jensen's inequality under `P` gives

```text
D(P || M)
 <= log E_P[P/M]
  = log(1 + chi2(P || M)).
```

The fixed-secret theorem makes the final chi-square value the same constant
`C = prod_i e_i/(Q-1)^(d-1)` for every `s`. Dropping the nonnegative divergence
of the mixture therefore gives `I(S;T) <= log(1+C)` for every prior. This is an
average information-leakage statement, not a simulator or composability claim.

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

Since `rank(M) <= min(|G|, |Z|)`, the remaining squared singular values sum to
at most `min(|G|-1, |Z|-1)`. Consequently every feasible energy is at most
`|G|-1` as well as `|Z|-1`.

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

## Real-orbit minimax theorem

Because every likelihood response `g_i(x,z)` is real,

```text
E_i(gamma^(-1)) = E_i(gamma).
```

For a nontrivial character define its real orbit

```text
C_H(gamma) = (H orbit gamma) union (H orbit gamma^(-1)).
```

This is either one inversion-stable `H`-orbit or two inverse `H`-orbits of equal
size. In the two-orbit case, conjugate-energy symmetry puts exactly half of each
channel's `C`-energy in either orbit. Substituting into the finite-abelian identity
shows in both cases that

```text
chi2 = sum_C prod_i e_i^R(C) / |C|^(d-1).
```

The factor check in the two-orbit case is

```text
2 * prod_i(e_i^R(C)/2) / (|C|/2)^(d-1)
  = prod_i e_i^R(C) / |C|^(d-1).
```

Put `m_R(H) = min_C |C|`. Independent uniform automorphisms therefore give

```text
chi2 <= prod_i epsilon_i / m_R(H)^(d-1),
```

using the same nonnegative diagonal-term inequality as before.

### Arbitrary-distribution lower bound

Fix a smallest real orbit `C` and a conjugate packet

```text
P_beta = {beta, beta^(-1)},
r = |P_beta| in {1,2}.
```

The `H`-orbit of this packet has `N = |C|/r` values. For arbitrary, possibly
correlated `D` on `H^(d-1)`, the packet tuple

```text
Y = (h_2 acting on P_beta, ..., h_d acting on P_beta)
```

has a cell of mass at least `N^(-(d-1))`.

### Exact packet capacity

Let `k` be the order of `beta`. For `k = 2`, a centered real likelihood response
supported on the packet has the form `a_z beta(x)`. Positivity gives `|a_z| <= 1`,
so its energy is at most one, attained by the binary character channel.

For `k >= 3`, every such response has the form

```text
g(x,z) = 2 Re(a_z beta(x)).
```

Among the `k` values of `beta(x)`, one lies within angle `pi/k` of the direction
opposite to `a_z`. Positivity of `1 + g` therefore gives

```text
|a_z| <= 1 / (2 cos(pi/k)).
```

The total packet energy is `2 E_z |a_z|^2`, hence at most

```text
kappa(k) = 1 / (2 cos(pi/k)^2).
```

This is attainable. Choose `k` coefficient phases spaced uniformly around the
circle, all at the maximum radius, and use them as the centered responses of a
uniform `k`-ary output channel. Their sum is zero, each likelihood is nonnegative,
and the two conjugate frequencies each receive half the stated energy. Radial
scaling attains every smaller energy.

Thus `kappa(2)=1` and the displayed formula applies for `k>=3`. Among the
smallest real orbits, choose one maximizing this capacity and call the value
`kappa_min(H)`. It is strictly above `1/2` for every fixed finite group and tends
to `1/2` as the relevant character order grows.

After the uniform translation removes cross-character terms, the exact expression
for arbitrary `D` is

```text
sum_[gamma nontrivial] E_1(gamma)
  E_[h tuple from D] prod_[i=2..d] E_i(h_i acting on gamma).
```

The local outputs, not the automorphisms, provide the product factorization. The
`r` initial frequencies contribute on the selected packet-alignment event, giving

```text
(prod_i epsilon_i / r^(d-1)) * Pr[Y = y]
 >= prod_i epsilon_i / (r N)^(d-1)
  = prod_i epsilon_i / |C|^(d-1).
```

This matches the uniform upper bound for every finite abelian group when every
budget is at most `kappa_min(H)`.

### Full-spectrum erasure witness

For `Q = |G|` and `0 <= epsilon <= Q-1`, set
`rho = epsilon/(Q-1)` and use the channel that reveals `x` with probability
`rho` and otherwise outputs an erasure symbol. The erasure response is zero. A
reveal output `y` has centered response `Q 1[x=y] - 1`, whose coefficient at
every nontrivial character has magnitude one. Averaging over the output mass
`rho/Q` gives

```text
E_W(gamma) = rho for every nontrivial gamma,
e(W) = (Q-1) rho = epsilon.
```

If there is one nontrivial real orbit, independent uniform automorphisms give
the upper bound `prod_i epsilon_i/(Q-1)^(d-1)` for every feasible budget. The
full-spectrum channels give the same value against every distribution `D`, so
the minimax value extends to the entire interval `[0,Q-1]`. This does not by
itself classify all minimizing `D` outside the packet-capacity range.

### Design consequences

For `G = GF(p)^n`, there are `Q-1` nontrivial characters, and `GL(n,p)` is
transitive on them. Positive-budget optimality among automorphism subgroups is
therefore equivalent to transitivity on conjugate-character packets. Such a group
has order at least `(Q-1)/r`, where `r=1` in characteristic two and `r=2`
otherwise.

For the additive group of `GF(Q)`, nonzero scalars are transitive on nontrivial
characters, so the minimax value holds for every feasible budget through `Q-1`.
All nontrivial characters have order `p = char(GF(Q))`. A multiplier distribution
whose projection modulo independent signs is uniform attains the exact minimax value at
every feasible budget.

The converse extends beyond the single-packet range. Suppose every budget lies strictly
between `0` and `Q-1`, and identify the packet set with the abelian group

```text
K = GF(Q)* / {+1,-1},    |K| = N = (Q-1)/r.
```

For each such budget `epsilon`, there is a channel with packet-energy vector

```text
v(c) = a + b 1[c=c_0],    a >= 0, b > 0, sum_c v(c) = epsilon.
```

For `epsilon <= kappa(p)`, tagged time sharing between a capacity packet channel and
an input-independent channel gives `a=0, b=epsilon`. For
`kappa(p) < epsilon < Q-1`, tagged time sharing between full reveal and a capacity
packet channel uses weights

```text
t = (epsilon-kappa)/(Q-1-kappa),
u = (Q-1-epsilon)/(Q-1-kappa),
```

and gives `a=r t, b=u kappa`. Disjoint output tags make channel spectral energies
the convex combination. Normalizing gives a probability distribution `p=v/epsilon`
on `K` whose every Fourier coefficient is nonzero: the uniform baseline contributes
zero at nontrivial frequencies and the positive point spike contributes a nonzero value.

For independent `C_i` with laws `p_i`, define

```text
V = (C_2 C_1^(-1), ..., C_d C_1^(-1)).
```

At a character tuple `(eta_2,...,eta_d)` of `K^(d-1)`, its Fourier transform is

```text
p_1_hat((prod_i eta_i)^(-1)) prod_[i=2..d] p_i_hat(eta_i),
```

which never vanishes. Convolution by the law of `V` is therefore injective. Moving
the local spikes translates this law by arbitrary elements of `K^(d-1)`. If the
projected multiplier law were nonuniform, its inner products with those translates
would be nonconstant; their average is `N^(-(d-1))`, so one is strictly larger.
The corresponding local channels exceed the minimax value. Thus projective uniformity
is necessary at every strictly interior budget, not only through `kappa(p)`.

Consequently an attaining deterministic seed in the strict interior needs min-entropy
at least

```text
(d-1) log_2((Q-1)/r).
```

In characteristic two the sign quotient is trivial, so the multiplier tuple itself
must be uniform and is the unique strict-interior minimizer. Budgets equal to zero or
`Q-1` can have additional minimizers and are not classified. No lower bound on the
translation randomness, or on arbitrary nonlocal encodings, has been proved.

Choosing one fixed scalar representative of each sign class realizes uniform projected
multipliers with exactly `(d-1) log_2 N` bits of entropy. Together with the independent
uniform translation, the compiler consumes

```text
log_2 Q + (d-1) log_2 N
```

fresh random bits in the information-theoretic sense, and its capsule can be indexed among
`Q N^(d-1)` possibilities. This is tight for the multiplier seed in the strict interior,
within the stated compiler. It is not a lower bound for unrelated encodings.

## Edge cases

- Trivial `G`: excluded from the minimax theorem because there is no nontrivial real
  orbit and `m_R(H)` would be undefined.
- Trivial `H`: a complex character and its inverse still form a real orbit of size two.
  Thus the minimax value need not be `prod_i epsilon_i`; real-valued channels cannot
  concentrate energy at only one non-real frequency.
- Multiple minimum-size orbits: the lower bound may use any one of them, while the upper
  bound sums all orbit contributions. No uniqueness of the optimal distribution is claimed.
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
3. For multiple real orbits, the general minimax theorem stops at the exact energy
   capacity of a single packet in a smallest orbit. Larger budgets can force energy
   onto additional characters, and the corresponding global extremal problem remains open.
4. For field multipliers, necessity of projective-uniform randomizers is proved at all
   strictly interior energies. Boundary minimizers and minimizers for general
   single-real-orbit actions remain unclassified.
5. Publication significance depends on whether the temporal leakage experiment has a
   compelling cryptographic realization.
