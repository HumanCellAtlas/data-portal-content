---
path: "/about/what-is-the-platform/ingest-service"
date: "2018-05-03"
title: "Ingest Service"
---

## Ingest Service

The Ingest Service is responsible for the intake of biomolecular data into the Human Cell Atlas (HCA) Data Coordination Platform (DCP). In particular, Ingest Service is tasked to process, validate, and assemble biomolecular data received before attempting to persist them into the central Data Storage System (DSS), where all HCA data are stored.

### Process

Biomolecular data are received as structured spreadsheets from data contributors. The data from these spreadsheets are processed into formats that enable interoperation with data coming from all other contributors. Actual files that contain important scientific data such as sequencing files do not undergo this process however; they are transferred to the HCA cloud storage through the Upload Service.

#### Upload Service

An important part of 

### Validate

Once the data are processed, they are validated to check if they conform to the right the format. In this stage, the Ingest Service is able to point out any errors in the submitted data based on 

### Assemble

All validated data are then 

