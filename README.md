# :house_with_garden: Introduction
This template enables you to build or use a random forest algorithm to predict the behavior of wild animals based on acceleration data (ACC). It is based on the publication Vaadia et al. submit.   
The template includes:  
- Two R scripts, to build a random forest model and/or use an existing random forest model;
- example datasets;
- a fully annotated behavioral dataset of Griffon vultures (_Gyps fulvys_)
<br><br>

## Get familiar with the workflow
The full workflow is described in Figure 2 of the paper; the section numbers in the R script match the workflow numbers. For example, the code to run section 2 of the workflow "Match ACC bouts and behaviors" can be found in section 2 of the R code.  

In summary, the first R script (`1 - building_rf_model.Rmd`) allows you to match your own behavioral annotated dataset with the raw ACC data, identify the distinct ACC bouts, extract all the statistical features required to build your own random forest, and then finally build and test the performance of the model.  

The second R script (`2 - using_rf_model.Rmd`) allows you then to use the random forest model you just built or use the griffon vulture random forest model provided (if you work with this or similar species) to annotate the data of unobserved wild animals and generate a dataset of behaviorally annotated ACC bouts.  
<br>

> [!NOTE]
We also provide the code to calculate a confidence score for each behavior classification, i.e., how confident the random forest model is on its prediction.
<br>

## Get familiar with the Griffon vulture dataset  
The example datasets provided, as well as the fully annotated training dataset, were collected from captive and free-roaming griffon vultures in Spain (captive) and Israel (captive and free-roaming).  

The training dataset contains 5783 ACC bouts, matched to six different behavioral classes:
- _Standing_ - vulture is upright (may include minor preening and changes in body posture); 
- _Lying_ - vulture is lying parallel to the ground, either resting or incubating; 
- _Feeding_ – vulture is either directly eating from a carcass, or engaged in intense social interactions next to the carcass (e.g., fighting, posturing towards other vultures before eating); 
- _Ground_ - includes all other active ground behaviors which are not directly related to feeding or resting (e.g., walking, running, hopping, etc.); 
- _Flapping_ - active flight with wingbeats; 
- _Soaring_ - passive flight (e.g., thermal soaring, gliding, etc.).
<br><br><br>

# :open_file_folder: Get started
## Create your own project
1 - Click [*here*](https://tauex-my.sharepoint.com/:u:/g/personal/martaoc_tauex_tau_ac_il/ETdtQt2a1qpKip8-lSrUBdcB6KEOiedubzwrjrZ9E1O3vg?e=wk3lhx) to download the repository directly  
2 - Unzip and rename the folder with your project name

## Are you building your own model or using an existing one?
Your first decision will be made here: do you want to build your own random forest model, or do you want to use the provided griffon vulture one (or other model already built)?
<br><br><br>

# :hammer_and_wrench: Build your own random forest model
If you want to build your own random forest model, start with Script `1 - building_rf_model.Rmd`.  

You will need:  
1 - Behavioral observations of your ACC-tagged individuals (tag number, date, time, and behavior) -  _Observations_data_;  
2 - Raw ACC measurements of the observed ACC-tagged individuals (tag number, date, time, ACC measurements) - _ACC_training_data_;  
3 - Tag calibration file (see Garde et al. 2022, https://doi.org/10.1111/2041-210X.13804) - _Calibration_data_  
<br>

> [!IMPORTANT]
Start by replacing the files in the folders _ACC_training_data_, _Observations_data_ and _Calibration_data_ with your own data files.  
Then, set your custom parameters in section _A - Set parameters_.
<br>

What parameters will you need to set?  
- `bout_type` - there are a few possible scenarios to identify each individual ACC bout:  
  - `bout_type == device` - the device indicates the start of an ACC bout. You also need to identify the column name of your dataset that identifies the start and end of the bout (`column_bout_id`), as well as the variable name that identifies the start of the bout (`start_bout_id`);  
  - `bout_type == time_diff` - the ACC is sampling every X minutes, so you can use the time difference between measurements to identify when a new bout started (X = `time_threshold`);  
  - `bout_type == cont` - the ACC is sampling continuously, in which case you can split the continuous data into bouts of Y measurements (Y = `bout_duration` * `acc_frequency`)    
- `bout_duration` - set your relevant bout duration, in seconds  
- `acc_frequency` - set the frequency of ACC collection, in Hz  

Then, read the script carefully and run each chunk separately, adjusting the datafiles and parameters as you go.  
<br>

> [!TIP]
> By the end of the first script, you will have created your own random forest model! :tada:

<br><br>
# :desktop_computer: Use an existing random forest model
If you've built your own random forest model using the first script, or if you want to use another existing random forest model (e.g., our provided Griffon vulture random forest), move on to the second script `2 - using_rf_model.Rmd`.  

You will need:  
- Raw ACC measurements of unobserved animals to classify their behaviors - _Unobserved_ACC_data_;
- A random forest model, either:
  - Your own model (built using the first script, or not) - _My_RF_model_  
  - The provided griffon vulture random forest - _Griffon_RF_model_

> [!IMPORTANT]
Start by replacing the files in the folders _Unobserved_ACC_data_.  
Then, set your custom parameters in section _A - Set parameters_.
<br>

What parameters will you need to set?  
You will need to set the same parameters as in the previous section (`bout_type`, `bout_duration` and `acc_frequency`). See the previous section for details on these variables.   
In addition, you will also need to set if you are using your own random forest model or if you are using the griffon vulture model:  
- `rf_model == "own_model"` - if you are using your own random forest model  
- `rf_model == "griffon_model"` - if you are using the griffon vulture model provided  
<br> 

Then, read the script carefully and run each chunk separately, adjusting the datafiles and parameters as you go.  
<br>

> [!TIP]
> By the end of the second script, you will have your ACC measurements of unobserved individuals annotated with the correspondent behaviors and confidence scores! :tada:

<br><br>
# :pushpin:	 Final remarks
Congratulations on making it this far!  
We hope the code is useful and easy to follow. Contact us for any questions or sugestions:   
<br>
:e-mail: Marta Acácio - marta.acacio@gmail.com  
:e-mail: Gideon Vaadia - gideonvaadia@gmail.com   
:e-mail: Orr Spiegel - orrspiegel@tauex.tau.ac.il  
<br><br>
