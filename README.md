# 🧬 Analyzing E. coli Genomes: A Step-by-Step NGS Pipeline

Welcome to my repository! In this project, I took raw genomic sequencing data from *Escherichia coli*, ran it through a complete Next-Generation Sequencing (NGS) pipeline, and identified genetic variants. 

The goal was to transform messy, raw machine readouts into clean, visualizable genomic variants against a trusted standard reference strain.

---

## 📊 The Dataset At A Glance

For this analysis, I fetched real-world sequence data from the NCBI public databases:

* **The Subject:** *Escherichia coli*
* **Raw Data Source:** NCBI Sequence Read Archive (SRA) 
* **Dataset ID:** [SRX16358820 / SRS13996491](https://www.ncbi.nlm.nih.gov/sra/SRX16358820[accn])
* **The Reference Blueprint:** The classic *E. coli* laboratory strain **K-12 (substr. MG1655)**. 
* **Reference Genome Link:** [NCBI Assembly GCF_000005845.2](https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/005/845/GCF_000005845.2_ASM584v2/)

---

## 🛠️ My Workflow & Roadmap

Here is how I processed the data from start to finish, broken down into six main phases:

### 🔍 Phase 1: Initial Quality Control
* **Tool Used:** `FastQC`
* **What I did:** Before jumping into analysis, I checked the overall health of the raw FASTQ files. This step let me evaluate base quality scores, find any adapter contamination, and spot anomalies in the raw sequencing data.

### ✂️ Phase 2: Data Cleaning & Trimming
* **Tool Used:** `Trimmomatic (v0.39)`
* **What I did:** Raw data is always a bit noisy. I used specific thresholds to slice away low-quality bases at the ends of reads and strip out technical adapter sequences. This ensured only high-quality data moved forward.

### 🗺️ Phase 3: Mapping to the Reference
* **Tool Used:** `BWA` (Burrows-Wheeler Aligner)
* **What I did:** With clean reads in hand, I mapped them back onto the *E. coli* K-12 genome sequence. This step aligns the short puzzle pieces of sequencing data to their correct locations on the reference blueprint.

### 🗂️ Phase 4: Organizing the Files
* **Tool Used:** `Samtools`
* **What I did:** Raw alignment files (SAM format) are massive and unorganized. I used Samtools to convert them into a compressed binary format (BAM), sort them by genomic coordinates, and index them so software could read them quickly.

### 🧬 Phase 5: Variant Calling
* **Tool Used:** `BCFtools`
* **What I did:** This is where the real magic happens. By comparing my aligned data against the reference strain, I isolated the exact points of difference—specifically identifying single-letter changes (SNPs) and tiny insertions or deletions (Indels).

### 🖥️ Phase 6: Visualizing the Results
* **Tool Used:** `IGV` (Integrative Genomics Viewer)
* **What I did:** To wrap things up and double-check the results, I loaded the alignment files and variants into IGV. This allowed me to visually inspect the genomic data and confirm the variants with my own eyes.

---

## 📂 Repository Contents

* `README.md` — You are here! An overview of my project and process
* I have uploaded some files in this repository due to large size of files its not possible to add all of them here so to have a look on all the files including raw data results im providing the link of google drive here as i have uploaded all the raw data , reference genome, alligned files ,filtered files , mpileup file , trimmed files , bam files , sam files , vcf files and all the results i got by analyzing my raw E.Coli reads by NGS https://drive.google.com/drive/folders/1jfvLTe7w3ICNIkjxuEPi4EakcTuuMKCu?usp=drive_link
  

---

### ✨ Let's Connect!
Thanks for checking out my bioinformatics project. If you have any questions about the steps I took or the parameters used, feel free to open an issue or reach out!
