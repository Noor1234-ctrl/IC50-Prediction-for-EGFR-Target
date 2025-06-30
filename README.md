# IC50-Prediction-for-EGFR-Target
Predicting IC50 for EGFR protein using molecular data and models including Random Forest and XGBoost

Project Overview

This project is focused on predicting the IC50 (bioactivity) of small molecules against the EGFR (Epidermal Growth Factor Receptor) protein target using machine learning.

- Molecular structures are represented by SMILES strings.
- Molecular fingerprints are generated using RDKit.
- An XGBoost regression model is trained to predict pIC50 and convert it to IC50 in nanomolar (nM).

Model Experimentation

Initially, I tested a basic regression model using Random Forest, but the performance was not satisfactory for this dataset.

After evaluating, I moved to XGBoost, which provided significantly better results with improved accuracy and generalization.

Model Performance (Tuned XGBoost)

| Metric  | Value  |
|---------|--------|
| MSE     | 0.677  |
| RMSE    | 0.823  |
| R²      | 0.760  |

The XGBoost model outperformed the previous Random Forest model significantly.
Model Performance (Comparison)
| Model               | MSE   | RMSE  | R²    |
| ------------------- | ----- | ----- | ----- |
| **Random Forest**   | 0.905 | 0.951 | 0.690 |
| **XGBoost (Tuned)** | 0.677 | 0.823 | 0.760 |

1. Fetch Data:Bioactivity data for the EGFR protein fetched using the ChEMBL API (Standard Type: IC50).
2. Data Preprocessing: 
   - Cleaned invalid or missing SMILES entries.  
   - Converted IC50 values into pIC50 (log scale) for regression.  
3. Feature Engineering: 
   - Generated Morgan fingerprints (radius=2, nBits=2048) from SMILES.  
4. Model Training:
   - Tested Random Forest (lower accuracy).  
   - Tuned and trained XGBoost, which performed better.  
5. Evaluation: 
   - Evaluated with MSE, RMSE, and R².  
6. Prediction App: 
   - Built a Gradio-based app for IC50 prediction.  

Project Structure

Example SMILES for Testing

- Benzene: `C1=CC=CC=C1`
- Ethanol: `CCO`
- Diethylamine: `CCN(CC)CC`

Tools and Libraries

- Python
- RDKit
- XGBoost
- Scikit-learn
- Gradio
- ChEMBL API
- Google Colab

Future Improvements

- Train on a larger dataset for better generalization.
- Add more chemical descriptors (LogP, TPSA, etc.) alongside fingerprints.
- Deploy as a permanent web app on Hugging Face or Streamlit.





