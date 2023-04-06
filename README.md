## amp-updrs-prediction
Predicting UPDRS scores from proteins in cerebrospinal fluid (CSF).

This data was curated by the team at Accelerating Medicines Partnership® Parkinson’s Disease (AMP®PD), who hosted a competition to find the best method of predicting UPDRS scores based on proetins and peptides found in CSF of Parkinsons patients. The data followed patients over a course of 3-108 months, with protein/peptide abundance and/or UPDRS scores recorded intermittently. This resulted in multiple data tables with protein concentration levels in train_proteins.csv, peptide abundance in train_peptides.csv and UPDRS scores in tclinical.csv. 

Thankfully this wasn't raw MS spectral data. Nevertheless, there was still much preprocessing, cleaning and data engineering to do before adequately exploring the data. All these can be found in the UPDRS-data-prepv2 python notebook. I first worked on the tclinical data by changing column titles, adding categorical values for UPDRS scores and also calculating the difference in UPDRS scores from month to month. The latter was in preperation for also determining the change in protein/peptide concentrations over time and seeing how that effected UPDRS scores. 
