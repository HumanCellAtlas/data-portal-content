---
path: "/develop/development-guides/ingest-broker-development-guide"
date: "2018-05-03"
title: "Ingest Broker Development Guide"
subTitle: "General guidelines for developing brokers for the Ingest API."
---

# Ingest Broker Development Guide

We envisage that Brokers will expose those parts of the Ingest API that it makes sense for a Submitter to call directly (e.g. data file upload). Brokers may therefore expose REST API functions to perform:

* List / view Metadata Schemas.
* Start / submit / cancel a submission.
* Upload / reupload JSON Metadata Files.
* Get state of a submission, including metadata and data validation.

## Data Submission Broker

All data that are made available for the Human Cell Atlas first go through the process of ingestion through the Ingest API. Submission brokers take care of storing, processing, and (if needed) converting submissions to ensure that data are interoperable. A submission refers to a collection of scientific files and the metadata about them, contributed to the HCA by scientific teams around the world.

### Authentication

In order to use the services through the API, the client must first obtain an authentication token through the authentication broker. The details for acquiring an auth token will be provided in the future. For now, the authentication token will be referred to as `$AUTH_TOKEN` in the examples.


### API Discovery

The Ingest API is mainly hypermedia driven using Hypermedia as the Engine of Application State (HATEOAS). As such, querying the API origin at, say, `http://api.ingest.data.humancellatlas.org`, for example,

    curl -H "Accept: application/json" http://api.ingest.data.humancellatlas.org

returns an embedded `_links` JSON map that contains links to important API endpoints. One such endpoint is the submissions endpoint in `/submissionEnvelopes`.

### Submission Process

1. [Create submission envelope](#step1)
1. [Add metadata to the submission envelope](#step2)

#### <a name="step1"></a>Create Submission Envelope

To create a new submission envelope, the client must send a HTTP POST request to the submission endpoint with an empty JSON.

```
curl -X POST \
     -H "Authorization: Bearer $AUTH_TOKEN" \
     -H "Content-type: application/json" \
     -d {} \
     http://api.ingest.data.humancellatlas.org/submissionEnvelopes
```

This will return details of the new submission envelope that looks like the following:

```
{
  "submissionDate" : "2018-10-19T13:18:01.108Z",
  "updateDate" : "2018-10-19T13:20:35.589Z",
  "user" : "...",
  "lastModifiedUser" : "anonymousUser",
  "uuid" : {
    "uuid" : "d2e8ccd7-6987-4b86-8eeb-188aeaf9ef7b"
  },
  "events" : [ ],
  "stagingDetails" : {...},
  "submissionState" : "Invalid",
  "triggersAnalysis" : true,
  "submissionErrors" : [ ],
  "open" : true,
  "_links" : {...}
}
```

The `_links` property contains a map of service discoverable endpoints associated with the create submission envelope. The `self` link refers back to the submission envelope itself. Some of the links in this map also come with human readable `title`s that help describe their respective service:

```
"_links" : {
    "self" : {
      "href" : "http://api.ingest.data.humancellatlas.org/submissionEnvelopes/5b4dec891edf300007b4b17b"
    },
    "submissionEnvelope" : {
      "href" : "http://api.ingest.data.humancellatlas.org/submissionEnvelopes/5b4dec891edf300007b4b17b",
      "title" : "A single submission envelope"
    },
    "biomaterials" : {
      "href" : "http://api.ingest.data.humancellatlas.org/submissionEnvelopes/5b4dec891edf300007b4b17b/biomaterials"
    },
    "processes" : {
      "href" : "http://api.ingest.data.humancellatlas.org/submissionEnvelopes/5b4dec891edf300007b4b17b/processes"
    },
    "files" : {
      "href" : "http://api.ingest.data.humancellatlas.org/submissionEnvelopes/5b4dec891edf300007b4b17b/files",
      "title" : "Access or create, within a submission envelope, a new assay"
    },
    "projects" : {
      "href" : "http://api.ingest.data.humancellatlas.org/submissionEnvelopes/5b4dec891edf300007b4b17b/projects",
      "title" : "Access or create projects. Creation can only be done inside a submission envelope"
    },
    "protocols" : {
      "href" : "http://api.ingest.data.humancellatlas.org/submissionEnvelopes/5b4dec891edf300007b4b17b/protocols",
      "title" : "Access or create protocols"
    },
	...
}
```

As the items in the links map are structured JSON objects, to refer to the actual link, they should be extracted from the nested `href` property. For example to retrieve the link to the submission envelope itself, the property chain is `_links.self.href`.

#### <a name="step2"></a>Add Metadata to a Submission Envelope

Once the submission envelope is ready, metadata can be added to it through the respective endpoints for the particular type of metadata. The sample links shown previously in the submission creation section demonstrate this. Sending a HTTP GET request to any of the links will return a list of metadata of the given type. For example if a GET request is sent to the `http://api.ingest.data.humancellatlas.org/submissionEnvelopes/5b4dec891edf300007b4b17b/biomaterials`, a list of biomaterial metadata contained in the submission envelope `5b4dec891edf300007b4b17b` will be returned.

To add metadata to the submission envelope, the client must send a HTTP POST request to the endpoint with the metadata content in JSON format. For example, to add biomaterial metadata to the endpoint above, the following cUrl command can be executed:

```
curl -X POST \
  http://api.ingest.data.humancellatlas.org/submissionEnvelopes/5b4dec891edf300007b4b17b/biomaterials \
  -H 'content-type: application/json' \
  -d '{
    "describedBy" : "https://schema.humancellatlas.org/type/biomaterial/10.1.1/donor_organism",
    "schema_version" : "10.1.1",
    "schema_type" : "biomaterial",
    "biomaterial_core" : {
      "biomaterial_id" : "DEMO-donor_MGH30",
      "biomaterial_name" : "DEMO donor MGH30",
      "ncbi_taxon_id" : [ 9606 ],
      "describedBy" : "https://schema.humancellatlas.org/core/biomaterial/7.0.3/biomaterial_core",
      "schema_version" : "7.0.3"
    },
    "genus_species" : [ {
      "describedBy" : "https://schema.humancellatlas.org/module/ontology/5.0.0/species_ontology",
      "text" : "Homo sapiens"
    } ],
    "is_living" : true,
    "biological_sex" : "unknown"
  }'
```

The example metadata content in this document may be out of date. The updated metadata schema can be found in [schema.humancellatlas.org](https://schema.humancellatlas.org/~).
