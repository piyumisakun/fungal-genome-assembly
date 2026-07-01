# Fungal Genome Assembly Workflow

## Overview

This repository documents a Linux-based bioinformatics workflow for **de novo fungal genome assembly** and assembly quality assessment using Illumina paired-end sequencing data. The workflow was developed during my MSc research on *Perenniporia cf. tephropora* DD18 and demonstrates the methodology, software, and analysis pipeline used to generate and evaluate the draft genome assembly.

---

## Objectives

* Assess the quality of Illumina paired-end sequencing reads.
* Assemble the fungal genome using de novo assembly methods.
* Improve assembly continuity through scaffolding.
* Evaluate genome assembly quality and completeness.
* Compare multiple genome assemblies to select the optimal assembly.

---

## Bioinformatics Workflow

```text
Raw Illumina Paired-End Reads (Forward & Reverse)
                │
                ▼
FastQC
                │
                ▼
SPAdes
                │
                ▼
SSPACE
                │
                ▼
QUAST
                │
                ▼
BUSCO
                │
                ▼
BBMap
                │
                ▼
Mosdepth
                │
                ▼
MultiQC
```

---

## Software Used

| Software | Purpose                                                                  |
| -------- | ------------------------------------------------------------------------ |
| FastQC   | Assess sequencing read quality                                           |
| SPAdes   | Perform de novo genome assembly                                          |
| SSPACE   | Scaffold assembled contigs                                               |
| QUAST    | Evaluate assembly quality                                                |
| BUSCO    | Assess genome completeness                                               |
| BBMap    | Map sequencing reads to the assembled genome                             |
| Mosdepth | Calculate sequencing depth and coverage                                  |
| MultiQC  | Summarize and compare assembly statistics from multiple analysis reports |

---

## Project Highlights

| Metric                   |                              Value |
| ------------------------ | ---------------------------------: |
| Organism                 | *Perenniporia cf. tephropora* DD18 |
| Genome size              |                           55.59 Mb |
| GC content               |                             54.88% |
| N50                      |                           11.9 Kbp |
| BUSCO completeness       |                              79.6% |
| Average sequencing depth |                               ~50× |

---

## Repository Structure

```text
fungal-genome-assembly
│
├── README.md
├── workflow.png
├── 01_Quality_Control
├── 02_Genome_Assembly
└── 03_Assembly_Assessment
```
