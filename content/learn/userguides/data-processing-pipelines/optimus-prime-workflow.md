---
path: "/learn/userguides/data-processing-pipelines/optimus-prime-workflow"
date: "2018-05-03"
title: "Optimus Prime Workflow"
---

## Introduction to the Optimus Prime Workflow

The long-term goal of the Optimus Prime workflow is to support any 3 prime single cell transcriptomics assay selected by the HCA project. Using the correct modularity, we hope to grow a generic pipeline that has specific modules to address differences in assays, while leveraging common code where steps of the assays are the same. We offer this as a community resource for community development and improvement. The first assay this workflow will support is the [10X Single Cell Expression (v2) assay](https://www.10xgenomics.com/solutions/single-cell).

## Commonalities Among Sequencing Assays

The introduction of droplet-based technologies such as inDrop ([Klein, et al., 2015](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4441768/)) and Drop-seq ([Macosko, et al., 2015](https://www.sciencedirect.com/science/article/pii/S0092867415005498)) moved the throughput of a single-cell RNA sequencing experiment from hundreds, to thousands, of cells. Technology developed by [10X Genomics](https://www.10xgenomics.com/) further increased throughput to tens or even hundreds of thousands of cells and has opened up the possibility of creating datasets for millions of cells. Common among many of the single cell transcriptomics high-throughput technologies is the use of:

* microfluidics, which captures individual cells in oil droplets containing barcoded beads and enzymes
* short read 3’ single-strand DNA sequencing 
* a unique molecular identifier (UMI) as well as a cell barcode to tag each transcript as a unique molecule from a particular cell 

The bead-specific barcodes and UMIs are encoded on sequencing primers that also contain polyT tracts to enable binding of the primers to polyA+ mRNA transcripts. After lysing cells, mRNA transcripts bind to the polyT tracts in the primer and transcripts are reverse transcribed to generate barcoded cDNA. Note that all cDNA molecules from a single cell have the same barcode, but they have different UMIs. Thus every transcript that is captured from an individual cell can be mapped to its cognate cell and also counted as a single transcript, correcting for PCR bias. cDNAs are pooled for amplification and construction of libraries to facilitate 3’ DNA sequencing.

We aspire to leverage commonalities in assays to enable a general computational workflow for processing many single cell transcriptomics modalities. While there will be some differences between assays that will have to be specifically addressed in the workflows, the many common steps will be leveraged into a general workflow.

## Quick Start Table

| Pipeline Features | Description | Source |
|-------------------|---------------------------------------------------------------|-----------------------|
| Overall Workflow  |Quality control module and transcriptome quantification module | Code available from [Github](https://github.com/HumanCellAtlas/skylab/blob/master/pipelines/optimus/Optimus.wdl) |
| Workflow Language |WDL          |[openWDL](https://github.com/openwdl/wdl)|
| Genomic Reference Sequence|GRCh38 human genome primary sequence|[GENCODE](https://www.gencodegenes.org/human/release_27.html)|
|Transcriptomic Reference Sequence |V27 GenCode human transcriptome |[GENCODE](https://www.gencodegenes.org/human/release_27.html)|
| Aligner           |STAR       |[Dobin, et al.,2013](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3530905/)|
| Transcript Quantification |[Sctools](https://github.com/HumanCellAtlas/sctools)        |                                              |                       |
|Data Input File Format | FASTQ      |                                              |                       |

## Optimus Modules Summary

Here we describe the modules of Optimus Prime; feel free to review [the code](https://github.com/HumanCellAtlas/skylab/blob/master/pipelines/optimus/Optimus.wdl), available from Github.

In total, the workflow corrects cell barcodes and Unique Molecular Identifiers (UMIs), aligns reads, marks duplicates, and returns data as alignments in BAM file format and as counts in sparse matrix exchange format. Input data is augmented with QC metrics derived during the processing steps. Rather than remove reads determined by the pipeline to be of lesser quality, all reads are kept with their associated QC metrics and incorporated into the output files. Thus, for example, reads that do not align with genes are not removed. This design, which differs from many pipelines currently available, enables use of the entire dataset by those who may want to use alternative filtering or leverage the data for methodological development associated with the data processing.

![Optimus Workflow](_images/optimus_workflow.png)

## Cell Barcode Correction

Although the function of the cell barcodes is to identify unique cells, several barcode errors can arise, such as incorporation of the barcode into contaminating DNA or sequencing and PCR errors. Therefore it can be challenging to distinguish unique cells from artifactual appearances of the barcode. The first step of this pipeline is to correct for cell barcode errors.

Cell barcode correction uses as input files in BAM file format; thus the fastq files containing the raw sequence data from the sequencer must first be converted to BAM files. This is done using the FastqToUBam.wdl tool, described [here](https://software.broadinstitute.org/gatk/documentation/tooldocs/4.0.3.0/picard_sam_FastqToSam.php). The output BAM files contain sequence that is complementary to the mRNA transcript data in the fastq files and can thus be aligned to the genomic sequence in a later alignment step.

The [Attach10xBarcodes](https://github.com/HumanCellAtlas/sctools) tool is then used to attach 10X barcodes found in the fastq sample to the corresponding reads in the BAM file, producing a barcoded.bam file. The tool uses as input three files:1) the original fastq file of forward reads (r1), containing the unique molecular identifier and cell barcode sequences, 2) an index fastq file which contains the Illumina sample barcodes, and 3) the unmapped bam file of reverse reads (r2), which is the alignable genomic information. The reads in these files are in the same order, and the tool works sequentially through the data, putting the barcodes found for each read of the first 2 fastq files  onto the corresponding read of the third (BAM) file.  The program returns as output a barcoded.bam file containing the reads with correct barcodes (this includes barcodes that came within one error of matching, which are corrected by this tool). These are assigned a “CB” tag. Uncorrected barcodes are preserved and given a “CR” (Cell barcode Raw) tag. During this process, barcoded reads are sorted into cell groups so that the data is divided into reads per cell chunks. The remainder of the pipeline processes these chunks in parallel.

WDL: [Attach10xBarcodes.wdl](https://github.com/HumanCellAtlas/skylab/blob/master/library/tasks/Attach10xBarcodes.wdl)

Docker: [Python3-scientific](https://github.com/HumanCellAtlas/skylab/blob/master/docker/python3-scientific/Dockerfile)

Key Library: [Sctools](https://github.com/HumanCellAtlas/sctools)

## Alignment

The [STAR](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3530905/) alignment software is used to map the reads to the GRCh38 human genome primary assembly reference. STAR (Spliced Transcripts Alignment to a Reference) is widely-used for RNA-seq alignment and identifies the best matching location(s) on the reference for each sequencing read.

## Gene Annotation

The [TagGeneExon](https://github.com/HumanCellAtlas/skylab/blob/master/pipelines/optimus/Optimus.wdl) tool is used to annotate each read with the type of sequence it aligned to. These annotations include `INTERGENIC`, `INTRONIC`, and `EXONIC`, and are stored in the `XF` tag. In cases where the gene corresponds to an intron or exon, the name of the gene that overlaps the alignment is associated with the read and stored in the `GE` tag.

WDL: [TagGeneExon](https://github.com/HumanCellAtlas/skylab/blob/master/pipelines/optimus/Optimus.wdl)

Docker:

Key Library:


## Duplicate Marking

Optical and PCR duplicates are marked using the [UmiAwareMarkDuplicates](https://broadinstitute.github.io/picard/command-line-overview.html#MarkDuplicates) tool. This tool corrects groups reads based on their UMI, gene, and alignment position. Future improvements will make this tool group by cell barcode as well. In groups containing more than one sequencing read, one read is selected as primary, and the rest are marked as duplicates. This tool also corrects cell barcodes using an approach modified from [Jaitin et al.](), wherein reads are subsumed into larger groups when they share the same position and gene, and the UMI is within an edit distance of 1.

WDL: 

Docker:

Key Library:


## Metrics

A number of quality control tools are used to assess the quality of the data output each time this pipeline is run. For a list of the tools and information about each one please see our [QC Metrics](/learn/userguides/data-processing-pipelines/qc-mertics) page.

## Count Matrix Construction

The pipeline outputs a count matrix that contains, for each cell and for each gene, the number of molecules that were observed. In practice, this equates to counting up the number of sequencing reads with 255 map quality (uniquely aligned to the genome) that are not duplicates (i.e., the representative member of one or more alignments that share the same UMI, and therefore derive from the same molecule). The count matrix is then generated as a tab-separated file.
