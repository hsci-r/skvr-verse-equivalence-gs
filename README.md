# SKVR verse equivalence gold standard

This repository contains the dataset used for the evaluation in the article:

Janicki M., Kallio K., Sarv M. *Exploring Finnic written oral folk poetry through string similarity.* Digital Scholarship in the Humanities, 2022 (in press).

The texts considered here come from the collection
[Suomen Kansan Vanhat Runot](https://skvr.fi). The verse pairs were sampled 
using a stratified sampling approach, so that different ranges of cosine 
similarity are equally represented (see the above article for details). The 
criteria for the annotation can be found in the article as well.

The data was annotated by four annotators:
* Jukka Saarinen (Finnish Literature Society)
* Kati Kallio (Finnish Literature Society)
* Mari Sarv (Estonian Literary Museum)
* Venla Sykäri (Finnish Literature Society)

Each annotator received a different sample of 3000 verse pairs. A concatenation 
of those gives a dataset of 12000 verse pairs usable for evaluation. 
Additionally, a distinct "common" sample was annotated by each annotator for 
the purpose of evaluating inter-annotator agreement. The common sample is not 
included in the evaluation dataset.

## `data/`

The subfolder `data/` contains the following files:
* `sample-common.csv` - the common sample used for evaluating inter-annotator agreement,
* `sample-{annotator}.csv` - the sample handed to each annotator individually,
* `results-common-{annotator}.csv` - the annotations of the common sample by each annotator,
* `results-{annotator}.csv` - the annotations of the annotator's individual sample.

The `sample-*` files contain the following columns:
* `id1`, `id2` - database-internal verse IDs,
* `sim` - the cosine similarity of the verses,
* `text1`, `text2` - verse texts.

The corresponding `results-*` files contain the following columns:
* `id1`, `id2` - the database-internal verse IDs,
* `class` - either `s` (similar = equivalent) or `d` (distinct = non-equivalent)

The verse pairs are given in the same order in both `sample-*` and `results-*` 
files. The database from which the IDs originally come from is no longer 
available in the same form, so the IDs have no other meaning than matching the 
pairs in both kinds of files.

## `analyses/`

The subfolder `analyses/` contains the following Excel spreadsheet:
* `common-sample-comparison.xlsx`: comparison of all four annotator's 
annotations on the common sample and Inter-Annotator Agreement computation.

**Note:** In addition to real disagreements, occasional errors (e.g. because of 
hitting a wrong button) are a normal feature of such annotation process, where 
quick decisions need to be made on a large mass of verse pairs taken out of 
context. The errors in the common sample were not corrected on purpose, because 
they provide insight into the rate of similar errors in the individual samples. 
Regardless of that, the inter-annotator agreement (Fleiss' kappa) is high, 
which speaks of the general reliability of the annotation.

## See also

* The [shortsim](https://github.com/hsci-r/shortsim) package contains methods 
used for the automatic discovery of equivalent verses.
