# Estonian Driving Licenses EDA (2021–2025)
![image](https://github.com/user-attachments/assets/56147d39-ed76-4ff1-b177-39b027e49e9a)

This repository contains a Jupyter Notebook performing Exploratory Data Analysis (EDA) on the Estonian Driving Licenses dataset for years 2021–2025.

## Dataset
All CSV snapshot files are included in the data/ folder of this repository. To verify, you can run:
```
ls data/*.csv
```

The data is available via Kaggle:

- **Dataset**: [Estonian Driving Licenses (2021-2025)](https://www.kaggle.com/datasets/kayrahanozcan/estonian-driving-licenses-2021-2025/data)

You need to download the CSV files from the Kaggle dataset and place them into the `data/` folder (create this folder if it doesn’t exist).

```
mkdir data
# Download from Kaggle and move CSVs into ./data/
```

## Requirements

Install Python dependencies using `pip`:

```bash
pip install -r requirements.txt
```

Or with Conda:

```bash
conda env create -f environment.yml
conda activate eda-estonian-licenses
```

## Project Structure

```
├── data/                   
│   ├── jl_2021-01-01.csv
│   ├── jl_2022-01-01.csv
│   ├── jl_2023-01-01.csv
│   ├── jl_2024-01-01.csv
│   ├── jl_2025-01-01.csv
│   ├── jl_2025-04-01.csv
├── notebooks/              # Jupyter Notebook(s)
│   └── EDA-test___.ipynb
├── requirements.txt        # pip dependencies
├── README-jl-AA.md    
└── README.md               # This file
```

## Usage

1. Clone this repository:
```bash
git clone https://github.com/yourusername/estonian-licenses-eda.git
cd estonian-licenses-eda
```
2. Install dependencies (see Requirements above).
3. Download the Kaggle dataset CSV files and place them in `data/`.
4. Launch Jupyter Notebook:
```bash
jupyter notebook notebooks/Estonian_Licenses_EDA.ipynb
```
5. Run all cells to reproduce the analysis and visualizations.

## Sections in the Notebook

1. **Introduction** – project overview and goals
2. **Data Loading & Preprocessing** – reading CSVs, renaming columns, parsing dates
3. **Demographic Analysis** – age & gender distributions
4. **Category Analysis** – frequency and combinations of license categories
5. **Office Analysis** – application vs. issuance offices (online vs. in-person)
6. **Temporal Trends** – issued vs. expired licenses over time and net growth
7. **Conclusions & Recommendations** – key insights and next steps

## License

This project is released under the MIT License. Feel free to use and adapt the code for your own purposes.

