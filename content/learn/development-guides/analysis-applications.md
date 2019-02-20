---
path: "/learn/development-guides/analysis-applications"
date: "2018-05-03"
title: "Analysis Applications"
subTitle: "Technical resources to support the development and integration of your analysis applications."
---

# Creating Solutions using the DCP

The Human Cell Atlas Data Coordination Platform aims to support and encourage cellular resolution research in a variety of biological and computational areas. This page highlights available resources for enabling these areas of scientific exploration.

We provide several REST APIs for programmatic interface, an open metadata standard, cloud-native pipelines that are portable to multiple environments, and standardized domain-specific analysis and visualization packages. To provide guidance, a growing collection of vignettes is available showing how to interact with different DCP components and how to use packages available in the Data Portal. 

Anyone who has developed their own analysis or visualization package that interacts with the DCP is highly encouraged to register it with the Data Portal for data hand-off or list it in the Methods Registry.

## Working with the Ingestion Service

The Ingestion Service provides a programmatic API for submitting data to the HCA DCP. The Ingest API could be used, for example, for enabling integration with existing LIMS software. Using the Ingest API requires authentication and contacting the Ingestion Service team at [data-help@humancellatlas.org](mailto:data-help@humancellatlas.org).

[Ingest Broker Development Guide](https://prod.data.humancellatlas.org/learn/development-guides/ingest-broker-development-guide)   
[GitHub Repository: Ingest Central (ingest-central)](https://github.com/HumanCellAtlas/ingest-central) (a good starting point)   
[GitHub Repository: Ingest API (ingest-broker-api)](https://github.com/HumanCellAtlas/ingest-broker-api)   
[HAL Browser for the Ingest API](http://api.ingest.dev.data.humancellatlas.org/browser/index.html)   

## Learning about Metadata

The [HCA metadata standard](https://dev.data.humancellatlas.org/learn/metadata/structure) is the common set of guidelines the HCA uses to describe samples, protocols, and files associated with projects. The metadata standard is expressed as JSON schemas representing the submitted entities, their associated fields, and the relationships between them. The HCA is committed to evolving the metadata standards based on the needs of the scientific community, so everyone is welcome to suggest metadata updates by creating GitHub issues or emailing the metadata team at [data-help@humancellatlas.org](mailto:data-help@humancellatlas.org).

[Metadata Dictionary](https://dev.data.humancellatlas.org/learn/metadata/metadata-dictionary)   
[Github Repository: metadata schema (metadata-schema)](https://github.com/HumanCellAtlas/metadata-schema)   
[GitHub Repository: metadata API library (metadata-api)](https://github.com/HumanCellAtlas/metadata-api)   

## Accessing the Data Store

Data in the HCA Data Store can be accessed programmatically through the consumer API. This interface includes both a REST API end point and a CLI (python).

[Consumer API Swagger](https://dss.integration.data.humancellatlas.org)   
[HCA DCP CLI](https://hca.readthedocs.io/en/latest)   

## Leveraging Data Processing Pipelines

The HCA DCP cloud-native data processing pipelines are created using GA4GH workflow languages (CWL or WDL). On release, these pipelines can be found on Dockstore, and during development they can be found in GitHub. The pipelines are modular, and anyone can reuse the tasks or tools that comprise them.

[GitHub Repository: Pipelines (Skylab)](https://github.com/HumanCellAtlas/skylab)   
[Pipeline Tasks](https://github.com/HumanCellAtlas/skylab/tree/master/library/tasks)   
[Dockstore](https://dockstore.org)   

## Accessing the Matrix Service

The Matrix Service enables the creation of matrices from underlying processed data in the HCA DCP. The Matrix Service currently exposes a REST API endpoint. This interface can be given a manifest of files to combine which can be polled until the service generates the requested matrix for download.

Matrix Service Description - Coming Soon    
Matrix Service swagger - Coming Soon   

## Finding Packages for Your Solution

**HCA DCP Methods Registry** The Methods Registry contains domain-specific computational methodology and visualization component packages that are standardized in a way we hope enables clear communication and ease of use between the methodologists and engineers.

[Methodology Listing](/analyze/methods/methods)   
[Visualization Component Listing](/analyze/visualization-components)   

## Registering with the Data Portal

**Portal hand-off** The Data Portal will soon provide the ability for portals and other solutions to "register" with the Data Portal. Registration enables users to move from the Data Portal to the registered product as they explore data, which is an excellent way to integrate with the DCP.

Hand-off Description - Coming Soon   
Register for the Hand-off - Coming Soon
If you are interested, please email us to be placed on an alpha user list.

## Listing Your Solution in the Registry

Please list your solution with the registry so our community of scientists knows about it and can easily find it.

[Submit a Portal](https://github.com/HumanCellAtlas/data-portal-content/issues/new?template=submit-portal)    
[Submit a Methodology](https://github.com/HumanCellAtlas/data-portal-content/issues/new?template=submit-method)     
[Submit a Visualization Component](https://github.com/HumanCellAtlas/data-portal-content/issues/new?template=submit-visualization-component)     
