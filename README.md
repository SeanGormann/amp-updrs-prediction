## amp-updrs-prediction
Predicting UPDRS scores from proteins in cerebrospinal fluid (CSF).

This data was curated by the team at Accelerating Medicines Partnership® Parkinson’s Disease (AMP®PD), who hosted a competition to find the best method of predicting UPDRS scores based on proetins and peptides found in CSF of Parkinsons patients. The data followed patients over a course of 3-108 months, with protein/peptide abundance and/or UPDRS scores recorded intermittently. This resulted in multiple data tables with protein concentration levels in train_proteins.csv, peptide abundance in train_peptides.csv and UPDRS scores in tclinical.csv. 

Thankfully this wasn't raw MS spectral data. Nevertheless, there was still much preprocessing, cleaning and data engineering to do before adequately exploring the data. All these can be found in the UPDRS-data-prepv2 python notebook. I first worked on the tclinical data by changing column titles, adding categorical values for UPDRS scores and also calculating the difference in UPDRS scores from month to month. The latter was in preperation for also determining the change in protein/peptide concentrations over time and seeing how that effected UPDRS scores. 

Multiple data tables were subsequently manipulated and merged. First was the addition of UPDRS score to the protein and peptide data. Another transformation was pivoting the dataframes so that each individual patient visit was treated as a single sample and the columns/features were the protein or peptide ID's. The values for this new pivoted dataframe were the corresponding concentrations. This approach aimed to tackle the predictive problem by only looking at the protein/peptide concentrations for a given time and UPDRS score, hopefully producing a more robust model with better predictive properties. Outliers were also identified as shown below:


![outliers](https://user-images.githubusercontent.com/100109163/230587134-26d7387b-4040-4f8f-8aa0-fe544823e2d8.png)


The benefit of having the data as described above is that I can used PCA and PLS-DA to determine relevant features and further transform the data. Below shows the PLS-DA of protein concentrations and the 4 different UPDRS scores. The two groups (1 being mild, 2 being moderate/severe) fail to significantly seperate apart and their remains a large overlap between the datapoints.


![PLSDA-protein-exp](https://user-images.githubusercontent.com/100109163/230587811-e4112b0c-1696-4a83-a888-cf45aea4475d.png)


I also wanted to get a sense of how the 4 different UPDRS score were correlated to one another. To do this I did a simple correlation matrix and plotted it using a heatplot. It shows scores 1 and 2 are highly correlated with one another. And that score 3 is quite independent. 

![updrs-correlation-matrix](https://user-images.githubusercontent.com/100109163/230588525-e31aa400-708f-4040-b90b-cf7b2303b725.png)


Finally, the processed data and new datasets were exported to a new directory (AMP_Data.zip). These are what will be used build machine learning models and predict UPDRS scores.
