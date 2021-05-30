# Comparative analysis of methods for batch correction in proteomics
**Student**: Danko Katerina

**Supervisors**: Lobov Arseniy, Danilov Lavrentii

**Organizations**: Bioinformatics Institute, Saint Petersburg State University, Institute of Cytology of the RAS

**Introduction**:
In this study we have analyzed Data were obtained from cells' proteomic analysis in undifferentiated and in osteogenic differentiation stages isolated from healthy donors and patients with aortic stenosis. This data contained severe technical batch effects caused by two-step biennial experimental design in this work.

**Aim**: to define the best batch-effect correction tool in order to analyse the differences in the molecular mechanisms of osteogenic differentiation 

**Methods**

The project was carried out using R language (version 3.6.3) in the RStudio IDE [](http://www.rstudio.com/). We used 5 packages to eliminate batch effect: sva (Leek et al., 2021), bapred (Hornung et al., 2016), limma (Ritchie et al., 2015), Harman (Oytam et al., 2016).
In order to choose optimal best correction method we used PCA (Principal component analysis), gPCA (guided PCA) and PLS-DA (Partial least squares-discriminant analysis).
Differential expression and GO (gene ontology) analyzes were applied to corrected data to reveal some molecular mechanisms of osteogenic differentiation.

**Results**

We have compared proteins identified by Peaks Xpro and MaxQuant softwares. It was shown that there were much more unique proteins identified by Peaks (Fig. 1).

![Figure 1. Venn Diagram illustrating number of identified proteins.](/Figures/Protein_identification.png)

*Figure 1.* Venn Diagram illustrating number of identified proteins (Figure was obtained with [Data_Preparation.Rmd](https://github.com/kvdanko/Project-spring-2021-BI/blob/main/Data_analysis/Data_Preparation.Rmd)).

Here we have used 5 batch corection methods (Table 1).

*Table 1.* Batch correction methods.
|           Method           |                               Description                               |        R package        |
|:--------------------------:|:-----------------------------------------------------------------------:|:-----------------------:|
| ComBat                     | Empirical Bayes method                                                  | sva (version 3.32.1)    |
| Harman                     | Based on PCA. Reduces batch effect and keeps user-defined class effects | Harman (version 1.12.0) |
| Ratio A                    | Ratio-based method scaling the expression values by the arithmetic mean | bapred (version 1.0)    |
| Ratio G                    | Ratio-based method  scaling the expression values by the geometric mean | bapred (version 1.0)    |
| BMC (batch mean centering) | Centering the variables within batches to have zero mean                | limma (version 3.40.6)  |

Depending on PCA, gPCA and PLS-DA analysis we have concluded that the best batch correction method is ComBat (Fig. 2, 3, Table 2).

![Figure 2. PCA results.](/Figures/PCA.png)

*Figure 2.* PCA results (figure was obtained with [Data_Preparation.Rmd](https://github.com/kvdanko/Project-spring-2021-BI/blob/main/Data_analysis/Data_Preparation.Rmd) and [Batch_correction.Rmd](https://github.com/kvdanko/Project-spring-2021-BI/blob/main/Data_analysis/Batch_correction.Rmd)).

*Table 2.* gPCA results (Table was obtained with [Batch_correction.Rmd](https://github.com/kvdanko/Project-spring-2021-BI/blob/main/Data_analysis/Batch_correction.Rmd)).

| Correction method | gPCA delta | p-value |
|-------------------|------------|---------|
| No correction     | 0.992      | <0.001  |
| ComBat            | 0.074      | 1       |
| BMC               | 0.004      | 1       |
| Ratio A           | 0.009      | 1       |
| Ratio G           | 0.383      | 0.801   |
| Harman            | 0.316      | 0.905   |

![Figure 3. PLS-DA results.](/Figures/PLS-DA_ComBat.png)

*Figure 3.* PLS-DA results (figure was obtained with [Batch_correction.Rmd](https://github.com/kvdanko/Project-spring-2021-BI/blob/main/Data_analysis/Batch_correction.Rmd)).

GO enrichment analysis revealed that proteins involved in connecting with immune responses activation were up-regulated, whereas proteins involved in cell transport processes were down-regulated (Fig. 4). 

![Figure 4. GO enrichment analysis results.](/Figures/GO_enrichment_analysis.png)

*Figure 4.* GO enrichment analysis results (figure was obtained with [GO_enrichment.Rmd](https://github.com/kvdanko/Project-spring-2021-BI/blob/main/Data_analysis/GO_enrichment.Rmd)).

**Conclusions**

* There were considerably more proteins identified by Peaks Xpro than by MaxQuant
* Wrong experimental design that included two-step data analysis in two years led in severe technical batch effect 
* 5 methods of batch correction were applied: ComBat, BMC, Ratio A, Ratio G, Harman
* Comparison of batch correction methods established that the optimal method is ComBat
* GO enrichment analysis conducted on corrected data revealed that proteins connected with immune response activation were up-regulated in differentiated cells, while proteins participating in cell transporting processes were down-regulated 

**References**

1. RStudio Team (2020). RStudio: Integrated Development for R. RStudio, PBC, Boston, MA URL http://www.rstudio.com/.
2. Leek JT, Johnson WE, Parker HS, Fertig EJ, Jaffe AE, Zhang Y, Storey JD, Torres LC (2021). sva: Surrogate Variable Analysis.
3. Hornung R, Boulesteix AL, Causeur D. Combining location-and-scale batch effect adjustment with data cleaning by latent factor adjustment. BMC Bioinformatics 17, 27 (2016). doi: 10.1186/s12859-015-0870-z.
4. Ritchie ME, Phipson B, Wu D, Hu Y, Law CW, Shi W, Smyth GK (2015). “limma powers differential expression analyses for RNA-sequencing and microarray studies.” Nucleic Acids Research, 43(7), e47. doi: 10.1093/nar/gkv007. 
5. Oytam Y, Sobhanmanesh F, Duesing K, Bowden JC, Osmond-McLeod M, Ross J (2016). “Risk-conscious correction of batch effects: maximising information extraction from high-throughput genomic datasets.” BMC Bioinformatics, 17(1), 1–17. doi: 10.1186/s12859-016-1212-5. 


