# Linkage Disequilibrium (LD): A Cornerstone of Genetic Analysis

## 2.1 From Linkage to Linkage Disequilibrium: A Critical Distinction

**Linkage disequilibrium (LD)** is a fundamental concept in population
genetics that describes the **non-random association of alleles** at
different loci within a population. It is crucial to distinguish LD from
genetic linkage. **Genetic linkage is a physical property, referring to
the co-location of genes on the same chromosome** in an individual. When
two loci are physically close on a chromosome, they are “linked” and
tend to be inherited together
([REF](https://en.wikipedia.org/wiki/Linkage_disequilibrium),
[REF](https://pmc.ncbi.nlm.nih.gov/articles/PMC8733019/)).

LD, in contrast, is a population-level phenomenon. It is a statistical
measure of how often alleles at different loci are found together on the
same chromosome compared to what would be expected if their associations
were random. Although closely linked loci often exhibit high LD, there
is no necessary relationship. LD is a property of a population’s
history, whereas linkage is a property of an individual’s genome. This
distinction is paramount for understanding the utility of GWAS
([REF](https://en.wikipedia.org/wiki/Linkage_disequilibrium)).

## 2.2 Causes and Dynamics of LD in Populations

The primary force that breaks down LD over generations is **meiotic
recombination**. Over time, recombination shuffles alleles, and the
expectation is that LD will decrease with each generation, eventually
approaching zero, even for physically linked loci. However, several
evolutionary and demographic forces can create and maintain LD,
preventing it from reaching a state of equilibrium
([REF](https://en.wikipedia.org/wiki/Linkage_disequilibrium)).

One of the most powerful causes of LD is **natural selection**. If a
particular combination of alleles at two different loci (a haplotype)
provides a **fitness advantage**, selection can favor and maintain this
combination, creating persistent LD. Another significant factor is
**random genetic drift in finite populations**. In small populations,
random sampling can by chance lead to an excess of a specific haplotype,
and this disequilibrium can persist for some time, particularly for
tightly linked genes. Non-random mating and gene flow between distinct
populations can also contribute to LD
([REF](https://www.blackwellpublishing.com/ridley/tutorials/Multi-locus_population_genetics9.asp),
[REF](https://pmc.ncbi.nlm.nih.gov/articles/PMC5124487/), [REF]()).

The most impactful cause of LD for GWAS is population structure and
admixture. When two populations with different allele frequencies mix,
the resulting admixed population will immediately exhibit LD between
alleles that are common in one ancestral population and rare in the
other, even if they are on different chromosomes
([REF](https://en.wikipedia.org/wiki/Linkage_disequilibrium),
[REF](https://pmc.ncbi.nlm.nih.gov/articles/PMC6007879/)).

The practical importance of LD in the context of GWAS cannot be
overstated. GWAS genotyping arrays do not assay every single variant in
the genome; rather, they genotype a representative subset of SNPs. LD
means that a genotyped SNP can serve as a proxy, or “tag,” for other
un-genotyped SNPs in the same LD block. If a causal variant for a trait
is not on the array but is in high LD with a genotyped tag SNP, the
association signal will be captured by the tag SNP. This crucial
principle makes GWAS a cost-effective method for discovering
associations without needing to sequence every individual’s entire
genome ([REF](https://en.wikipedia.org/wiki/Linkage_disequilibrium)).

## 2.3 Quantifying Non-Random Association: The *r*<sup>2</sup> Statistic and its Interpretation

Several measures exist to quantify the extent of LD, including
Lewontin’s D’, but the most widely used and intuitive is the squared
correlation coefficient, *r*<sup>2</sup>. The *r*<sup>2</sup> statistic
can be interpreted as the squared correlation between two SNPs’ allele
dosages. It quantifies the proportion of the variation at one locus that
can be explained by the variation at a second locus
([REF](https://pmc.ncbi.nlm.nih.gov/articles/PMC2580747/),
[REF](https://pmc.ncbi.nlm.nih.gov/articles/PMC7199518/)).

The value of *r*<sup>2</sup> ranges from 0 to 1. An *r*<sup>2</sup>
value of 1 indicates perfect LD, meaning that the two SNPs are in
perfect correlation and provide identical information about the
underlying haplotype. An *r*<sup>2</sup> value of 0 indicates a state of
complete linkage equilibrium, where the alleles at the two loci are
randomly associated
([REF](https://pmc.ncbi.nlm.nih.gov/articles/PMC2580747/)). The
*r*<sup>2</sup> measure is particularly valuable for GWAS because it is
directly related to statistical power. The observed effect size at a tag
SNP is a function of the true causal effect and the *r*<sup>2</sup>
between the tag SNP and the causal variant. A higher *r*<sup>2</sup>
leads to a stronger signal at the tag SNP.

While `D'` is also a popular measure, it is less sensitive to allele
frequency differences than *r*<sup>2</sup>. For the purposes of GWAS and
related analyses like LDSC, which rely on the amount of variance
captured by each SNP, *r*<sup>2</sup> is the preferred metric. LDSC, in
particular, uses a matrix of *r*<sup>2</sup> values to partition
heritability across the genome, making this a critical measure for the
tutorial’s audience.
