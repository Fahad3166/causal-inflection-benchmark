Two datasets with 500+ observations each where the causal direction between variables flips based on threshold values. Features surface energy balance (soil heat flux vs. net radiation) and traffic dynamics (speed vs. density) with ground truth from Brutsaert (1982) and Kerner (2004).

# Causal Inflection Benchmark: Value-Dependent Causal Reversal

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Data: AmeriFlux](https://img.shields.io/badge/Data-AmeriFlux-green.svg)](https://ameriflux.lbl.gov/)
[![Data: PeMS](https://img.shields.io/badge/Data-PeMS-orange.svg)](https://pems.dot.ca.gov/)

## Overview

This repository contains two benchmark datasets for **value-dependent causal reversal** — a phenomenon where the causal direction between two variables flips based on the value of one variable. Each dataset includes 500+ observations with known ground truth from peer-reviewed literature.

### The Causal Reversal Problem

Standard causal discovery assumes a fixed direction (`X → Y` or `Y → X`). However, many real-world systems exhibit **regime-dependent causality**:

| Dataset | Low/Free Regime | High/Congested Regime | Switching Point |
|:--------|:----------------|:----------------------|:----------------|
| **Soil Heat Flux** | `X → Y` (Daytime) | `Y → X` (Nighttime) | X = 10 to -40 W/m² |
| **Traffic Dynamics** | `X → Y` (Free flow) | `Y → X` (Congested) | Y = 25 veh/km |

## Datasets

### Dataset 1: Surface Energy Balance

| Property | Value |
|:---------|:------|
| **X (Cause)** | Net Radiative Flux (W/m²) |
| **Y (Effect)** | Soil Heat Flux (W/m²) |
| **Sample Size** | 500 observations |
| **Ground Truth** | Brutsaert (1982) |
| **Source** | AmeriFlux Network |

**Causal Regimes:**
- **Daytime (X > 10 W/m²):** `X → Y` — Solar radiation drives downward heat flux
- **Nighttime (X ≤ -40 W/m²):** `Y → X` — Subsurface heat conducts upward to cooling surface

### Dataset 2: Traffic Dynamics

| Property | Value |
|:---------|:------|
| **X (Cause)** | Average Vehicle Speed (km/h) |
| **Y (Effect)** | Traffic Density (veh/km) |
| **Sample Size** | 500 observations |
| **Ground Truth** | Kerner (2004) |
| **Source** | Caltrans PeMS |

**Causal Regimes:**
- **Free Flow (Y ≤ 25 veh/km):** `X → Y` — Driver speed choices determine density
- **Congested (Y > 25 veh/km):** `Y → X` — Physical density constraints force speed reduction

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

Create Conda -n c_challenge envoirment 


conda install numpy pandas matplotlib scipy

Ground Truth Citations
Dataset 1
Brutsaert, W. (1982). Evaporation into the Atmosphere: Theory, History, and Applications. Springer.
DOI: 10.1007/978-94-017-1497-6

Dataset 2
Kerner, B. S. (2004). The Physics of Traffic: Empirical Phenomena of Chaotic Mobile Systems. Springer.
DOI: 10.1007/978-3-540-40986-1

Data Sources
Dataset	Source	Link
Soil Heat Flux	AmeriFlux Network	ameriflux.lbl.gov
Traffic Dynamics	Caltrans PeMS	pems.dot.ca.gov
Key Findings
Causal direction is not always fixed — It can depend on the value of a conditioning variable

Physical thresholds matter — At X > 10 W/m², net radiation drives soil heat; at X ≤ -40 W/m², the relationship reverses

Infrastructure exhibits regime switching — Traffic shows opposite causal structures below and above 25 veh/km

Applications
This benchmark can be used for:

Testing causal discovery algorithms on regime-switching data

Evaluating threshold detection methods

Developing conditional causal inference models

Educational demonstrations of non-stationary causality

License
MIT License — feel free to use, modify, and distribute with attribution.

Author


FAHAD ALI


Project submitted as part of Causal Inference for Temporal and Non-Temporal Data, University of Vienna, Summer 2026.

Citation


If you use this dataset in your research, please cite:

bibtex
@misc{causal-inflection-benchmark-2026,
  author = {ALI, FAHAD},
  title = {Causal Inflection Benchmark: Value-Dependent Causal Reversal},
  year = {2026},
  publisher = {GitHub},
  url = {https://github.com/Fahad3166/causal-inflection-benchmark}
}

License
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



Acknowledgments


Prof. Kateřina Schindlerová, University of Vienna

AmeriFlux Network for open meteorological data

Caltrans PeMS for traffic telemetry access

Brutsaert (1982) and Kerner (2004) for foundational ground truth


