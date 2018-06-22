---
layout: post
title: Singularity Hub Container Guts
tags: "software,singularity,container,files"
github: "https://www.github.com/singularityhub/api"
categories: software
snippet: "Extraction of ~265 Singularity Container Guts"
editable: software
---

{% include toc.html %}


## Summary
[![DOI](https://zenodo.org/badge/131761241.svg)](https://zenodo.org/badge/latestdoi/131761241)

The [Singularity Hub Container]({{ page.github }}) dataset is a set of complete
extractions of files, packages, and inspection metadata for approximately ~263
containers from [Singularity Hub](https://www.singularity-hub.org).

## Data

The data is organized in a top folder, data, with subfolders corresponding to
collection names, container names, then GIthub commit and container hash. 
Within each folder we can find files named accordingly to the file type, e.g.,:


```bash

$ cd data/singularityhub/
 
       [owner]          [collection]       [commit]     [version]
$ tree DeepLearnPhysics/larcv2-singularity/d011b820d.../3e58481fa958cf6c09f097963fd9aee8/
├── files.json
├── inspect.json
└── packages.json

0 directories, 3 files

```

Each of the json files has extracted metadata about the particular container, including files:

```bash

[
  {
    "Image": "/tmp/tmp.KlGR2uUO7i/8f7be9fee0334de6cf8de6cad6757bdbd58436c....tar",
    "AnalyzeType": "File",
    "Analysis": [
      {
        "Name": "/bin",
        "Size": 7825046
      },
      {
        "Name": "/bin/bash",
        "Size": 1037528
      },
      {
        "Name": "/bin/bunzip2",
        "Size": 31288
      },

...
```

and packages:

```bash

[
  {
    "Image": "/tmp/tmp.KlGR2uUO7i/8f7be9fee0334de6cf8de6cad6757bdbd58436c....tar",
    "AnalyzeType": "Apt",
    "Analysis": [
      {
        "Name": "acl",
        "Version": "2.2.52-3",
        "Size": 204800
      },
      {
        "Name": "adduser",
        "Version": "3.113 nmu3ubuntu4",
        "Size": 663552
      },
      {
        "Name": "adwaita-icon-theme",
        "Version": "3.18.0-2ubuntu3.1",
        "Size": 6492160
      },


```

and finally, an inspection of the container to derive complete metadata. In this
example, the top of the inspection that we see has the complete "deffile" which
is the Singularity Recipe used to build the container.

```bash

# produced with singularity inspect [container]

{
    "data": {
        "attributes": {
            "deffile": "Bootstrap: docker\nFrom: nvidia/cuda:9.0-cudnn7-devel-ubuntu...
...

            "labels": {
                "org.label-schema.usage.singularity.deffile.bootstrap": "docker",
                "maintainer": "NVIDIA CORPORATION <cudatools@nvidia.com>",
                "org.label-schema.usage.singularity.deffile": "Singularity.ubuntu16.04-gpu",
                "org.label-schema.usage": "/.singularity.d/runscript.help",
                "org.label-schema.schema-version": "1.0",
                "com.nvidia.cudnn.version": "7.1.1.5",
                "com.nvidia.cuda.version": "9.0.176",
                "VERSION": "ubuntu16.04-root06.08.06-gpu",

...
                "MAINTAINER": "drinkingkazu",
                "com.nvidia.volumes.needed": "nvidia_driver",
                "org.label-schema.build-size": "6647MB"
            },
            "environment": "# Custom environment shell code should follow\n\n
            "runscript": "#!/bin/sh\n\nexec \"/bin/bash\" \"$@\"\n",
            "test": null
        },
        "type": "container"
    }
}


```


### Download

Since this dataset (despite the huge number of files!) fits still in a Github repository, the
files are provided as is under version control, and don't require any special downloading aside
from cloning the repo, or downloading the archive.

```bash

git clone https://www.github.com/singularityhub/api
wget https://github.com/singularityhub/api/archive/v1.0.0.zip
wget https://github.com/singularityhub/api/archive/v1.0.0.tar.gz

```

Additionally, this dataset will be made [available on kaggle](https://www.kaggle.com/stanfordcompute/singularity-guts)


### Generation
For complete details on the container API, see [this post](https://vsoch.github.io///2018/container-diff/#the-container-differences-api).
Essentially, this is the output of the [container-diff](https://vsoch.github.io///2018/container-diff/#container-diff-no-its-not-c-diff) tool that is run across images from Singularity Hub, and served statically
from a Github repository for your use. The generation is done locally, and pushed to Github. The steps are the following:

 - Connect to the Google Storage for Singularity Hub
 - Compare the Containers in Storage to the Local Record
 - For new containers, pull and update the metadata, extract the files mentioned above

We then push to Github. You can take a look at the [generation script here](https://github.com/singularityhub/api/blob/master/generate.py) if you are interested.


### Questions
Many of the <a href="https://vsoch.github.io/datasets/2018/zenodo/" target="_blank">same questions</a> about signatures of software can be tested or generally relevant for this dataset. This is a unique dataset in that we have the complete "guts" of a container (packages and files) along with versions, and metadata about how the container was produced. This means that we could additionally ask the following:

 - How does a build recipe result in a container filesystem? Can we predict a filesystem from the build recipe?
 - What are the filesystem and package signatures that correspond with different commands in the recipe?


### Other questions?

Thanks for reading! If you have other questions, or want help for your project, please don't hesitate to <a href="{{ post.github }}">reach out</a>.
