# Introduction
This template enables you to build or use a random forest algorithm to predict the behavior of wild animals based on acceleration data (ACC). It is based on the publication Vaadia et al.  
The template includes:  
- Two R scripts, to build a random forest model and/or use an existing random forest model;
- example datasets;
- a fully annotated behavioral dataset of Griffon vultures (_Gyps fulvys_)


## Get familiar with the workflow
The full workflow is described in Figure 2 of the paper; the section numbers in the R script match the workflow numbers. For example, the code to run section 2 of the workflow "Match ACC bouts and behaviors" can be found in section 2 of the R code.  

In summary, the first R script (`1 - building_rf_model.Rmd`) allows you to match your own behavioral annotated dataset with the raw ACC data, identify the distinct ACC bouts, extract all the statistical features required to build your own random forest, and then finally build and test the performance of the model.  

The second R script (`2 - using_rf_model.Rmd`) allows you then to use the random forest model you just built or use the griffon vulture random forest model provided (if you work with this or similar species) to annotate the data of unobserved wild animals and generate a dataset of behaviorally annotated ACC bouts.  

> [!IMPORTANT]
We also provide the code to calculate a confidence score for each behavior classification, i.e., how confident the random forest model is on its prediction. 
