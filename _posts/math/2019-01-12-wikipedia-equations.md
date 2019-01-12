---
layout: post
title: Wikipedia Equation Embeddings
tags: "wikipedia,equations,embeddings,math,statistics"
github: "https://www.github.com/vsoch/wikipedia-equations"
categories: math
snippet: "~63K Equation Embeddings for Wikipedia Statitics and Math Articles"
editable: math
---

{% include toc.html %}


## Summary

[![DOI](https://zenodo.org/badge/165427328.svg)](https://zenodo.org/badge/latestdoi/165427328)

The [Wikipedia Equation Embeddings]({{ page.github }}) dataset includes two datasets
that each container word2vec embeddings generated from latex equations extracted
from Wikipedia statistics and math articles. You can see the README.md in
each of the [math](https://github.com/vsoch/wikipedia-equations/tree/master/math) 
and [statistics](https://github.com/vsoch/wikipedia-equations/tree/master/statistics) 
subfolders for information on generation and using the data.


### Download

The datasets are both provided via the Github repository:

```bash

git clone https://www.github.com/vsoch/wikipedia-equations
wget https://github.com/vsoch/wikipedia-equations/archive/0.0.1.zip
wget https://github.com/vsoch/wikipedia-equations/archive/0.0.1.tar.gz

```

### Questions

Here are some interesting questions these datasets might help answer:

 - Can you predict terms from equations? Meaning, you can take a new equation, and generate terms that describe how it's been used or described?
 - Can you predict equations from terms? Meaning, you could create a search engine where a user searches for a term, and gets back equations that are associated?
 - What domains of math are more strongly associated with different domains (of science? something else?)

### Other questions?

If you have other questions, or want help for your project, please don't hesitate to <a href="{{ post.github }}">open an issue</a>. If you use any of the datasets in your work,
please remember to include the doi.
