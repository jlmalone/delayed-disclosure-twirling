# Delayed-Disclosure Twirling for Additive Secret Sharing

This repository develops an information-theoretic analysis of additive secret sharing when
local share encodings are randomized by hidden metadata, leakage is obtained once, and the
recovery metadata is disclosed only after that leakage snapshot.

The central candidate result is an exact fixed-secret chi-square identity for arbitrary
conditionally independent local stochastic leakage channels. The project also studies a
finite-abelian-group orbit decomposition, minimax optimality of uniform field multipliers,
and the impossibility of obtaining the same protection when leakage functions can depend on
the randomizer.

## Status

Research draft. The proofs have received a static adversarial pass, but the manuscript has
not yet received independent expert review. The novelty search is active and explicitly
incomplete. Nothing in this repository should be represented as accepted, published, or
certified novel.

## Repository map

- `paper/main.tex`: manuscript source.
- `paper/references.bib`: verified bibliography entries used by the manuscript.
- `docs/model.md`: security experiment, quantifier order, and excluded attacks.
- `docs/proof-audit.md`: independent derivation checks and edge cases.
- `docs/novelty-audit.md`: closest-known-result matrix and search ledger.
- `docs/research-plan.md`: concrete gates between the current draft and submission.

## Core claim, informally

Let a secret in a finite field of size \(Q\) be additively shared among \(d\) parties. Translate
one share by a hidden uniform field element and multiply each other share by an independent
hidden uniform nonzero field element. Let party \(i\)'s one-shot leakage channel have local
chi-square information \(e_i\) under a uniform input. If the recovery metadata is disclosed
only after leakage, then for every fixed secret the transcript has exact chi-square divergence

\[
\frac{\prod_{i=1}^d e_i}{(Q-1)^{d-1}}
\]

from the product of its public-metadata and local-leakage marginals.

The delayed-disclosure condition is essential. A leakage function that knows a local bijection
can invert it before applying any attack on the original share.

## Verification state

The active resource-constrained window prohibits compiling the LaTeX manuscript or executing
verification code. Only source inspection, proof checking, repository checks, commits, and the
requested Git push are permitted. Exact future verification commands are recorded in
`docs/research-plan.md`.
