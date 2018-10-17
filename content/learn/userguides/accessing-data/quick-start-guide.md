---
path: "/learn/userguides/accessing-data/quick-start-guide"
date: "2018-05-30"
title: "Quick Start Guide"
---


## Quick Start Guide
There are several ways to access the data in the Data Store. This section briefly reviews how to find and download data using the most common methods, the Data Browser and the CLI, and finally, it points to some software programs that demonstrate some programmatic access patterns. Downloading data via the Data Browser and the CLI both first require installation of the HCA CLI.

Data in the *Data Store* is organized into data bundles. A bundle is a group of files organized into a versioned set and tagged with a unique global identifier. One of the goals of the *Data Store* is to provide a structure that makes it easy to keep related files together. Bundles make it easy to keep metadata together with associated data. The versioning structure also allows for parts of a bundle to be updated. The *Data Store* keeps all versions of data. This way research can be pinned to a specific version of data and metadata.

### Installing the HCA CLI
It is recommended that the CLI be run in a virtual environment to control Python library dependencies. A common utility for creating and managing virtual environment is `virtualenv`. Installation instructions for `virtualenv` can be found online. In Mac OS High Sierra, one might use:

`sudo pip install virtualenv`

`virtualenv venv`

`source venv/bin/activate`

Now install the HCA command line interface:

`pip install hca`

There are detailed configuration instructions [here](https://hca.readthedocs.io/en/latest/) as well as basic instructions for using each of the available CLI commands.

### Using the Data Browser to Access Data
#### Finding Data
The **Explore** section of the data portal provides an interactive data browser. Select a subset of data by checking various boxes in the Organ, Method, Donor, Specimen sections. You can see how many specimens have been selected in the **Specimens** tab. It also gives an estimate of the size of the data set if the entire list were downloaded.

#### Downloading a Data Manifest
Once you have selected data through the user interface, click the Download button on the right hand side of the page to download the list of data sets (note that the actual data specified by the list is NOT downloaded in this step). We call this list a manifest. The Download dialog box gives you the option to further refine the types of files you would like to be included in the manifest. Select which files to include in the manifest. Be cognizant that the sizes listed are for the actual files and not the manifest itself. 

Press the _Download Manifest_ button and a file called `export.tsv` will be saved to your local file system.

The format of the Manifest file is a simple tab separated text file, with the first line representing the header title for each column. It is OK to remove rows for unwanted files but the header row must remain, and the columns should remain the same.

### Using the CLI to Access Data
The CLI is a powerful tool that can be used to find and download data from the *Data Store*. There are several subsections to the `hca` tool. Data search, inspection and download are all available from the `hca dss` section. Help text is available by typing:

`hca dss --help`

Help is also available for the commands under the `dss` section. For example help on the get-bundle command can be seen by entering

`hca dss get-bundle --help`

Now let's try using the manifest file to download files. 

Print the help for how to download the manifest of files:

`hca dss download_manifest --help`

Now execute the command to begin the download of the files listed in the `export.tsv` file:

`hca dss download_manifest --manifest export.tsv --replica aws`

Note that the download could take a long time depending on the number and size of files included in the Manifest file.

#### Finding Data
You can easily get a list of bundles in the *Data Store* by using the following Elastic Search command:

`hca dss post-search --es-query "{}" --replica=aws | less`
    
Note that this will return the first page of results found with the command. Searching for all bundles in the Data Store is not very useful though. 

`hca dss post-search --replica aws --es-query '{"query": {"bool": {"must": {"match": {"files.project_json.insdc_project.text": "SRP075496"}} , "must_not": { "exists": { "field": "files.analysis_file_json" }} } } }'`

This command will find all the ids of the original files associated with the project `SRP075496`, and not the analysis files.

#### Downloading Data
Once you find bundles that you would like to download use the command below. (Note that this command can be scripted to iterate through a list of bundle IDs with some basic shell scripting).

For example, if your search returned the following bundle ID information:

    {
      "bundle_fqid": "2f08b7cd-2e39-44f2-b7fa-d4a373266104.2018-08-28T213422.136870Z",
      "bundle_url": "https://dss.data.humancellatlas.org/v1/bundles/2f08b7cd-2e39-44f2-b7fa-d4a373266104?version=2018-08-28T213422.136870Z&replica=aws",
      "search_score": null
    }

then to download that bundle from the AWS replica you would use this command:

    hca dss download --bundle-uuid 2f08b7cd-2e39-44f2-b7fa-d4a373266104 --version 2018-08-28T213422.136870Z --replica aws

### Using the Data
The Data Coordination Platform (DCP) offers a number of different programatic ways to access the data. The Application Programming Interfaces (APIs) that we provide are described [here](https://dev.data.humancellatlas.org/develop/api-documentation/data-store-consumer-api). The developers of the DCP have also created a number of example programs demonstrating how to use the APIs, and they can be found [here](https://dev.data.humancellatlas.org/develop/development-guides/consumer-vignettes). These examples are designed to demonstrate basic access patterns, but they  are not intended to demonstrate any type of analysis.
