# Clustering Analysis with Shiny HeatMap (CASH)

Is a shiny tool that lets you create a HeatMap with only the minimum knowledge of heatmaps and minimal coding experience. The user may upload their own data or use the provided BRCA example data to generate the HeatMap using any distance or clustering method of their choice. Along with the HeatMap, the column and row dendrograms are displayed individually in separate tabs. If you wish to know the samples within each cluster, this information can be downloaded using the cutree download button inside the row/column dendrogram tab. The novelty about this app is that it is highly reproducible and also provides a p-value to test significance between the clusters.

#### INSTALLATION
Firstly, you should have the most recent version of R or RStudio.
Next install required packages. Cut and paste what's below in an R session.

``` R
install.packages(c("shiny", "shinyFiles", "shinyjs", "openxlsx", "openxlsx", "gplots", "reshape", "scales", "RColorBrewer", "stats", "graphics", "ggplot2", "gdata", "plyr", "dendextend", "DT", "gridExtra", "htmlwidgets", "matrixStats"))
source("http://bioconductor.org/biocLite.R")
biocLite("impute")
```
You only need to do this once.

Then, you may run CASH any time in an R session as follows.

``` R
library(shiny)
library(shinyFiles)
runGitHub("CASH", "manalirupji")
```

It may take upto several minutes for the webpage to show in your browser depending on your computer.

#### INPUT DATA REQUIREMENTS

Data should be input as a .txt or .xlsx or .csv file. The first two rows of the data file have information about the patients/specimens and their response/subtype; all remaining rows have gene expression data, one row per gene. In the case of Microarray gene expression data in which there are several probes corresponding to a single gene, a unique identifier would need to be created to separately identify each probe such as, 'Gene 1_p1', 'Gene1_p2' indicating Gene 1 has two probes. The columns represent the different experimental samples. A maximum of up to 10 different sample groups and 6 different gene groups may be used with this tool.

##### DATA FORMAT

1.	The first line of the file contains the gene identifier 'gene_id' (column 1), gene group classification 'Groups' (column 2) followed by the patient IDs e.g. TCGA.01.1A2B, one per column, starting at column 3. Column 1 gene identifier has to be labelled 'gene_id' and column 2 header should be labelled 'Groups' for using this tool. Other titles may cause the program to display errors. 
2.	The second line of the file contains the patient response classification e.g. Fav/Unf for favorable outcome group vs the unfavorable outcome group or Normal/Tumor, etc., in alphabetical order, starting at column 3. The first two columns for this row should be blank.
3.	The remaining lines contain gene expression measurements one line per gene, described in the format below.
a) Column_1. This should contain the gene name, for the user's reference.
b) Column_ 2. This should contain the gene group classification e.g. O/U for Over-expressed/Under-expressed or Hyper/Hypo for hypermethylated/hypomethylated in alphabetical order. If only one gene group, use any alphabet e.g. A for each row instead.
c) Remaining Columns. These should contain the expression measurements as numbers. Data inputted should be non-negative. Columns and rows with zero variance should be removed from the data. Rows containing missing expression measurements, should be also be removed from the input data or it will cause the tool to run into errors.

| gene_id           | Groups | GSM9981 | GSM1870  | GSM4618 | GSM7689  | GSM8772 | GSM1121  | GSM1250 | GSM3112  | GSM4987 | GSM1277 |
| -------------     |:------:| -------:|---------:|--------:|---------:|--------:|---------:|--------:|---------:|--------:|--------:|
|                   |        | MM      | MM       | MM      | MM       | MM      | MUGS     | MUGS    | NPC      | SM      | SM      |
| YWHAE>210996_s_at | A      | 1.47    |  2.18    | 5.87    |	9.12     |	7.34   | 1.56     |	3       |	7.77     |	3.4    |	1.56   |
| YWHAE>201020_at   | A      | 1.98    |  7.93    | 2.76	  | 9.11     |	8.46   | 0.98     |	5.98    |	8.19     |	8.91   |	5.98   |
| YWHAH>33323_r_at  | A      | 8.02    |  8       | 3.19	  | 11.86    |	6.54   | 8.17     |	2       |	0.99     |	2      |	1.17   |



##### Terms of Use

This tool was prepared by members of the Winship Biostatistics and Bioinformatics Shared Resource (BBISR) of Emory University. 
Use of either should properly acknowledge the Winship BBISR in publications, abstracts, presentations, posters, grant proposals, etc. by using the following text	

'Research reported in this publication was supported in part by the Biostatistics and Bioinformatics Shared resource of Winship Cancer Institute of Emory University and NIH/NCI under award number P30CA138292. The content is solely the responsibility of the authors and does not necessarily represent the official views of the National Institutes of Health. 

Authors- Manali Rupji, dual M.S., Bhakti Dwivedi Ph.D. & Jeanne Kowalski Ph.D.

Maintainer- Manali Rupji 'manali(dot)rupji(at)emory(dot)edu'
