# Leakage experiment and scope

## Objects

Let `F` be a finite field of order `Q` and let `d >= 2`. A secret `s in F` is
shared by sampling `U_1, ..., U_{d-1}` independently and uniformly and setting

```text
U_d = s - U_1 - ... - U_{d-1}.
```

The encoder samples independent recovery metadata

```text
B uniform in F,
A_2, ..., A_d uniform in F minus {0},
```

and stores

```text
X_1 = U_1 + B,
X_i = A_i U_i for 2 <= i <= d.
```

The recovery capsule is `R = (B, A_2, ..., A_d)`. It is held outside the
components on which the leakage snapshot is taken.

## Pairwise distinguishing experiment

1. The adversary selects two secrets `s_0, s_1` and local leakage channels
   `W_i : F -> Z_i`. The choices may depend on the public construction and on both
   challenge secrets, but not on the still-unsampled recovery capsule.
2. The challenger samples a uniform challenge bit `C`, shares `s_C`, samples `R`,
   and computes the stored values.
3. A single leakage snapshot is taken. Conditional on the stored values, the local
   outputs are independent and satisfy `Z_i ~ W_i(. | X_i)`.
4. The challenger discloses `R`.
5. The adversary receives `(R, Z_1, ..., Z_d)` and guesses `C`.

The theorem bounds the statistical distance between the two transcript
distributions. It is information theoretic and places no computational restriction on
the individual channels.

## Exact quantifier boundary

The proven order is

```text
choose local channels;
sample hidden recovery metadata;
take one leakage snapshot;
disclose recovery metadata.
```

The following stronger orders are not claimed:

- choosing or modifying a channel after learning any part of `R`;
- taking another leakage snapshot after `R` is disclosed;
- adaptively choosing one party's channel after seeing another party's output;
- a joint channel that reads multiple stored values;
- leakage from the component holding `R` during the snapshot;
- leakage during reconstruction.

Independent stochastic channels include deterministic local leakage functions. If an
adversary uses public shared coins to choose deterministic local functions before the
capsule is sampled, the theorem can be applied after conditioning on those coins. The
exact product identity then uses the conditional local energies. It does not generally
equal the product of the energies averaged over the shared coins.

## Reference distribution

For a channel `W_i`, let `X` be uniform in `F` and set

```text
q_i(z) = Q^(-1) sum_x W_i(z | x).
```

Outputs with `q_i(z) = 0` are omitted. Define

```text
e_i = chi2(P_(X,Z_i) || P_X P_(Z_i)).
```

Every encoded share is marginally uniform for every fixed secret, so `q_i` is also
the fixed-secret marginal of `Z_i`. The exact theorem compares the real transcript
with

```text
P_R times P_(Z_1) times ... times P_(Z_d).
```

This common reference is independent of the challenge secret.

## Consequences for arbitrary secret priors

Let `T = (R, Z_1, ..., Z_d)` and give `S` any prior distribution independent of
the sharing randomness. The common-reference identity implies

```text
I(S;T) <= log(1 + prod_i e_i/(Q-1)^(d-1))
```

with natural logarithms. This follows from the relative-entropy barycenter identity
and `D(P || M) <= log(1 + chi2(P || M))`. It is an average one-shot information
bound. It is not a simulator, a sequential-composition theorem, or permission to
take another leakage snapshot after capsule disclosure.

## Standard-game embedding

Regard `R` as one additional, oversized share. Then `(R, X_1, ..., X_d)` is a
perfect `(d+1)`-out-of-`(d+1)` sharing:

- if `R` is known but some `X_j` is missing, the view reduces by local inversion
  to at most `d-1` additive shares;
- if `R` is missing, the whole `X` tuple is independent uniform because `B`
  independently masks `X_1` and `(U_2, ..., U_d)` is uniform for fixed `s`.

In the standard nonadaptive local-leakage game, designate the capsule component as
the fully revealed unauthorized set and require the leakage functions on the other
components to be fixed independently of that revealed share. The resulting view is
identically distributed to the transcript above. Thus the chronology is an operational
interpretation of an established game slice, not a claim to a new security definition.

This does not establish a full leakage-resilient secret-sharing scheme: the theorem
covers only the designated unauthorized set containing `R`, whereas the standard
definition quantifies over every unauthorized set. The capsule also has larger size than
each encoded-share component.

## Operational interpretation

The narrow motivating case is a one-time forensic, cold-boot, or memory-snapshot
event against several components, while a small recovery capsule resides in a different
protection domain. The capsule may later be compromised or intentionally disclosed, but
the attacker cannot remeasure the earlier device states.

This interpretation remains a research hypothesis. A publication must justify when the
fixed-channel and no-remeasurement assumptions match a real leakage process.

## Public-capsule impossibility

Let a local encoding for metadata `rho` be any bijection `pi_rho`. If `rho` is
available to the leakage function, then for every attack `f` on an unencoded share the
channel can use

```text
ell(rho, x) = f(pi_rho^(-1)(x)).
```

Thus hidden local bijections cannot improve information-theoretic security against
arbitrary metadata-aware leakage. The delayed-disclosure condition is a mathematical
boundary, not an implementation detail.
