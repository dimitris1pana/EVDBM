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
- **`energYproductionEVA2CompareScenarios.ipynb`**: Notebook comparing two different use cases under extreme event conditions.
- **Data Files**: Please ensure the necessary data files (time series of relevant variables) are available in the same directory as the notebooks.

## Dependencies

To run these notebooks, the following Python libraries are required:

- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `scipy`
- `scikit-learn`
- `pyEVA` (optional, for Extreme Value Analysis)

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
$$ B_{\text{total}} = S_{\text{count}} \times \sum_{i=1}^{n} w_i \times \Delta C_{\text{low}}^{\text{norm}}(V_i) $$

- $$\( S_{\text{count}} \)$$: Scaling factor for the count of extreme observations.
- $$\( w_i \)$$: Weight assigned to each variable $$\( V_i \)$$.
- $$\( \Delta C_{\text{low}}^{\text{norm}}(V_i) \)$$: Normalized difference in variable $$\( V_i \)$$ between two scenarios.

- **Single Scenario Analysis**: The EVA results highlight which variables are most correlated with extreme events and provide insights into the factors influencing system performance under extreme conditions.
- **Scenario Comparison**: The comparison provides a benchmarking score that indicates which scenario performs better under extreme conditions and offers insights into the variables that are most influential.

The results can be used to guide operational decisions, risk management strategies, or further analyses based on extreme event occurrences in various domains.

## Contributing

Contributions to this repository are welcome. Feel free to fork the project and submit a pull request with any additional features or improvements.

## License

This project is licensed under the MIT License. Please see the LICENSE file for more details.