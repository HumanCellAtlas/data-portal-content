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
[![Build Status](https://travis-ci.org/pinellolab/STREAM.svg)](https://travis-ci.org/pinellolab/STREAM)

[STREAM](https://bioconda.github.io/recipes/stream/README.html) is an interactive computational pipeline for reconstructing complex cellular developmental trajectories from sc-qPCR, scRNA-seq or scATAC-seq data.

# Use

`docker pull quay.io/biocontainers/stream`

## Test data

`curl -L -o testData.zip https://www.dropbox.com/sh/n8qq4m7w17i6b07/AAAro_qY_-q5VBDC1sZg-LE5a?dl=0?dl=1`

Input files must be located in the directory where the docker container will be launched

## Trajectory inference with marker gene exploration (transcriptomic data)

<ul> <li style="list-style-type: none;">

### For Mac OS and Linux:

`docker run  -v $PWD:/data -w /data  pinellolab/stream STREAM -m `[ data_Nestorowa.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AAB9GyV9LjVoxZfOiT-h5B2Qa/Nestorowa_2016/data_Nestorowa.tsv.gz?dl=1)` -l `[ cell_label.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AAD38lqq1vKvPOXN5AgkMBfYa/Nestorowa_2016/cell_label.tsv.gz?dl=1)` -c `[ cell_label_color.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AABKYz6iITR0MHGoSLKTYxVta/Nestorowa_2016?dl=0&preview=cell_label_color.tsv.gz?dl=1)` --DE --TG --LG `


### For Windows:

`docker run  -v ${pwd}:/data -w /data  pinellolab/stream STREAM -m `[ data_Nestorowa.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AAB9GyV9LjVoxZfOiT-h5B2Qa/Nestorowa_2016/data_Nestorowa.tsv.gz?dl=1)` -l `[ cell_label.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AAD38lqq1vKvPOXN5AgkMBfYa/Nestorowa_2016/cell_label.tsv.gz?dl=1)` -c `[ cell_label_color.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AABKYz6iITR0MHGoSLKTYxVta/Nestorowa_2016?dl=0&preview=cell_label_color.tsv.gz?dl=1)` --DE --TG --LG `
</li> </ul>

## Feature mapping

<ul> <li style="list-style-type: none;">

### For Mac OS and Linux:


`docker run  -v $PWD:/data -w /data  pinellolab/stream STREAM -m `[ data_Olsson.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AAAnq2J4jQFGi-fari9MdTvla/Olsson_2016/data_Olsson.tsv.gz?dl=1)` -l `[ cell_label.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AADijJwgDGhzV_9ysH0sI31Ya/Olsson_2016/cell_label.tsv.gz?dl=1)` -c `[ cell_label_color.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AAA8-eOtgzplTQvRP4vfs7iFa/Olsson_2016/cell_label_color.tsv.gz?dl=1)` --lle_components 4 --EPG_shift`

`docker run  -v ${pwd}:/data -w /data  pinellolab/stream STREAM --new`[ data_perturbation.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AAAEZCnFl-EoAyGutCuzuyLGa/Olsson_2016/data_perturbation.tsv.gz?dl=1)`--new_l `[ cell_perturbation_label.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AABb5KU4S7GLtZM8NhVRErsqa/Olsson_2016/cell_perturbation_label_color.tsv.gz?dl=1)` --new_c `[ cell_perturbation_label_color.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AACVyTQDrmQHtuQhUqyG0ngCa/Olsson_2016/cell_perturbation_label.tsv.gz?dl=1)



### For Windows:

`docker run  -v ${pwd}:/data -w /data  pinellolab/stream STREAM -m `[ data_Olsson.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AAAnq2J4jQFGi-fari9MdTvla/Olsson_2016/data_Olsson.tsv.gz?dl=1)` -l `[ cell_label.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AADijJwgDGhzV_9ysH0sI31Ya/Olsson_2016/cell_label.tsv.gz?dl=1)` -c `[ cell_label_color.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AAA8-eOtgzplTQvRP4vfs7iFa/Olsson_2016/cell_label_color.tsv.gz?dl=1)` --lle_components 4 --EPG_shift`

 `docker run  -v ${pwd}:/data -w /data  pinellolab/stream STREAM --new`[ data_perturbation.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AAAEZCnFl-EoAyGutCuzuyLGa/Olsson_2016/data_perturbation.tsv.gz?dl=1)`--new_l `[ cell_perturbation_label.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AABb5KU4S7GLtZM8NhVRErsqa/Olsson_2016/cell_perturbation_label_color.tsv.gz?dl=1)` --new_c `[ cell_perturbation_label_color.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AACVyTQDrmQHtuQhUqyG0ngCa/Olsson_2016/cell_perturbation_label.tsv.gz?dl=1)
</li> </ul>

## Trajectory inference (scATAC-seq data)

<ul> <li style="list-style-type: none;">

### For Mac OS and Linux:

`docker run  -v $PWD:/data -w /data  pinellolab/stream STREAM --atac --atac_counts `[ count_file.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AADLjVwHSII5klgjy_oEGjNsa/Buenrostro_2018/count_file.tsv.gz?dl=1) `--atac_samples`[ sample_file.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AADEVxZGT1-0e5D31o_NIxv-a/Buenrostro_2018/sample_file.tsv.gz?dl=1) `--atac_regions `[ region_file.bed.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AAAnNaOw6L1v7BsKmdy38cqUa/Buenrostro_2018/region_file.bed.gz?dl=1) `-l` [ cell_label.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AACHsOfkrmOSF59RyjprdzD6a/Buenrostro_2018/cell_label.tsv.gz?dl=1) `-c`[ cell_label_color.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AABny8uO3UknufsUtlOKQsyma/Buenrostro_2018/cell_label_color.tsv.gz?dl=1) `--lle_components 4`


### For Windows:

`docker run  -v ${pwd}:/data -w /data  pinellolab/stream STREAM --atac --atac_counts `[ count_file.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AADLjVwHSII5klgjy_oEGjNsa/Buenrostro_2018/count_file.tsv.gz?dl=1) `--atac_samples`[ sample_file.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AADEVxZGT1-0e5D31o_NIxv-a/Buenrostro_2018/sample_file.tsv.gz?dl=1) `--atac_regions `[ region_file.bed.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AAAnNaOw6L1v7BsKmdy38cqUa/Buenrostro_2018/region_file.bed.gz?dl=1) `-l` [ cell_label.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AACHsOfkrmOSF59RyjprdzD6a/Buenrostro_2018/cell_label.tsv.gz?dl=1) `-c`[ cell_label_color.tsv.gz ](https://www.dropbox.com/sh/n8qq4m7w17i6b07/AABny8uO3UknufsUtlOKQsyma/Buenrostro_2018/cell_label_color.tsv.gz?dl=1) `--lle_components 4`

</li> </ul>

# Validate
validation command line pending


# Integrate
View STREAM in its [production portal](http://stream.pinellolab.org/).

<a href="http://stream.pinellolab.org/" target="_blank">
  <img src="../_images/methods/stream_logo.png" width=200/>
</a>

# Contact
Huidong Chen (<a href="mailto://huidong.chen@mgh.harvard.edu">huidong.chen@mgh.harvard.edu</a>), Luca Pinello (<a href="mailto://lpinello@mgh.harvard.edu">lpinello@mgh.harvard.edu</a>)