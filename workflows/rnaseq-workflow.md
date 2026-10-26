# RNA-Seq Analysis Workflow for Moringa oleifera

## Overview

This project investigates the genomic basis of nutritional and medicinal traits in *Moringa oleifera* using publicly available RNA-seq data and bioinformatics tools.

The workflow includes data acquisition, quality assessment, genome alignment, gene prediction, expression quantification, and candidate gene identification.

---

## Workflow Summary

```text
RNA-seq Reads
      ↓
Quality Assessment
      ↓
Reference Genome Selection
      ↓
HISAT2 Alignment
      ↓
Samtools Quality Assessment
      ↓
Samtools Sorting and Indexing
      ↓
BRAKER3 Gene Prediction
      ↓
featureCounts
      ↓
Gene Expression Matrix
      ↓
Candidate Gene Identification
```

---

## Step 1: Data Acquisition

### Genome Assembly

Assembly:
- GCA_021397835.1 (ASM2139783v1)

Species:
- Moringa oleifera (Bhagya cultivar)

Downloaded files:
- Genome FASTA (.fna)

### RNA-Seq Dataset

SRA Accession:
- SRR5834758

Sequencing Type:
- Paired-end RNA sequencing

---

## Step 2: Sequence Alignment

### Tool

HISAT2

### Purpose

HISAT2 was used to align RNA-seq reads to the reference genome.

### Input

- Forward reads (FASTQ)
- Reverse reads (FASTQ)
- Reference genome FASTA

### Output

- BAM alignment file

---

## Step 3: Alignment Quality Assessment

### Tool

Samtools Flagstat

### Purpose

To evaluate alignment performance and mapping quality.

### Results

| Metric | Value |
|----------|----------|
| Total Reads | 38,419,053 |
| Mapped Reads | 37,442,131 |
| Mapping Rate | 97.46% |
| Properly Paired Reads | 31,075,152 |
| Properly Paired Rate | 94.08% |

### Interpretation

The alignment achieved a high mapping rate, indicating strong correspondence between the RNA-seq dataset and the selected reference genome.

---

## Step 4: BAM Processing

### Tools

- Samtools Sort
- Samtools Index

### Purpose

To prepare the alignment file for downstream analysis.

### Outputs

- Sorted BAM file
- BAM index file

---

## Step 5: Gene Prediction

### Tool

BRAKER3

### Purpose

To generate structural gene annotations for the Bhagya genome assembly.

### Inputs

- Reference genome FASTA
- RNA-seq alignment BAM

### Expected Output

- GTF annotation file
- Predicted genes
- Predicted transcripts

### Current Status

In Progress

---

## Step 6: Gene Expression Quantification

### Tool

featureCounts

### Purpose

To quantify the number of mapped reads associated with predicted genes.

### Input

- Sorted BAM file
- BRAKER3-generated GTF annotation

### Output

- Gene count matrix

---

## Step 7: Candidate Gene Identification

### Objective

To identify genes potentially associated with:

#### Nutritional Traits

- Protein biosynthesis
- Nitrogen metabolism
- Vitamin biosynthesis
- Nutrient accumulation

#### Medicinal Traits

- Flavonoid biosynthesis
- Phenolic compound production
- Antioxidant activity
- Stress-response pathways

---

## Expected Outcomes

The study aims to:

1. Generate gene annotations for the selected Moringa genome.
2. Quantify gene expression patterns.
3. Identify genes associated with nutritional traits.
4. Identify genes associated with medicinal traits.
5. Provide a genomic resource for future Moringa research.

---

## Project Status

### Completed

- Literature review
- Genome selection
- RNA-seq dataset selection
- HISAT2 alignment
- Alignment quality assessment
- BAM sorting
- BAM indexing

### In Progress

- BRAKER3 annotation

### Pending

- featureCounts analysis
- Expression matrix generation
- Candidate gene validation
- Final report preparation
