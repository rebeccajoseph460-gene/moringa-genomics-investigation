# Moringa Genomics Project

Investigating the genetic basis of nutritional and medicinal traits in *Moringa oleifera* through genome annotation, functional annotation, and candidate gene discovery.

---

## Project Aim

### Research Question

**Which genes and biological pathways contribute to the nutritional and medicinal properties of *Moringa oleifera*?**

---

## Data Resources

### Reference Genome

- Species: *Moringa oleifera*
- Cultivar: Bhagya
- Assembly: ASM2139783v1
- Accession: GCA_021397835.1

### RNA-Seq Dataset

- Accession: SRR5834758
- Tissue: Young leaf
- Sequencing Type: Paired-end RNA-Seq

---

## Workflow

```text
Genome Assembly
      ↓
RNA-Seq Acquisition
      ↓
Quality Assessment
      ↓
HISAT2 Alignment
      ↓
SAM/BAM Processing
      ↓
AUGUSTUS Gene Prediction
      ↓
Protein & CDS Extraction
      ↓
eggNOG Functional Annotation
      ↓
Candidate Gene Identification
      ↓
Pathway Analysis
      ↓
Final Report
```

---

## Repository Structure

```text
proposal/
workflow/
notes/
candidate_genes/
results/
references/
```

---

## Author

**Rebecca O. Joseph**

A genomics and bioinformatics project focused on identifying genes and biological pathways associated with the nutritional and medicinal traits of *Moringa oleifera* through genome annotation, functional genomics, and candidate gene discovery.
