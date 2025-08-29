# Confounding Factors: Population Stratification and its Correction

## The Confounding Effect of Population Stratification

Population stratification (PS) refers to the presence of systematic
differences in allele frequencies between subpopulations within a larger
study cohort. This phenomenon arises from non-random mating, which can
be a result of geographic isolation, migration, or cultural factors.
When populations are separated, genetic drift and selection can cause
their allele frequencies to diverge over generations
([REF](https://pmc.ncbi.nlm.nih.gov/articles/PMC6007879/),
[REF](https://en.wikipedia.org/wiki/Population_structure_(genetics))).

This is a critical issue in genetic studies because PS can lead to
spurious associations. A spurious association is a statistical
correlation between two variables that is not causally related but is
instead driven by a third, unseen, or “confounding” factor. In GWAS, PS
acts as a confounding variable. If a disease is more prevalent in one
subpopulation due to environmental or cultural factors, and that same
subpopulation also happens to have a higher frequency of a particular
allele, a GWAS might falsely conclude that the allele causes the
disease. The observed correlation is real, but it is driven by the
shared ancestry (the confounder) rather than a direct genetic link to
the allele itself. This is akin to the well-known example of a spurious
correlation between ice cream sales and shark attacks, where both are
actually influenced by a confounding variable: temperature
([REF](https://en.wikipedia.org/wiki/Spurious_relationship)[REF](https://statisticsbyjim.com/basics/spurious-correlation/)).

## Mitigating Stratification: The Role of Principal Component Analysis (PCA) in GWAS

To prevent spurious associations, it is essential to account for
population structure. One of the most widely used and effective methods
for this is Principal Component Analysis (PCA). PCA is a linear
dimensionality reduction technique that identifies continuous axes of
genetic variation within a dataset
([REF](https://pmc.ncbi.nlm.nih.gov/articles/PMC3215268/#:~:text=PCA%20is%20a%20linear%20dimensionality,covariates%20in%20a%20regression%20setting.),
[REF](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0012510)).

When PCA is applied to a matrix of genotype data from a GWAS cohort, the
first few principal components (PCs) capture the largest sources of
genetic variation, which typically correspond to the population
structure present in the sample. For example, the first PC might
differentiate individuals of European and East Asian ancestry, while the
second PC might separate Southern Europeans from Northern Europeans.
Once these axes of variation are identified, the top PCs are included as
covariates in the statistical association model (e.g., linear
regression). By “regressing out” the effect of these PCs, the
association signals that are due to population stratification are
effectively removed, leaving a more accurate and robust estimate of the
true genetic effect. This approach provides an elegant and powerful
statistical solution to a complex biological problem, as it can account
for the continuous and often subtle nature of genetic admixture
([REF](https://pmc.ncbi.nlm.nih.gov/articles/PMC3215268/#:~:text=PCA%20is%20a%20linear%20dimensionality,covariates%20in%20a%20regression%20setting.),
[REF](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0012510)).
