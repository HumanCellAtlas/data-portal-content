---
path: "/learn/userguides/accessing-data/using-the-cli-to-access-data"
date: "2018-05-30"
title: "Using the CLI to Access Data"
---
## Using the CLI to Access Data
### Installation
It is reccommended that the CLI be run in a virtual environment to be sure of which dependency versions you are using. A common utility for creating and managing vritual environment is `virtualenv`. Installation instructions for `virtualenv` can be found online. In Mac OS High Sierra, one might use

`sudo pip install virtualenv`

`virtualenv venv`

`source venv/bin/activate`

Now follow the instructions [heere](https://hca.readthedocs.io/en/latest/) to install the CLI. That link also covers basic instructions for using each of the available CLI commands. This page reviews a specific example for how the CLI can be used to download data.

### Finding Data
You can easily list all bundles in the Data Store by using the following Elastic Search command:

    hca dss post-search --es-query "{}" --replica=aws | less
    
This section is not meant to be a tutorial on how to use Elastic Search for searching the Data Browser, but here is a more complicated example:



### Downloading Data
Once you find bundles that you would liek to download then you can use the following command to download a bundle. This can be scripted to itterate through a list of bundle IDs with some basic shell scripting.

Say your search returned the following bundle ID information:

    {
      "bundle_fqid": "2f08b7cd-2e39-44f2-b7fa-d4a373266104.2018-08-28T213422.136870Z",
      "bundle_url": "https://dss.data.humancellatlas.org/v1/bundles/2f08b7cd-2e39-44f2-b7fa-d4a373266104?version=2018-08-28T213422.136870Z&replica=aws",
      "search_score": null
    }

To then download that bundle from the AWS replica you would use this command:

    hca dss download --bundle-uuid 2f08b7cd-2e39-44f2-b7fa-d4a373266104 --version 2018-08-28T213422.136870Z --replica aws


