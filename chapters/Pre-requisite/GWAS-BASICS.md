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
([REF](https://www.mv.helsinki.fi/home/mjxpirin/GWAS_course/material/GWAS2.html)).

The output of a GWAS is not raw genotype data but a highly compressed
set of results known as “summary statistics.” These statistics provide a
comprehensive, aggregate overview of the association data for every
variant analyzed in the study. This aggregated format makes the data
from different studies interoperable and facilitates downstream
meta-analyses and other advanced statistical methods, such as LD Score
Regression (LDSC). The generation of these summary statistics is a
crucial step that transforms vast datasets into a manageable and
shareable format for the wider research community
([REF](https://www.ebi.ac.uk/gwas/docs/summary-statistics-format)).

## 1.2 Dissecting GWAS Summary Statistics: The Language of Association

GWAS summary statistics are a concise representation of the results for
each tested SNP. The primary components provided by an additive
regression model for each variant are the effect size estimate
`($\hat\beta$)`, `its standard error (SE)`, and a `p-value`. These three
metrics are intrinsically linked and provide a complete picture of the
association signal for a given SNP
([REF](https://www.mv.helsinki.fi/home/mjxpirin/GWAS_course/material/GWAS2.html)).

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

The interpretation of **p-values in GWAS** is complicated by the
**challenge of multiple hypothesis testing**. Because millions of SNPs
are tested simultaneously, there is a high probability of **finding
significant associations purely by chance, even if no true associations
exist**. For instance, with a **standard p-value threshold of 0.05, a
study with one million independent tests would expect 50,000 false
positives**. To address this issue, GWAS employs a far more **stringent
significance threshold, typically 5 × 10<sup>−8</sup>**. This empirical
cutoff is roughly equivalent to a **conservative Bonferroni correction
for one million independent tests**, ensuring that very few of the
identified “hits” are false discoveries. The **p-value’s primary role is
to evaluate the evidence for a non-zero effect, but it does not convey
information about the magnitude of that effect**.
([REF](https://www.mv.helsinki.fi/home/mjxpirin/GWAS_course/material/GWAS2.html),
[REF](https://taylorandfrancis.com/knowledge/Medicine_and_healthcare/Epidemiology/Manhattan_plot/))

### 1.2.2 Effect Sizes and Standard Errors: Quantifying the Genetic Impact

While the p-value indicates statistical significance, the effect size
and standard error provide critical quantitative information. The effect
size estimate `($\hat\beta$)` quantifies the change in the trait for
each additional copy of the effect allele. For a quantitative trait like
height, a positive `($\hat\beta$)` means the effect allele is associated
with increased height, while for a disease, it might represent a change
in disease risk. The `standard error (SE)` measures the uncertainty in
the effect size estimate. A **smaller SE indicates a more precise
estimate of the effect**, which is typically achieved with **larger
sample sizes** and more common variants
([REF](https://www.mv.helsinki.fi/home/mjxpirin/GWAS_course/material/GWAS2.html),
[REF](https://www.mv.helsinki.fi/home/mjxpirin/GWAS_course/material/GWAS3.html)).

The p-value is mathematically derived from a test statistic that
incorporates both the effect size and the standard error. For example,
the Wald test statistic is calculated as $z = \frac{\hat\beta}{SE}$ This
relationship demonstrates that a highly significant p-value (a very
small value) can result from a large effect size, a very small standard
error (due to a large sample size), or a combination of both. It is a
common misconception that a non-significant p-value means a variant has
no effect. In reality, it may simply indicate that the study was
underpowered to detect a small but real effect. This highlights the
importance of reporting effect sizes and their standard errors alongside
p-values, as these metrics provide a more complete assessment of the
association
([REF](https://www.mv.helsinki.fi/home/mjxpirin/GWAS_course/material/GWAS3.html)).

### 1.3 Visualizing the Results: Manhattan and Regional Plots

The results of a GWAS, which often include millions of data points, are
best summarized visually. The most common visualization is the Manhattan
plot, so named for its resemblance to the New York City skyline. In a
Manhattan plot, the negative logarithm of the p-value
(−*l**o**g*<sub>10</sub>(*P*)) for each SNP is plotted against its
chromosomal position on the x-axis.
([REF](https://taylorandfrancis.com/knowledge/Medicine_and_healthcare/Epidemiology/Manhattan_plot/),
[REF](https://pmc.ncbi.nlm.nih.gov/articles/PMC2865585/#:~:text=Manhattan%20plots%20represent%20the%20P,the%20decimal%20point%20plus%20one))).

The Manhattan plot provides a genomic-scale overview of the study’s
findings. SNPs are ordered sequentially by chromosome, creating distinct
columns of points. The y-axis, representing −*l**o**g*<sub>10</sub>(*P*)
, amplifies small p-values, turning highly significant associations into
tall peaks. The genome-wide significance threshold of
5*X*10<sup>−8</sup> is typically represented by a horizontal line, and
any peaks that rise above this line are considered significant “hits”
([REF](https://taylorandfrancis.com/knowledge/Medicine_and_healthcare/Epidemiology/Manhattan_plot/)).

For a more detailed view of a specific significant locus, researchers
use a regional association plot. This plot zooms in on a particular
genomic region, showing the p-values of SNPs within that area alongside
gene annotations and local linkage disequilibrium (LD) patterns. This
allows for a deeper exploration of the candidate causal genes and
variants within a significant peak
([REF](https://taylorandfrancis.com/knowledge/Medicine_and_healthcare/Epidemiology/Manhattan_plot/)).

#### Table resperesenting Statistical Test in GWAS

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;">Statistics</th>
<th style="text-align: left;">Definition</th>
<th style="text-align: left;">Purpose/Interpretation</th>
<th style="text-align: left;">Significance in GWAS</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;"><strong>P-value</strong></td>
<td style="text-align: left;">The probability of observing a result as
or more extreme than the one observed, assuming the null hypothesis is
true.</td>
<td style="text-align: left;">Measures the statistical evidence against
the null hypothesis (no association). A smaller value indicates stronger
evidence.</td>
<td style="text-align: left;">The primary metric for identifying
significant associations, requiring a stringent genome-wide threshold
(<span class="math inline">5<em>x</em>10<sup>−8</sup></span>) to correct
for multiple testing.</td>
</tr>
<tr>
<td style="text-align: left;"><strong>Effect Size (<span
class="math inline"><em>β̂</em></span>)</strong></td>
<td style="text-align: left;">An estimate of the change in a trait for
each additional copy of the effect allele.</td>
<td style="text-align: left;">Quantifies the magnitude and direction of
the genetic effect on the phenotype.</td>
<td style="text-align: left;">Provides the core quantitative measure of
the association, complementing the p-value’s measure of
significance.</td>
</tr>
<tr>
<td style="text-align: left;"><strong>Standard Error (SE)</strong></td>
<td style="text-align: left;">A measure of the statistical uncertainty
surrounding the effect size estimate.</td>
<td style="text-align: left;">Describes the precision of the effect size
estimate. A smaller SE indicates a more reliable estimate.</td>
<td style="text-align: left;">A critical component of the test statistic
(<span class="math inline">$z = \frac{\hat\beta}{SE}$</span>), it links
the magnitude of the effect to its statistical significance.</td>
</tr>
</tbody>
</table>
