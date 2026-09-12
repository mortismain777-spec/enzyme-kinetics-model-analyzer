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

## Using your own data

1. Replace `data/Datos_experimento.csv` with your own CSV file.

2. Keep the same filename, or change `FILE_NAME` in the notebook
   to match the path and name of your file.

3. The CSV must contain these columns:

   - `S`: substrate concentration.
   - `rep1`, `rep2`, `rep3`: three reaction velocity measurements.
   - `I`: inhibitor concentration. Use zero only when no inhibitor
     is present.

4. Use consistent units throughout the dataset.

5. Adjust the simulation settings in the notebook if needed:

   - `SIGMA_MAX`: maximum standard deviation of the added noise,
     in the same units as reaction velocity.
   - `N_MONTE_CARLO`: number of simulations per noise level.
   - `RANDOM_SEED`: seed used for reproducibility.

6. Run the notebook from beginning to end.

7. Generated tables and figures are saved in `results/`.
   Files with the same names are overwritten when the analysis is run again.

### Google Colab

Opening the notebook from GitHub does not automatically download
the CSV. Upload your CSV into a folder named `data`, or change
`FILE_NAME` to its uploaded location.

## Example results

Using the included demonstration dataset, the noncompetitive inhibition
model obtained the lowest BIC among the evaluated models.

| Model | MSE | AIC | BIC |
|---|---:|---:|---:|
| Noncompetitive | 0.1706 | -9.9157 | -9.3240 |
| Competitive | 0.2333 | -7.0991 | -6.5074 |
| Uncompetitive | 0.3477 | -3.5073 | -2.9157 |
| No inhibitor | 6.9225 | 21.4130 | 21.8074 |

Estimated parameters for the selected model:

- Vmax = 54.58
- Km = 2.06
- Ki = 1.91

### Model fit

![Enzyme kinetics model fit](results/model_fit.png)

### Substrate and inhibitor map

![Substrate and inhibitor map](results/substrate_inhibitor_map.png)

### Monte Carlo parameter stability

![Monte Carlo parameter stability](results/monte_carlo_stability.png)

### Monte Carlo distributions

![Monte Carlo histograms](results/monte_carlo_histograms.png)

### Result files

- [Model comparison table](results/model_comparison.csv)
- [Monte Carlo simulation results](results/monte_carlo_results.csv)

## Limitations
Model selection identifies the best-supported model among the candidates
evaluated, but does not independently establish the biological inhibition
mechanism.
