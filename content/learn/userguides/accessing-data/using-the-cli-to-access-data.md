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

Now install the `hca` command line

`pip install hca`

### Usage
The hca package installs a command-line utility `hca`.

To see the list of commands you can use, type `hca --help`.  Commands are grouped into major categories that
roughly correspond to DCP system components, e.g. DSS, Staging Service.  To get detailed help for a particular
command group type, e.g. `hca dss --help`.  Details for all the `hca` command line options can be found [here](https://hca.readthedocs.io/en/latest/)

### Configuration management
The HCA CLI supports ingesting configuration from a configurable array of sources. Each source is a JSON file.
Configuration sources that follow the first source update the configuration using recursive dictionary merging. Sources
are enumerated in the following order (i.e., in order of increasing priority):

- Site-wide configuration source, ``/etc/hca/config.json``
- User configuration source, ``~/.config/hca/config.json``
- Any sources listed in the colon-delimited variable ``HCA_CONFIG_FILE``
- Command line options

### Finding Data

### Downloading Data


