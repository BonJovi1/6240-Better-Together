# Better Together: Combining Textual and Graph Embeddings for Directed Edge Prediction in Citation Networks
A final project for Georgia Tech's CSE 6240 - Web Search & Text Mining

Group 19 - Christian Clark, Abhinav Gupta, Shashank Srikanth, Suryatej Reddy Vyalla

## Introduction

## Replication Instructions
### Dataset
This project uses the [High-Energy Physics Theory Citation Network dataset](https://snap.stanford.edu/data/cit-HepTh.html), collected and hosted by SNAP (the Stanford Network Analysis Project). In order to run the code in this repository, you will need to download the following files and unzip them in the directory of your choice.

- [cit-HepTh.txt.gz](https://snap.stanford.edu/data/cit-HepTh.txt.gz)
- [cit-HepTh-abstracts.tar.gz](https://snap.stanford.edu/data/cit-HepTh-abstracts.tar.gz)

You should then open the Jupyter notebook entitled **CleanDataset.ipynb** and follow the contained instructions in order to clean the dataset for use in our embedding generation models.

Before running any of our baseline models, you will need to first create text embeddings for the paper abstracts in this dataset. To do so, simply follow the instructions in the **GenerateTextEmbeddings.ipynb** notebook.

### Baseline Models - GraphSAGE
The code for generating GraphSAGE embeddings and training the multi-layer perceptron over the data is provided in the notebook `GraphSAGE.ipynb`. Simply run all the cells one after the other and you should be able to run the code. The results are summarized as below: 

| Model | Accuracy | ROC-AUC | Precision | Recall | F1 |
|------|------|------|------|------|-----|
| GraphSAGE - Node | 0.664 | 0.752 | 0.621 | 0.842 | 0.714
| GraphSage - Text | 0.797 | 0.875 | 0.776 | 0.836 | 0.805 

### Baseline Models - DeepWalk, Sentence-Transformers
The code for generating DeepWalk node embeddings and training a multi-layer perceptron over these embeddings as well as the textual embeddings from the BERT transformer model are provided in `DeepWalkText.ipynb`. Again, simply run all the cells in the notebook one after the other to replicate the results. The results obtained are summarized below: 

| Model | Accuracy | ROC-AUC | Precision | Recall | F1 |
|------|------|------|------|------|-----|
| DeepWalk | 0.807 | 0.877 | 0.802 | 0.814 | 0.866    
| Sentence Transformer | 0.846 | 0.921 | 0.811 | 0.901 | 0.853  

### Proposed Model - Graph and Text ConCATenated Embeddings (GAT-CAT)
For this model, we combine the embeddings obtained from DeepWalk (node embeddings) and from the sentence transformer model (text embeddings) to obtain a richer representation of the information that incorporates both, the graph information as well as the textual information from the abstracts of the paper. The code for concatenating these embeddings and training our model is provided in `DeepWalkText.ipynb`. Again, simply run all the cells in the notebook one after the other to replicate the results. The results obtained are summarized below: 


| Model | Accuracy | ROC-AUC | Precision | Recall | F1 |
|------|------|------|------|------|-----|
| GraphSAGE - Node | 0.664 | 0.752 | 0.621 | 0.842 | 0.714
| GraphSage - Text | 0.797 | 0.875 | 0.776 | 0.836 | 0.805 
| DeepWalk | 0.807 | 0.877 | 0.802 | 0.814 | 0.866    
| Sentence Transformer | 0.846 | 0.921 | 0.811 | 0.901 | 0.853
| GAT-CAT | 0.877 | 0.932 | 0.852 | 0.912 | 0.881

### Model Hyperparameters

In order to replicate the results stated in our report, you should use the hyperparameters listed below:

| Model | Training Epochs | Learning Rate | Optimizer | Loss Function |
|------|------|------|------|------|
| GraphSAGE | 100 | 0.01 | ADAM | Binary Cross-Entropy |
| DeepWalk | 30 | 0.0001 | ADAM | Binary Cross-Entropy |
| Sentence-Transformers (all-MiniLM-L6-v2) | 30 | 0.0001 | ADAM | Binary Cross-Entropy |
| GAT-CAT | 30 | 0.0001 | ADAM | Binary Cross-Entropy | 

## Report
For more background and details about the results of this project, please see our report or presentation (stored in this repo as **Report19_S22.pdf** and **Presentation19_S22.pdf** respectively).

