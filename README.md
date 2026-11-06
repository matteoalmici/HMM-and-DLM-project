# Modelling PM2.5 in the US West: HMM and Dynamic Linear Models

Group project for the Time Series course (Bocconi University, MSc in Economic and Social Sciences). We model hourly PM2.5 concentrations from EPA monitoring stations in the western US during summer 2020, to understand pollution dynamics and to test how well state-space models can filter and forecast them.

**Report:** [Final_project_ts_group_15.pdf](Final_project_ts_group_15.pdf) | **Code:** [Final_project_ts_group_15.Rmd](Final_project_ts_group_15.Rmd)

## What we did

1. **Hidden Markov Models** (R, `depmixS4`) on hourly PM2.5 and on its 24-hour moving average, with 2 and 3 states. The states identify pollution regimes (a low-level, low-variance state and a higher, more volatile one, which shows up from late August) and their persistence through the transition matrices. Standard errors and confidence intervals are reported for the parameters.
2. **State decoding** to see when the process switches regime.
3. **Dynamic Linear Models** (R, `dlm`) for filtering and online forecasting of the underlying pollution level, with maximum likelihood estimation.
4. **Spatial DLM** for four stations (41, 47, 96, 99), using the distances between stations to model spatial dependence.
5. **Model comparison** based on forecast accuracy (MAPE).

## Main takeaways

- The HMM is useful for a first, intuitive reading of pollution levels and how unstable they are.
- DLMs are accurate for nowcasting and noise reduction (low MAPE), but lose reliability for multi-step-ahead forecasts. Adding external regressors (e.g. climate, demography, energy and transport variables) is a natural next step.

## Reproducing the results

The Rmd reads a CSV of EPA hourly data (`ts_epa_2020_west_sept_fill.csv`), which is not included in this repository. Set the path at the top of the Rmd before knitting. Main R packages: `depmixS4`, `dlm`, `forecast`, `astsa`, `imputeTS`, `tidyverse`, `sf`.

## Author

Matteo Almici, with classmates from group 15. [LinkedIn](https://www.linkedin.com/in/matteo-almici-matt2001/)
