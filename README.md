# Are fast test results preferable to high test sensitivity in contact-tracing strategies?

This repository contains the source code for the research paper *"Are fast test results preferable to high test sensitivity in contact-tracing strategies?"* by Jonas L. Juul and Morten R. Boilesen from IT University of Copenhagen and Kaare Græsbøll from the Department of Data Science and AI in Health, Statens Serum Institut.

## Abstract

When an epidemic is spreading in a population,
mitigation measures often rely on testing individuals, tracing possible secondary infections, and isolating known or suspected infected individuals. 
Because more accurate tests often take longer to analyse, and the benefits of contact tracing are strengthened by rapid diagnosis, there exists a trade-off in test sensitivity and test waiting time in test-trace-isolate strategies.
Here we ask: How many false negatives can be tolerated in a rapid test so that it reduces transmission better than a slower, more accurate test?
How does this change with contact tracing efficiency and test waiting time?
We examine these questions using a mathematical branching-process model with adjustable contact tracing efficiency, test turnaround times, test sensitivity, and disease infectiousness profile. 
For a disease with infectiousness profile similar to that of COVID-19, we find that highly-accurate tests with turnaround times less than 6 days result in greater transmission reduction than less-accurate rapid tests for most parameter choices.
If contact tracing is highly effective, however, fast and less reliable test results can be preferable to slower and more accurate tests. 
Furthermore, we find that if the sensitivity of the rapid test is not static, but correlates with the time-dependent viral load of patients, the rapid test is more often preferable to the slower more accurate test. We support our numerical contributions with analytical results that support the findings and clarify the trade-offs between the key parameters in our model: test sensitivity, turnaround time, and contact tracing efficiency. We analytically demonstrate that, under our model, a rapid test with zero turnaround time never exceeds a test with perfect sensitivity but non-zero turnaround time in the absence of contact tracing.
Our analysis suggests employing rapid tests to reduce test turnaround times as a viable strategy to reduce transmission when testing infrastructure is under severe stress.


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
   - Options: `"empirical"`, `"FlatSkewed"`'
     
- **main.jl**: Implements simulations with **constant test sensitivity (baseline assumption)** 

- **main_Se.jl**: Implements simulations with **viral load-dependent test sensitivity (Section IIIA)** 

## Output Files

- Simulation results are saved in `code/outputs/`
- Offspring distribution data is stored in `code/offspringdistributions/`

## Figures

Use the provided Python and Jupyter notebook tools for data analysis and visualization:

- `code/plot_definitions.py`: useful definitions
- `code/Plot_main.ipynb`: Jupyter notebook displaying the figures from the paper


