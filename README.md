# MIA-HeatMap
Minimum Information About - HeatMap

Is a shiny app that lets you create HeatMap with only the minimum knowledge of heatmaps. The user doesn't need to have any coding experience. This tool is written in R and can be run using the next few lines of code in the R console:

Firstly, you should have the most recent version of R or RStudio.
Next install required packages. Cut and paste what's below in an R session.

install.packages(c("shiny", "shinyFiles", "openxlsx", "openxlsx", "gplots", "reshape", "scales", "RColorBrewer", "stats", "graphics", "ggplot2", "gdata", "plyr"))
source("http://bioconductor.org/biocLite.R")
biocLite("impute")

You only need to do this once.

Then, you may run MIA-HeatMap any time in an R session as follows.

library(shiny)
library(shinyFiles)
runGitHub("MIA-HeatMap", "manalirupji")

DATA REQUIREMENTS

Data should be input as a .txt or .xlsx or .csv file. The first two rows of the data file have information about the patients/specimens and their response/subtype; all remaining rows have gene expression data, one row per gene. In the case of Microarray gene expression data in which there are several probes corresponding to a single gene, a unique identifier would need to be created to separately identify each probe such as, 'Gene 1_p1', 'Gene1_p2' indicating Gene 1 has two probes. The columns represent the different experimental samples. A maximum of up to 10 different sample groups and 6 different gene groups may be used with this tool.
