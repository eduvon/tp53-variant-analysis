# Biological Interpretation

## Overview

The primary analysis investigated whether predicted molecular consequences of
TP53 variants were associated with their clinical significance classifications
in ClinVar.

The analysis focused on four consequence categories:

- Missense
- Frameshift
- Stop gained
- Canonical splice site

For the primary statistical analysis, variants classified by ClinVar as
**Pathogenic** were compared with variants classified as **Uncertain**. VEP
annotations were evaluated on the TP53 MANE Select transcript
(`NM_000546.6`).

The goal was not to determine whether a particular consequence *causes*
pathogenicity, but to investigate whether particular molecular consequence
types are associated with different clinical classification patterns.

---

## Results

The descriptive analysis showed substantial differences between the Pathogenic
and Uncertain groups:

| Consequence | Pathogenic | Uncertain |
|---|---:|---:|
| Missense | 11.2% | 64.8% |
| Frameshift | 66.8% | 7.8% |
| Stop gained | 12.0% | 0.3% |
| Canonical splice site | 5.5% | 1.4% |

The corresponding odds-ratio analysis produced the following results:

| Consequence | Odds Ratio | 95% CI | Adjusted p-value |
|---|---:|---:|---:|
| Missense | 0.068 | 0.053–0.089 | 5.00 × 10⁻¹¹⁹ |
| Frameshift | 23.820 | 17.962–31.589 | 7.49 × 10⁻¹⁵³ |
| Stop gained | 43.089 | 13.578–136.745 | 1.96 × 10⁻²⁹ |
| Canonical splice site | 4.222 | 2.245–7.939 | 1.95 × 10⁻⁶ |

Odds ratios greater than 1 indicate higher odds of the consequence being
present in the Pathogenic group relative to the Uncertain group. An odds ratio
less than 1 indicates higher odds in the Uncertain group.

All four associations remained statistically significant after
Benjamini-Hochberg correction for multiple comparisons.

---

## Missense Variants

Missense variants showed the opposite pattern from the truncating consequence
categories. A missense consequence was reported for 11.2% of Pathogenic
variants compared with 64.8% of Uncertain variants.

This does **not** indicate that missense variants are inherently less
pathogenic than frameshift variants. Instead, it suggests that missense
variants represented a much larger proportion of the Uncertain group in this
ClinVar dataset.

A missense variant changes a single amino acid while generally leaving the
overall length of the protein unchanged. The functional effect of the change
can therefore vary substantially depending on the affected residue and its
structural and functional context.

For example, an amino-acid substitution occurring in an important functional
domain may disrupt protein structure, stability, molecular interactions, or
DNA binding, while another substitution may have little measurable effect.

Consequently, the classification of individual missense variants may require
evidence beyond the predicted consequence itself, such as functional,
structural, population, or clinical evidence.

This provides a biologically plausible explanation for why missense
consequences are strongly represented among variants of Uncertain significance.

---

## Frameshift Variants

Frameshift consequences showed a strong association with the Pathogenic group.

Approximately 66.8% of Pathogenic variants had a frameshift consequence,
compared with 7.8% of Uncertain variants. The resulting odds ratio was 23.82
(95% CI: 17.96–31.59).

A frameshift occurs when an insertion or deletion changes the reading frame of
a coding sequence. Because codons are read in groups of three nucleotides, a
shift in the reading frame changes the interpretation of downstream codons.

Conceptually:

    DNA insertion/deletion
            ↓
       reading-frame shift
            ↓
    altered downstream codons
            ↓
    potentially abnormal protein
            ↓
    possible loss of normal function

Frameshift variants can therefore produce substantial changes to the
resulting protein and may introduce a premature termination codon.

For a tumor-suppressor gene such as TP53, substantial disruption of normal
protein function provides a biologically plausible mechanism for the strong
association observed between frameshift consequences and Pathogenic
classification.

However, the statistical analysis itself establishes an association with
ClinVar classification; it does not demonstrate that every frameshift variant
causes loss of function or that loss of function is responsible for the
clinical classification of every variant.

---

## Stop-Gained Variants

Stop-gained variants also showed a strong association with the Pathogenic
group.

A stop-gained consequence was present in 12.0% of Pathogenic variants but only
0.3% of Uncertain variants. The estimated odds ratio was 43.09
(95% CI: 13.58–136.74).

A stop-gained variant introduces a premature termination codon:

    DNA variant
         ↓
    premature STOP
         ↓
    truncated protein

Depending on its position and transcript context, a premature stop can result
in a shortened protein or trigger degradation of the affected transcript.

This provides a straightforward biological mechanism by which a stop-gained
variant could substantially disrupt TP53 function.

The stop-gained estimate should nevertheless be interpreted with some caution.
Only three Uncertain variants in the analyzed dataset had a stop-gained
consequence. The association is therefore statistically strong, but the wide
confidence interval indicates that the precise magnitude of the association
is estimated less precisely than for some of the other consequence
categories.

---

## Canonical Splice-Site Variants

Canonical splice-site variants were also more strongly associated with the
Pathogenic group.

A canonical splice-site consequence was present in 5.5% of Pathogenic variants
and 1.4% of Uncertain variants, producing an odds ratio of 4.22
(95% CI: 2.25–7.94).

The biological mechanism differs from that of a simple coding substitution.
A splice-site variant changes DNA at a position important for normal
pre-mRNA splicing:

    DNA variant
         ↓
    altered splice-site recognition
         ↓
    abnormal RNA processing
         ↓
    altered mature mRNA
         ↓
    potentially altered protein

Possible consequences include exon skipping, intron retention, or use of an
abnormal splice site.

Importantly, a splice-site variant does not automatically imply that the final
protein will be altered in a particular way. The actual consequence depends on
how RNA processing is affected in the relevant transcript and cellular
context.

In this project, the primary splice-site category was deliberately restricted
to VEP's canonical `splice_acceptor_variant` and `splice_donor_variant`
consequences. Other splice-related annotations were not included in this
primary grouping.

---

## Why the Missense Pattern Is Different

One of the most interesting features of the analysis is the contrast between
missense and truncating or splice-altering consequences.

Missense consequences were much more prevalent among Uncertain variants,
whereas frameshift, stop-gained, and canonical splice-site consequences were
more prevalent among Pathogenic variants.

A possible biological explanation is that these consequence classes provide
different amounts of information about functional disruption.

A frameshift or premature stop can produce a large and readily interpretable
change to a protein or transcript. A single amino-acid substitution, however,
can range from functionally negligible to severely disruptive.

This does not mean that missense variants are generally less important in
TP53 biology. Rather, it suggests that **the molecular consequence label alone
provides different amounts of information for different classes of variants**.

In particular, the effect of a TP53 missense variant may depend strongly on the
position of the affected residue, its structural environment, and its role in
protein function.

---

## ClinVar and Cancer Biology Are Different Questions

These results should not be interpreted as a description of the mutation
spectrum of TP53 in cancer.

This project uses **ClinVar**, a database of clinical variant
interpretations. The analysis therefore asks a question about the relationship
between molecular consequence annotations and clinical classifications in the
ClinVar dataset.

A different dataset, such as a catalog of somatic mutations observed in
tumors, would address a different question.

For example:

    This project:
    TP53 consequence + ClinVar classification
                    ↓
          clinical association

    Cancer mutation analysis:
    TP53 mutation + tumor data
                    ↓
        cancer mutation spectrum

The two analyses can reveal different patterns without contradicting one
another.

Therefore, the strong association between frameshift consequences and
Pathogenic classification in this ClinVar analysis should not be interpreted
as evidence that frameshift mutations are more important than missense
mutations in TP53 cancer biology.

---

## Limitations

### Association Is Not Causation

The statistical analysis identifies associations between VEP consequence
categories and ClinVar classifications. It does not establish a causal
relationship between a particular molecular consequence and pathogenicity.

The biological interpretations presented here are mechanistic explanations
that are consistent with the observed statistical patterns.

### ClinVar Classifications Are Interpretations

ClinVar aggregates clinical variant interpretations rather than providing a
single direct experimental measurement of biological function.

Different submitters may evaluate the same variant using different evidence or
interpretation criteria. As a result, conflicting or uncertain classifications
can occur.

The Uncertain group should therefore not be treated as a biologically uniform
class.

### Classification Is Variant-Specific

A consequence category such as "missense" or "frameshift" describes a class of
molecular change, not the complete biological effect of every variant in that
class.

The effect of an individual TP53 variant can depend on its precise location,
transcript context, protein domain, and other biological factors.

### Transcript Context Matters

A genomic variant can have different consequences on different transcripts.

This analysis therefore examined both the full set of TP53 transcript
annotations and the standardized MANE Select transcript. The broad pattern
was similar between the two approaches for the four primary consequence
categories.

The primary statistical analysis used the MANE Select transcript to provide a
consistent transcript context across variants.

---

## Overall Interpretation

Taken together, the analysis demonstrates a biologically meaningful
relationship between molecular variant consequences and clinical
classification within the analyzed ClinVar TP53 dataset.

Frameshift, stop-gained, and canonical splice-site consequences were strongly
associated with Pathogenic classification, while missense consequences were
more prevalent among variants classified as Uncertain.

These patterns are biologically plausible because truncating and splice-altering
variants can substantially disrupt gene expression or protein structure,
whereas the functional effect of a missense substitution can vary widely
between individual variants.

The results also illustrate an important principle of computational biology:
**variant annotation provides a bridge between raw genomic sequence and
biological or clinical interpretation, but molecular consequence predictions
must be interpreted in the context of the underlying biology and the
limitations of the clinical dataset.**