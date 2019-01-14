---
path: "/analyze/methods/methods-packages/stream"
date: "2018-12-07"
title: "STREAM: Single-cell Trajectories Reconstruction, Exploration And Mapping of single-cell data"
author: "Huidong Chen, Luca Pinello"
githubUrl: "https://github.com/pinellolab/STREAM/"
appUrl: " http://stream.pinellolab.org/"
dockerUrl: "https://quay.io/repository/biocontainers/stream"
Language: Python
upstreamregistryUrl: "https://bioconda.github.io/recipes/stream/README.html"
testdatalocation: "in docker container"
usageExample: "docker run  -v $PWD:/data -w /data  pinellolab/stream STREAM -m data_Guo.tsv.gz -l cell_label.tsv.gz -c cell_label_color.tsv.gz -s all"
validateCommand: ""
description: "STREAM is an interactive computational pipeline for reconstructing complex cellular developmental trajectories from sc-qPCR, scRNA-seq or scATAC-seq data."
logoUrl: "https://github.com/HumanCellAtlas/data-portal-content/raw/master/content/analyze/_images/methods/stream_logo.png"
implementationUrl: "http://stream.pinellolab.org/"
componentName: "analysisDetail"
---

STREAM is an interactive computational pipeline for reconstructing complex cellular developmental trajectories from sc-qPCR, scRNA-seq or scATAC-seq data.
