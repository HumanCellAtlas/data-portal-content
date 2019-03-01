---
path: "/learn/api-documentation/data-store-consumer-api"
date: "2018-05-03"
title: "Data Store Consumer API"
---

## Data Store API

The [HCA Data Storage System](https://github.com/HumanCellAtlas/data-store) (DSS) is a replicated data storage system designed for hosting large sets of scientific experimental data on 
[Amazon S3](https://aws.amazon.com/s3/) and [Google Storage](https://cloud.google.com/storage/).

The DSS exposes both Python and REST APIs for interacting with the data and is built using [Chalice](https://github.com/aws/chalice),
[API Gateway](https://aws.amazon.com/api-gateway/) and [AWS Lambda](https://aws.amazon.com/lambda/). The API also
implements [Step Functions](https://aws.amazon.com/step-functions/) to orchestrate Lambdas for long-running tasks such
as large file writes. 

### Rest API 
You can find the API documentation and give it a try [here](https://dss.data.humancellatlas.org/).

### Python Library
The Python library is documented [here](https://hca.readthedocs.io/en/latest/).
 
