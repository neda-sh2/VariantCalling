# CRISPR Project Pipeline
The purpose of this project is to evaluate the efficacy and specificity of CRISPR/Cas9 genome editing in mammalian cells using sequencing data
Requirements include:
```
bwa
samtools
bcftools
vcftools
cyvcf2
pandas
```
Input files include the reference genome and the alternate genome for the mouse sample being used
## Pipeline workflow
The reference genome for is prepared for alignment
Next, the CRISPR sequencing reads were aligned to the reference genome using BWA's algorithm, creating alignment results in the SAM file format
These alignments were then converted to a BAM file, and the reads were sorted
After sorting, low-quality reads were removed to include only high-quality data in the analysis. 
The filtered data is read to show the genotypes present, which allows for a comparison between the alternate mouse genome and the reference genome
A python script is used to filter mutations based on quality
To determine the effectiveness of CRISPR editing mutations caused by CRISPR the intended target sites are identified
Off-target effects are also measured
```
CRISPR.R1.fastq CRISPR.R2.fastq > aligned_reads_chr2.sam
samtools view -Sb aligned_reads_chr2.sam > aligned_reads_chr2.bam
samtools sort aligned_reads_chr2.bam -o sorted_reads_chr2.bam
samtools index sorted_reads_chr2.bam
```
