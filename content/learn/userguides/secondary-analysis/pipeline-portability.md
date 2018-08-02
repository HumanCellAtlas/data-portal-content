---
path: "/learn/userguides/secondary-analysis/pipeline-portability"
date: "2018-07-12"
title: "Secondary Analysis Pipeline Portability"
---

## Secondary Analysis Pipeline Portability

### What do we mean by portability?

When developing a pipeline, it can be easy to build in assumptions about the environment and infrastructure in which it will run. This makes is difficult for others to use or modify the pipeline. One goal of the Human Cell Atlas (HCA) is to create secondary analysis pipelines that can be run by many investigators, not just within the Data Coordination Platform (DCP), and we call this goal secondary analysis pipeline portability.

### Introduction

The HCA aims to break down barriers in data use, offering immediate and open access to data. But we also want everyone to be able to use the data. To truly break the walls that silo many data repositories we have to go beyond data access and enable data interoperability between repositories. If pipelines are portable, data within and outside the HCA project can be processed using the same methodology and used together to make scientific observations. This data interoperability enhances the impact on scientific discovery.  Given the importance of portability, we have developed a service that does the following:

1. measures if HCA workflows can run in a variety of environments outside of the DCP (local, grid-based, and cloud-based environments). 
2. enables others to extend the service so pipelines can be regularly tested for portability in additional execution environments beyond what we specify. 

We use this service as part of our testing during pipeline development so that we can be sure that pipelines developed for the HCA can be executed successfully in many environments.

The HCA is a driver project of the [Global Alliance for Genomics and Health (GA4GH)](https://www.ga4gh.org/), and the portability service helps demonstrate GA4GH APIs for executing workflows in different infrastructures. In conjunction with the GA4GH and their other driver projects we are working to develop policies, standards, and tools for genomic and health-related data sharing. We welcome community involvement and feedback; contact [GA4GH](INFO@GA4GH.ORG) or the [HCA DCP](mailto:data-help@humancellatlas.org) for more information.

### How can I use the Portability Service?

The portability service enable you to:
1. Submit pipelines to the service to check if they can run in different environments. This step can be incorporated into your continuous integration plan.
2. Attach your environment to the portability service to receive submitted pipelines and confirm they run in your environment.

### Portability Service Execution Environments
* [dxWDL](https://github.com/dnanexus/dxWDL) on [DNAnexus](https://www.dnanexus.com/)
* [Cromwell](https://github.com/broadinstitute/cromwell) with a local, Linux backend
* More coming!

### How do I submit a pipeline to the portability service?

HCA pipelines are automatically submitted to this service as a part of our development process. If you are interested in submitting a pipeline to the portability service, please contact us (data-help@humancellatlas.org).
