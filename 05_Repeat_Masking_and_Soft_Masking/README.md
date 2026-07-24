# Repeat Masking and Soft Masking

## Repeat Identification Using RepeatModeler

### Overview
RepeatModeler is a de novo repeat discovery tool used to identify repetitive DNA sequences within a genome assembly. It automatically detects repeat families without relying on existing repeat databases and generates a species-specific repeat library. This repeat library is subsequently used by RepeatMasker to identify and soft-mask repetitive regions before structural genome annotation.

### Rationale
Repetitive DNA sequences can interfere with accurate gene prediction by producing false or fragmented gene models. Therefore, repetitive elements should be identified before structural annotation. RepeatModeler performs de novo repeat discovery by analyzing the assembled genome and constructing a species-specific repeat library. This custom repeat library improves repeat detection accuracy, particularly for organisms whose repetitive elements are poorly represented in public databases.

### Workflow
```
Assembled Genome
        │
        ▼
Build Genome Database
        │
        ▼
RepeatModeler
        │
        ▼
De novo Repeat Discovery
        │
        ▼
Species-specific Repeat Library
        │
        ▼
RepeatMasker
```

### Methodology

#### Step 1 – Build the Genome Database
The assembled genome was converted into a searchable database using the BuildDatabase utility provided with RepeatModeler.

##### Representative Commands
```
BuildDatabase \
-name perenniporia_db \
sspace_output.filtered_1000.fasta
```

#### Step 2 – Perform De Novo Repeat Discovery
RepeatModeler iteratively analyzed the genome database to identify repetitive sequence families using its integrated repeat discovery algorithms.

##### Representative Commands
```
RepeatModeler \ 
-database perenniporia_db \
-threads 12 \ 
-LTRStruct
```

#### Step 3 – Generate a Species-specific Repeat Library
The identified repeat families were combined into a custom repeat library, which was used as the reference library for RepeatMasker to perform repeat masking and soft masking.

##### Representative Commands
```
RepeatMasker \
-pa 12 \ 
-xsmall \
-lib perenniporia_db-families.fa \
sspace_output.filtered_1000.fasta
```


