# Preparing for LDSC: Navigating Genomic Data Files

The power of tools like LDSC is unlocked not just by understanding the
underlying concepts but also by correctly preparing the input files.
This chapter provides an overview of the essential file formats and data
quality control steps required for a successful LDSC analysis.

## The PLINK File Formats: A Data Management Standard

PLINK is a widely used command-line tool in statistical genetics, often
described as a “swiss army knife” for its versatility in data cleaning
and analysis. PLINK’s binary file format is a popular way to store
genotype data. This format consists of three core files that are always
used together: a `.bed`, a `.bim`, and a `.fam` file
([REF](https://sites.google.com/a/broadinstitute.org/ricopili/required-computational-skills),
[REF](https://wanggroup.org/compbio_tutorial/plink_format.html)).

#### Binary File format for GWAS

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr>
<th style="text-align: left;">File extension</th>
<th style="text-align: left;">Content</th>
<th style="text-align: left;">Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;"><code>.bed</code></td>
<td style="text-align: left;">Binary file containing genotype data</td>
<td style="text-align: left;">Stores the raw genotype data in a
compressed format, as a sample-by-variant matrix. This file is not
human-readable and should not be edited manually.</td>
</tr>
<tr>
<td style="text-align: left;"><code>.fam</code></td>
<td style="text-align: left;">Plain text file containing sample
information</td>
<td style="text-align: left;">Stores information about each individual
in the cohort, including a Family ID (FID), an Individual ID (IID),
maternal and paternal IDs, sex, and phenotype status (e.g.,
case/control).</td>
</tr>
<tr>
<td style="text-align: left;"><code>.bim</code></td>
<td style="text-align: left;">Plain text file containing variant
information</td>
<td style="text-align: left;">Stores information about each SNP,
including chromosome number, SNP ID, genetic distance, and chromosomal
position in base pairs. Each row describes one SNP.</td>
</tr>
</tbody>
</table>

Together, these files provide a complete and efficient way to manage and
process large-scale genotype data.

## Quality Control of GWAS Summary Statistics

rior to any advanced analysis, GWAS summary statistics must undergo a
rigorous quality control (QC) process to ensure their integrity and
usability. The GWAS Catalog, for instance, has a standard format for
summary statistics to ensure interoperability
([REF](https://academic.oup.com/bioinformatics/article/37/23/4593/6380562?login=false),
[REF](https://www.ebi.ac.uk/gwas/docs/summary-statistics-format)).

Key QC steps include:

-   **Header and Format Consistency**: Tools exist to check and
    standardize column headers (e.g., SNP, CHR, BP, A1, A2, P) and to
    convert files to a consistent format, such as `.tsv`
    ([REF](https://academic.oup.com/bioinformatics/article/37/23/4593/6380562?login=false),
    [REF](https://www.ebi.ac.uk/gwas/docs/summary-statistics-format)). .
-   **Variant Filtering**: QC is used to remove problematic SNPs. This
    includes removing non-biallelic SNPs, SNPs with missing data, and
    SNPs with P-values that are too small or equal to zero
    ([REF](https://academic.oup.com/bioinformatics/article/37/23/4593/6380562?login=false)).
-   **Allele Direction and Strand Ambiguity**: It is crucial to ensure
    that the effect allele (A1) and non-effect allele (A2) from the
    summary statistics match a reference genome to maintain consistent
    directionality of effects. Some software also filters out
    “strand-ambiguous” SNPs (A/T or C/G) that are difficult to orient
    correctly ([REF](https://www.sanger.ac.uk/data/hapmap-3/),
    [REF](https://academic.oup.com/bioinformatics/article/37/23/4593/6380562?login=false)).
-   **Sample Size and Imputation Quality**: QC procedures can filter out
    SNPs with imputation quality scores (INFO score) below a certain
    threshold (e.g., &lt; 0.9) and remove SNPs that have a sample size
    that is substantially different from the rest of the study
    ([REF](https://academic.oup.com/bioinformatics/article/37/23/4593/6380562?login=false)).

These steps are essential to produce a clean, standardized summary
statistics file that can be used effectively by downstream analysis
software like LDSC.

## Essential Reference Files for LDSC

LDSC requires several key reference files to perform its analyses. These
files are typically pre-computed and are matched to the specific
population being analyzed (e.g., European ancestry)
([REF](https://github.com/bulik/ldsc/wiki/Partitioned-Heritability)).

## 1000 Genomes Project PLINK Files

The 1000 Genomes Project PLINK files are used as a foundational
reference panel for LD estimation. Specifically, the European (EUR)
population from Phase 3 of the project is often used for analyses of
European-ancestry cohorts. These files provide the detailed genotype
data from which the LD scores are calculated
([REF](https://www.internationalgenome.org/category/phase-3/),
[REF](https://github.com/bulik/ldsc/wiki/Partitioned-Heritability)).

## HapMap3 SNP List (w\_hm3.snplist)

The HapMap3 SNP list `(w_hm3.snplist)` is a curated list of
approximately 1 million SNPs from the third phase of the International
HapMap Project. This list serves a critical purpose in LDSC as the
recommended set of “regression SNPs”. These SNPs are used to perform the
core LDSC regression and are selected because they are well-imputed in
most GWAS and are not located in the highly complex Major
Histocompatibility Complex (MHC) region
([REF](https://www.broadinstitute.org/medical-and-population-genetics/hapmap-3),
[REF](https://github.com/bulik/ldsc/wiki/Partitioned-Heritability)).

## Partition Annotation Files

For partitioned heritability analysis, LDSC uses annotation files (e.g.,
`.annot.gz` files) to assign each SNP to one or more functional
categories (e.g., exonic, intronic, regulatory regions). This allows the
heritability to be partitioned across different genomic features. These
files are essential when using the `--overlap-annot` flag in LDSC, which
handles the analysis of categories that are not mutually exclusive
([REF](https://github.com/bulik/ldsc/wiki/Partitioned-Heritability),
[REF](https://github.com/bulik/ldsc/wiki/Partitioned-Heritability-from-Continuous-Annotations)).

## SNP Weights Files

SNP weights files are also critical for LDSC regression. These are LD
score files, typically with a `.l2.ldscore.gz` suffix, that provide the
independent variable for the LDSC regression. They are also used as
regression weights in the analysis, which helps to account for the LD
patterns in the reference panel. The most common sets of weights files
are based on the `baseline` and `baseline-LD` models, which provide a
rich set of annotations for heritability partitioning. These files are
usually computed on the HapMap3 SNPs and matched to a specific
population
([REF](https://github.com/bulik/ldsc/wiki/Partitioned-Heritability),
[REF](https://github.com/bulik/ldsc/wiki/Partitioned-Heritability-from-Continuous-Annotations)).
