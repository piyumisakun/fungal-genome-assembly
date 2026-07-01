# Genome Assembly

## Overview

This section describes the de novo genome assembly workflow used to assemble the fungal genome from Illumina paired-end sequencing reads.

---

## Objective

- Assemble high-quality sequencing reads into contiguous sequences (contigs).
- Improve genome continuity through scaffolding.
- Generate a draft fungal genome assembly suitable for downstream analyses.

---

## Input Data

- Quality-assessed Illumina paired-end reads

---

## Software

| Software | Purpose |
|----------|---------|
| SPAdes | De novo genome assembly |
| SSPACE | Scaffolding of assembled contigs |

---

## Operating System

- Linux (WSL Ubuntu)

---

## Methodology

The fungal genome was assembled using SPAdes, followed by scaffolding with SSPACE to improve assembly continuity. The resulting scaffold assembly was used for downstream quality assessment and genome annotation.

---

## Example Commands

### SPAdes

```bash
spades.py \
-1 reads_R1.fastq.gz \
-2 reads_R2.fastq.gz \
-o spades_output
```

### SSPACE

```bash
perl SSPACE_Standard_v3.0.pl \
-l libraries.txt \
-s contigs.fasta
```

---

## Output

- Contigs
- Scaffold assembly

---

## Notes

The scaffold assembly was used for assembly quality assessment using QUAST, BUSCO, BBMap, Mosdepth, and MultiQC.

---

## References

Bankevich et al. (2012). SPAdes: A New Genome Assembly Algorithm.
