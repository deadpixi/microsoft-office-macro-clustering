# Microsoft Office Macro Clustering
This repository contains the data files and algorithms for clustering Microsoft Office documents by their macro content.

## Table of Contents
* `av_labels/`: Directory of JSON files, one per sample, containing AntiVirus labels (if any).
* `macros/`: Directory of raw VBA macro files, extracted from the document samples. Original documents can be found on [InQuest Labs](https://labs.inquest.net).
* `vba_features.csv`: CSV representation of VBA feature vectors extracted from the raw macros above.
