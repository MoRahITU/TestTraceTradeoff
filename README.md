# Test-Trace Tradeoff: Contact Tracing Strategies Analysis

This repository contains the source code for the research paper *"Are fast test results preferable to high test sensitivity in contact-tracing strategies?"* by Jonas L. Juul and Morten R. Boilesen from IT University of Copenhagen and , Kaare Græsbøll from the Department of Data Science and AI in Health, Statens Serum Institut.

## Overview

This project investigates the tradeoffs between test speed and test sensitivity in contact tracing strategies for epidemic control. The code implements epidemiological simulations to evaluate different testing scenarios and their effectiveness in controlling disease spread.


## Key Differences Between main.jl and main_Se.jl

- **main.jl**: Implements simulations with **constant test sensitivity** - the probability of detecting infection remains fixed regardless of viral load or disease stage.

- **main_Se.jl**: Implements simulations with **viral load-dependent test sensitivity** - the test sensitivity varies as a function of viral load, providing a more realistic representation of how diagnostic tests perform throughout the course of infection.

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

- Simulation results are saved in `code/outputsFinal/` with descriptive filenames including all parameter values
- Output files contain columns for false negative test rates, tracing efficiency, infection counts, reproduction numbers, and other epidemiological metrics
- Offspring distribution data is stored in `code/offspringdistributions/`

## Visualization

Use the provided Python and Jupyter notebook tools for data analysis and visualization:

- `code/plot_definitions.py`: Python plotting utilities
- `code/Plot_main.ipynb`: Interactive Jupyter notebook for result visualization

## License

Please refer to the publication and contact the authors for usage rights and licensing information.