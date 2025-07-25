
# Drug–Target Interaction Prediction Using Machine Learning

This repository contains code, data, and molecular docking files for a machine learning-based pipeline focused on predicting the bioactivity of small molecules against key therapeutic targets related to Alzheimer's disease, Parkinson's Disease and Type 2 Diabetes.

The project includes:

- **Alzheimer’s Pipeline**: Predicting IC50 values of compounds targeting Acetylcholinesterase (AChE) using molecular descriptors derived from SMILES strings and regression models.
- **Diabetes Pipeline**: Analysis and prediction of bioactive compounds against alpha-glucosidase for managing postprandial blood glucose levels.
- **AutoDock Vina Setup**: Ligand-receptor interaction studies via molecular docking to validate binding affinity.
- **Preprocessing Scripts**: Standardized workflows for descriptor calculation, data cleaning, and visualization.
- **Organized Directory Structure**: Clear separation of raw datasets, processed results, and docking files.

This unified pipeline aims to combine cheminformatics and docking-based methods for robust drug-target interaction prediction.

## Final Report

- [Drug Target Interaction Prediction Using Machine Learning (PDF)](https://drive.google.com/file/d/1gg3f8TrlH6L94q90kwe5oInl10chNTwR/view?usp=drive_link)


## Repository Structure

```
.
├── Initial_Datasets
│   ├── AChE_Bioactivity_data_1.csv        # ChEMBL AChE dataset (15K+ compounds)
│   ├── AChE_Bioactivity_data_2.csv        # Alternate ChEMBL AChE subset (12K+ compounds)
│   ├── mao_a_ic50.csv                     # MAO-A inhibitors (2,400+ rows)
│   └── mao_b_ic50.csv                     # MAO-B inhibitors (300+ rows)
├── Notebooks
│   ├── Drug_Target_Interaction_Prediction_Dataset1.ipynb    # Pipeline for AChE Dataset 1
│   ├── Drug_Target_Interaction_Prediction_Dataset2.ipynb    # Pipeline for AChE Dataset 2
│   ├── {File_name}.ipynb                                   # Experiments: Playing around with different model architecture and combination of datasets
├── complete_mL_pipeline_best_performers.ipynb           # Final pipeline: multi-task NN, ensemble, MAO integration
├── LLM_Ollama.ipynb                                     # Initial LLM experiments using TinyLlama + prompt engineering
├── Diabetes_ppar_descriptor.ipynb                       # Initial Diabetes PPAR Descriptor Notebook


├── final_working_pipeline/                              # Finalized, production-ready ML + docking pipelines
│   ├── alzheimers_parkinsons_dti_pipeline/              # Alzheimer's + Parkinson’s complete ML pipeline
│   │   ├── complete_ml_pipeline_best_performers.ipynb
│   │   └── dataset/                                     # Curated dataset subset for this pipeline
│   │       ├── AChE_Bioactivity_data_2.csv
│   │       ├── mao_a_ic50.csv
│   │       └── mao_b_ic50.csv
│   ├── diabetes_dti_pipeline/                           # Diabetes pipeline (ML + docking + descriptors)
│   │   ├── Diabetes_ppar_descriptor.ipynb               # Integrated pipeline for PPAR-related drug prediction
│   │   ├── autodock_files/                              # Files used in AutoDock Vina docking workflow
│   │   │   ├── config/                                  # Docking configuration
│   │   │   │   └── config.txt
│   │   │   ├── docking_results/                         # Output from docking simulations
│   │   │   │   └── ppar_docking.csv
│   │   │   ├── ligand/                                  # Ligand molecule files
│   │   │   │   ├── ligand.pdb
│   │   │   │   ├── ligand.pdbqt
│   │   │   │   └── ligand_atoms.txt
│   │   │   └── receptor/                                # Receptor (PPAR) structure files
│   │   │       ├── 4ema.pdb
│   │   │       └── ppar.pdbqt
│   │   └── datasets/                                    # Diabetes-specific datasets and preprocessing
│   │       ├── alpha_glucosidase/                       # Raw alpha-glucosidase ChEMBL compound datasets
│   │       │   ├── CHEMBL1163102.csv
│   │       │   ├── CHEMBL1293309.csv
│   │       │   ├── ...                                  # Other compound files
│   │       │   └── alpha_glucosidase.csv
│   │       ├── alpha_glucosidase_targets/               # Target info for alpha-glucosidase compounds
│   │       │   └── targets_alpha_glucosidase.csv
│   │       └── processed_dataset/                       # Cleaned and merged data for training/testing
│   │           ├── merging_alpha_glucosidase.csv
│   │           ├── merging_alpha_glucosidase_cleaned.csv
│   │           └── ppar_2d_descriptors.csv

├── README.md           # Project overview and instructions

```

###  Results

#### Diabetes

<img width="1664" height="1632" alt="image" src="https://github.com/user-attachments/assets/4435b7c2-4831-4250-a429-00c2beb70c9c" />


#### Alzheimer's and Parkinson's

<img width="1052" alt="results_o:p" src="https://github.com/user-attachments/assets/b0b712fd-db5e-4a68-9edb-45976e8f0a5d" />

<img width="332" alt="evaluation_metrics" src="https://github.com/user-attachments/assets/2cfed9dc-4e4c-44c2-b993-a1b1d246654e" />


## License

This project is intended for academic and research purposes. Attribution required for reuse.
