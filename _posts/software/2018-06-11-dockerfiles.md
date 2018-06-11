---
layout: post
title: Dockerfiles
tags: "software,docker,container,dockerfile"
github: "https://www.github.com/vsoch/dockerfiles"
categories: software
snippet: "Approximately 130K Dockerfiles"
editable: software
---

{% include toc.html %}

## Summary

The [Dockerfiles]({{ page.github }}) dataset is a set of approximately 130,000 Dockerfiles
extracted in early summer 2018 across a sampling of search prefixes.

```bash

$ find data -type f -name Dockerfile | wc -l
129,519

```

The files are hosted as public images on <a href="https://hub.docker.com" target="_blank">Docker Hub</a> 
and thus freely available for download and parsing. 

## Data

The files are currently provided in their raw format,
each named `Dockerfile` under an organization by the Docker Hub username. For example, here is the top level of folders under "data" in the repository:


```bash

data
├── 0
├── 1
├── 2
├── 3
├── 4
├── 5
├── 6
├── 7
├── 8
├── 9
├── a
├── b
├── c
...

├── w
├── x
├── y
└── z

36 directories, 0 files

```

and within each, we have folders that represent Docker Hub usernames:

```bash

data/a
├── a13r
├── a13xx
├── a1exanderjung
...
├── azuresdk
├── azzanatsu
└── azzra

```

And then each Dockerhub username has subfolders with container names, and the subfolders
contain the Dockerfiles (no pun intended).

```bash

data/a/a13r
├── waecm-2018-group-16-bsp-1-backend
│   └── Dockerfile
├── waecm-2018-group-16-bsp-1-frontend
│   └── Dockerfile
└── waecm-2018-group-16-bsp-1-revproxy
    └── Dockerfile

```

### Download

Since this dataset (despite the huge number of files!) fits still in a Github repository, the
files are provided as is under version control, and don't require any special downloading aside
from cloning the repo, or downloading the archive.

```bash

git clone https://www.github.com/vsoch/datasets
wget https://github.com/vsoch/dockerfiles/archive/1.0.0.zip
wget https://github.com/vsoch/dockerfiles/archive/1.0.0.tar.gz

```

### Questions
Many of the <a href="https://vsoch.github.io/datasets/2018/zenodo/" target="_blank">same questions</a> about signatures of software can be tested or generally relevant for this dataset. Additionally, we might
ask the following:

 - How do containers relate (or inherit) from one another? For example, if we use the FROM statements to build a graph, what interesting things do we find?
 - What are signatures (of installation routines?) common across different containers?


### Other questions?

Thanks for reading! If you have other questions, or want help for your project, please don't hesitate to <a href="{{ post.github }}">reach out</a>.
