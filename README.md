4 datasets with 300+ observations each where the causal direction between variables flips based on threshold values. Features surface energy balance (soil heat flux vs. net radiation) and traffic dynamics (speed vs. density) with ground truth from Brutsaert (1982) and Kerner (2004).


 A complete  Causal Challenge Report.pdf  is attached in docs folder. 


# Causal Inflection Benchmark: Value-Dependent Causal Reversal

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Dataset: CauseEffectPairs](https://img.shields.io/badge/Dataset-CauseEffectPairs-green.svg)](https://webdav.tuebingen.mpg.de/cause-effect/)

## Overview

This repository contains four benchmark datasets for **value-dependent causal reversal**  a phenomenon where the causal relationship between two variables changes strength or structure based on threshold values. Each dataset includes 300+ real-world observations with known ground truth from peer-reviewed literature (Mooij et al., 2016, JMLR).

### The Causal Reversal Problem

Standard causal discovery assumes a fixed direction (X → Y or Y → X). However, many real-world systems exhibit **regime-dependent causality** where the strength and reliability of causal relationships change across thresholds.

## Datasets

### Dataset 1: Elevation vs. Temperature (Pair 0001)

| Property | Value |
|:---------|:------|
| **X** | Altitude / Elevation (meters above sea level) |
| **Y** | Mean Annual Temperature (°C) |
| **Sample Size** | 349 weather stations |
| **Ground Truth** | Altitude → Temperature (Mooij et al., 2016) |
| **Source** | Deutscher Wetterdienst (DWD) via MPI |

**Causal Regimes:**
| Regime | Condition | Characterization |
|:-------|:----------|:-----------------|
| Low-to-Mid Elevations | X ≤ 800m | Strong X → Y (adiabatic lapse rate) |
| High Elevations | X > 800m | Weak / Confounded X → Y (alpine complexity) |

### Dataset 2: Abalone Weight vs. Age (Pair 0006)

| Property | Value |
|:---------|:------|
| **X** | Shell Weight (dry grams) |
| **Y** | Biological Age (years, from shell rings) |
| **Sample Size** | 4,177 marine specimens |
| **Ground Truth** | Age → Shell Weight (Mooij et al., 2016) |
| **Source** | Tasmanian marine biology survey |

**Causal Regimes:**
| Regime | Condition | Characterization |
|:-------|:----------|:-----------------|
| Juvenile Growth | X ≤ 0.15g | Strong Age → Weight (linear growth) |
| Mature Phase | X > 0.15g | Diminishing relationship (growth plateau) |

### Dataset 3: Net Radiative Flux vs. Soil Heat Flux (AmeriFlux)

| Property | Value |
|:---------|:------|
| **X** | Net Radiative Flux (W/m²) |
| **Y** | Soil Heat Flux (W/m²) |
| **Sample Size** | 500 observations |
| **Ground Truth** | Day: X → Y, Night: Y → X (Brutsaert, 1982) |
| **Source** | AmeriFlux Network |

### Dataset 4: Traffic Speed vs. Density (Caltrans PeMS)

| Property | Value |
|:---------|:------|
| **X** | Vehicle Speed (km/h) |
| **Y** | Traffic Density (veh/km) |
| **Sample Size** | 500 observations |
| **Ground Truth** | Free flow: X → Y, Congested: Y → X (Kerner, 2004) |
| **Source** | Caltrans PeMS |

## Repository Structure

## Repository Structure


causal-inflection-benchmark/
├── data/
│   ├── soil_heat_flux_data.csv
│   └── traffic_dynamics_data.csv
├── plots/
│   ├── soil_heat_flux_plot.png
│   └── traffic_dynamics_plot.png
├── docs/
│   └── Causal Challenge Report.pdf
├── README.md          
├── LICENSE            
└── .gitignore        

## Quick Start

### Prerequisites

Create conda environment:
conda create -n c_challenge python=3.8
conda activate c_challenge
conda install numpy pandas matplotlib scipy

## Ground Truth Citations

Dataset 1
Brutsaert, W. (1982). Evaporation into the Atmosphere: Theory, History, and Applications. Springer.
DOI: 10.1007/978-94-017-1497-6


Dataset 2
Kerner, B. S. (2004). The Physics of Traffic: Empirical Phenomena of Chaotic Mobile Systems. Springer.
DOI: 10.1007/978-3-540-40986-1

## Data Sources


Dataset	Source	Link

Soil Heat Flux	AmeriFlux Network	ameriflux.lbl.gov
Traffic Dynamics	Caltrans PeMS	pems.dot.ca.gov


## Key Findings


Causal relationships are regime-dependent  The strength of Altitude → Temperature weakens significantly above 800m elevation

Biological growth has thresholds  Abalone weight-age relationship plateaus after 0.15g (maturity)

Physical thresholds matter  Day/night flips soil heat flux direction; free-flow/congested flips traffic causality

Real-world data confirms theory  All datasets are observational, not synthetic


## Applications

This benchmark can be used for:

Testing causal discovery algorithms on regime-switching data

Evaluating threshold detection methods

Developing conditional causal inference models

Educational demonstrations of non-stationary causality


## Author


FAHAD ALI


Project submitted as part of Causal Inference for Temporal and Non-Temporal Data, University of Vienna, Summer 2026.

## Citation


If you use this dataset in your research, please cite:

bibtex
@misc{causal-inflection-benchmark-2026,
  author = {ALI, FAHAD},
  title = {Causal Inflection Benchmark: Value-Dependent Causal Reversal},
  year = {2026},
  publisher = {GitHub},
  url = {https://github.com/Fahad3166/causal-inflection-benchmark}
}

## License
MIT License — feel free to use, modify, and distribute with attribution.

⚠️ Important: While the code is under MIT license, the data remains the property of the original creators (AmeriFlux Network and Caltrans PeMS). Please cite them appropriately when using the data.

@misc{ameriflux_base,
  title = {AmeriFlux BASE Data Product},
  author = {{AmeriFlux Management Project}},
  year = {2020},
  publisher = {Lawrence Berkeley National Laboratory},
  doi = {10.17190/AMF/1246084},
  howpublished = {\url{https://ameriflux.lbl.gov/}}
}


@techreport{pems,
  title = {PeMS: A Freeway Performance Measurement System},
  author = {Chen, C. and Petty, K. and Skabardonis, A. and Varaiya, P. and Jia, Z.},
  year = {2001},
  institution = {University of California, Berkeley},
  howpublished = {\url{https://pems.dot.ca.gov/}}
}



## Acknowledgments


Prof. Kateřina Schindlerová, University of Vienna

AmeriFlux Network for open meteorological data

Caltrans PeMS for traffic telemetry access

Brutsaert (1982) and Kerner (2004) for foundational ground truth


