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

### Create Submission Envelope

To create a new submission envelope, the client must send a HTTP POST request to the submission endpoint with an empty JSON.

```
curl -X POST \
     -H "Authorization: Bearer $AUTH_TOKEN" \
     -H "Content-type: application/json" \
     -d {}
     http://api.ingest.data.humancellatlas.org/submissionEnvelopes

```
