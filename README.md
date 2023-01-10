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
- "RandForPSD.ipynb" in the main repository directory
- Observed PSD data that we want to predict the coronal height
- Pre-computed IR functions (e.g., from KYNxilrev model)

# ML Algorithms
- sklearn.ensemble.RandomForestRegressor (RFR algorithm)
- sklearn.model_selection.GridSearchCV (cross-validation)

# Outputs

# Current version of the RanForPSD model
