---
path: "/analyze/methods/methods-packages/stream"
date: "2018-12-07"
title: "STREAM: Single-cell Trajectories Reconstruction, Exploration And Mapping of single-cell data"
author: "Huidong Chen, Luca Pinello"
description: "STREAM is an interactive computational pipeline for reconstructing complex cellular developmental trajectories from sc-qPCR, scRNA-seq or scATAC-seq data."
githubUrl: "https://github.com/pinellolab/STREAM/"
appUrl: " http://stream.pinellolab.org/"
componentName: "analysisDetail"
---

[STREAM](https://bioconda.github.io/recipes/stream/README.html) is an interactive computational pipeline for reconstructing complex cellular developmental trajectories from sc-qPCR, scRNA-seq or scATAC-seq data.

# Use

`docker pull quay.io/biocontainers/stream:0.3.2--py35r351h26a2512_1`

`docker run  -v $PWD:/data -w /data  pinellolab/stream STREAM -m data_Guo.tsv.gz -l cell_label.tsv.gz -c cell_label_color.tsv.gz -s all`

# Validate
validation command line pending


# Integrate
View STREAM in its [production portal](http://stream.pinellolab.org/).

<a href="http://stream.pinellolab.org/" target="_blank">
  <img src="../_images/methods/stream_logo.png" width=200/>
</a>

# Contact
Huidong Chen (<a href="mailto://huidong.chen@mgh.harvard.edu">huidong.chen@mgh.harvard.edu</a>), Luca Pinello (<a href="mailto://lpinello@mgh.harvard.edu">lpinello@mgh.harvard.edu</a>)