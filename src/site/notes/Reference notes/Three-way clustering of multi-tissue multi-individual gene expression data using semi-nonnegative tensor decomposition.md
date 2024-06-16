---
{"dg-publish":true,"permalink":"/reference-notes/three-way-clustering-of-multi-tissue-multi-individual-gene-expression-data-using-semi-nonnegative-tensor-decomposition/","title":"Three-way clustering of multi-tissue multi-individual gene expression data using semi-nonnegative tensor decomposition","tags":["collaboration","duke-nus"],"noteIcon":""}
---


**Abstract**: The advent of high-throughput sequencing technologies has led to an increasing availability of large multi-tissue data sets which contain gene expression measurements across different tissues and individuals. In this setting, variation in expression levels arises due to contributions specific to genes, tissues, individuals, and interactions thereof. Classical clustering methods are ill-suited to explore these three-way interactions and struggle to fully extract the insights into transcriptome complexity contained in the data. We propose a new statistical method, called MultiCluster, based on semi-nonnegative tensor decomposition which permits the investigation of transcriptome variation across individuals and tissues simultaneously. We further develop a tensor projection procedure which detects covariate-related genes with high power, demonstrating the advantage of tensor-based methods in incorporating information across similar tissues. Through simulation and application to the GTEx RNA-seq data from 53 human tissues, we show that MultiCluster identifies three-way interactions with high accuracy and robustness.

## Notes [Original paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7771883/)

### The dataset and algorithm details
The authors have data (that is much smaller than ours) of genes, tissues, and individuals as a 3-dimensional tensor. They use the GTEx v6 gene expression data, which consists of RNA-seq samples collected from 544 individuals across 53 human tissues, including 13 brain subregions, adipose, heart, artery, skin, and more: [data](https://www.gtexportal.org/home/datasets). After cleaning and preprocessing the data as detailed in the [Supplement](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7771883/#SD1) ([Wang, Fischer and Song 2018](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7771883/#R39)), gene expression measurements were organized into a gene × individual × tissue multi-way array $𝒴∈ℝ^{𝑛_𝐺×𝑛_𝐼×𝑛_𝑇}$ where $n_G = 18,481$ (genes), $n_I = 544$ (individuals) and $n_T = 53$ (tissues). 

The data we have are slightly different. Firstly, it is much larger than this, and it holds much more details on the cells, their type, and the genetic sequence.  Our data provides more resolution of our cells and their expressed genes. This paper, however, smudges all of them and only collects one averaged gene expression for a tissue. Enrico wishes to retain the additional information that sub-grouping of the cells has to analyze the results and arrive at better conclusions (not our job to analyze the data results). 

![Screenshot 2024-06-16 at 6.38.36 PM.png|A schematic of the algorithm used in this paper](/img/user/Image%20files/Screenshot%202024-06-16%20at%206.38.36%20PM.png)

The details of the algorithm are not so clear. I need to read more about tensor networks and sit with some experts to understand what they apply here. 

### How fast is the algorithm

>[!cite] 
>To compare the computational performance of each algorithm, we simulated a large order-3 tensor of 18,000 genes × 500 individuals × 40 tissues as these dimensions mimic those of the processed GTEx RNA-seq data set. We then recorded the run times for each method when decomposing the tensor into 10 components. We found that _MultiCluster_ is computationally competitive with _HOSVD_ while being more computationally efficient than _SDA_. In particular, it took ≈ 1.6 hours for _HOSVD_, ≈ 1.7 hours for _MultiCluster_, and ≈ 20.1 hours for _SDA_ to complete the task.

SDA stands for Sparse Decomposition Algorithm and HOSVD is Higher-Order SVD. 