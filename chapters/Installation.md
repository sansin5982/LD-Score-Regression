# Setting Up LDSC: Installation and Required Data

## Installing LDSC Software

LD Score Regression (LDSC) is a command-line tool for estimating
heritability and genetic correlation from GWAS summary statistics. The
software can be installed using a `conda`-compatible package manager
such as `mamba`, `micromamba`, or `conda` itself, from the Bioconda
channel. A typical installation command using `mamba` would be
`mamba install ldsc`. This process automatically handles the software’s
dependencies, which include libraries like `numpy`, `pandas`, `scipy`,
and `bitarray` within a Python environment.

## The Baseline-LD Model

The `baseline-LD` model is a recommended set of annotations used for
partitioned heritability analysis with LDSC. This model extends the
basic baseline model by incorporating several continuous annotations to
enable a more fine-grained partitioning of heritability. The annotations
and corresponding LD scores for this model can be downloaded as
pre-computed files, with version 2.2 being a commonly used iteration.
This model is foundational for partitioning heritability by functional
categories.

## Data Files Required for LDSC Analysis

To perform a partitioned heritability analysis, LDSC requires several
types of pre-computed reference files. These files are typically large
and should be downloaded and prepared before running the analysis. The
core files include:

-   \*\*Annotation files `(.annot.gz)`\*: These files contain
    annotations for each SNP, assigning it to one or more functional
    categories or providing a continuous score. They are used to
    partition heritability across different genomic features, such as
    exonic, intronic, or regulatory regions. LDSC uses these files when
    the `--overlap-annot` flag is specified, as they provide the
    information necessary to interpret the results for overlapping
    categories.

#### File format for .annot.gz

<table>
<thead>
<tr>
<th style="text-align: left;">CHR</th>
<th style="text-align: left;">BP</th>
<th style="text-align: left;">SNP</th>
<th style="text-align: left;"><code>Baseline_annotation_1</code></th>
<th style="text-align: left;"><code>Baseline_annotation_2</code></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">1</td>
<td style="text-align: left;">10000</td>
<td style="text-align: left;">rs1234</td>
<td style="text-align: left;">1</td>
<td style="text-align: left;">0</td>
</tr>
<tr>
<td style="text-align: left;">1</td>
<td style="text-align: left;">10050</td>
<td style="text-align: left;">rs5678</td>
<td style="text-align: left;">0</td>
<td style="text-align: left;">1</td>
</tr>
<tr>
<td style="text-align: left;">2</td>
<td style="text-align: left;">20000</td>
<td style="text-align: left;">rs9101</td>
<td style="text-align: left;">1</td>
<td style="text-align: left;">1</td>
</tr>
</tbody>
</table>

-   **LD Score files (`.l2.ldscore.gz`)**: These files contain the
    pre-computed LD scores for each SNP. LD scores are the independent
    variable in the LDSC regression and are typically calculated from a
    reference panel, such as the 1000 Genomes Project data. These files
    are crucial for the main heritability estimation, and different sets
    of LD scores correspond to different annotation models, such as the
    `baseline` and `baseline-LD` models.

#### File format for .l2.ldscore.gz

<table>
<thead>
<tr>
<th style="text-align: left;">CHR</th>
<th style="text-align: left;">BP</th>
<th style="text-align: left;">SNP</th>
<th style="text-align: left;"><code>L2</code></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">1</td>
<td style="text-align: left;">10000</td>
<td style="text-align: left;">rs1234</td>
<td style="text-align: left;">2.5</td>
</tr>
<tr>
<td style="text-align: left;">1</td>
<td style="text-align: left;">10050</td>
<td style="text-align: left;">rs5678</td>
<td style="text-align: left;">1.8</td>
</tr>
<tr>
<td style="text-align: left;">2</td>
<td style="text-align: left;">20000</td>
<td style="text-align: left;">rs9101</td>
<td style="text-align: left;">3.10</td>
</tr>
</tbody>
</table>

-   **Frequency files (`.frq`)**: These files contain allele frequency
    information for the SNPs in the reference panel, and they are used
    to analyze SNPs with a minor allele frequency (MAF) above a certain
    threshold, typically 5%. These files are required when using the
    `--overlap-annot` flag.

#### File format for .frq file

<table>
<thead>
<tr>
<th style="text-align: left;">CHR</th>
<th style="text-align: left;">SNP</th>
<th style="text-align: left;">A1</th>
<th style="text-align: left;">A2</th>
<th style="text-align: left;">MAF</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">1</td>
<td style="text-align: left;">rs1234</td>
<td style="text-align: left;">A</td>
<td style="text-align: left;">G</td>
<td style="text-align: left;">0.25</td>
</tr>
<tr>
<td style="text-align: left;">1</td>
<td style="text-align: left;">rs5678</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">T</td>
<td style="text-align: left;">0.45</td>
</tr>
<tr>
<td style="text-align: left;">2</td>
<td style="text-align: left;">rs9101</td>
<td style="text-align: left;">T</td>
<td style="text-align: left;">G</td>
<td style="text-align: left;">0.15</td>
</tr>
</tbody>
</table>

-   **SNP Weights files (`.l2.ldscore.gz` or similar)**: These files
    contain LD scores that are used as regression weights in the LDSC
    analysis. These weights are typically computed on a specific set of
    SNPs, such as the HapMap3 SNPs, which are known to be well-imputed.
    Using these weights helps to account for the LD patterns in the
    reference panel and provides more robust heritability estimates. The
    files for the HapMap3 regression SNPs, excluding the MHC region, are
    commonly used for this purpose.

#### File format for .l2.ldscore.gz

<table>
<thead>
<tr>
<th style="text-align: left;">CHR</th>
<th style="text-align: left;">BP</th>
<th style="text-align: left;">SNP</th>
<th style="text-align: left;"><code>L2</code></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">1</td>
<td style="text-align: left;">10000</td>
<td style="text-align: left;">rs1234</td>
<td style="text-align: left;">2.5</td>
</tr>
<tr>
<td style="text-align: left;">1</td>
<td style="text-align: left;">10050</td>
<td style="text-align: left;">rs5678</td>
<td style="text-align: left;">1.8</td>
</tr>
<tr>
<td style="text-align: left;">2</td>
<td style="text-align: left;">20000</td>
<td style="text-align: left;">rs9101</td>
<td style="text-align: left;">3.10</td>
</tr>
</tbody>
</table>
