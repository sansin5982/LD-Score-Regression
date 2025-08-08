<script type="text/javascript" async
    src="https://polyfill.io/v3/polyfill.min.js?features=es6">
</script>
<script type="text/javascript" async
    src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>

# LD Score

The **LD score** of a SNP is the **sum of its squared correlations
(r²)** with all other SNPs in a given window (often genome-wide, but
limited by distance).

#### Formula

$$
\large \text{LD Score For} SNP\_{j} = \sum\_{k=1}^M r^2\_{jk}
$$

where:

-   *j* is the SNP of interest
-   *M* is the number of SNPs considered (usually within a certain
    base-pair distance or across the chromosome)
-   *r*<sub>*j**k*</sub><sup>2</sup> is the squared correlation
    coefficient between SNP *j* and SNP *k*

#### Interpretation:

-   A SNP with **high LD score** is in strong LD with many nearby SNPs.
-   A SNP with **low LD score** is relatively independent of other SNPs.

## Why do we need LD score?

### Main purposes:

#### 1. LD Score Regression (LDSC) in GWAS:

-   Separates true polygenic signal from confounding (e.g., population
    stratification).
-   Helps estimate **SNP-based heritability**.
-   Estimates genetic correlation between traits.

#### 2. Understanding genetic architecture:

-   High LD score → SNP is tagging many others, so its GWAS signal might
    be inflated just because it’s linked to many causal variants.

#### 3. Polygenic risk score weighting:

-   LD scores can help adjust weights in PRS to avoid redundancy.

#### 4. Fine-mapping & post-GWAS analysis:

-   Knowing LD helps identify independent signals.

### How to Calculate LD Score?

You need:

-   **Genotype reference panel** (e.g., 1000 Genomes EUR samples)
-   **Software**: ldsc.py (from LDSC package), PLINK, or custom script.

#### Steps using PLINK & Python:

#### 1. Calculate pairwise r² between SNPs within a window (commonly 1 cM or 1 Mb):

    plink --bfile reference_genotype \
          --ld-snp rs12345 \
          --ld-window-kb 1000 \
          --ld-window 99999 \
          --ld-window-r2 0

#### 2. Square r values (if not already squared) and sum for each SNP:

$$
\large LD Score = \sum r^2
$$

#### Using LDSC software:

    python ldsc.py \
      --bfile 1000G_EUR_Phase3_plink/1000G.EUR.QC. \
      --l2 \
      --ld-wind-kb 1000 \
      --out output_prefix

#### What does LD Score tell us?

-   **High LD score**: SNP tags many others → it’s more likely to
    capture polygenic signal, but also \* more prone to inflation due to
    confounding.

-   **Low LD score**: SNP is relatively independent → less tagging power
    but more “specific” to itself.

#### In LD Score Regression:

-   If inflation in GWAS test statistics is proportional to LD score →
    inflation is from polygenic effects.
-   If inflation is *not* proportional → inflation is likely due to
    confounding.
