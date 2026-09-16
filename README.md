# Methyl linoleate oxidation monitored by Vocus HR-CI-TOF-MS
This repository contains the Python analysis notebooks supporting the manuscript “Single-platform monitoring of methyl linoleate oxidation by Vocus high-resolution chemical-ionisation time-of-flight mass spectrometry”.
The workflow combines dynamic headspace (DHS) and dynamic solution injection (DSI) measurements acquired with an NH4+ Vocus high-resolution chemical-ionisation time-of-flight mass spectrometer. It performs signal normalisation, matched-blank subtraction, feature selection, data fusion, anchor-centred correlation analysis and generation of the temporal-profile figures reported in the manuscript.
Repository contents
The analysis is divided into three notebooks:
`notebooks/ML_oxidation_data_processing_and_feature_selection.ipynb` reproduces the principal data-processing workflow, including normalisation, blank subtraction, Wilcoxon testing with Bonferroni correction, DHS–DSI fusion and anchor-centred Pearson correlation analysis.
`notebooks/ML_oxidation_representative_time_profiles_four_features.ipynb` generates the representative temporal profiles of the four anchor features.
`notebooks/ML_oxidation_grouped_profiles_38_features.ipynb` generates the four grouped figures showing the anchor features and their selected correlated features.
The source and processed data are archived separately at Zenodo:
Zenodo record: `ZENODO_DOI_HERE`
The Zenodo record is the permanent archive of the data and exact analysis release associated with the manuscript. The GitHub repository provides a browsable and reusable version of the code.
Software requirements
Python 3.10 or later is recommended. Install the required packages in a new environment:
```bash
python -m venv .venv
```
Activate the environment on Linux or macOS:
```bash
source .venv/bin/activate
```
Or on Windows PowerShell:
```powershell
.venv\Scripts\Activate.ps1
```
Then install the dependencies:
```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```
Obtaining the data
Download the data package from the Zenodo record above. Arrange the downloaded files as described in `data/README.md`. The notebooks use relative paths so that they can be run locally, in JupyterLab or in Google Colab after the repository and data have been made available in the same working directory.
The expected analysis layout is:
```text
repository_root/
├── notebooks/
│   ├── ML_oxidation_data_processing_and_feature_selection.ipynb
│   ├── ML_oxidation_representative_time_profiles_four_features.ipynb
│   └── ML_oxidation_grouped_profiles_38_features.ipynb
├── source_data/
│   ├── DHS/
│   │   ├── log.csv
│   │   └── extracted DHS CSV files
│   └── DSI/
│       ├── log.csv
│       └── extracted DSI CSV files
├── processed_data/
│   └── 55_most_abundant_features_annotated_final.xlsx
├── data/
│   └── README.md
├── requirements.txt
├── CITATION.cff
└── LICENSE
```
The source-data and generated-output directories are excluded from Git tracking because the archived data are distributed through Zenodo.
Running the analysis
Start JupyterLab from the repository root:
```bash
jupyter lab
```
Run the notebooks in the following order:
`ML_oxidation_data_processing_and_feature_selection.ipynb`
`ML_oxidation_representative_time_profiles_four_features.ipynb`
`ML_oxidation_grouped_profiles_38_features.ipynb`
The notebooks should be executed from the repository root, or their project-root variable should be set to the repository root. Generated tables and figures are written to the output directories defined within each notebook.
Principal verification points
With the archived dataset, the main processing notebook should reproduce:
1,087 initial DHS mass-spectral features;
1,571 initial DSI mass-spectral features;
304 retained DHS features;
474 retained DSI features;
778 features in the fused dataset; and
307 significant anchor–feature associations, corresponding to 213 unique target features.
These checks verify implementation of the reported workflow; they do not independently confirm the structural annotations assigned to individual mass-spectral features.
Citation
If you use this code or dataset, please cite the Zenodo record and the associated article. Citation metadata for the software are provided in `CITATION.cff`. The article citation should be added here once its bibliographic details are available.
Licences
The analysis code is released under the MIT License. The data are distributed under the licence specified in the Zenodo record.
Contact
Questions about the workflow may be submitted through the GitHub issue tracker or directed to the corresponding author of the associated manuscript.
