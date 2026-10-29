# Week 2 Progress Report

## Project

**Moringa Genomics Project: Exploring the Genetic Basis of Nutritional and Medicinal Traits in *Moringa oleifera***

## Reporting Period

**26 October 2026 – 30 October 2026**

## Reflection

This week marked the transition from background research to practical bioinformatics analysis. After spending Week 1 understanding the nutritional, medicinal, and genomic significance of *Moringa oleifera*, I began working directly with genomic and transcriptomic datasets.

A major part of this week involved building and troubleshooting an RNA-seq analysis workflow. While I anticipated moving quickly from sequence alignment to gene expression analysis, I soon discovered that bioinformatics often involves understanding file formats, annotations, and software compatibility just as much as running computational tools. Although some analyses did not work as expected on the first attempt, the troubleshooting process significantly improved my understanding of RNA-seq workflows and genome annotation.

---

## Objectives for the Week

- Align RNA-seq reads to the selected reference genome.
- Assess alignment quality.
- Prepare alignment files for downstream analysis.
- Generate gene annotations for the selected genome assembly.
- Continue developing and documenting the project repository.

---

## Activities Completed

### 1. RNA-Seq Alignment

I aligned RNA-seq reads from the young leaf tissue dataset (**SRR5834758**) to the selected *Moringa oleifera* reference genome using HISAT2.

#### Inputs

- Reference genome: GCA_021397835.1 (ASM2139783v1)
- Forward reads
- Reverse reads

#### Output

- BAM alignment file containing mapped reads.

The alignment completed successfully and provided the foundation for all downstream analyses.

---

### 2. Alignment Quality Assessment

To evaluate the quality of the alignment, I used **Samtools Flagstat**.

#### Results

- Total reads: **38,419,053**
- Mapped reads: **37,442,131**
- Mapping rate: **97.46%**
- Properly paired reads: **31,075,152**
- Properly paired rate: **94.08%**

#### Interpretation

These results indicate a very successful alignment between the RNA-seq dataset and the selected *Moringa oleifera* genome assembly. The high mapping percentage gave me confidence that the dataset was suitable for downstream analyses.

---

### 3. Troubleshooting Gene Quantification

After alignment, I attempted to quantify gene expression using **featureCounts**.

However, the analysis failed because the available annotation file was derived from a GBFF file and did not contain the required genomic features needed by featureCounts.

Through investigating the error messages and exploring the annotation files, I learned more about the differences between:

- FASTA files
- GBFF files
- GFF3 files
- GTF files

This was an important lesson because it showed how strongly downstream analyses depend on having appropriate annotation resources.

---

### 4. BAM File Processing

To prepare the alignment file for subsequent analyses, I used several SAMtools utilities.

#### Tools Used

- Samtools Flagstat
- Samtools Sort
- Samtools Idxstats

#### Purpose

- Evaluate alignment quality.
- Sort alignments by genomic coordinates.
- Examine read distribution across genomic contigs.

The sorted BAM file was successfully generated and validated.

---

## 5. Genome Annotation Strategy

The selected *Moringa oleifera* genome assembly did not provide a readily available GTF or GFF annotation file suitable for RNA-seq expression analysis. As a result, I explored alternative approaches for generating gene annotations.

My initial strategy was to use BRAKER3 because it combines genome sequence data and RNA-seq evidence to generate gene predictions and transcript annotations. Given the availability of a high-quality RNA-seq alignment, this appeared to be the most suitable approach.

The annotation workflow was intended to combine:

- Reference genome sequence
- RNA-seq alignment evidence

to generate predicted gene models and transcript annotations for downstream expression analysis.

---

## 6. Annotation Challenges and Alternative Approach

### Initial Annotation Attempt: BRAKER3

BRAKER3 was configured using:

#### Inputs

- *Moringa oleifera* genome FASTA
- Sorted RNA-seq BAM alignment file

#### Parameters

- Species name: Moringa
- Soft-masked genome: No
- Output format: GTF

Although the job was successfully submitted and executed, BRAKER3 repeatedly failed during the generation of RNA-seq hints. The software reported that the hints file was empty despite the availability of high-quality RNA-seq alignments.

This result was unexpected because the RNA-seq dataset had already demonstrated excellent alignment statistics, indicating strong compatibility between the sequencing reads and the reference genome.

## Alternative Annotation and Functional Annotation

Due to challenges with BRAKER3 and annotation compatibility, AUGUSTUS was used for structural genome annotation.

### Results

✅ Generated GFF3 annotation file

✅ Generated 79,227 CDS sequences

✅ Generated 79,227 protein sequences

✅ Successfully completed structural annotation

The predicted protein sequences were subsequently analysed using eggNOG-mapper for functional annotation.

### Functional Annotation Results

| Metric | Value |
|----------|----------|
| Proteins submitted | 79,227 |
| Functionally annotated proteins | 34,675 |
| GO terms assigned | Yes |
| KEGG pathways assigned | Yes |

### Candidate Genes Identified

**Nutritional Traits**
- Molybdate transporter (g155)
- FAD-dependent glycerol-3-phosphate dehydrogenase (g159)
- Aminoacyl-tRNA synthetase (g180)
- Gluconokinase (g445)

**Medicinal Traits**
- Sterol 3-beta-glucosyltransferase UGT80A2-like (g1, g182)
- Glycosyltransferase family 28 (g181, g436)
- Glycosyl hydrolase family 1 (g458, g459, g460)

---

## Deliverables Completed

✅ HISAT2 RNA-seq alignment

✅ Alignment quality assessment

✅ BAM sorting and indexing

✅ AUGUSTUS structural annotation

✅ GFF3 annotation generation

✅ CDS sequence generation

✅ Protein sequence generation

✅ eggNOG functional annotation

✅ Candidate gene identification

✅ Candidate gene prioritisation

✅ KEGG pathway analysis

✅ Biological interpretation of candidate genes

✅ GitHub documentation and repository updates

---

## Key Lessons Learned

- Genome annotation is essential for downstream genomic analyses.
- Successful alignment does not guarantee successful downstream analysis.
- Functional annotation is critical for assigning biological meaning to predicted genes.
- Troubleshooting and workflow adaptation are important skills in bioinformatics research.
- Understanding annotation formats significantly improves project execution.
- Pathway analysis helps connect gene functions to complex biological traits.
- Bioinformatics research requires both computational analysis and biological interpretation.

---

## Overall Progress

By the end of Week 2, the project successfully progressed from RNA-seq processing and genome annotation to functional interpretation of candidate genes and biological pathways. Structural annotation, functional annotation, candidate gene discovery, candidate gene prioritisation, pathway analysis, and biological interpretation were completed, providing a strong foundation for the final reporting stage.

---

## Next Steps

1. Complete the final project report.
2. Review and refine the discussion and conclusion sections.
3. Prepare recommendations for future research.
4. Verify all GitHub documentation for accuracy and consistency.
5. Organize figures and supporting files within the repository.
6. Conduct a final review of project outputs and findings.

---

## Personal Takeaway

This week represented an important transition from computational data processing to biological interpretation.

At several points I encountered challenges, particularly when featureCounts failed due to annotation limitations and when BRAKER3 was unable to generate RNA-seq hints despite the successful alignment of over 97% of the sequencing reads. Although these setbacks initially slowed progress, they ultimately strengthened my understanding of genome annotation, RNA-seq workflows, and bioinformatics troubleshooting.

One of the most rewarding milestones was achieving successful functional annotation of 34,675 predicted proteins and identifying candidate genes associated with nutritional and medicinal traits in *Moringa oleifera*. The subsequent KEGG pathway analysis helped connect these genes to biological processes involved in nutrient metabolism, protein biosynthesis, energy production, sterol metabolism, and secondary metabolite biosynthesis.

More importantly, this week reinforced that bioinformatics research extends beyond running computational tools. It requires interpreting biological meaning from genomic data, evaluating evidence, and adapting analytical strategies when initial approaches do not work as expected. The experience has significantly improved my understanding of genome annotation, functional genomics, pathway analysis, and scientific interpretation of bioinformatics results.
