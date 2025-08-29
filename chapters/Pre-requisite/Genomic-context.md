# The Importance of Genomic Context: Annotation and Reference Panels

## 3.1 What is a SNP and Why Do We Annotate It?

A single-nucleotide polymorphism (SNP) is a single base-pair change in a
DNA sequence that is commonly found in a population. While only a small
fraction of the genome is comprised of protein-coding genes, SNPs can
occur anywhere, from exons to distant regulatory regions. Given that a
GWAS can identify millions of associated SNPs, it is essential to
understand their potential function and effect. SNP annotation is the
process of predicting the biological function or consequence of a
variant ([REF](https://en.wikipedia.org/wiki/SNP_annotation),
[REF](https://www.nealelab.is/blog/2017/9/13/heritability-201-types-of-heritability-and-how-we-estimate-it)).

Annotation tools categorize SNPs based on their genomic location and
predicted effect. Gene-based annotation determines whether a SNP lies
within or near a gene, an exon, or a splice site, and can predict if it
might disrupt the protein sequence. Functional annotation identifies if
a variant is located in a known functional region, such as an enhancer,
promoter, or transcription factor binding site. This is particularly
important for non-coding variants, which constitute the vast majority of
GWAS-identified loci and can affect gene regulation. Knowledge-based
annotation links a variant to known biological pathways or disease
associations documented in public databases like the GWAS Catalog or
ClinVar. By providing this context, annotation helps researchers
prioritize significant variants and formulate hypotheses about their
biological role
([REF](https://www.snp-nexus.org/v4/about/)[REF](https://en.wikipedia.org/wiki/SNP_annotation)).

## 3.2 The Role of Large-Scale Reference Panels (HapMap and 1000 Genomes)

Large-scale reference panels are foundational resources in statistical
genomics. These are publicly available datasets of sequenced or
genotyped individuals from diverse populations that provide a
comprehensive catalog of human genetic variation.

The International HapMap Project was a landmark effort to develop a
haplotype map of the human genome. Its goal was to characterize the
patterns of common human DNA sequence variation and identify LD blocks.
The HapMap Project, through its various phases (HapMap I, II, and III),
provided the first high-resolution LD maps and recombination hotspots,
which became crucial for designing early GWAS studies and selecting tag
SNPs ([REF](https://www.sanger.ac.uk/data/hapmap-3/),
[REF](https://www.coriell.org/1/NIGMS/Collections/HapMap-project)).

The 1000 Genomes Project built upon HapMap’s work by aiming to discover
a much broader spectrum of genetic variation, including rarer SNPs and
structural variants, by sequencing the genomes of more than 1,000
individuals from multiple populations worldwide. This project created a
far more comprehensive catalog of human genetic variation than was
previously available
([REF](https://pmc.ncbi.nlm.nih.gov/articles/PMC4690620/#:~:text=The%201000%20Genomes%20Project%20is,to%20human%20health%20and%20disease.),[REF](https://www.broadinstitute.org/projects/1000-genomes)).

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;">Feature</th>
<th style="text-align: left;">HapMap</th>
<th style="text-align: left;">1000 Genomes Project</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;"><strong>Goal</strong></td>
<td style="text-align: left;">To create a haplotype map of the human
genome and describe common patterns of variation.</td>
<td style="text-align: left;">To create a comprehensive catalog of human
genetic variation by sequencing genomes.</td>
</tr>
<tr>
<td style="text-align: left;"><strong>Sample Size</strong></td>
<td style="text-align: left;">Began with 269 individuals in four
populations (Phase I), expanding to 1,301 individuals in multiple
populations (HapMap 3).</td>
<td style="text-align: left;">Sequenced genomes from over 1,000
individuals from diverse populations.</td>
</tr>
<tr>
<td style="text-align: left;"><strong>Variant Types</strong></td>
<td style="text-align: left;">Focused on common SNPs, with some
sequencing to assess genotyping quality.</td>
<td style="text-align: left;">Cataloged a broader range of variants,
including SNPs and structural variants, especially those with lower
minor allele frequencies.</td>
</tr>
<tr>
<td style="text-align: left;"><strong>Key Contribution</strong></td>
<td style="text-align: left;">Provided the first high-resolution LD maps
and recombination hotspots, which guided the design of early GWAS.</td>
<td style="text-align: left;">Offered a more comprehensive catalog of
human genetic variation, serving as a superior reference panel for
modern imputation and LD estimation.</td>
</tr>
</tbody>
</table>

## Practical Applications: Using Reference Panels for Imputation and LD Estimation

Reference panels are not merely archives of genetic data; they are
actively used for two critical applications in GWAS.

The first is **genotype imputation**, a statistical process that uses a
reference panel to infer the genotypes of untyped SNPs for a study
cohort. Imputation leverages the patterns of LD found in the reference
panel to “fill in the blanks” from a genotyping array, effectively
increasing the density of the assayed variants. This is a crucial step
for increasing the power of a GWAS, as it provides a more complete set
of SNPs to test, raising the probability that a causal variant will be
accurately “tagged” by a genotyped or imputed SNP. The accuracy of
imputation depends on the quality of the reference panel and the genetic
similarity between the study cohort and the individuals in the reference
panel. A mismatch can lead to poor imputation accuracy, which is why
population-specific reference panels are increasingly being developed
([REF](https://pubmed.ncbi.nlm.nih.gov/40631173/)).

The second key application is **LD estimation**. The LD score regression
method (LDSC) relies on a matrix of LD information, typically calculated
from a reference panel. The local patterns of LD vary significantly
across the genome and between different populations. For instance,
African populations, having a larger and more ancient effective
population size, exhibit more fragmented LD blocks compared to European
populations, which have experienced more recent bottlenecks and
expansions. This means that for an accurate LDSC analysis, it is
essential to use an LD reference panel that is population-matched to the
GWAS summary statistics. Failure to do so can lead to biased
heritability estimates. Therefore, reference panels are the engine that
provides the necessary LD information to translate GWAS summary
statistics into meaningful heritability and genetic architecture
insights ([REF](https://pmc.ncbi.nlm.nih.gov/articles/PMC6007879/),
[REF](https://www.coriell.org/1/NIGMS/Collections/HapMap-project)).
