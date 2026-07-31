# Research repository instructions

## Purpose

Develop and audit the mathematical and cryptographic claims concerning hidden local
automorphism randomization, one-shot local leakage, and delayed disclosure of recovery
metadata for additive secret sharing.

## Claim discipline

- Correctness takes precedence over novelty and presentation.
- Do not describe a theorem as novel, first, optimal, secure, practical, composable, or
  publication-ready unless the precise scope is proved and the claim is supported by a
  documented primary-source comparison.
- Distinguish public repository, manuscript draft, preprint, submitted manuscript, accepted
  paper, and publication as separate states.
- Record counterexamples, failed proof attempts, and narrowing assumptions in the audit files.
- Treat stochastic leakage channels as conditionally independent unless a theorem explicitly
  handles shared adversarial coins or joint leakage.
- State quantifier order in every security experiment. In particular, record whether leakage
  functions are selected before or after encoding randomness is sampled or disclosed.

## Sources

- Prefer peer-reviewed proceedings, journal versions, authors' manuscripts, and official
  conference metadata.
- Verify every bibliography entry against a primary or authoritative bibliographic source.
- Never fabricate a citation or infer theorem content from an abstract alone.
- Mark search coverage and unresolved novelty risks explicitly.

## Proof workflow

1. State definitions and normalization conventions.
2. Prove each analytic identity from those definitions.
3. Test degenerate parameters, maximal leakage, constant leakage, public-randomizer attacks,
   correlated leakage, and repeated-leakage variants.
4. Maintain `docs/proof-audit.md` as an independent static check of the manuscript.
5. Keep theorem labels synchronized across the manuscript and audit documents.

## Repository workflow

- The canonical branch is `master`.
- Keep the manuscript in `paper/` and research evidence in `docs/`.
- Do not commit generated LaTeX artifacts.
- Every completed tracked change requires static verification, a focused commit, and a push.
