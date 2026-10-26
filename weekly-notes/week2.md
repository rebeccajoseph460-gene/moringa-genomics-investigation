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

### Alternative Annotation Strategy: AUGUSTUS

To continue the project without significant delays, I adopted AUGUSTUS as an alternative gene prediction approach.

AUGUSTUS was configured using:

- *Moringa oleifera* reference genome
- Plant-based prediction model
- Protein and coding sequence outputs enabled

#### Current Status

✅ AUGUSTUS configured

✅ Job submitted successfully

🔄 Gene prediction currently running

Expected outputs include:

- Predicted genes
- Predicted transcript structures
- Coding sequences (CDS)
- Predicted protein sequences
- Annotation files suitable for downstream analysis

These outputs will provide the annotation resources required for subsequent gene expression and candidate gene analyses.

---

## 7. GitHub Repository Development

Significant progress was made in organizing and documenting the project repository.

### Completed

- Updated repository structure.
- Created candidate gene documentation.
- Added nutritional trait candidate gene information.
- Added medicinal trait candidate gene information.
- Added workflow documentation.
- Created results documentation.
- Revised Week 1 progress notes.
- Created Week 2 progress notes.
- Updated the main project README.
- Improved project organization for reproducibility and future updates.

These improvements have transformed the repository into a more structured and reproducible bioinformatics project.

---

## Challenges Encountered

One of the biggest challenges this week was obtaining suitable annotation resources for gene expression analysis.

After successfully aligning the RNA-seq reads, I expected to move directly into gene quantification. However, featureCounts repeatedly failed because the available annotation resource lacked the gene features required for counting reads.

This led me to spend considerable time investigating:

- Genome annotation formats
- Differences between FASTA, GBFF, GFF3, and GTF files
- Gene prediction tools
- RNA-seq workflow requirements

Another challenge was the failure of BRAKER3 despite excellent alignment statistics. This required troubleshooting, evaluating alternative strategies, and ultimately transitioning to AUGUSTUS for gene prediction.

In addition, learning how to interpret alignment metrics and validate BAM files using SAMtools helped strengthen my understanding of RNA-seq quality assessment.

Despite these challenges, each obstacle provided an opportunity to better understand bioinformatics workflows and improve my problem-solving skills.

---

## Lessons Learned

This week reinforced that bioinformatics is much more than running software tools.

Some important lessons I learned include:

- High-quality annotations are just as important as high-quality genome assemblies.
- Strong alignment statistics do not guarantee that downstream analyses will work automatically.
- Annotation resources can become a major bottleneck when working with non-model organisms.
- Quality control should be performed throughout a workflow, not only at the beginning.
- Troubleshooting and adapting workflows are essential skills in bioinformatics research.
- Understanding file formats and tool requirements greatly improves problem-solving.

---

## Deliverables Completed

✅ HISAT2 RNA-seq alignment

✅ Alignment quality assessment using SAMtools Flagstat

✅ BAM file sorting

✅ BAM statistics generation using SAMtools Idxstats

✅ Candidate gene documentation

✅ Workflow documentation

✅ Results documentation

✅ GitHub repository updates

✅ BRAKER3 evaluation and troubleshooting

✅ AUGUSTUS configuration and submission

---

## Next Steps

- Monitor AUGUSTUS completion.
- Review generated gene predictions and annotation outputs.
- Identify annotation files suitable for expression analysis.
- Run featureCounts using the generated annotations.
- Generate a gene count matrix.
- Continue candidate gene investigation.
- Explore expression patterns associated with nutritional and medicinal traits.
- Continue developing the final project report.

---

## Personal Takeaway

This week gave me my first real experience building and troubleshooting an RNA-seq analysis workflow.

At several points I felt stuck, particularly when featureCounts failed and later when BRAKER3 was unable to generate RNA-seq hints despite the successful alignment of over 97% of the sequencing reads. Initially, these setbacks were frustrating, but they ultimately helped me develop a deeper understanding of genome annotation and RNA-seq analysis.

One of the most rewarding moments was confirming that the RNA-seq dataset aligned successfully to the *Moringa oleifera* genome with a mapping rate of 97.46%. That result gave me confidence that the data were suitable for further analysis and that the challenges I encountered were related to annotation rather than data quality.

More importantly, this week taught me that real-world bioinformatics often involves adapting to unexpected problems, exploring alternative solutions, and learning from failure. Although the workflow did not proceed exactly as planned, I now have a much stronger understanding of RNA-seq analysis, genome annotation, and the practical realities of computational biology research.
