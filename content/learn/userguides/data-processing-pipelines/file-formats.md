---
path: "/learn/userguides/data-processing-pipelines/file-formats"
date: "2018-05-03"
title: "Data Processing Pipelines File Formats"
---

## File Formats of the Data Processing Pipelines Service

### Data Storage File Format

The Data Processing Pipelines Service uses the [Zarr version 2](https://zarr.readthedocs.io/en/stable/spec/v2.html) format for storage of expression matrices and their associated metadata. Basically, this format stores information in groups and arrays; where groups can contain other groups and arrays are stored chunked and compressed. The group and chunk structure is conveyed in the file names and directory structure. For information about creating and using the Zarr format see this [Zarr tutorial](https://zarr.readthedocs.io/en/stable/tutorial.html#). For information about the file structure and content of the files we generate, see [this doc](https://github.com/HumanCellAtlas/skylab/blob/6aa3a97800aab23c18cd746800b9e4073e53e810/docs/matrix_format_spec.md).

### Matrix Service Download File Formats

The Matrix Service receives requests for data through an API call using bundle UUIDs. Users can specify the desired file type for the outputs from among three choices: Zarr, CSV, and .loom formats. The Service then accesses data files from the Data Store and moves the data into the designated file type.

The files can be used with the following applications (point to Geneviee's consumer vignettes). They can be imported into different environments using ...code.
