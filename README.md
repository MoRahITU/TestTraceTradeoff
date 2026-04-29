# Test-Trace Tradeoff: Contact Tracing Strategies Analysis

This repository contains the source code for the research paper *"Are fast test results preferable to high test sensitivity in contact-tracing strategies?"* by Jonas L. Juul and Morten R. Boilesen from IT University of Copenhagen and Kaare Græsbøll from the Department of Data Science and AI in Health, Statens Serum Institut.

## Overview

This project investigates the tradeoffs between test speed and test sensitivity in contact tracing strategies for epidemic control. The code implements epidemiological simulations to evaluate different testing scenarios and their effectiveness in controlling disease spread.

- **main.jl**: Implements simulations with **constant test sensitivity (baseline assumption)** 

- **main_Se.jl**: Implements simulations with **viral load-dependent test sensitivity (Section IIIA)** 

## Usage

Run the Julia simulation with the following command:

```bash
# Run the Julia script (Argument order: testwait, resultwait, Pasymp, R0, OffspringDistribution, InfectiousProfile)
julia code/main.jl 0.0 0.0 0.3 2.0 "negativebinomial" "empirical"
```

### Command Line Arguments

The simulation scripts accept the following arguments in order:

1. **testwait**: Number of days before test is taken
2. **resultwait**: Number of days before test result arrives after test is taken  
3. **Pasymp**: Fraction of infected individuals who remain asymptomatic (e.g., 0.3 = 30%)
4. **R0**: Basic reproduction number (mean number of secondary infections)
5. **OffspringDistribution**: Distribution type for offspring generation
   - Options: `"poisson"`, `"negativebinomial"`, `"geometric"`
6. **InfectiousProfile**: Infectious profile model
   - Options: `"empirical"`, `"FlatSkewed"`

## Output Files

- Simulation results are saved in `code/outputsFinal/`
- Offspring distribution data is stored in `code/offspringdistributions/`

## Visualization

Use the provided Python and Jupyter notebook tools for data analysis and visualization:

- `code/plot_definitions.py`: useful definitions
- `code/Plot_main.ipynb`: Jupyter notebook displaying the figures from the paper

## License

Please refer to the publication and contact the authors for usage rights and licensing information.
