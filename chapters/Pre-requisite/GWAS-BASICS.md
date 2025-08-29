# 1. The GWAS Framework: Identifying Genetic Associations

## 1.1 The Core Logic of Genome-Wide Association Studies

A **genome-wide association study (GWAS)** is a powerful method used to
systematically scan the human genome to identify common genetic variants
associated with a particular trait or disease. The fundamental principle
involves genotyping a large cohort of individuals and then testing for a
statistical association between each genetic marker and the phenotype of
interest. The most common type of genetic marker analyzed is the
**single-nucleotide polymorphism (SNP)**, which is a variation at a
single base pair in the DNA sequence. The standard approach involves
testing millions of SNPs, often one at a time, using statistical models
such as additive regression
[REF](https://www.mv.helsinki.fi/home/mjxpirin/GWAS_course/material/GWAS2.html).

The output of a GWAS is not raw genotype data but a highly compressed
set of results known as “summary statistics.” These statistics provide a
comprehensive, aggregate overview of the association data for every
variant analyzed in the study. This aggregated format makes the data
from different studies interoperable and facilitates downstream
meta-analyses and other advanced statistical methods, such as LD Score
Regression (LDSC). The generation of these summary statistics is a
crucial step that transforms vast datasets into a manageable and
shareable format for the wider research community
[REF](https://www.ebi.ac.uk/gwas/docs/summary-statistics-format).

## 1.2 Dissecting GWAS Summary Statistics: The Language of Association

GWAS summary statistics are a concise representation of the results for
each tested SNP. The primary components provided by an additive
regression model for each variant are the effect size estimate
`($\hat\beta$)`, `its standard error (SE)`, and a `p-value`. These three
metrics are intrinsically linked and provide a complete picture of the
association signal for a given SNP
[REF](https://www.mv.helsinki.fi/home/mjxpirin/GWAS_course/material/GWAS2.html).

### 1.2.1 P-values and the Challenge of Multiple Testing

The **p-value** is a central summary statistic in GWAS, serving as a
numerical summary of the consistency between the observed data and the
null hypothesis. In the context of GWAS, the **null hypothesis states
that the genetic variant has an effect size of exactly zero and is
therefore not associated with the trait**. A **p-value is the
probability of obtaining a result at least as extreme as the one
observed, assuming this null hypothesis is true**. Consequently, a very
small p-value is interpreted as strong evidence against the null
hypothesis, suggesting that an association likely exists.
([REF](https://www.mv.helsinki.fi/home/mjxpirin/GWAS_course/material/GWAS2.html)).

The interpretation of **p-values in GWAS is complicated by the challenge
of multiple hypothesis testing**. Because millions of SNPs are tested
simultaneously, there is a high probability of **finding significant
associations purely by chance, even if no true associations exist**. For
instance, with a **standard p-value threshold of 0.05, a study with one
million independent tests would expect 50,000 false positives**. To
address this issue, GWAS employs a far more **stringent significance
threshold, typically 5 × 10<sup>8</sup>**. This empirical cutoff is
roughly equivalent to a **conservative Bonferroni correction for one
million independent tests**, ensuring that very few of the identified
“hits” are false discoveries. The **p-value’s primary role is to
evaluate the evidence for a non-zero effect, but it does not convey
information about the magnitude of that effect**.
