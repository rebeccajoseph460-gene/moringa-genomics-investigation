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

### 5. Genome Annotation Strategy

Because the selected genome assembly did not provide a readily available GTF or GFF annotation suitable for expression analysis, I explored alternative annotation approaches.

After evaluating several options, I selected **BRAKER3** for gene prediction and genome annotation using RNA-seq evidence.

The annotation workflow combines:

- Reference genome sequence
- RNA-seq alignment data

to generate predicted gene models and transcript annotations.

---

### 6. BRAKER3 Configuration

BRAKER3 was configured using:

#### Inputs

- *Moringa oleifera* genome FASTA
- Sorted BAM alignment file

#### Parameters

- Species name: Moringa
- Soft-masked genome: No
- Output format: GTF

#### Current Status

✅ Configuration completed

✅ Job successfully submitted

🔄 BRAKER3 currently running

Expected outputs include:

- Predicted genes
- Transcript models
- GTF annotation file

These outputs will be used in downstream expression analysis and candidate gene investigation.

---

### 7. GitHub Repository Development

Significant progress was also made on project documentation and repository organization.

#### Completed

- Updated repository structure.
- Added workflow documentation.
- Created candidate gene documentation.
- Added nutritional trait candidate gene information.
- Added medicinal trait candidate gene information.
- Revised Week 1 progress notes.
- Updated project README.

These updates improve project organization and help maintain reproducibility throughout the investigation.

---

## Challenges Encountered

One of the biggest challenges this week was dealing with genome annotation files.

After successfully aligning the RNA-seq reads, I expected to move directly into gene quantification. Instead, featureCounts repeatedly failed because the available annotation file did not contain the required genomic features.

This challenge forced me to spend time learning how genome annotations are structured and understanding the differences between various genomic file formats.

Another challenge was learning how to assess whether alignment jobs had truly succeeded. Using tools such as Samtools Flagstat and Samtools Idxstats helped me develop a better understanding of alignment quality metrics and BAM file validation.

Despite these challenges, each obstacle provided an opportunity to deepen my understanding of bioinformatics workflows.

---

## Lessons Learned

This week reinforced that bioinformatics is not simply about running software tools. Success often depends on understanding the biological data, file formats, and relationships between different stages of the workflow.

Some key lessons I learned include:

- High-quality annotations are just as important as high-quality genome assemblies.
- Alignment success does not automatically guarantee downstream analyses will work.
- Quality control should be performed at every major stage.
- Troubleshooting is an essential part of bioinformatics research.
- Understanding the purpose of each tool makes problem-solving much easier.

---

## Deliverables Completed

✅ HISAT2 RNA-seq alignment

✅ Alignment quality assessment using Samtools Flagstat

✅ BAM file sorting

✅ BAM statistics generation using Samtools Idxstats

✅ Candidate gene documentation

✅ Workflow documentation

✅ GitHub repository updates

✅ BRAKER3 configuration and submission

---

## Next Steps

- Monitor BRAKER3 completion.
- Review generated gene annotations.
- Run featureCounts using the predicted GTF annotation.
- Generate a gene count matrix.
- Continue candidate gene investigation.
- Explore expression patterns of genes associated with nutritional and medicinal traits.
- Continue developing the final project report.

---

## Personal Takeaway

This week gave me my first real experience building and troubleshooting an RNA-seq workflow from start to finish. There were moments when I felt stuck, especially when featureCounts failed and I realized that the available annotation resources were not suitable for the analysis.

Working through those challenges taught me much more than if every step had worked perfectly from the beginning. I became more comfortable interpreting alignment statistics, processing BAM files, troubleshooting software outputs, and understanding the importance of genome annotation in RNA-seq analysis.

One of the most encouraging moments of the week was seeing that over **97% of the RNA-seq reads mapped successfully** to the *Moringa oleifera* genome. That result confirmed that the dataset and reference genome were compatible and gave me confidence that the project is progressing in the right direction.

Although this week involved more troubleshooting than expected, I now have a much clearer understanding of RNA-seq workflows and the practical challenges involved in transforming raw sequencing data into meaningful biological insights.
