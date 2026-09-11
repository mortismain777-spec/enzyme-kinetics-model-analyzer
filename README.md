# enzyme-kinetics-model-analyzer
Python tool for fitting enzyme inhibition models, comparing model performance, and evaluating parameter robustness through Monte Carlo simulation.

## Features
- Michaelis-Menten model fitting
- Competitive, noncompetitive and uncompetitive inhibition models
- Model comparison using MSE, AIC and BIC
- Monte Carlo robustness analysis
- Publication-quality visualizations

## Technologies
Python, NumPy, Pandas, SciPy and Matplotlib

## Data
The repository includes a demonstration dataset with substrate
concentrations, inhibitor concentrations and triplicate velocity measurements.

## Running the project
1. Install the required packages:
   pip install -r requirements.txt
2. Open and run `enzyme_kinetics_analysis.ipynb` in Google Colab or Jupyter Notebook.

## Example results

The demonstration dataset was best described by the noncompetitive
inhibition model according to BIC.

Estimated parameters:

- Vmax: 54.58
- Km: 2.06
- Ki: 1.91

![Model fit](results/model_fit.png)

## Limitations
Model selection identifies the best-supported model among the candidates
evaluated, but does not independently establish the biological inhibition
mechanism.
