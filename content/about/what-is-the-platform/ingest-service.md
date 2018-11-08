---
path: "/about/what-is-the-platform/ingest-service"
date: "2018-05-03"
title: "Ingest Service"
---

## Ingest Service

The Ingest Service is responsible for the intake of biomolecular data into the Human Cell Atlas (HCA) Data Coordination Platform (DCP). In particular, Ingest Service is tasked to process, validate, and assemble biomolecular data received before attempting to persist them into the central Data Store, where all HCA data are stored.

### Process

Biomolecular data are received as structured spreadsheets from data contributors. The data from these spreadsheets are processed into formats that enable interoperation with data coming from all other contributors. Actual files that contain important scientific data such as sequencing files do not undergo this process, however; they are transferred to the HCA cloud storage through the Upload Service.

#### Upload Service

An important part of the data ingestion stage is the upload of biomolecular data files that form the core of the Human Cell Atlas. Data files are initially stored through the Upload Service before they are transferred to the central Data Store.

### Validate

Once the data are processed, they are validated to check if they conform to the right the format. At this stage, the Ingest Service is able to point out any errors in the submitted data based on HCA metadata schema. Also at this stage, data files are checked for any erors to ensure that they are well-formed and that they conform to data standards.

### Assemble

All validated data are then transmitted to the Data Store. The Ingest Service prepares the data received from the contributors so that they can searched, browsed, analysed, etc. through the Data Portal.

