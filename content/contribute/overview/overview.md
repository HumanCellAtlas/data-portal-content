---
path: "/contribute/overview/overview"
date: "2018-05-03"
title: "Overview"
template: "contributeOverviewTemplate"
linked:
    - ./contact-us.md
    - ./prepare-metadata.md
    - ./upload-data.md
    - ./see-and-share.md
---

## What data can be submitted?

The Human Cell Atlas is interested in all types of cellular resolution 'omics data. If you have cellular resolution data of any type which is consented for open data release, please talk to us and we are happy to discuss if it is suitable for the atlas.

### SmartSeq2 and 10X v2 single cell RNAseq

Our standard [data processing pipelines](https://dev.data.humancellatlas.org/learn/userguides/data-processing-pipelines/overview-of-data-processing-pipelines-user-guides) can process SmartSeq2 and 10X v2 single cell RNA-Seq data. All submitted SmartSeq2 and 10X v2 experiments will be processed by these pipelines, and the alignment and quantification results will be made available alongside the raw data.

###Single nucleus sequencing and Image-based transcriptomics

We are actively investigating standard analysis pipelines for these data types. If you are generating data like this, we are very interested to collect it and work with you to better understand these data types and how to process them.

### Other data types

Ultimately many types of cellular resolution data will be needed to build the Human Cell Atlas. If you have other data types not mentioned here, please reach out to us. As our platform develops we will want to use these data to build the atlas; help you share these data with the community, and we will make it available in cloud environments for you and your collaborators to use.

## The submission process

Our current submission process uses spreadsheets to collect the metadata and an upload tool to deposit the data files in our cloud infrastructure. You will be supported in the process by our data wranglers. Currently submission is a collaborative process between you and one of our wranglers. As our platform evolves, we aim to make the submission process more self-service.

The current data submission journey looks like this:

1. Talk to a data wrangler about your project and the types of samples you are collecting and experiments you are running.
1. Be given a spreadsheet template tailored to your project so you can provide details about your project, samples, and experiments.
1. Be given credentials in order use the Human Cell Atlas upload tool  to upload your data files to the cloud.
1. Fill out your spreadsheet and upload your data files.
1. Be given validation results back by the data wrangler and work with them to fix any errors that were discovered.
1. Be given a summary of your submission to review to ensure you are happy with the data and metadata you have submitted.
1. Agree to the HCA DCP Terms and Conditions for data sharing and reuse.
1. The wrangler will submit the data to our data store and it will be available in our data portal.

There is also a programmatic submission route which enables more automation of the process. If you wish to investigate this submission route, please contact us.  

The submission process is evolving and we are working to improve the systems you interact with and make the process more self-driven. We are keen to hear your feedback on the existing process and what features would make the submission process more straightforward for you to use. Please let us know if you have any suggestions.

## After submission

After the data has been submitted, it will be made available in our data portal. For SmartSeq2 and 10x v2 single cell RNAseq experiments, the data will also be processed by our standard analysis pipelines. These results will be deposited in the data store alongside your raw data and will be discoverable via the data portal. Your data will also be available for use directly in the [analysis applications](https://dev.data.humancellatlas.org/analyze/methods/methods) available throught this platform. 

### Archival submission

In order to support you when you publish using your data we will also submit data to community standard archives and return you the archival accessions that you need to publish the data. 

Currently we are able to archive any sequencing data which is submitted to us. Our default archives for submission are the BioStudies, BioSamples, and European Nucleotide Archives based at EMBL-EBI. We are working towards supporting submission to GEO if your funding mandates submission there. Please let the data wrangler know if this is the case when you start your submission process.

At the moment we will not automatically archive imaging data but we are engaged with the community to understand what are the archival best practice for biological images and then we will work to support submission to these archives.  

Start the HCA submission process by emailing [data-help@humancellatlas.org](mailto:data-help@humancellatlas.org).
