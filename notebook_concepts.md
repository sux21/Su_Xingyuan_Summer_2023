# Genome assembly
## Quast outputs
Quast outputs the followings information in a ``report.txt`` file:
- [# contigs (>= ...bp)](https://quast.sourceforge.net/docs/manual.html#sec3)
- [Total length (>= ...bp)](https://quast.sourceforge.net/docs/manual.html#sec3)
- [Largest contig](https://quast.sourceforge.net/docs/manual.html#sec3)
- [Total length](https://quast.sourceforge.net/docs/manual.html#sec3)
- [GC (%)](https://quast.sourceforge.net/docs/manual.html#sec3)
- [N50, N90](https://quast.sourceforge.net/docs/manual.html#sec3)
- [auN](https://lh3.github.io/2020/04/08/a-new-metric-on-assembly-contiguity)
- [L50, L90](https://quast.sourceforge.net/docs/manual.html#sec3)
- [# N's per 100 kbp](https://quast.sourceforge.net/docs/manual.html#sec3)

## Qualimap 
BAM QC outputs basic statistic for an alignment in a ``qualimapReport.html`` file. Explanations of these outputs below are copied from http://qualimap.conesalab.org/doc_html/analysis.html#output. 
- **Globals:** This section contains information about the total number of reads, number of mapped reads, paired-end mapping performance, read length distribution, number of clipped reads and duplication rate (estimated from the start positions of read alignments). <br>
- **ACGT Content:** Nucleotide content and GC percentage in the mapped reads. <br>
- **Coverage:** Mean and standard deviation of the coverage depth. <br>
- **Mapping Quality:** Mean mapping quality of the mapped reads. <br>
- **Insert size:** Mean, standard deviation and percentiles of the insert size distribution if applicable. The features are computed based on the TLEN field of the SAM file. <br>
- **Mismatches and indels:** The section reports general alignment error rate (computed as a ratio of total collected edit distance to the number of mapped bases), total number of mismatches and total number of indels (computed from the CIGAR values). Additionally fraction of the homopolymer indels among total indels is provided. Note, the error rate and mismatches metrics are based on optional fields of a SAM record (NM for edit distance, MD for mismatches). The features are not reported if these fields are missing in the SAM file. <br>
- **Chromosome stats:** Number of mapped bases, mean and standard deviation of the coverage depth for each chromosome as defined by the header of the SAM file. <br>
- **Coverage across reference:** This plot consists of two figures. The upper figure provides the coverage distribution (red line) and coverage deviation across the reference sequence. The coverage is measured in X [1]. The lower figure shows GC content across reference (black line) together with its average value (red dotted line). <br>
[1]	Example for the meaning of X: If one genomic region has a coverage of 10X, it means that, on average, 10 different reads are mapped to each nucleotide of the region. <br>
- **Coverage Histogram:** Histogram of the number of genomic locations having a given coverage rate. The bins of the x-axis are conveniently scaled by aggregating some coverage values in order to produce a representative histogram also in presence of the usual NGS peaks of coverage. <br> 
- **Coverage Histogram (0-50X):** Histogram of the number of genomic locations having a given coverage rate. In this graph genome locations with a coverage greater than 50X are grouped into the last bin. By doing so a higher resolution of the most common values for the coverage rate is obtained. <br>
- **Genome Fraction Coverage:** Provides a visual way of knowing how much reference has been sequenced with at least a given coverage rate. This graph should be interpreted as in this example: <br>
If one aims a coverage rate of at least 25X (x-axis), how much of reference (y-axis) will be considered? The answer to this question in the case of the whole-genome sequencing provided example (copied below) is ~83%. <br>
- **Duplication Rate Histogram:** This plot shows the distribution of duplicated read starts. Due to several factors (e.g. amount of starting material, sample preparation, etc) it is possible that the same fragments are sequenced several times. For some experiments where enrichment is used (e.g. ChIP-seq ) this is expected at some low rate. If most of the reads share the exact same genomic positions there is very likely an associated bias. <br>
- **Mapped Reads Nucleotide Content:** This plot shows the nucleotide content per position of the mapped reads. <br>
- **Mapped Reads GC-content Distribution:** This graph shows the distribution of GC content per mapped read. If compared with a precomputed genome distribution, this plot allows to check if there is a shift in the GC content. <br>
- **Mapped Reads Clipping Profile:** Represents the percentage of clipped bases across the reads. The clipping is detected via SAM format CIGAR codes ‘H’ (hard clipping) and ‘S’ (soft clipping). In addition, the total number of clipped reads can be found in the report Summary. The plot is not shown if there are no clipped-reads are found. Total number of clipped reads can be found in Summary. <br>
- **Homopolymer Indels:** This bar plot shows separately the number of indels that are within a homopolymer of A’s, C’s, G’s or T’s together with the number of indels that are not within a homopolymer. Large numbers of homopolymer indels may indicate a problem in a sequencing process. An indel is considered homopolymeric if it is found within a homopolymer (defined as at least 5 equal consecutive bases). Owing to the fact that Qualimap works directly from BAM files (and not from reference genomes), we make use of the CIGAR code from the corresponding read for this task. Indel statistics cam be found in a dedicated section of the Summary report. <br>
This chart is not shown if the sample doesn’t contain any indels. <br>
- **Mapping Quality Across Reference:** This plot provides the mapping quality distribution across the reference. To construct the plot mean mapping quality is computed for each window. <br>
- **Mapping Quality Histogram:** Histogram of the number of genomic locations having a given mapping quality. To construct the histogram mean mapping quality is computed at each genome position with non-zero coverage and collected. According to Specification of the SAM format the range for the mapping quality is [0-255]. [SAMv1.pdf](https://github.com/sux21/Su_Xingyuan_Summer_2023/files/11644726/SAMv1.pdf) <br>
- **Insert Size Across Reference:** This plot provides the insert size distribution across the reference. Insert size is collected from the SAM alignment field TLEN. Only positive values are taken into account. To construct the plot mean insert size is computed for each window. <br>
- **Insert Size Histogram:** Histogram of insert size distribution. To construct the histogram all collected insert size values (number of read alignments of a certain insert size) are seprated in bins. The default number of bins is 50. The number of reads in the bin will be the sum from insert size of the bins. The detailed values for insert are reported in raw data report. <br>

# Blast
- bit score: information content in a sequence alignment. It is expressed in base 2 log units. 
- E value: the number of alignments with a particular score, or a better score, that are expected to occur by chance when comparing two random sequences.

# FastANI
https://doi.org/10.1038/s41467-018-07641-9 <br>
- ANI: average nucleotide identity of all orthologous genes shared between any two genomes; ANI is only for shared genomes
- same species show >= 95% ANI; 

# Glimmer3
Glimmer is a system for finding genes in microbial DNA, especially the genomes of bacteria, archaea, and viruses.

Instructions are in [glim302notes.pdf](https://github.com/sux21/2020_Experimental_Evoluntion/files/11819304/glim302notes.pdf). 

**Run Glimmer3 using g3-iterated.csh** <br>
It combines g3-from-scratch.csh and g3-from-training.csh. It uses the predictions from the scratch run to create a training set for the second run.

```
### What you type
g3-iterated.csh genom.seq run3

=

### What it runs
long-orfs -n -t 1.15 genom.seq run3.longorfs
extract -t genom.seq run3.longorfs > run3.train
build-icm -r run3.icm < run3.train
glimmer3 -o50 -g110 -t30 genom.seq run3.icm run3.run1

tail +2 run3.run1.predict > run3.coords
upstream-coords.awk 25 0 run3.coords | extract genom.seq - > run3.upstream
elph run3.upstream LEN=6 | get-motif-counts.awk > run3.motif
set startuse = ‘start-codon-distrib -3 genom.seq run3.coords‘
glimmer3 -o50 -g110 -t30 -b run3.motif -P $startuse genom.seq run3.icm run3
```

Output files: 
- <tag>.longorfs - coordinate file of training sequences
- <tag>.train - the multifasta file of training sequences
- <tag>.icm - model
- <tag>.run1.detail - the first Glimmer3 output detail
- <tag>.run1.predict - the first Glimmer3 predictions
- <tag>.coords - the training coordinates for starts and the PWM
- <tag>.upstream - the regions before the starts in <tag>.coords
- <tag>.motif -  a PWM of the upstream regions
- <tag>.detail - the final Glimmer3 output detail 
- <tag>.predict - the final Glimmer3 predictions
