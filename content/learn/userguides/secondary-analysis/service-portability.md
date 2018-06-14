---
path: /learn/userguides/secondary-analysis/service-portability
date: "2018-05-03"
title: "Secondary Analysis Service Portability"
---

## Secondary Analysis Service Portability

### What do we mean by portability?

In the software world, portability describes software that can be transferred from one machine or system to another. For pipelines, the degree to which a pipeline can be run in multiple execution environments is a reflection of its portability. One goal of the HCA computational pipelines effort is to implement pipelines that are portable to many environments.

### Introduction

The Human Cell Atlas Data Portal aims to break down barriers in data use, offering immediate and open access to data. But we also want everyone to be able to use the data. To truly break the walls that silo many data repositories we have to go beyond data access and enable data interoperability between repositories. If pipelines are portable, data within and outside the HCA project can be processed using the same methodology and used together to make scientific observations. This data interoperability enhances the impact on scientific discovery.  Given the importance of portability, we have developed a service that does the following:
1. measures if HCA workflows can run in a variety of environments outside of the DCP (local, grid-based, and cloud-based environments) 
2. enables others to extend the service so pipelines can be regularly tested for portability in additional execution environments beyond what we specify 

The HCA portability service is a driver project of the [Global Alliance for Genomics and Health (GA4GH)](https://www.ga4gh.org/), demonstrating APIs targeting the sharing of workflows. In conjunction with the GA4GH and their other driver projects we are working to develop policies, standards, and tools for genomic and health-related data sharing. We welcome community involvement and feedback; contact [GA4GH](INFO@GA4GH.ORG) or the [HCA DCP](mailto:data-help@humancellatlas.org) for more information.

### How can I use the Portability Service?

The portability service enable you to:
1. Submit pipelines to the service to check if they can run in HCA-supported environments. This step can be incorporated into your continuous integration plan.
2. Submit pipelines to check if they can run in environments external to the HCA (eg. DNAnexus).
3. Attach your environment to the portability service to receive submitted pipelines and confirm they run in your environment.

### Portability Service Execution Environments
* [DNAnexus](https://www.dnanexus.com/)
* Others?
* 

### How do I submit a pipeline to the portability service?

HCA pipelines are automatically submitted to this service as a part of our development process. If you are interested in submitting a pipeline to the portability service, please see this tutorial.
