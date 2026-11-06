# industrial-heat-pypsa
Noah Zuijderwijk
Modelling for Transitions, University of Amsterdam
 October 2026

This repository contains a PyPSA model of the Dutch energy system, used to explore how heat pump investment subsidies and carbon pricing influence industrial heat electrification and decarbonisation between 2020 and 2050. The model builds on an earlier group assignment with Rosa Muilu, Sabrina Liu and Sabine Whittman. That project examined the transition from steam methane reforming (SMR) to water electrolysis for hydrogen production under different assumptions about gas prices, electrolyser capital costs and carbon prices. In this individual extension, I represent industrial heat demand in greater detail by splitting the original high-temperature demand category into two segments: high-temperature processes, such as steelmaking, and low-to-medium-temperature processes, such as food processing. I then use scenario analysis to examine how heat pump investment subsidies and carbon pricing affect technology investment and the supply of industrial heat.

## Repo structure
## Repository structure

```text
Individual/
├── FinalModel/
│   ├── energy_model/
│   ├── input_databases/
│   │   └── default/
│   ├── results/
│   │   ├── temporal_scenarios/
│   │   ├── visualisations/
│   │   └── solver_run.log
│   ├── interface.ipynb
│   └── visualisations.ipynb
├── OLD/
│   └── P06/
├── Final_report.pdf
├── group-mt-env.yml
└── README.md
```

The interface notebook is where you can run the model. Model run outputs are stored in Individual/FinalModel/results/temporal_scenarios/

## Model structure

The final report, containing model assumptions, limitations, and main takeaways is included as "Final_report.pdf". This si also where you can find the model topology, and information about the model implementation. For further information on PyPSA, see https://docs.pypsa.org/latest/

## Setup

```bash
conda env create -f group-mt-env.yml
conda activate group-mt-env
```

## Usage

Everything is in `FinalModel/`:

- `interface.ipynb` runs the scenarios and saves them to `results/` as `.nc` files
- `visualisations.ipynb` makes data visualizations

The model code is in `energy_model/` and the input data (demand, supply, technologies) is in `input_databases/`.

## Scenarios

| Scenario family | Heat pump CAPEX multiplier | Heat pump efficiency multiplier | Carbon price multiplier |
|:----------------|:---------------------------|:--------------------------------|:------------------------|
| Baseline | 1 | 1 | 1 |
| Heat pump scenarios | 1, 0.93, 0.87, 0.80 | 1, 1.04, 1.08, 1.12 | 1 |
| Carbon pricing scenarios | 1 | 1 | 1, 4, 8, 12 |
| Combined scenarios | 1, 0.93, 0.87, 0.80 | 1, 1.04, 1.08, 1.12 | 1, 4, 8, 12 |

All multipliers are relative to the baseline assumptions. A multiplier of 1
leaves the corresponding parameter unchanged. CAPEX refers to the investment
cost of large-scale heat pumps.
