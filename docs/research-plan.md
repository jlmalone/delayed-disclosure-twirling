# Publication-readiness plan

## Current milestone

Create a public, auditable research package containing the exact theorem statements, complete
paper proof, adversarial boundaries, and a primary-source novelty matrix. Public availability is
not a preprint publication and is not peer review.

## Correctness gates

- [x] Fix the security experiment and quantifier order.
- [x] Embed the transcript into the standard nonadaptive local-leakage game and record
      the designated-unauthorized-set limitation.
- [x] Derive the field identity using explicit Fourier normalizations.
- [x] Derive the finite-abelian orbit identity.
- [x] Prove the minimum-real-dual-orbit minimax theorem for arbitrary finite abelian
      groups throughout the conjugate-packet capacity range.
- [x] Derive the exact conjugate-packet energy capacity and an attaining finite-output
      channel for every character order.
- [x] Prove projective-transitivity optimality and the exact field-action projective
      entropy corollary, including strict-interior uniqueness via invertible packet
      convolution and the characteristic-two case.
- [x] Prove the all-feasible-energy minimax value for single-real-orbit actions using
      full-spectrum erasure channels.
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
- [x] Compare the stated models and contributions of CRYPTO 2023, EUROCRYPT 2025,
      ITC 2025, and the ASIACRYPT 2025 circulant-spectrum paper.
- [x] Compare with the ISIT 2024 arbitrary-noisy-channel analysis of Shamir sharing
      and derive the manuscript's arbitrary-prior mutual-information consequence.
- [x] Compare with the ASIACRYPT 2025 decomposition analysis of noisy leakage for
      additive masking over finite abelian groups.
- [x] Compare with current Hamming-weight leakage work.
- [ ] Obtain and read the subscription-only full text of Koga--Abe, ASIACRYPT 2025,
      and the SITA 2025 one-bit general-formula follow-up; abstract and program-level
      comparisons are not sufficient to clear the packet-extremizer claim.
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
- [x] Express the exact chi-square identity as an arbitrary-prior mutual-information
      bound for independent noisy channels; a comparative advantage over existing
      Shamir bounds remains to be demonstrated.
- [x] Quantify ideal capsule storage, fresh random entropy, share size, and recovery
      arithmetic for the field compiler; implementation-specific serialization and
      isolation costs remain open.
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
