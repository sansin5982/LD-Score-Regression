# Background Foundations

-   GWAS basics (summary statistics, effect sizes, standard errors,
    p-values)
-   Linkage disequilibrium (LD) concept
-   SNP annotation and reference panels (1000 Genomes, HapMap3, etc.)
-   Population stratification and principal components
-   Heritability: narrow-sense (h²) and SNP-based heritability

------------------------------------------------------------------------

# File Preparation

-   PLINK file formats: .bed, .bim, .fam
-   Quality control of GWAS summary statistics
-   Reference data: 1000G EUR Phase3 plink files
-   HapMap3 SNP list (w\_hm3.snplist)
-   Partition annotations: .bed, .annot.gz files
-   SNP weights files (baseline, baselineLD, etc.)

------------------------------------------------------------------------

# LDSC Software Setup

-   Installing LDSC (Python environment, dependencies)
-   Data required by LDSC (annot, ldscore, weights, freq files)
-   Understanding baseline model (baselineLD v2.2)

------------------------------------------------------------------------

# LDSC Analyses

-   Univariate LD Score regression (estimating h²)
-   Genetic correlation (ldsc.py –rg)
-   Partitioned heritability (functional categories)
-   Cell-type–specific annotation models
-   Jackknife resampling for SE estimation

------------------------------------------------------------------------

# Advanced / Integration

-   Using LDSC with stratified analyses (by tissue, cell type,
    functional category)
-   Meta-analysis and combining multiple GWAS datasets
-   Integration with FUMA, MAGMA, or other post-GWAS tools
-   Interpretation of LDSC outputs (chi-square inflation, intercept,
    ratio)

------------------------------------------------------------------------
