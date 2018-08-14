---
path: "/develop/development-guides/tertiary-portal-development-guide"
date: "2018-05-03"
title: "Tertiary Portal Development Guide"
subTitle: "Tertiary Portal Development Guide"
---

# Creating Solutions using the DCP

The Human Cell Atlas Data Coordination Platform holds much potential to support and enrich solutions for single cell genomics. We hope this will point you to the resources to leverage to enable your creativity.

## General Description

We provide several computational solutions to leverage in building products. We have several REST APIs for programmatic inteface, an open metadata schema to leverage, cloud-native pipelines that are portable to multiple environments, and standardized domain specific methodology and visualizations. We provide a growing collection of vignettes as examples of interacting with different aspects of the DCP. After you have made a product interacting with the DCP, please register it with the Data Portal for data hand-off or list it in our Registry.

## Examples

**Consumer Vignettes** These vignettes highlight the process of certain programmatic tasks that involve the DCP.

[Consumer Vignettes](develop/development-guides/consumer-vignettes)   

## Working with Ingest

**Ingest API** Ingest provides a programmatic API for submitting data. This may be useful, for example, for LIMs integration solutions. This does require authentication and would require contacting the ingest team.

[Starting point: GitHub Repository Ingest Central (ingest-central)](https://github.com/HumanCellAtlas/ingest-central)    
[GitHub Repository for Ingest API(ingest-broker-api)](https://github.com/HumanCellAtlas/ingest-broker-api)    
[HAL Browser for the Ingest API](http://api.ingest.dev.data.humancellatlas.org/browser/index.html)   

## Learning More About Metadata

**HCA Metadata** The HCA metadata schema is a curated description of the entities and thier relationships captured in HCA data. The metadata schema is public to review on GitHub. The metadata schema is also extensible and open for changes through pull requests.

[Learn More About Metadata](https://github.com/HumanCellAtlas/metadata-schema/tree/master/docs)   
[Github Repository for metadata schema (metadata-schema)](https://github.com/HumanCellAtlas/metadata-schema)   
[GitHub Repository for the metadata API Library (metadata-api)](https://github.com/HumanCellAtlas/metadata-api)   

## Accessing the Datastore

**Consumer API** Data in the HCA data store can be accessed programmatically through the consumer API. This interface includes both a REST API end point and a CLI (python).

[Consumer API Swagger](https://dss.integration.data.humancellatlas.org)   
[HCA DCP CLI](https://hca.readthedocs.io/en/latest)   

## Leveraging Pipelines

**Pipelines** Our cloud-native pipelines are created using GA4GH workflow languages (CWL or WDL). On release, these pipelines can be found on Dockstore and during development can be found in GitHub. Our pipelines are modular and one can also reuse the tasks (or tools) that comprise the pipelines; we point to both pipelines and tasks below.

[GitHub Repository for Pipelines (Skylab)](https://github.com/HumanCellAtlas/skylab)   
[Pipeline Tasks](https://github.com/HumanCellAtlas/skylab/tree/master/library/tasks)   
[Dockstore](https://dockstore.org)   

## Accessing the Matrix Service

**Matrix Service API** The matrix service enables the ability to create matrices from underlying data in the DCP. The matrix service currently exposes a REST API endpoint. This can be given a manifest of files to combine, that can be polled until the service generates the requested martix for download.

Matrix Service Description - Coming Soon    
Matrix service swagger - Coming Soon   

## Finding Modules for your Solution

**HCA DCP Methods Registry** The methods registry contains domain specific computational methodology and visualization that are standardized in a way we hope enables clear communication and ease of use between the methodologists and engineers who may want to leverage the software.

[Methodology Listing](analyze/methods/methods)   
[Visualizations Listing](analyze/visualization-components/visualization-components)   

## Registering with the Data Portal

**Portal hand-off** The data portal provides the ability for portals and other solutions to "register" to the data portal. This enable users to move from the data portal to the registered product as they explore data. This is an excellent way to integrate with the DCP.

Hand-off Description - Coming Soon   
Register for the Hand-off - Coming Soon  

## List Your Solution in the Registry

Please list your solution with the registry so our community of scientists know about it and can easily find it as they need it.

Instructions - Coming Soon   
