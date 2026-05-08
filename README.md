{\rtf1\ansi\ansicpg1252\cocoartf2868
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;}
{\colortbl;\red255\green255\blue255;}
{\*\expandedcolortbl;;}
\paperw11900\paperh16840\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0

\f0\fs24 \cf0 # Replication Material\
\
This repository contains the replication material for the paper:\
\
**Investigating Regional Electricity Consumption Across Europe: A Spatial Analysis**\
\
The repository provides the code and input files needed to reproduce the construction of the analytical dataset and the empirical analysis presented in the paper.\
\
The complete regional electricity consumption dataset is publicly available on Figshare:\
\
https://doi.org/10.6084/m9.figshare.25864429\
\
The replication material uses this dataset together with socioeconomic and climate covariates from ARDECO and Eurostat NUTS geometries to construct the final analytical sample used in the paper.\
\
## Repository structure\
\
The replication material is organized as follows:\
\
    replication_material/\
    \uc0\u9474 \
    \uc0\u9500 \u9472 \u9472  data/\
    \uc0\u9474    \u9500 \u9472 \u9472  ELC_dataset.xlsx\
    \uc0\u9474    \u9500 \u9472 \u9472  gdp.csv\
    \uc0\u9474    \u9500 \u9472 \u9472  real_compensation.csv\
    \uc0\u9474    \u9500 \u9472 \u9472  population.csv\
    \uc0\u9474    \u9500 \u9472 \u9472  HDD.csv\
    \uc0\u9474    \u9500 \u9472 \u9472  CDD.csv\
    \uc0\u9474    \u9500 \u9472 \u9472  dd.csv\
    \uc0\u9474    \u9500 \u9472 \u9472  NUTS_RG_20M_2021_3035.gpkg\
    \uc0\u9474    \u9492 \u9472 \u9472  dataset.csv\
    \uc0\u9474 \
    \uc0\u9500 \u9472 \u9472  plots/\
    \uc0\u9474 \
    \uc0\u9500 \u9472 \u9472  create_dataset.ipynb\
    \uc0\u9500 \u9472 \u9472  analysis.ipynb\
    \uc0\u9492 \u9472 \u9472  README.md\
\
## Input data\
\
All input data used to construct the final analytical sample are stored in the `data/` folder.\
\
The file `ELC_dataset.xlsx` contains the complete regional electricity consumption dataset used as the starting point for the analysis. This dataset is the public electricity consumption dataset made available on Figshare: https://doi.org/10.6084/m9.figshare.25864429. It includes regional electricity consumption data collected and harmonized from national and European sources.\
\
The socioeconomic and climate covariates are provided as separate CSV files in the `data/` folder:\
\
- `gdp.csv`: regional GDP per capita;\
- `real_compensation.csv`: real compensation per employee;\
- `population.csv`: regional population;\
- `HDD.csv`: regional Heating Degree Days;\
- `CDD.csv`: regional Cooling Degree Days;\
- `dd.csv`: additional HDD and CDD information used for the United Kingdom and Switzerland.\
\
The regional geometries are stored in:\
\
- `NUTS_RG_20M_2021_3035.gpkg`\
\
This file contains the Eurostat NUTS regional boundaries used to build the spatial dataset and produce the maps.\
\
## Dataset construction\
\
The notebook `create_dataset.ipynb` processes the input files contained in the `data/` folder and constructs the final analytical sample used in the empirical analysis.\
\
Specifically, the notebook:\
\
1. loads the complete electricity consumption dataset from `ELC_dataset.xlsx`;\
2. loads the socioeconomic and climate covariates from the CSV files;\
3. loads the Eurostat NUTS regional geometries;\
4. merges electricity consumption data with the covariates;\
5. applies the sample restrictions described in the paper;\
6. attaches the relevant NUTS geometries;\
7. creates the final analytical dataset;\
8. reports the description and unit of measurement of the variables included in the analysis.\
\
The output of this notebook is saved as:\
\
    data/dataset.csv\
\
This file is the final dataset used by the empirical analysis notebook.\
\
## Empirical analysis\
\
The notebook `analysis.ipynb` reproduces the empirical results reported in the paper.\
\
The notebook uses the following input file:\
\
    data/dataset.csv\
\
It reproduces the spatial statistics, GWR and MGWR results, clustering analysis, tables, and figures included in the paper.\
\
All generated plots are saved in the `plots/` folder.\
\
## Reproducibility workflow\
\
To reproduce the results, run the notebooks in the following order:\
\
1. `create_dataset.ipynb`\
2. `analysis.ipynb`\
\
The first notebook creates the final analytical dataset. The second notebook uses that dataset to reproduce the empirical analysis, tables, and figures.\
\
## Notes on data sources\
\
The public electricity consumption dataset and the replication material serve different purposes.\
\
The public dataset on Figshare documents the complete electricity consumption data collection effort, including country-level coverage, source links, territorial granularity, temporal coverage, and data transformations.\
\
The replication material uses that dataset, together with additional covariates and spatial geometries, to construct the specific 2021-2023 analytical sample used in the paper.\
\
The independent variables used in the empirical analysis are not part of the public electricity consumption dataset. They are provided separately in the `data/` folder and are derived from the European Commission's Annual Regional Database, ARDECO, as described in the paper.\
\
## Output\
\
Running the full workflow produces:\
\
- the final analytical dataset: `data/dataset.csv`;\
- the empirical tables reported in the paper;\
- the spatial statistics, GWR, MGWR, and clustering results;\
- the figures and maps saved in the `plots/` folder.\
\
}