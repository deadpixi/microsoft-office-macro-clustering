# Microsoft Office Macro Clustering
This repository contains the data files and algorithms for clustering Microsoft Office documents by their macro content. For access to the original documents, please see [InQuest Labs](https://labs.inquest.net/).

## Table of Contents
* `av_labels/`: Directory of JSON files, one per sample, containing AntiVirus labels (if any).
* `macros/`: Directory of raw VBA macro files, extracted from the document samples. Original documents can be found on [InQuest Labs](https://labs.inquest.net).
* `classification.csv`: CSV representation of hash, AV positive count and label (one of UNKNOWN, MALICIOUS, BENIGN).
* `vba_features.csv`: CSV representation of VBA feature vectors extracted from the raw macros above.
