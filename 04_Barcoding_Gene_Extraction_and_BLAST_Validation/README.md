# Barcoding Gene Extraction and BLAST Validation

## Overview

This module demonstrates the workflow used to extract conserved fungal DNA barcode genes from a draft genome assembly and validate their identities using NCBI BLASTn. The validated marker genes were subsequently used for downstream analyses.

## Rationale

Conserved DNA barcode genes are widely used for fungal species identification and phylogenetic analyses. Although these genes are expected to be present in the assembled genome, their identities should be verified before they are used in downstream analyses. This workflow demonstrates the extraction of representative barcode genes from the genome assembly and their validation against the NCBI nucleotide database using BLASTn. Confirming sequence identity ensures that the recovered markers are suitable for comparative and phylogenetic studies.

## Workflow
```
Genome Assembly
↓
Barcode Gene Extraction
↓
Selection of Candidate Regions
↓
NCBI BLASTn Validation
↓
Evaluation of Sequence Similarity
↓
Validated Marker Genes
```
## Barcode Gene Extraction

### Purpose
The assembled genome was examined to identify candidate regions corresponding to conserved fungal DNA barcode genes, including ITS, LSU, SSU, TEF1, β-tubulin, and RPB2.

### Step 1 – Identify Candidate Gene Regions

#### Purpose
Identify candidate genomic regions containing the target barcode gene by aligning a reference gene sequence against the assembled genome using BLASTn.

#### Representative command
```
blastn \
-query query.txt \
-subject perenniporia_assembled_genome.fasta \
-out blast_results.tsv \
-outfmt "6 qseqid sseqid pident length mismatch gapopen qstart qend sstart send qlen slen" \
-max_target_seqs 5
```

#### Representative Screenshot 
Figure 1. Running BLASTn to identify candidate genomic regions corresponding to the target barcode gene in the assembled genome.

#### Interpretation
BLASTn identified multiple candidate alignments between the reference barcode gene and the assembled genome. These candidate regions were used for subsequent filtering and coordinate analysis.

### Step 2 – Filter High-Confidence Alignments

#### Purpose
Filter BLAST results to retain only high-confidence alignments based on sequence identity and alignment length.

#### Representative command
```bash
awk 'BEGIN {OFS="\t"}
$3>=85 && $4>=300 {print}
' ssu_result.tsv > ssu_filtered.tsv
```
#### Representative Screenshot 
Figure 2. Filtering BLASTn alignments based on sequence identity and alignment length.

#### Interpretation
Filtering removed low-confidence matches and retained only candidate alignments meeting the predefined similarity criteria for downstream analysis.

### Step 3 – Normalize Alignment Coordinates

#### Purpose
Normalize genomic coordinates to ensure that sequence extraction is performed using correctly ordered start and end positions.

#### Representative Command


