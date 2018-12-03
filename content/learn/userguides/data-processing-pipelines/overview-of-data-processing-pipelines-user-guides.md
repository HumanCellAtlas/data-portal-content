---
path: "/learn/userguides/data-processing-pipelines/overview-of-data-processing-pipelines-user-guides"
date: "2018-05-03"
title: "Overview of Data Processing Pipelines"
---

## What is Data Processing?
In the HCA DCP, data processing refers to the use of a computational pipeline, designed to analyze raw experimental data from a specific assay. Data processing of HCA data produces collections of quality metrics and features that can be used for further analysis. For example, the processing of single-cell RNA-Seq data produces aligned, QC’d reads, a matrix of gene expression, and a matrix of quality control metrics describing the data.   

## What is the Data Processing Pipeline Service?
The Data Processing Pipeline Service consists of analysis pipelines and execution infrastructure that move raw data through analysis, producing measurements that are ingested into the Data Store for storage and download by anyone, including you! The HCA DCP stores both the submitted raw data and data resulting from data processing, and each type is available for download. As new single-cell technologies and analysis methods are developed and accepted by the research community, we will implement new data processing pipelines and make both the pipelines and the data publically available.

Data processing pipelines are each bespoke to the characteristics of the data they process. These pipelines can attempt to address the quality of the measurements, detecting false positives or negatives, optimal processing (such as aligning, collapsing UMIs, or segmenting images into accurate features), and many other concerns. Please see the details about each of our pipelines and send us your feedback and suggestions!

The following are pipelines in development or in production in this platform:

| Pipeline Name | Data Type                                   | Description                                                                                                                            | Analysis Output                                     |
|------------------|---------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------|
| Smart-seq2    | Full transcript single-cell transcriptomics | This pipeline currently supports the Smart-seq2 protocol as described [here](https://www.nature.com/articles/nprot.2014.006). Read more about the pipeline [here](/learn/userguides/data-processing-pipelines/smart-seq2-workflow).                              | Aligned BAM with tagsCounts Matrix (genes)QC Matrix |
| 10x v2 scRNA-seq pipeline | 3’ capture single-cell transcriptomics      | This pipeline, in development, supports our first offering for 3’ scRNA-Seq, 10X V2 library prep and processing. | Aligned BAM with tagsCounts Matrix (genes)QC Matrix |

## Portability Service 
In keeping with our goal of enabling the community to analyze single-cell data using the most reliable and informative approaches currently available, and to facilitate computational development, our pipelines have been constructed to be portable to environments outside of the HCA. Using the Portability Service, you can determine whether a workflow you’ve developed will work in the HCA, or select non-HCA environments. Additionally, you can attach an environment to the portability system to check whether an HCA pipeline works in your own system. Read more about portability [here](/learn/userguides/data-processing-pipelines/pipeline-portability).

## Access to pipeline outputs
Data bundles containing outputs are publicly available and can be accessed programmatically or through the HCA Data Browser. For information about programmatic access, view the documentation for the CLI [here](/learn/userguides/accessing-data/using-the-cli-to-access-data). Additional analysis options are accessible from the *Anlayze* section of this site.








