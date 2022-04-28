# Better Together: Combining Textual and Graph Embeddings for Directed Edge Prediction in Citation Networks
A final project for Georgia Tech's CSE 6240 - Web Search & Text Mining

Group 19 - Christian Clark, Abhinav Gupta, Shashank Srikanth, Suryatej Reddy Vyalla

## Introduction

## Replication Instructions
### Dataset
This project uses the [High-Energy Physics Theory Citation Network dataset](https://snap.stanford.edu/data/cit-HepTh.html), collected and hosted by SNAP (the Stanford Network Analysis Project). In order to run the code in this repository, you will need to download the following files and unzip them in the directory of your choice.

- [cit-HepTh.txt.gz](https://snap.stanford.edu/data/cit-HepTh.txt.gz)
- [cit-HepTh-abstracts.tar.gz](https://snap.stanford.edu/data/cit-HepTh-abstracts.tar.gz)

You should then open the Jupyter notebook entitled **"CleanDataset.ipynb"** and follow the contained instructions in order to clean the dataset for use in our embedding generation models.

Before running any of our baseline models, you will need to first create text embeddings for the paper abstracts in this dataset. To do so, simply follow the instructions in the **GenerateTextEmbeddings.ipynb** notebook.

### Baseline Models - GraphSAGE

### Baseline Models - DeepWalk, Sentence-Transformers

### Proposed Model - Graph and Text ConCATenated Embeddings (GAT-CAT)

| Model | Training Epochs | Learning Rate | Optimizer | Loss Function |
|------|------|------|------|------|
| GraphSAGE | 100 | 0.01 | ADAM | Binary Cross-Entropy |
| DeepWalk | 30 | 0.0001 | ADAM | Binary Cross-Entropy |
| Sentence-Transformers (all-MiniLM-L6-v2) | 30 | 0.0001 | ADAM | Binary Cross-Entropy |
| GAT-CAT | 30 | 0.0001 | ADAM | Binary Cross-Entropy | 

## Report
For more background and details about the results of this project, please see our report or presentation (stored in this repo as **"Report19_S22.pdf"** and **Presentation19_S22.pdf** respectively).

