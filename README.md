# Moringa Genomics Project

Exploring the genetic basis of nutritional and medicinal traits in *Moringa oleifera* using genomics and RNA-seq analysis.

## Objectives

- Review genomic resources available for *Moringa oleifera*
- Investigate genes associated with nutritional traits
- Investigate genes associated with medicinal traits
- Analyze publicly available RNA-seq data
- Identify potential candidate genes for future studies

## Repository Structure

```text
project-proposal/
literature-review/
weekly-notes/
candidate-genes/
workflows/
images/
final-report.md
```

## Workflow

```text
RNA-seq Reads
    ↓
HISAT2 Alignment
    ↓
Samtools Flagstat
    ↓
Samtools Sort
    ↓
BRAKER3 Annotation
    ↓
featureCounts
    ↓
Candidate Gene Analysis
```

## Current Progress

### Completed
- Literature review
- Candidate gene identification
- HISAT2 alignment
- Alignment quality assessment
- BAM sorting

### In Progress
- BRAKER3 genome annotation

### Upcoming
- featureCounts analysis
- Gene expression analysis
- Candidate gene validation
- Final report

## Alignment Summary

- Total reads: 38,419,053
- Mapped reads: 37,442,131
- Mapping rate: 97.46%
- Properly paired reads: 31,075,152
- Properly paired rate: 94.08%

## Project Status

✅ Week 1 Completed  
🔄 Week 2 In Progress  
