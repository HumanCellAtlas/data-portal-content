---
path: "/analyze/methods/methods-packages/sc3"
date: "2018-09-14"
title: "Single-cell consensus clustering (SC3)"
author: "Martin Hemberg"
description: "SC3 is an unsupervised clustering method for scRNA-seq data."
githubUrl: "https://github.com/hemberg-lab/SC3"
appUrl: "http://bioconductor.org/packages/SC3"
upstreamRegistryUrl: "http://bioconductor.org/packages/SC3"
componentName: "analysisDetail"
---

[![Build Status](http://www.bioconductor.org/shields/build/release/bioc/SC3.svg)](https://git.bioconductor.org/packages/SC3)

[SC3](http://bioconductor.org/packages/SC3) is an unsupervised clustering method for scRNA-seq data. SC3 also estimates the number of clusters and it provides features to aid the biological interpretation of the clusters.

# Use

docker pull command pending

``docker run -v `pwd`:/sc3_data -w /sc3_data --rm sc3 Rscript /software/scripts/run_sc3.R --input="``[deng-reads.rds](https://github.com/hemberg-lab/scRNA.seq.course/raw/master/deng/deng-reads.rds)``" --cell_labels ``


# Validate 
``docker run -v `pwd`:/sc3_data -w /sc3_data --rm sc3 Rscript /software/scripts/run_sc3.R --validate``

# Contact
Martin Hemberg (<a href="mailto://mh26@sanger.ac.uk">mh26@sanger.ac.uk</a>)
