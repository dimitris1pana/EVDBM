# Extreme Value Analysis and Scenario Comparison

This repository contains notebooks that apply **Extreme Value Analysis (EVA)** to assess and compare the performance of different systems under extreme conditions. The analysis provides insights into how various environmental or operational factors influence extreme events and uses a benchmarking methodology to compare different use cases or scenarios.

## Table of Contents

- [Overview](#overview)
- [Files](#files)
- [Dependencies](#dependencies)
- [Usage](#usage)
- [Methodology](#methodology)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Overview

The analysis conducted in these notebooks focuses on the identification of **extreme events** and the comparison of **different scenarios** or **use cases** under extreme conditions. The analysis can be applied to any domain or dataset where extreme value analysis and scenario comparisons are important (e.g., weather events, operational risk analysis, financial risk, etc.).

1. **`energyProductionEVA.ipynb`**: This notebook performs **Extreme Value Analysis (EVA)** on time-series data to identify extreme events based on Peaks Over Threshold (POT) and compare how environmental or operational variables correlate with those events.

2. **`energYproductionEVA2CompareScenarios.ipynb`**: This notebook compares two **scenarios** or **use cases** under extreme conditions using a benchmarking methodology that normalizes and weights variables to account for different units and significance levels.

## Files

- **`energyProductionEVA.ipynb`**: Notebook performing EVA on a single use case.
- **`energYproductionEVA2CompareScenarios.ipynb`**: Notebook for the Extreme Value Dynamic Benchmarking Method (EVDM) incorporating the Dynamic Identification of Significant Correlation (DISC) - thresholding algortihm. The purpose of this is the extraction of insights from the EVA results and and scoring each use case.
- **`energYproductionEVA2CompareScenariosGridSearch.ipynb**: Implements the EVDBM framework. This notebook:
	-	Integrates EVA with the DISC-Thresholding algorithm for enhanced interpretability.
	-	Uses a grid search approach to optimize weight shifting among related variables, thereby fine-tuning the benchmarking scores.
	-	Demonstrates significant improvements in  R^2  (an increase of 13.21%) compared to standard EVA.
	-	Provides a detailed comparison of scenarios (e.g., different PV farms) while maintaining transparency in variable importance.
- **Data Files**: Please ensure the necessary data files (time series of relevant variables) are available in the same directory as the notebooks.

## Dependencies

To run these notebooks, the following Python libraries are required:

- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `scipy`
- `scikit-learn`
- `pyextremes` (for Extreme Value Analysis)

Install the dependencies via `pip`:

pip install numpy pandas matplotlib seaborn scipy scikit-learn

## Usage

1. **Clone the repository**:

   git clone https://github.com/dimitris1pana/EVDBM.git

   ## Methodology

The analysis follows a structured approach using **Extreme Value Analysis (EVA)** and **Scenario Comparison**:

1. **Extreme Value Identification**: Using the Peaks Over Threshold (POT) method, extreme events are identified within the time-series data. These events are then analyzed to understand their correlation with various explanatory variables (e.g., environmental or operational factors).

2. **Scenario Comparison**: The second notebook compares two different scenarios or use cases by applying a **benchmarking methodology**:
   - Each variable is **normalized** (Min-Max normalization) to account for differences in units (e.g., temperature in °C, pressure in Pa, etc.).
   - Variables are **weighted** based on their relative importance to the system's performance under extreme conditions.
   - A **scaling factor** is introduced to account for the number of extreme observations in each scenario.

3. **Weights and Normalization**:
   - Variables are weighted to reflect their influence on the system’s performance under extreme conditions.
   - Min-Max normalization is used to bring all variables to a common scale for meaningful comparisons.

4. **Benchmarking Formula**:
   The following formula is applied to compare scenarios:

## Results
$$ B_{\text{i}} = S_j\times\sum_{i=1}^{n} b(V_i) $$

- $$\ b(V_i) =  w_i \times{C_\text{extreme}}(V_i)$$: Scaling factor for the count of extreme observations.
- $$\ ( w_i ) $$ : Weight assigned to each variable $$\ ( V_i ) $$.
- $$\ S_j = E_c \times P(X>x) $$: Accounting for historical occurrences and the associated probabilities with a final scaling factor
- $$\ E_c = \frac{N}{\sum_{k=1}^{m} N_k} $$: frequency and intensity of extreme events by normalizing the number of extreme events
   - N  is the number of extreme events for a case (c)
   - $$\ \sum_{k=1}^{m} N_k $$ is the total number of extreme events across all cases
- Empirical calculation of R^2:
   -  $$\ R^2 = 1 - \frac{\text{SS}{\text{residual}}}{\text{SS}{\text{total}}} $$
   where: 
      - $$\ \text{SS}{\text{residual}} = \sum_{i=1}^{n} \left( y_i - \hat{y}_i \right)^2 $$
      - $$\ \text{SS}{\text{total}} = \sum_{i=1}^{n} \left( y_i - \bar{y} \right)^2 $$
- Grid Search Weight Shifting for Optimization:
   -  $$\ \text{SumweightedCircumstances} = \sum_{i=1}^{n} (w_i \cdot V_i) $$
   where: 
      - $$\mathbf{w}^* = \arg\max_{\mathbf{w}} \left( R^2 = 1 - \frac{\text{SS}{\text{residual}}}{\text{SS}{\text{total}}} \right) $$
         - $ \mathbf{w}^*$ represents the optimal weight vector that maximizes    $R^2$

- **Single Scenario Analysis**: The EVA results highlight which variables are most correlated with extreme events and provide insights into the factors influencing system performance under extreme conditions.
- **Scenario Comparison**: The comparison provides a benchmarking score to identify which scenario performs better under extreme conditions and offers insights into the variables that are most influential.

The results can be used to guide operational decisions, risk management strategies, or further analyses based on extreme event occurrences in various domains.

## Performance Gains with EVDBM:
| **Metric** | **EVA (Baseline)** | **EVDBM (Optimized)** | **Improvement** |
|-----------|-------------------|----------------------|----------------|
| **R²**    | -4.253            | -3.691               | **+13.21%**   |
| **MAE**   | 9.691             | 9.740                | **+0.51%**    |
| **MSE**   | 115.897           | 117.110              | **+1.05%**    |

## Contributing

Contributions to this repository are welcome. Feel free to fork the project and submit a pull request with any additional features or improvements.

## License

This project is licensed under the MIT License. Please see the LICENSE file for more details.

## Citation (bibtex)
@misc{panagoulias2024integratingdynamiccorrelationshifts,
      title={Integrating Dynamic Correlation Shifts and Weighted Benchmarking in Extreme Value Analysis}, 
      author={Dimitrios P. Panagoulias and Elissaios Sarmas and Vangelis Marinakis and Maria Virvou and George A. Tsihrintzis},
      year={2024},
      eprint={2411.13608},
      archivePrefix={arXiv},
      primaryClass={stat.AP},
      url={https://arxiv.org/abs/2411.13608}, 
}
```
