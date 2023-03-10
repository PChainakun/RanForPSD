# Model description
RanForPSD model is a Random Forest Regressor (RFR) model for mapping the X-ray coronal height based on the reverberation features that appear in the power spectral density (PSD) of AGN. It computes the PSD profiles in the form of a power-law where the reverberation effects due to the lamp-post source are imprinted on. The model requires the pre-computed impulse response (IR) functions of the X-ray source illuminating the accretion disc. The key model parameters include:
- black hole mass --> pre-computed IR 
- black hole spin --> pre-computed IR 
- inclination --> pre-computed IR functions 
- coronal height (lamp-post geometry) --> pre-computed IR
- inner disc radius --> pre-computed IR
- outer disc radius --> pre-computed IR
- PSD index --> RanForPSD model
- reflection fraction (defined as reflection/continuum) --> RanForPSD model

The simulated PSD data are rebinned so that their frequency range and bin-size are matched with the observed PSD profile. Then, they are split into the training and test dataset. The model is trained and validated via the K-fold cross-validation process to fine-tune two RFR hyperparameters including the maximum depth (MP) and the number of estimators (NE). The developed model with the best MP and NE is then used to predict the coronal height from the observed PSD data.

# Required files
- "RFR_model" in the main repository directory
- observed PSD data that we want to predict the coronal height
- pre-computed IR functions (e.g., from KYNxilrev model) - Note that the response functions provided in this GitHub is computed using the BH mass of 10^6 M_{sun}, with the black hole spin a = 0.998 and the inclination i = 45 degrees.

# ML Algorithms
- sklearn.ensemble.RandomForestRegressor (RFR algorithm)
- sklearn.model_selection.GridSearchCV (cross-validation)

# Outputs
It will print the report on the total number of the simulated PSD profiles (with plots of all PSD) and the best MP and NE, the accuracy score for training/validating and test set, and the predicted coronal height 

# Current version of the RFR model
- black hole mass, spin and inclination are fixed at the values used to compute the IR
- If the assumed AGN mass (M_BH_AGN) is different from the mass used to calculate the IR (M_BH_response), it will systematically shift the PSD profiles to higher or lower frequencies with the mass fraction defined as (M_BH_AGN)/(M_BH_response) 
