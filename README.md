
# Drug–Target Interaction Prediction Using Machine Learning

This repository contains code and data for a machine learning-based study aimed at predicting the bioactivity of compounds targeting **Acetylcholinesterase (AChE)** — a key therapeutic target in the treatment of Alzheimer's disease. The project leverages molecular descriptors derived from SMILES strings to predict IC50 values using regression models.

## Repository Structure
'''
.
├── Initial_Datasets                           # All raw datasets from ChEMBL / other sources
│   ├── AChE_Bioactivity_data_1.csv            # ChEMBL AChE dataset (15K+ compounds)
│   ├── AChE_Bioactivity_data_2.csv            # Alternate AChE subset (12K+ compounds)
│   ├── HIV_combined_IC50_dataset.csv          # HIV inhibitors merged dataset
│   ├── HIV_dataset.csv                        # HIV dataset - original (individual file)
│   ├── mao_a_ic50.csv                         # MAO-A inhibitors (2,400+ rows)
│   ├── mao_b_ic50.csv                         # MAO-B inhibitors (300+ rows)
│   └── ppar_binding_affinity_dataset.csv      # PPAR binding affinity data for diabetes

├── Notebooks                                  # Experimental / exploratory notebooks
│   ├── Drug_Target_Interaction_Prediction_Dataset1.ipynb        # Pipeline for AChE Dataset 1
│   ├── Drug_Target_Interaction_Prediction_Dataset2.ipynb        # Pipeline for AChE Dataset 2
│   ├── Drug_Target_Interaction_Prediction_mao_b.ipynb           # MAO-B-specific DTI pipeline
│   ├── Drug_Target_Interaction_Prediction_Neural_Network.ipynb  # NN-based general DTI modeling
│   ├── Classification_ECFP4_FingerPrint_and_Neural_Network.ipynb# Classification using ECFP4 + NN
│   ├── ECFP4_FingerPrint_and_Neural_Network.ipynb               # Feature exploration with ECFP4
│   ├── mao_b_and_AChe_regression.ipynb                          # Regression tasks on AChE + MAO-B
│   └── {File_name}.ipynb                                        # Experimental: model/dataset trials

├── complete_ml_pipeline_best_performers.ipynb   # Final DTI pipeline (multi-task NN + ensemble + MAO)

├── Diabetes_ppar_descriptor.ipynb               # PPAR-specific pipeline with descriptor engineering

├── LLM_Ollama.ipynb                             # LLM experiments using TinyLlama for DTI tasks

├── README.md                                    # Project overview, setup instructions, usage guide

└── final_working_pipeline/                      # Finalized, production-ready ML + docking pipelines
    ├── alzheimers_parkinsons_dti_pipeline/      # Alzheimer's + Parkinson’s complete ML pipeline
    │   ├── complete_ml_pipeline_best_performers.ipynb
    │   └── dataset/                             # Curated dataset subset for this pipeline
    │       ├── AChE_Bioactivity_data_2.csv
    │       ├── mao_a_ic50.csv
    │       └── mao_b_ic50.csv

    └── diabetes_dti_pipeline/                   # Diabetes pipeline (ML + docking + descriptors)
        ├── Diabetes_ppar_descriptor.ipynb       # Integrated pipeline for PPAR-related drug prediction
        ├── autodock_files/                      # Files used in AutoDock Vina docking workflow
        │   ├── config/                          # Docking configuration
        │   │   └── config.txt
        │   ├── docking_results/                 # Output from docking simulations
        │   │   └── ppar_docking.csv
        │   ├── ligand/                          # Ligand molecule files
        │   │   ├── ligand.pdb
        │   │   ├── ligand.pdbqt
        │   │   └── ligand_atoms.txt
        │   └── receptor/                        # Receptor (PPAR) structure files
        │       ├── 4ema.pdb
        │       └── ppar.pdbqt
        └── datasets/                            # Diabetes-specific datasets and preprocessing
            ├── alpha_glucosidase/               # Raw alpha-glucosidase ChEMBL compound datasets
            │   ├── CHEMBL1163102.csv
            │   ├── CHEMBL1293309.csv
            │   ├── ...                          # Other compound files
            │   └── alpha_glucosidase.csv
            ├── alpha_glucosidase_targets/       # Target info for alpha-glucosidase compounds
            │   └── targets_alpha_glucosidase.csv
            └── processed_dataset/               # Cleaned and merged data for training/testing
                ├── merging_alpha_glucosidase.csv
                ├── merging_alpha_glucosidase_cleaned.csv
                └── ppar_2d_descriptors.csv

'''

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

- **Model**: Random Forest Regressor (scikit-learn), Neural Networks and Ensemble modelling
- **Features**: RDKit molecular descriptors
- **Target**: `log_ic50`
- **Evaluation Metrics**:  
  - R² Score  
  - RMSE (Root Mean Square Error)

###  Results

<img width="1052" alt="results_o:p" src="https://github.com/user-attachments/assets/b0b712fd-db5e-4a68-9edb-45976e8f0a5d" />

<img width="332" alt="evaluation_metrics" src="https://github.com/user-attachments/assets/2cfed9dc-4e4c-44c2-b993-a1b1d246654e" />

## Dependencies

- Python 3.8+
- pandas
- numpy
- scikit-learn
- rdkit
- matplotlib (optional)

### Install Requirements

```bash
pip install pandas matplotlib seaborn rdkit scikit-learn tensorflow datasets scikit-learn pandas numpy transformers
```

## Future Plans

- Explore and play around with LLM's
- Extend to other disaeses
- Create a more robust ML pipleine 

## Learning Outcomes

- Working with cheminformatics datasets and SMILES strings
- Molecular descriptor computation using RDKit
- Regression modeling with scikit-learn
- Model evaluation using R² and RMSE

## License

This project is intended for academic and research purposes. Attribution required for reuse.
