# Replication Material

This repository contains the replication material for the paper:

**Investigating Regional Electricity Consumption Across Europe: A Spatial Analysis**

https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5289637

The repository provides the code and input files needed to reproduce the construction of the analytical dataset and the empirical analysis presented in the paper.

The complete regional electricity consumption dataset is publicly available on Figshare:

https://doi.org/10.6084/m9.figshare.25864429

The replication material uses this dataset together with socioeconomic and climate covariates from ARDECO and Eurostat NUTS geometries to construct the final analytical sample used in the paper.

## Repository structure

The replication material is organized as follows:

```text
regional-electricity-consumption-europe/
│
├── data/
│   ├── ELC_dataset.xlsx
│   ├── gdp.csv
│   ├── real_compensation.csv
│   ├── population.csv
│   ├── HDD.csv
│   ├── CDD.csv
│   ├── dd.csv
│   ├── NUTS_RG_20M_2021_3035.gpkg
│   └── dataset.csv
│
├── plots/
│
├── create_dataset.ipynb
├── analysis.ipynb
└── README.md
```

## Input data

All input data used to construct the final analytical sample are stored in the `data/` folder.

The file `ELC_dataset.xlsx` contains the complete regional electricity consumption dataset used as the starting point for the analysis. This dataset is the public electricity consumption dataset made available on Figshare:

https://doi.org/10.6084/m9.figshare.25864429

It includes regional electricity consumption data collected and harmonized from national and European sources.

The socioeconomic and climate covariates are provided as separate CSV files in the `data/` folder:

- `gdp.csv`: regional GDP per capita;
- `real_compensation.csv`: regional real compensation per employee;
- `population.csv`: regional population;
- `HDD.csv`: regional Heating Degree Days;
- `CDD.csv`: regional Cooling Degree Days;
- `dd.csv`: additional HDD and CDD information used for the United Kingdom and Switzerland.

The regional geometries are stored in:

- `NUTS_RG_20M_2021_3035.gpkg`

This file contains the Eurostat NUTS regional boundaries used to build the spatial dataset and produce the maps.

## Dataset construction

The notebook `create_dataset.ipynb` processes the input files contained in the `data/` folder and constructs the final analytical sample used in the empirical analysis.

Specifically, the notebook:

1. loads the complete electricity consumption dataset from `ELC_dataset.xlsx`;
2. loads the socioeconomic and climate covariates from the CSV files;
3. loads the Eurostat NUTS regional geometries;
4. merges electricity consumption data with the covariates;
5. applies the sample restrictions described in the paper;
6. attaches the relevant NUTS geometries;
7. creates the final analytical dataset;
8. reports the description and unit of measurement of the variables included in the analysis.

The output of this notebook is saved as:

```text
data/dataset.csv
```

This file is the final dataset used by the empirical analysis notebook.

## Empirical analysis

The notebook `analysis.ipynb` reproduces the empirical results reported in the paper.

The notebook uses the following input file:

```text
data/dataset.csv
```

It reproduces the spatial statistics, GWR and MGWR results, clustering analysis, tables, and figures included in the paper.

All generated plots are saved in the `plots/` folder.

## Reproducibility workflow

To reproduce the results, run the notebooks in the following order:

1. `create_dataset.ipynb`
2. `analysis.ipynb`

The first notebook creates the final analytical dataset. The second notebook uses that dataset to reproduce the empirical analysis, tables, and figures.

## Notes on data sources

The public electricity consumption dataset and the replication material serve different purposes.

The public dataset on Figshare documents the complete electricity consumption data collection effort, including country-level coverage, source links, territorial granularity, temporal coverage, and data transformations.

The replication material uses that dataset, together with additional covariates and spatial geometries, to construct the specific 2021-2023 analytical sample used in the paper.

The independent variables used in the empirical analysis are not part of the public electricity consumption dataset. They are provided separately in the `data/` folder and are derived from the European Commission's Annual Regional Database, ARDECO, as described in the paper.

## Output

Running the full workflow produces:

- the final analytical dataset: `data/dataset.csv`;
- the empirical tables reported in the paper;
- the spatial statistics, GWR, MGWR, and clustering results;
- the figures and maps saved in the `plots/` folder.

## Citation

If you use this replication material, please cite the paper.
