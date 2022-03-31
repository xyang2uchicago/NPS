# BioTIP: an R-package for Characterization of Biological Tipping Points
### What is BioTIP?
Abrupt and often irreversible changes (or tipping points) are decisive in the progression of biological processes. We, therefore, developed this R-package for the characterization of biological tipping points using gene expression profiles. BioTIP is the first toolset that amalgamates two computational impediments in multivariate expression-data analysis: (1) detection of tipping points accurately, and (2) identification of significant critical transition signals (CTSs). 

The following figure outlines BioTIP pipeline: 

a, Analytic pipeline of single-cell RNA-seq analysis, with BioTIP as an alternative to mainstream analyses by focusing on transition states. The arrows in orange show that BioTIP is applied to cell state ensembles (clusters) without inputting the pseudo-order information. The dashed orange arrow shows that BioTIP may use pseudo-order information to visualize and interpret the results.  

b, Overview of BioTIP’s three analytical steps. The scRNA-seq profiles with cell cluster IDs are the inputs, which can be generated by independent pipelines. The outputs are significant CT states and their characteristic CTSs which can infer CT-driven transcription factors. Three analytic steps HVG: highly variable genes. DNB: dynamic biomarker network; Ic: index of criticality. 

<img src="https://github.com/xyang2uchicago/BioTIP/blob/master/results/Fig1_BioTIP_github.jpg"> 

### Why BioTIP?
BioTIP addresses and shows robust performances by addressing three analytical challenges of the existing tipping-point methods:

1. The sizes of the statistical ensembles (e.g., cellular populations) vary considerably. BioTIP provides Ic.shrink score (an improved version on Ic score) to address the bias towards differently sized populations.
2. Multiple tipping points may coexist during an observed progression and multiple CTSs may coexist in the same critical transition state. BioTIP can detect multiple tipping points and CTSs. 
3. Under exposure to a stimulus, the same population of cells faces multiple trajectories. BioTIP has robust performance for different trajectory inference methods. 

#### 6 Case Studies

We applied BioTIP to six datasets and compared BioTIP's performance with other existing tools (see [examples](https://github.com/xyang2uchicago/BioTIP/blob/master/examples)). The six datasets are as following:

1. Dataset 1 consists of 96 selected genes in 929 human embryonic stem cells (hESCs) of predefined 9 clusters ([Bargaje et al., 2017](https://pubmed.ncbi.nlm.nih.gov/28167799/)). 
2. Dataset 2 consists of 10.3k genes in 131 mouse lung alveolar type (AT2) development, collected at four time points ([Treutlein et al., 2014](https://pubmed.ncbi.nlm.nih.gov/24739965/)). 
3. Dataset 3 consists of 10.9k genes of 7,240 developing mesoderm cells collected at embryonic day (E) 8.25 when precursor cells of major organs have been formed ([Pijuan-Sala et al., 2019](https://pubmed.ncbi.nlm.nih.gov/30787436/)). 
4. Dataset 4 contained 12.7k genes in 11k E8.25 cells, with 16 predefined developing mesoderm subtypes ([Ibarra-Soria et al., 2018](https://www.nature.com/articles/s41556-017-0013-z)). 
5. Dataset 5 contained 15.2k genes of 1,531 mesoderm cells of embryoid bodies (EB), describing how hemangiogenic (HA) and smooth muscle lineages are specified from FLK1-expressing (FLK1+) mesoderm ([Zhao and Choi, 2019](https://pubmed.ncbi.nlm.nih.gov/31740535/)). 
6. Dataset 6 is an epithelial-to-mesenchymal transition (EMT) data simulated from an established 18-gene regulatory network of 5,363 cells consisting of four stable states and between-state transition cells ([Sha et al., 2020](https://academic.oup.com/nar/article/48/17/9505/5900115)). 

For each dataset, cell-type biomarkers or cluster identities are given by the original publications. The scRNA-seq data quality control (e.g., removing triplicate cell and mitochondria gene), normalize distinct sequencing depths, general feature selections, and cell cluster are performed following the corresponding manuscripts.

#### Method Comparison

<img src="https://github.com/xyang2uchicago/BioTIP/blob/master/results/6db_for_git.jpg"> 

#### Robustness

Cell clustering is a prerequisite for CTS identification with BioTIP. While different cell cluster numbers may affect BioTIP's prediction, a reasonable clustering method (with reasonably chosen parameters) will not have a major impact on the CTSs identified. BioTIP is designed for the case where the transition state can be identified as a cell cluster, and therefore soft clustering is not always applicable. 

BioTIP also demonstrated robustness with respect to different clustering methods. Details can be found [here](https://github.com/xyang2uchicago/BioTIP/blob/master/results/robustness.md). 


### Where to apply BioTIP?
To adopt tipping-point theory to transcriptomic analysis, there are two commonly accepted premises:  

1. The system of the individual cell has a dissipative structure (e.g., having discrete states, including the one showing semi-stability).
2. Each state has a characteristic gene expression profile and thus presents a distinct molecular phenotype.  

BioTIP applies to data meeting these premises, including both single-cell and bulk-cell transcriptomes. The impending transition states are called ‘critical transition states’ or ‘tipping points.’

We have successfully applied BioTIP to identify temporal features of molecular-network dynamics from gene expression profiles. Importantly, the CTS identifications helped infer the underlying gene-regulatory network and the involving key transcription factors.

### How does BioTIP work? 

1. [BioTIP tutorial](https://htmlpreview.github.io/?https://github.com/xyang2uchicago/BioTIP/blob/master/tutorial/Gastrulation.html): This is a detailed walkthrough of BioTIP on one of our key results (Mouse Gastrulation, GSE87038, [E8.25 2019](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE87038)). 

2. [Vignette](https://bioconductor.org/packages/release/bioc/vignettes/BioTIP/inst/doc/BioTIP.html): This documented exampled case studies on bulk (GSE6136) and single-cell ([Nestorowa 2016](https://pubmed.ncbi.nlm.nih.gov/27365425/)) datasets.

### How to install?
To use the newest BioTIP package, either clone/download this repository, or you can install BioTIP with:

```r
library("devtools")
devtools::install_github("xyang2uchicago/BioTIP")
```

You can install the released version of BioTIP from [CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("BioTIP")
```
or even better:
``` r
source('http://bioconductor.org/biocLite.R')
biocLite("BioTIP")
```

### Acknowledgements
BioTIP is made possible by contributions from the following authors: Xinan H Yang, Zhezhen Wang, Yuxi Sun, Andrew Goldstein, Dannie Griggs, Antonio Feliciano, Yanqiu Wang, Biniam Feleke, Qier An, Ieva Tolkaciovaite, and John M Cunningham. 
