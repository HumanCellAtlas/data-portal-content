---
path: "/develop/development-guides/pipeline-development-guide"
date: "2018-05-03"
title: "Pipeline Development Guide"
subTitle: "Pipeline Development Guide Yo I am subtitle"
---
## Quick Start Guide for Building Analysis Pipelines

The building blocks of a robust analytical pipeline include:
* a workflow language
* tools designed to manipulate the data type particular to the pipeline
* a containerization mode that enables the components of the pipeline to be bundled together for ease of use
* a benchmarking or testing protocol that can evaluate the accuracy and flexibility of the pipeline

Here we highlight resources we have successfully used for pipeline building. There are many more resources in the community and this list is not meant to be exhaustive; we simply offer it as a starting guide based on our experience.

Our pipelines for analysis of data from Smart-seq2 and 10x v2scRNA-seq assays are in the Github [Sylab repository](https://github.com/HumanCellAtlas/skylab/tree/master/pipelines).

### Workflow Language Resources

Workflow Description Language, or [WDL](https://software.broadinstitute.org/wdl/), was designed by the Broad Institute as a human-readable and writable language for describing workflows and tasks. The [OpenWDL](http://www.openwdl.org/ community has moved WDL into the broader community to guide development and adoption. 

Common Workflow Language, or [CWL](https://www.commonwl.org/), is also widely used to develop analysis workflows and tools for data-intensive fields like genomics. See the [CWL User Guide](https://www.commonwl.org/user_guide/) for more information.

### Utilities for Manipulating Data Types

[SCTools](https://github.com/HumanCellAtlas/sctools) are a package of utilities for manipulating sequence data for analysis of large biological datasets.

[Picard Tools](https://broadinstitute.github.io/picard/) are command line tools that enable manipulation of large-scale sequencing data and data file formats like SAM/BAM/CRAM and VCF.

* SAM stands for Sequence Alignment Map, and is a tab-delimited text file of nucleotide sequence alignment data.
* The binary version of a SAM file is called a BAM file.
* A CRAM file is a compressed version of an alignment file.
* VCF, or Variant Call Format, is a text file format, generally compressed, that has meta-information and data about variants identified in the sequence.

[Samtools](https://sourceforge.net/projects/samtools/) are tools for manipulating next-generation sequencing data in the SAM format.

[HISAT2](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4655817/) (Hierarchical Indexing for Spliced Alignment of Transcripts) is a tool that aligns RNA sequence reads to a reference sequence to enable association of transcripts to their cognate genes.

[RSEM](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3163565/) (RNA-Seq by Expectation Maximization) is a tool that quantifies the abundances of transcripts identified in an RNA sequencing experiment.

### Testing and Benchmarking

Unity Benchmarking Service, currently under construction and described [here], (https://docs.google.com/document/d/1_gxct8eVb2dXjQe3YXAFh_0R5dtYMvpc9lfhRh0JgU4/edit) is designed to facilitate community development and contribution of pipelines and pipeline improvements.

[Portability Service](/learn/userguides/secondary-analysis/pipeline-portability) allows you to determine whether your pipeline works in the HCA, or in select non-HCA environments. Additionally, you can attach your environment of interest to the portability system to check whether an HCA pipeline works in that environment.

### Containerization Resources

Containers are used to store and execute all the software needed to run a program or set of programs; they are described in more detail [here](https://software.broadinstitute.org/firecloud/documentation/article?id=11252).

[Docker](https://www.docker.com/) is the most widely used brand of container.

[Dock Store](https://dockstore.org/), used by the [GA4GH](https://www.ga4gh.org/), is an open platform that stores docker-based tools written in WDL or CWL.


## Getting Involved in Pipeline Development

We welcome your feedback about our current pipelines and your ideas for development of new pipelines. Send your thoughts via Canny (HCA Canny project?), or by contacting us directly at data-help@humancellatlas.org.

You are also welcome to attend meetings and participate in Slack discussions about secondary analysis pipelines. Here are some details:

1. Analysis Community Biweekly meetings are held every other Tuesday at 11AM, Eastern Time; view the [Agenda](https://docs.google.com/document/d/1860cE2zk2baXYefu5-WzQM_p_uTGjph6dWnehiRaFDw/edit#heading=h.rt36ocexz2z5)
2. Join the HCA Slack channels: go to [Join Slack http://join-slack.humancellatlas.org/](https://join-hca-slack.herokuapp.com/) to obtain an invitation. Once connected to Slack, consider joining these channels:  #general, #dcp, #ingestion-service, #data-store, #secondary analysis, #dcp-meeting-digest
3. Attend our Demos - when and how to view?
4. Coming soon:
  * Workshop on pipeline development - sign up! 
  * Forum - designed for community discussion about pipelines and analysis
5. Points of contact for specific needs: 
		Portability service
