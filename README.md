# Microsoft Office Macro Clustering
This repository contains the data files and algorithms for clustering Microsoft Office documents by their macro content. For access to the original documents, please see [InQuest Labs](https://labs.inquest.net/).

## Table of Contents
* `av_labels/`: Directory of JSON files, one per sample, containing AntiVirus labels (if any).
* `macros/`: Directory of raw VBA macro files, extracted from the document samples. Original documents can be found on [InQuest Labs](https://labs.inquest.net).
* `cluster.ipynb`: Jupyter notebook demonstrating K-means clustering over the corpus.
* `classification.csv`: CSV representation of hash, AV positive count and label (one of UNKNOWN, MALICIOUS, BENIGN).
* `vba_features.csv`: CSV representation of VBA feature vectors extracted from the raw macros above.

### classification.csv
This file consists of three columns `SHA256, AV Positives, classification`. AV positives is the number of engines within [VirusTotal](https://www.virustotal.com) that detected the file as malicious. The total number of engines is variable, for a number of reasons. It would be reasonable to consider the total number as 60. The number of requisite AV positives required to consider a sample as "malicious" is subjective. The third column, classification, is one of "UNKNOWN", "BENIGN", or "MALICIOUS". A number of factors went into application of these labels, the distribution of which is shown here:

```
$ cut -d',' -f3 classification.csv | distribution
      Key|Ct   (Pct)    Histogram
  UNKNOWN|8055 (80.55%) --------------------------------------------------------
MALICIOUS|1790 (17.90%) -------------
   BENIGN| 155  (1.55%) --
```

Generally, when you're looking to train a supervised model, you'll want 80% of your data to carry labels. Our ratio here is opposite but that's ok for an unsupervised model. In fact, the entire goal of this effort is to automatically expand on our labels within some threshold of confidence. The labels within `classification.csv` were applied through a variety of checks and balances to ensure fidelity. Within `av_labels` you can find a JSON dictionary containing the AV scan results for each of the documents. This data can of course be sourced to generate labels with varying threshold of confidence. For example, rewriting `classification.csv` to label any sample with 4 or more AV positives as malicious, 0 positives as benign, and everything inbetween us unknown, will result in about 85% labeling of the corpus.
