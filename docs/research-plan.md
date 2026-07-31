# Publication-readiness plan

## Current milestone

Create a public, auditable research package containing the exact theorem statements, complete
paper proof, adversarial boundaries, and a primary-source novelty matrix. Public availability is
not a preprint publication and is not peer review.

## Correctness gates

- [x] Fix the security experiment and quantifier order.
- [x] Derive the field identity using explicit Fourier normalizations.
- [x] Derive the finite-abelian orbit identity.
- [x] Restrict the minimax lower bound to the range where the binary witness channel is valid.
- [x] Check constant and identity leakage channels.
- [x] State the public-randomizer cancellation attack.
- [ ] Obtain an independent line-by-line proof review from an information-theoretic
  cryptographer.
- [ ] Mechanize the finite-distribution identity or exhaustively verify it on small fields after
  resource constraints are lifted.
- [ ] Extend or sharply delimit shared-randomness and joint-leakage variants.

## Novelty gates

- [x] Compare with CRYPTO 2018 local leakage of linear secret sharing.
- [x] Compare with ITC 2022 tight additive-sharing leakage estimates.
- [x] Compare with CRYPTO 2021 adaptive leakage and reveal.
- [x] Compare with ITC 2022 equivocal secret sharing and data-at-rest leakage.
- [x] Compare with EUROCRYPT 2024 physical prime-field masking analysis.
- [x] Compare with current Hamming-weight leakage work.
- [ ] Read every proof and appendix of the two closest Fourier papers, not only their theorem
  statements and searchable text.
- [ ] Complete citation-forward and citation-backward searches for hidden preprocessing,
  post-leakage helper-data disclosure, randomized local encodings, channel symmetrization,
  and automorphism-orbit leakage.
- [ ] Ask at least two active leakage-resilient-secret-sharing researchers whether the exact
  orbit/minimax package has an antecedent.
- [ ] Freeze the novelty claim only after those checks.

## Significance gates

- [ ] Formalize a credible single-snapshot threat model with the recovery capsule stored in a
  separately protected component.
- [ ] Determine whether the construction gives a meaningful advantage under a standard noisy
  leakage metric, not only bounded output length.
- [ ] Quantify storage, randomness, and recovery costs.
- [ ] Prove a composable or sequential statement, or explain precisely why the contribution is
  intentionally one-shot.
- [ ] Decide whether the natural contribution is an ITC paper, a broader TCC paper, or a short
  note after expert feedback.

## Packaging gates

- [x] Maintain a standalone LaTeX source and bibliography.
- [ ] Compile with `latexmk -pdf -halt-on-error main.tex` from `paper/`.
- [ ] Inspect the PDF for overflow, broken references, and mathematical typography.
- [ ] Run a spelling and prose pass consistent with the target venue.
- [ ] Prepare an anonymous submission version and a separate public preprint version.
- [ ] Verify current venue page limits, deadlines, anonymity policy, and simultaneous-submission
  rules before submission.

## Commands deferred until resource constraints are lifted

From `paper/`:

```sh
latexmk -pdf -halt-on-error main.tex
```

From the repository root:

```sh
git diff --check
rg -n "TODO|FIXME|novel|first|optimal|secure|publication-ready" .
```

The second command is a claim audit, not a proof of correctness.
