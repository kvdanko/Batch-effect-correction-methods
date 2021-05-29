# Comparative analysis of methods for batch correction in proteomics
**Student**: Danko Katerina

**Supervisors**: Lobov Arseniy, Danilov Lavrentii

**Organizations**: Bioinformatics Institute, Saint Petersburg State University, Institute of Cytology of the RAS

**Introduction**:
In this study we have analyzed Data were obtained from cells' proteomic analysis in undifferentiated and in osteogenic differentiation stages isolated from healthy donors and patients with aortic stenosis. This data contained severe technical batch effects caused by two-step biennial experimental design in this work.

**Aim**: to define the best batch-effect correction tool in order to analyse the differences in the molecular mechanisms of osteogenic differentiation 

**Methods**
In order to choose optimal best correction method we used PCA (Principal component analysis), gPCA (guided PCA) and PLS-DA (Partial least squares-discriminant analysis).
Differential expression and GO (gene ontology) analyzes were applied to corrected data to reveal some molecular mechanisms of osteogenic differentiation.

**Results**
We have compared proteins identified by Peaks Xpro and MaxQuant softwares. It was shown that there were much more unique proteins identified by Peaks (Fig. 1).

![Figure 1. Venn Diagram illustrating number of identified proteins.](/Figures/Protein_identification.png)


Here we have used 5 batch corection methods (Table 1)

Table 1.

![](/Figures/Batch_correction_methods.png)

Depending on PCA, gPCA and PLS-DA analysis we have concluded that the best batch correction method is ComBat (Fig. 2, 3, Table 2).

![Figure 2. PCA results.](/Figures/PCA.png)

Table 2. gPCA results.

![](/Figures/gPCA.png)

![Figure 3. PLS-DA results.](/Figures/PLS-DA_ComBat.png)





