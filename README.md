# Differential_Expression_PCA.R

Differential_Expression_PCA is a script written by Alexzandra Morris and Nick Bayley from the UCLA Graeber Lab. This script has specific functionality for differential expression results as it includes signed p value functions, and outputs volcano plots along with PCA plots. 

## Installation

[//]: # "Use the package manager [pip](https://pip.pypa.io/en/stable/) to install foobar."

```bash
install.packages("EnhancedVolcano")
install.packages("dplyr")
install.packages("ggplot2")
install.packages("base")
```
## Set-up Directories/ Get datasets
```r
working_dir<-"/Users/....."
setwd(working_dir)
filename_prefix = "Proj"
orig <- read.table("orig_dataset.txt", sep = "\t", row.names = 1, header = T)
projected <- read.table("projected_dataset.txt", sep = "\t", row.names = 1, header = T)
```

## Set-up Variables

This script can run pca on just the original dataset or it can run the original set and the projected set. Make sure to change projected_dataset to False if it doesn't exist. This script uses signed p value. 

```r
projected_dataset <- T

#Ensure both datasets are the same dimensions
run_match.rows <- T 
run_match.cols <- T 

colNames = c("log2FoldChange", "signed.log.p") #used for run_pca()
```

## Input Data .txt file formats
![Original Data Input Format](https://github.com/1014violin/PCA/blob/main/orig_data_3.png)
![Projected Data Input Format](https://github.com/1014violin/PCA/blob/main/projected_data2.png)

## Functions
```r
#checks to see if columns are the same 
match.columns(origg, projectedd)

#if both datasets have different number of rows, match them
match.rows(data_list) 

add.signed.log.p(de_table, col_name = "padj", sign_name = "log2FoldChange")

#only for original data
run.pca(data, scale = F)

#only for original dataset 
get.pc.score(pca, full_results = F)

pca.projection(pca, new_data, scale = F, self_center = F, full_results = F)

save_num_results(all_scoress, all_projected_scoress, loadingss, evalss)

make_plots(de_pcaa, all_scoress, all_projected_scoress, datasetss)
```



## Resulting Plots

* Original Data: PC1 v. PC2
* Volcano Plot: Original Data
* Original Data: PC1 vs. log2FoldChange
* Projected Data: PC1 v. PC2
* PC1 Scores v. PC1 Projected Scores
* Volcano Plot: Projected Data
* Original Data: PC1 vs. Signed.log.p
* Projected Data: PC1 vs. Signed.log.p
* Projected Data: PC1 vs. log2FoldChange

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## Contact
alexzandradmorris@gmail.com
