# Session handoff

Updated: 2026-08-05.

## Current state

- The public repository is `jlmalone/delayed-disclosure-twirling` on canonical branch
  `master`.
- The manuscript contains the field identity, finite-abelian orbit formulas, scoped
  minimax results, field-multiplier classification, resource accounting, and the
  metadata-aware cancellation boundary.
- `docs/model.md`, `docs/proof-audit.md`, and `docs/novelty-audit.md` record the model,
  independent static derivations, counterexamples, and closest known work.
- Static source checks passed during the research session. The LaTeX manuscript has
  not been compiled, rendered, or independently reviewed.
- This is a public research draft. It is not a submitted paper, accepted paper,
  certified novelty result, or publication-ready artifact.

There is no uncommitted implementation or hidden local artifact required to resume the
project. It is safe to end the current session after this handoff is pushed.

## Submission blockers

1. Obtain and read the complete Koga--Abe ASIACRYPT 2025 chapter and SITA 2025
   one-bit follow-up. Perform a proof-level comparison with the packet-capacity lemma
   and randomizer minimax theorems. Abstract-level comparison is insufficient.
2. Obtain an independent line-by-line review from an information-theoretic
   cryptographer. The fixed-secret identity, real-orbit reduction, packet-capacity
   calculation, arbitrary-group minimax lower bound, and strict-interior convolution
   argument are the highest-priority proof targets.
3. After resource constraints are lifted, compile `paper/main.tex`, inspect the PDF,
   and repair any citation, overflow, reference, or typography defects.
4. Exhaustively verify the finite-distribution identities on small fields or mechanize
   them. Treat this as validation, not as a replacement for proof review.
5. Resolve positioning: either supply a credible separately protected single-snapshot
   capsule application, prove a broader security statement, or deliberately target a
   focused information-theoretic note. Do not imply composability or full LRSS security.
6. Only after the preceding gates, choose a venue, verify its current rules, and prepare
   distinct anonymous-submission and public-preprint versions.

## Exact next step

Acquire the two Koga--Abe full texts and update `docs/novelty-audit.md` with a theorem-by-
theorem comparison. If either paper subsumes the packet extremizer or orbit/minimax
claim, narrow or withdraw that claim before spending effort on submission formatting.

The complete gate list and deferred commands remain in `docs/research-plan.md`.

## Do not overstate

- The disclosure chronology is a security assumption: leakage channels are selected
  without the recovery capsule, one snapshot is taken, and only then is the capsule
  disclosed.
- Capsule-aware leakage can invert the local bijections and recover a standard
  character attack.
- The standard-game embedding covers one designated unauthorized capsule component,
  not every unauthorized set required of a general leakage-resilient secret-sharing
  construction.
- Existing literature already contains Fourier product mechanisms, noisy stochastic
  leakage, additive-group masking, projection decompositions, erasure witnesses, and
  randomized multipliers. Any defensible novelty claim must remain confined to the
  exact hidden-automorphism and capsule-conditioned orbit/minimax package.
