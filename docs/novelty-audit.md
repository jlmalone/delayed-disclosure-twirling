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
6. a matching characteristic-two minimax attack and entropy characterization; and
7. a cancellation impossibility when leakage is metadata-aware.

This is a provisional gap statement, not a claim of novelty. The fixed-secret field
identity is a short consequence of established Fourier machinery once the hidden translation
and multiplier experiment is posed. The orbit and minimax package is the more credible source
of mathematical novelty.

## Closest primary literature

| Work | What is already established | Exact distinction still visible | Risk to claim |
|---|---|---|---|
| Benhamouda, Degwekar, Ishai, Rabin, CRYPTO 2018, [On the Local Leakage Resilience of Linear Secret Sharing Schemes](https://doi.org/10.1007/978-3-319-96884-1_18) | Local leakage for additive and Shamir sharing; Fourier and additive-combinatorial analysis; worst-case secret comparison. | The inspected material does not introduce hidden local automorphisms later disclosed or the stated chi-square/orbit minimax identity. | Very high. The central product-of-Fourier-coefficients mechanism is prior art. |
| Maji, Nguyen, Paskin-Cherniavsky, Suad, Wang, Ye, Yu, ITC 2022, [Tight Estimate of the Local Leakage Resilience of the Additive Secret-Sharing Scheme and Its Consequences](https://doi.org/10.4230/LIPIcs.ITC.2022.16) | Tight vulnerability estimates for additive sharing, physical-bit probing, and Fourier analysis. | Different leakage representation and no located delayed-capsule minimax theorem. | Very high. Appendices and lower-bound attacks require line-by-line comparison. |
| Maji et al., TCC 2022, [Leakage-resilient Linear Secret-sharing Against Arbitrary Bounded-size Leakage Family](https://doi.org/10.1007/978-3-031-22318-1_13) | Linear secret sharing against bounded families of joint leakage attacks; Fourier bottlenecks and non-Fourier techniques. | The adversarial class and construction objective differ from a one-shot hidden-randomizer identity. | Medium. It broadens the surrounding leakage landscape and may contain reusable lower-bound ideas. |
| Maji, Paskin-Cherniavsky, Suad, Wang, CRYPTO 2021, [Constructing Locally Leakage-resilient Linear Secret-sharing Schemes](https://www.cs.purdue.edu/homes/hmaji/papers/MPSW21.pdf) | Constructions of linear schemes and new tests for local leakage, using discrete Fourier analysis among other tools. | No located recovery-capsule chronology or automorphism-orbit optimization. | Medium to high. |
| Chandran, Kanukurthi, Obbattu, Sekar, CRYPTO 2021, [Adaptive Extractors and their Application to Leakage Resilient Secret Sharing](https://eprint.iacr.org/2020/1252) | An adaptive leakage-and-reveal model where leakage is obtained from some shares and other shares are later revealed in full; adaptive extractor machinery. | Their reveal phase exposes different shares, not hidden local-encoding metadata. Their adversary is adaptive, whereas the exact identity here needs metadata-oblivious local channels. | High model-overlap risk. The terminology must not imply that leakage followed by reveal is new. |
| Hu, Zhang, Wang, Dong, 2022, [On the Security Proof of CKO+21 Secret Sharing Scheme](https://eprint.iacr.org/2022/593) | Published criticism of the CRYPTO 2021 construction's security proof. | Not an antecedent to the present identity, but it prevents treating the earlier construction as an uncontested foundation. | High correctness-context relevance. The final publication must determine the current resolution of this critique. |
| Hazay, Venkitasubramaniam, Weiss, ITC 2022 and Journal of Cryptology 2025, [Protecting Distributed Primitives Against Leakage](https://doi.org/10.1007/s00145-024-09524-3) | Equivocal secret sharing, adaptive probing, later explanation/reveal behavior, linear reconstruction, and a data-at-rest motivation. | Their focus is probing leakage and equivocation; no located exact stochastic-channel twirling identity. | High model and motivation overlap. Their definitions and simulator order need detailed comparison. |
| Faust, Masure, Micheli, Orlt, Standaert, EUROCRYPT 2024, [Connecting Leakage-Resilient Secret Sharing to Practice](https://doi.org/10.1007/978-3-031-58737-5_12) | Exact Fourier expressions for prime-field masking, average and worst-case statistical metrics, and physical leakage scaling. | No hidden automorphism/capsule experiment was located. The present fixed-secret result may nevertheless be viewed as a simple symmetrization of their established formulas. | Critical significance risk. This is the closest bridge from Fourier theory to practical leakage. |
| Biswas, Hwang, Maji, Shkredov, Ye, current author-hosted draft, [Beyond Threshold Security: Additive Secret Sharing under Hamming-Weight Leakage](https://www.cs.purdue.edu/homes/hmaji/papers/BHMSY26.pdf) | Sharp additive-sharing results for Hamming-weight leakage using Fourier, complex-analytic, and matrix methods. | It studies a specific leakage function without the delayed recovery capsule. | Medium. It shows the frontier is moving and makes a simple generic Fourier note harder to position. |
| Calmon, Makhdoumi, Medard, Varia, Christiansen, Duffy, IEEE TIT 2017, [Principal Inertia Components and Applications](https://doi.org/10.1109/TIT.2017.2700857) | Spectral decomposition of dependence and privacy through the conditional-expectation operator. | No secret-sharing or delayed-disclosure result. | High ingredient-overlap risk for interpreting local chi-square information as total nonconstant spectral energy. |
| Makur, Polyanskiy, 2016 preprint, [Comparison of Channels: Criteria for Domination by a Symmetric Channel](https://arxiv.org/abs/1609.06877) | Chi-square characterizations of channel comparison and finite-abelian additive-noise channels. | No located local-secret-sharing product identity. | Medium. Broader channel-symmetrization literature remains incompletely searched. |

## What cannot be claimed

- Fourier analysis of local leakage is not new.
- Product formulas over the dual code of additive sharing are not new.
- Worst-case comparison between fixed secrets is not new.
- A leakage phase followed by a reveal phase is not new.
- Data-at-rest leakage protection is not a new motivation.
- Chi-square spectral energy and principal inertia are not new.
- The hidden translation by itself is not a substantial contribution: it converts a
  uniform-secret average into a fixed-secret transcript calculation by a direct relabeling.

## Defensible draft claim

Subject to completion of the search, the manuscript may claim to identify and exactly analyze
a specific hidden-local-randomization compiler for additive sharing in a one-snapshot,
post-snapshot-disclosure experiment. Its candidate contributions are:

- an exact channel-independent chi-square factorization;
- a dual-orbit formula for arbitrary finite abelian groups and automorphism subgroups;
- a minimax characterization over `GF(2^n)` showing that uniform relative multipliers defeat
  concentrated one-character leakage optimally within this compiler class; and
- a matching randomizer-entropy statement and metadata-aware impossibility boundary.

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

Primary or authoritative sources were preferred. Search-engine failure interrupted an earlier
expansion pass, but later targeted searches succeeded. Search results alone were not treated as
proof that a theorem is absent.

## Required remaining search

1. Read the complete CRYPTO 2018 and ITC 2022 proofs and appendices, tracking every exact
   identity and lower-bound witness.
2. Follow all works citing those papers through 2026, especially masking and physical-leakage
   papers.
3. Search information theory for group-averaged channels, invariant decision problems,
   Hunt-Stein symmetrization, and chi-square contraction identities.
4. Search leakage-resilient storage and preprocessing literature for hidden state that is
   revealed only after a bounded or one-time leak.
5. Search coding theory for random monomial equivalence or scalar scramblers analyzed against
   coordinatewise observation channels.
6. Obtain expert feedback from authors active in additive-sharing leakage before fixing the
   novelty language.

## Current assessment

The theorem package is plausible as a focused information-theoretic cryptography paper, but
the current material does not justify calling it a breakthrough. A submission needs either a
stronger model/classification theorem or a compelling concrete application in addition to the
exact identity.
