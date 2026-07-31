# Novelty audit

Last updated: 2026-07-31.

## Provisional result

No inspected source states the full package currently proved in this repository:

1. hidden local translation and automorphisms applied to additive shares;
2. one-shot local stochastic leakage selected without the hidden metadata;
3. disclosure of that metadata after the snapshot;
4. an exact fixed-secret chi-square identity expressed solely through the local
   chi-square informations;
5. a finite-abelian dual-orbit decomposition;
6. a matching minimum-real-dual-orbit minimax theorem for arbitrary finite abelian
   groups throughout an explicit character-order-dependent budget range, including
   the exact conjugate-packet capacity and projective field-multiplier entropy
   characterization;
7. an all-feasible-energy minimax identity when the automorphisms and inversion have
   one nontrivial dual orbit, together with a complete projective-randomizer
   classification for field multipliers at every strictly interior budget; and
8. a cancellation impossibility when leakage is metadata-aware.

This is a provisional gap statement, not a claim of novelty. The fixed-secret field
identity is a short consequence of established Fourier machinery once the hidden translation
and multiplier experiment is posed. The orbit and minimax package is the more credible source
of mathematical novelty.

## Closest primary literature

| Work | What is already established | Exact distinction still visible | Risk to claim |
|---|---|---|---|
| Benhamouda, Degwekar, Ishai, Rabin, CRYPTO 2018, [On the Local Leakage Resilience of Linear Secret Sharing Schemes](https://doi.org/10.1007/978-3-319-96884-1_18) | Local leakage for additive and Shamir sharing; Poisson summation over a dual code; Theorem 4.7 bounds additive-sharing leakage; Section 6 proves impossibility of some noninteractive local share conversions. | The inspected proofs do not introduce hidden local automorphisms later disclosed or the stated chi-square/orbit minimax identity. The present compiler preserves the share alphabet and relies on separate recovery state, so it is not a local share conversion in their sense. | Very high. The central product-of-Fourier-coefficients mechanism is prior art, and the extra capsule must be treated as a real resource. |
| Maji, Nguyen, Paskin-Cherniavsky, Suad, Wang, Ye, Yu, ITC 2022, [Tight Estimate of the Local Leakage Resilience of the Additive Secret-Sharing Scheme and Its Consequences](https://doi.org/10.4230/LIPIcs.ITC.2022.16) | Tight vulnerability estimates for additive sharing and the parity-of-parity physical-bit attack. Lemma 12 reuses Poisson summation and the proof exploits the repetition dual code. | Different leakage representation and no delayed capsule, automorphism, multiplier, orbit, or randomized-encoding construction located in the searchable paper text. | Very high. Its exact lower-bound attack confirms that common-character alignment is established prior art. |
| Koga, Abe, ASIACRYPT 2025, [New Tight Bounds on the Local Leakage Resilience of the Additive (n,n)-Threshold Scheme Determined by the Eigenvalues of Circulant Matrices](https://doi.org/10.1007/978-981-95-5125-5_2) | Ordinary additive sharing over prime fields; worst-case pairwise total variation over deterministic `L`-ary local leakage; a tight asymptotic order and extremizer classification for `L=2`; a majorization bound for `L>=3`. | The publisher abstract states no per-sharing hidden randomizer, delayed capsule, stochastic-channel chi-square identity, automorphism orbit, or randomizer minimax. The full chapter is subscription-only and no author or ePrint copy was located, so a proof-level distinction is not yet established. | Critical unresolved risk. Its circulant eigenvalues are the same Fourier spectrum in matrix form, and its extremizers may overlap the packet-capacity lemma. |
| Maji et al., TCC 2022, [Leakage-resilient Linear Secret-sharing Against Arbitrary Bounded-size Leakage Family](https://doi.org/10.1007/978-3-031-22318-1_13) | Linear secret sharing against bounded families of joint leakage attacks; Fourier bottlenecks and non-Fourier techniques. | The adversarial class and construction objective differ from a one-shot hidden-randomizer identity. | Medium. It broadens the surrounding leakage landscape and may contain reusable lower-bound ideas. |
| Maji, Paskin-Cherniavsky, Suad, Wang, CRYPTO 2021, [Constructing Locally Leakage-resilient Linear Secret-sharing Schemes](https://www.cs.purdue.edu/homes/hmaji/papers/MPSW21.pdf) | Constructions of linear schemes and new tests for local leakage, using discrete Fourier analysis among other tools. | No located recovery-capsule chronology or automorphism-orbit optimization. | Medium to high. |
| Srinivasan, Vasudevan, CRYPTO 2019, [Leakage Resilient Secret Sharing and Applications](https://doi.org/10.1007/978-3-030-26951-7_17) | Standard local leakage with an unauthorized set revealed in full; a general compiler for monotone access structures with asymptotically optimal leakage rate. Leakage functions in the basic notion are fixed independently of revealed shares. | Treating the capsule as an oversized share makes the present transcript a designated-unauthorized-set instance of their standard game, but the exact structured chi-square/orbit calculation is not located there. | Critical significance risk. Their compiler has far stronger rate and access-structure guarantees; this work cannot claim a new model or general LRSS compiler. |
| Chandran, Kanukurthi, Obbattu, Sekar, CRYPTO 2021, [Adaptive Extractors and their Application to Leakage Resilient Secret Sharing](https://eprint.iacr.org/2020/1252) | An adaptive leakage-and-reveal model where leakage is obtained from some shares and other shares are later revealed in full; adaptive extractor machinery. | Their reveal phase exposes different shares, not hidden local-encoding metadata. Their adversary is adaptive, whereas the exact identity here needs metadata-oblivious local channels. | High model-overlap risk. The terminology must not imply that leakage followed by reveal is new. |
| Hu, Zhang, Wang, Dong, 2022, [On the Security Proof of CKO+21 Secret Sharing Scheme](https://eprint.iacr.org/2022/593) | Published criticism of the CRYPTO 2021 construction's security proof. | Not an antecedent to the present identity, but it prevents treating the earlier construction as an uncontested foundation. | High correctness-context relevance. The final publication must determine the current resolution of this critique. |
| Hazay, Venkitasubramaniam, Weiss, ITC 2022 and Journal of Cryptology 2025, [Protecting Distributed Primitives Against Leakage](https://doi.org/10.1007/s00145-024-09524-3) | Equivocal secret sharing, adaptive probing, later explanation/reveal behavior, linear reconstruction, and a data-at-rest motivation. | Their focus is probing leakage and equivocation; no located exact stochastic-channel twirling identity. | High model and motivation overlap. Their definitions and simulator order need detailed comparison. |
| Faust, Masure, Micheli, Orlt, Standaert, EUROCRYPT 2024, [Connecting Leakage-Resilient Secret Sharing to Practice](https://doi.org/10.1007/978-3-031-58737-5_12) | Exact Fourier expressions for prime-field masking, average and worst-case statistical metrics, and physical leakage scaling. Appendix B explicitly uses equal magnitudes at conjugate harmonics for real leakage. | No hidden automorphism/capsule experiment or automorphism-orbit minimax theorem was located. The present fixed-secret and real-orbit formulas may nevertheless be viewed as simple reorganizations of established Fourier facts. | Critical significance risk. This is the closest bridge from Fourier theory to practical leakage, and conjugate-energy symmetry is explicitly prior art. |
| Jahandideh, Mennink, Batina, ASIACRYPT 2025, [A Decomposition Approach for Evaluating Security of Masking](https://eprint.iacr.org/2025/270) | Probabilistic noisy leakage from ordinary additive masks; binary-projection decomposition and tight success-rate bounds in characteristic two; prime-field analysis; a finite-abelian-group security threshold; erasure/random-probing comparison; physical leakage certification. | Its core mask shares are not freshly transformed by a hidden automorphism distribution later disclosed, and it does not state the capsule-conditioned chi-square orbit identity or minimize over automorphism laws. | Critical significance and ingredient risk. Noisy channels, additive groups, projection spectra, erasure witnesses, and practical masking-order interpretation are all prior art. The manuscript's defensible scope is narrower than a new theory of group masking. |
| Nguyen, EUROCRYPT 2025, [Physical-Bit Leakage Resilience of Linear Code-Based Secret Sharing](https://doi.org/10.1007/978-3-031-91101-9_3) | A perfect-security/complete-insecurity dichotomy for physical-bit leakage over binary extension fields, a minimal-dual-codeword characterization, and a Monte Carlo GRS construction with randomized multipliers. | The accessible primary slides use random multipliers to select fixed code parameters, not fresh hidden local encodings with later disclosure. The leakage family and security criterion are also different. | Critical terminology and ingredient risk. Random multipliers in leakage-resilient secret-sharing design cannot be claimed as new. |
| Hwang, Maji, Nguyen, Ye, ITC 2025, [Leakage-Resilience of Shamir's Secret Sharing: Identifying Secure Evaluation Places](https://doi.org/10.4230/LIPIcs.ITC.2025.3) | Algorithms and explicit regimes for classifying Shamir evaluation places under physical-bit probes, using square-wave orthogonality and arithmetic structure. | Fixed Shamir evaluation places and physical-bit leakage differ from per-sharing hidden automorphisms and arbitrary stochastic local channels. | High frontier risk. It shows that choosing algebraic action parameters to disrupt leakage correlations is an active line. |
| Gupta, Mahdavifar, ISIT 2024, [Bounds on the Statistical Leakage-Resilience of Shamir's Secret Sharing](https://doi.org/10.1109/ISIT57864.2024.10619359) | Independent arbitrary noisy leakage channels in a wiretap formulation; bounds for mutual-information, semantic, and distinguishing leakage of Shamir sharing, including specialized binary-symmetric-channel analysis. | It bounds leakage of a fixed Shamir scheme and does not state a hidden per-sharing automorphism distribution, delayed capsule, exact fixed-secret chi-square factorization, or dual-orbit minimax problem. | High terminology and metric risk. General stochastic local channels and information-leakage formulations are prior art; only the exact structured identity and optimization can distinguish this manuscript. |
| Klein, Komargodski, CRYPTO 2023, [New Bounds on the Local Leakage Resilience of Shamir's Secret Sharing Scheme](https://doi.org/10.1007/978-3-031-38557-5_5), and Maji, Nguyen, Paskin-Cherniavsky, Ye, EUROCRYPT 2024, [Composite Order Fields](https://doi.org/10.1007/978-3-031-58737-5_11) | Improved Shamir leakage bounds and constructions over additional field regimes. | They optimize the underlying sharing scheme or its fixed public parameters, not a hidden one-snapshot recovery capsule. | Medium to high. They constrain significance claims relative to stronger full LRSS results. |
| Biswas, Hwang, Maji, Shkredov, Ye, current author-hosted draft, [Beyond Threshold Security: Additive Secret Sharing under Hamming-Weight Leakage](https://www.cs.purdue.edu/homes/hmaji/papers/BHMSY26.pdf) | Sharp additive-sharing results for Hamming-weight leakage using Fourier, complex-analytic, and matrix methods. | It studies a specific leakage function without the delayed recovery capsule. | Medium. It shows the frontier is moving and makes a simple generic Fourier note harder to position. |
| Calmon, Makhdoumi, Medard, Varia, Christiansen, Duffy, IEEE TIT 2017, [Principal Inertia Components and Applications](https://doi.org/10.1109/TIT.2017.2700857) | Spectral decomposition of dependence and privacy through the conditional-expectation operator. | No secret-sharing or delayed-disclosure result. | High ingredient-overlap risk for interpreting local chi-square information as total nonconstant spectral energy. |
| Makur, Polyanskiy, 2016 preprint, [Comparison of Channels: Criteria for Domination by a Symmetric Channel](https://arxiv.org/abs/1609.06877) | Chi-square characterizations of channel comparison and finite-abelian additive-noise channels. | No located local-secret-sharing product identity. | Medium. Broader channel-symmetrization literature remains incompletely searched. |

## What cannot be claimed

- Fourier analysis of local leakage is not new.
- Product formulas over the dual code of additive sharing are not new.
- Impossibility phenomena for noninteractive local share conversion are not new.
- Worst-case comparison between fixed secrets is not new.
- A leakage phase followed by a reveal phase is not new.
- The nonadaptive game in which an unauthorized share is fully revealed and local
  leakage functions on other shares are fixed independently is not new.
- Data-at-rest leakage protection is not a new motivation.
- Chi-square spectral energy and principal inertia are not new.
- Equal Fourier energy at conjugate characters for real leakage functions is not new.
- Independent arbitrary stochastic/noisy local leakage channels and mutual-information
  leakage metrics for Shamir sharing are not new.
- Noisy leakage analysis for ordinary additive masking over finite abelian groups,
  projection-based decompositions, and erasure/random-probing witnesses are not new.
- The hidden translation by itself is not a substantial contribution: it converts a
  uniform-secret average into a fixed-secret transcript calculation by a direct relabeling.

## Defensible draft claim

Subject to completion of the search, the manuscript may claim to identify and exactly analyze
a specific hidden-local-randomization compiler for additive sharing in a one-snapshot,
post-snapshot-disclosure experiment. Its candidate contributions are:

- an exact channel-independent chi-square factorization;
- dual-orbit and real-orbit formulas for arbitrary finite abelian groups and automorphism
  subgroups;
- a minimax classification for arbitrary finite abelian groups showing that the smallest
  inversion-closed dual orbit exactly determines worst-case leakage within the
  local-automorphism compiler class throughout the exact energy range attainable by a
  channel supported on one smallest-orbit conjugate packet;
- an exact trigonometric formula for that packet capacity as a function of character
  order;
- optimality of projectively transitive actions on elementary abelian groups, with an
  exact projective field-multiplier entropy statement and a strict-interior
  classification obtained from invertible packet convolution;
- an all-energy minimax value for single-real-orbit actions, using a full-spectrum
  erasure witness; and
- a metadata-aware impossibility boundary.

The compiler should not be described as a new leakage-resilient secret-sharing scheme:
when the capsule is treated as a share, the theorem proves security only for one designated
unauthorized set, not all unauthorized sets.

The words "first", "novel", "optimal" without a scope qualifier, "practical", and
"composable" should not appear in an abstract until the remaining gates close.

## Search ledger

Searches performed through 2026-07-31 included combinations of:

- additive secret sharing, local leakage, Fourier, Parseval, and chi-square;
- leakage-and-reveal, delayed disclosure, helper data, and after-the-fact leakage;
- leakage-resilient storage, preprocessing, public randomness, and randomized encoding;
- finite abelian groups, automorphism actions, orbit energy, channel symmetrization, and
  principal inertia components;
- Singer cycles, random multipliers, minimax leakage, and seed entropy.
- circulant-matrix eigenvalues and extremizing local leakage functions;
- randomized GRS multipliers, secure Shamir evaluation places, and binary-image
  dual-code characterizations.
- arbitrary noisy share channels, wiretap formulations, mutual-information leakage,
  and semantic leakage for Shamir sharing.
- decomposition-based noisy-leakage analysis for additive groups, group quotients,
  and erasure/random-probing reductions.

Primary or authoritative sources were preferred. Search-engine failure interrupted an earlier
expansion pass, but later targeted searches succeeded. Search results alone were not treated as
proof that a theorem is absent.

## Required remaining search

1. Obtain and inspect the complete Koga--Abe ASIACRYPT 2025 chapter and their
   Japanese-language SITA 2025 one-bit general-formula paper. Publisher abstracts
   and program metadata are insufficient to exclude overlap with the packet
   extremizer or a disguised randomization theorem.
2. Finish the complete CRYPTO 2018 and ITC 2022 appendix audit. The additive-sharing
   Fourier proofs, Poisson-summation lemmas, ITC parity-of-parity lower bound, and CRYPTO
   local-conversion section have been inspected; unrelated appendices remain to be ruled out.
3. Follow all works citing those papers through 2026, especially masking and physical-leakage
   papers.
4. Search information theory for group-averaged channels, invariant decision problems,
   Hunt-Stein symmetrization, and chi-square contraction identities.
5. Search leakage-resilient storage and preprocessing literature for hidden state that is
   revealed only after a bounded or one-time leak.
6. Search coding theory for random monomial equivalence or scalar scramblers analyzed against
   coordinatewise observation channels.
7. Obtain expert feedback from authors active in additive-sharing leakage before fixing the
   novelty language.

## Current assessment

The theorem package is plausible as a focused information-theoretic cryptography paper. The
real-orbit classification, exact packet capacity, all-energy single-orbit minimax value, and
strict-interior uniqueness theorem are materially stronger than the initial field-only identity.
The inaccessible Koga--Abe full texts are now the largest novelty-review risk. The current material
still does not justify calling the work a breakthrough. A submission needs that comparison,
independent proof review, and either a compelling concrete application or a broader security-model
result in addition to the exact classification.
