
# Drug–Target Interaction Prediction Using Machine Learning

This repository contains code and data for a machine learning-based study aimed at predicting the bioactivity of compounds targeting **Acetylcholinesterase (AChE)** — a key therapeutic target in the treatment of Alzheimer's disease. The project leverages molecular descriptors derived from SMILES strings to predict IC50 values using regression models.

## Repository Structure

```
.
├── Initial_Datasets
│   ├── AChE_Bioactivity_data_1.csv      # Dataset from ChEMBL (15K+ compounds)
│   └── AChE_Bioactivity_data_2.csv      # Dataset from CHEMBL with different subset (12K + compounds)
├── Notebooks
│   ├── Drug_Target_Interaction_Prediction_Dataset1.ipynb  # Pipeline for Dataset 1
│   └── Drug_Target_Interaction_Prediction_Dataset2.ipynb  # Pipeline for Dataset 2
└── README.md                            # Project overview and instructions
```

## Datasets

Each dataset contains key columns:
- `molecule_chembl_id`: Unique ChEMBL compound ID
- `canonical_smiles`: SMILES string encoding molecular structure
- `standard_value`: Bioactivity value (e.g., IC50)

### Preprocessing Steps:
- Dropping missing values (`NaN`)
- Removing extreme outliers (`standard_value` ≥ 1,000,000)
- Adding `log_ic50 = log10(standard_value)` column
- Computing molecular descriptors using RDKit:
  - Molecular Weight
  - LogP (octanol-water partition coefficient)
  - Number of Hydrogen Donors
  - Number of Hydrogen Acceptors

## Modeling Approach

- **Model**: Random Forest Regressor (scikit-learn)
- **Features**: RDKit molecular descriptors
- **Target**: `log_ic50`
- **Evaluation Metrics**:  
  - R² Score  
  - RMSE (Root Mean Square Error)

### 📈 Results

| Dataset     | R² Score   | RMSE     |
|-------------|------------|----------|
| Dataset 1   | -0.0603    | 1.3540   |
| Dataset 2   |  0.0170    | 1.7108   |

These results indicate scope for improvement via feature engineering or advanced ML techniques.

## Dependencies

- Python 3.8+
- pandas
- numpy
- scikit-learn
- rdkit
- matplotlib (optional)

### Install Requirements

```bash
pip install pandas numpy scikit-learn rdkit
```

## Future Plans

- Explore advanced models (e.g., XGBoost, Deep Learning)
- Add molecular fingerprints & physicochemical features
- Extend predictions to other Alzheimer’s-related targets

## Learning Outcomes

- Working with cheminformatics datasets and SMILES strings
- Molecular descriptor computation using RDKit
- Regression modeling with scikit-learn
- Model evaluation using R² and RMSE

## License

This project is intended for academic and research purposes. Attribution required for reuse.
