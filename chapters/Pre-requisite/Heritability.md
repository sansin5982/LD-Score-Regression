# Deconstructing Heritability: From Family Studies to Genomic Estimates

## Heritability: A Statistical Concept, Not an Individual Metric

Heritability is a statistical concept that quantifies the proportion of
variation in a trait within a population that can be attributed to
inherited genetic factors. It is often expressed as a value between 0
and 1, or as a percentage. A heritability estimate close to zero
indicates that environmental factors are the primary drivers of trait
variability, while a value close to one suggests that genetic
differences are the dominant influence
([REF](https://medlineplus.gov/genetics/understanding/inheritance/heritability/),
[REF](https://www.cancer.gov/publications/dictionaries/genetics-dictionary/def/heritability)).

A critical point of clarification is that heritability is a
population-specific measure and cannot be applied to individuals. For
example, a heritability of 0.7 for height does not mean that an
individual’s height is 70% determined by their genes. Instead, it means
that 70% of the observed differences in height among people in that
specific population are due to genetic differences between them.
Furthermore, heritability estimates are specific to a particular
environment and population and can change over time as circumstances
change. Heritability also does not imply that a trait is unchangeable;
for instance, hair color has high heritability, but it can be easily
changed with dye
([REF](https://medlineplus.gov/genetics/understanding/inheritance/heritability/),
[REF](https://www.cancer.gov/publications/dictionaries/genetics-dictionary/def/heritability)).

## Narrow-Sense vs. Broad-Sense Heritability: Understanding the Genetic Components

In quantitative genetics, the total phenotypic variance
(*V*<sub>*P*</sub>) of a trait is partitioned into genetic variance
(*V*<sub>*G*</sub>) and environmental variance (*V*<sub>*E*</sub>).

$$
\large V\_P = V\_G + V\_E
$$

Broad-sense heritability (*H*<sup>2</sup>) is the ratio of the total
genetic variance to the total phenotypic variance
$(H^2 = \frac{V\_G}{V\_P})$. This measure captures all genetic effects,
including additive, dominance, and gene-gene interactions (epistasis).
It is a flexible measure but provides no information on the nature of
the genetic effects ([REF](https://www.youtube.com/watch?v=dSFNb5T2Ml0),
[REF](https://www.nealelab.is/blog/2017/9/13/heritability-201-types-of-heritability-and-how-we-estimate-it)).

Narrow-sense heritability (*h*<sup>2</sup>) s a more specific and widely
used measure, defined as the proportion of phenotypic variance that is
attributable only to additive genetic effects
$(h^2 = \frac{V\_A}{V\_P})$
([REF](https://pubmed.ncbi.nlm.nih.gov/28854176/#:~:text=Narrow%2Dsense%20heritability%20(h2,generated%20by%20all%20causal%20variants.),%20%5BREF%5D(https://www.youtube.com/watch?v=dSFNb5T2Ml0)).
Additive genetic variance represents the average effect of substituting
one allele for another. This is the component of genetic variance that
is predictably passed from parents to offspring, making narrow-sense
heritability a crucial metric for predicting the response of a trait to
selection, as in animal and plant breeding. Narrow-sense heritability is
typically smaller than broad-sense heritability unless there are no
dominance or epistatic effects
([REF](https://www.nealelab.is/blog/2017/9/13/heritability-201-types-of-heritability-and-how-we-estimate-it),
[REF](https://www.zoology.ubc.ca/~whitlock/bio434/overheads/09_Quantitative_genetics.pdf),
[REF](https://www.youtube.com/watch?v=dSFNb5T2Ml0)).

Historically, heritability was estimated using family-based study
designs, such as twin studies, which compare trait similarity in
identical versus fraternal twins. Narrow-sense heritability can also be
estimated from the slope of a parent-offspring regression. While these
methods provided valuable estimates of heritability, they could not
identify the specific genetic variants responsible for the observed
variation. The advent of high-throughput genotyping and GWAS provided a
new way to estimate heritability directly from common genetic variants
([REF](https://www.zoology.ubc.ca/~whitlock/bio434/overheads/09_Quantitative_genetics.pdf),
[REF](https://medlineplus.gov/genetics/understanding/inheritance/heritability/)).

## SNP-Based Heritability (*h*<sub>*g*</sub><sup>2</sup>): The Genetic Variation Captured by Common SNPs

SNP-based heritability (*h*<sub>*g*</sub><sup>2</sup>) is defined as the
proportion of phenotypic variance that is explained by the additive
effects of the set of common SNPs observed in a study
([REF](https://www.nealelab.is/blog/2017/9/13/heritability-201-types-of-heritability-and-how-we-estimate-it)).
The formula is

$$
\large h^2\_g = \frac{V\_SNPs}{V\_P}
$$

This metric emerged as a direct consequence of the availability of
large-scale GWAS datasets. It is important to understand that
*h*<sub>*g*</sub><sup>2</sup> is not a synonym for narrow-sense
heritability (*h*<sup>2</sup>). While *h*<sub>*g*</sub><sup>2</sup>
measures additive effects, it is typically considered a lower bound for
the total narrow-sense heritability. This is because it only accounts
for the heritability captured by the specific set of common SNPs that
are genotyped or imputed in a study. The difference between
*h*<sup>2</sup> and *h*<sub>*g*</sub><sup>2</sup> became known as the
“missing heritability” problem, which puzzled researchers for years. It
is now understood that a large portion of this heritability is actually
captured by the collective, small additive effects of a vast number of
common SNPs, most of which do not reach genome-wide significance
individually. Methods like LD Score Regression are specifically designed
to estimate this *h*<sub>*g*</sub><sup>2</sup> by leveraging the rich
information contained within the complete GWAS summary statistics,
including those with non-significant p-values
([REF](https://www.nealelab.is/blog/2017/9/13/heritability-201-types-of-heritability-and-how-we-estimate-it)).

#### Explaining different types of heritability

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;">Metric</th>
<th style="text-align: left;">Formula</th>
<th style="text-align: left;">Genetic Components Included</th>
<th style="text-align: left;">Estimation Method</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;"><strong>Broad-Sense Heritability <span
class="math inline">(<em>H</em><sup>2</sup>)</span></strong></td>
<td style="text-align: left;"><span class="math inline">$H^2 =
\frac{V_G}{V_P}$</span></td>
<td style="text-align: left;">All genetic effects (additive, dominance,
epistasis).</td>
<td style="text-align: left;">Twin studies, inbred line analysis.</td>
</tr>
<tr>
<td style="text-align: left;"><strong>Narrow-Sense Heritability <span
class="math inline">(<em>h</em><sup>2</sup>)</span></strong></td>
<td style="text-align: left;"><span class="math inline">$h^2 =
\frac{V_G}{V_P}$</span></td>
<td style="text-align: left;">Additive genetic effects only.</td>
<td style="text-align: left;">Parent-offspring regression, twin
studies.</td>
</tr>
<tr>
<td style="text-align: left;"><strong>SNP-Based Heritability <span
class="math inline">(<em>h</em><sub><em>g</em></sub><sup>2</sup>)</span></strong></td>
<td style="text-align: left;"><span class="math inline">$h^2_g =
\frac{V_SNPs}{V_P}$</span></td>
<td style="text-align: left;">Additive effects from observed SNPs.</td>
<td style="text-align: left;">GWAS summary statistics, LD Score
Regression.</td>
</tr>
</tbody>
</table>

#### Conclusion: Integrating Concepts for Advanced Analyses

The foundational concepts explored in this lecture—GWAS summary
statistics, linkage disequilibrium, SNP annotation, population
stratification, and heritability—are not isolated topics but form a
deeply interconnected framework. A comprehensive understanding of each
is essential for conducting and interpreting modern statistical genomic
analyses.

A GWAS study’s output, a set of summary statistics, provides the raw
material for analysis. The utility of these statistics is dependent on
the fundamental principle of linkage disequilibrium, which allows common
SNPs to serve as proxies for unmeasured causal variants. The accuracy of
these proxies is governed by the LD patterns of a population, which are
cataloged in large-scale reference panels like the 1000 Genomes Project.
To ensure that the identified associations are not spurious and are, in
fact, due to true genetic effects, confounding factors like population
stratification must be meticulously controlled for, a task often
accomplished through the application of Principal Component Analysis.
Finally, heritability provides the overarching quantitative framework
for understanding the genetic contribution to a trait, and advanced
methods like LD Score Regression leverage the entire set of GWAS summary
statistics and LD information to estimate the portion of heritability
captured by common SNPs.

Mastery of these concepts is the first step toward understanding the
sophisticated methods that are now routinely used to dissect the genetic
architecture of complex traits. By building a tutorial on LD Score
Regression upon this solid foundation, the instructor can ensure that
users not only understand the code but also grasp the profound
biological and statistical principles that make such powerful analyses
possible.
