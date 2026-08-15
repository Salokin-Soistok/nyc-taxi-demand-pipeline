# NYC Taxi Demand Data Pipeline

A Python data engineering and analytics project that cleans, transforms,
integrates and analyses NYC Yellow Taxi trip data using Pandas, DuckDB
and SQL.

The project focuses on identifying taxi demand patterns across pickup
zones, boroughs and different periods of the day.

## Technologies

- Python
- Pandas
- NumPy
- DuckDB
- SQL
- Matplotlib
- Jupyter Notebook

## Project Overview

The project processes NYC Yellow Taxi trip data and a taxi-zone lookup
dataset to analyse demand across New York City.

The original taxi dataset contained approximately 3.7 million trip
records. A reduced set of relevant variables was selected before
cleaning and analysis.

The workflow includes:

- Data profiling
- Data minimisation
- Duplicate detection and removal
- Timestamp validation
- Invalid-distance and fare filtering
- Missing-value handling
- Feature engineering
- Dataset integration
- SQL-based analysis with DuckDB
- Data visualisation

## Data Cleaning

Several data-quality issues were identified and addressed during the
pipeline.

Examples include:

- 539 duplicate taxi records removed
- Invalid and inconsistent timestamp records removed
- Impossible or unreliable trip-distance records filtered
- Negative fare records removed
- Invalid passenger-count values handled
- Missing taxi-zone labels replaced with `Unknown`

After cleaning, the taxi dataset contained approximately 3.56 million
trip records.

## Feature Engineering

New variables were created to support analysis, including:

- `pickup_hour`
- `pickup_date`
- `day_of_week`
- `time_period`
- `trip_duration_minutes`
- Trip-distance categories

Trips were grouped into:

- Peak
- Off-peak
- Late-night

## Dataset Integration

The cleaned taxi-trip data was joined with the NYC Taxi Zone lookup
dataset using pickup and drop-off location IDs.

This added geographic information such as:

- Pickup borough
- Pickup zone
- Pickup service zone
- Drop-off borough
- Drop-off zone
- Drop-off service zone

The resulting integrated dataset contained approximately 3.56 million
rows and 20 columns.

## SQL Analysis

DuckDB was used to query the processed dataset.

The analysis examined:

- Taxi demand by time period
- Highest-demand pickup zones
- Demand by borough and time period
- Highest-demand late-night pickup zones

### Demand by Time Period

| Time Period | Trips |
|---|---:|
| Off-peak | 2,151,252 |
| Peak | 1,074,477 |
| Late-night | 335,065 |

## Example Finding

East Village recorded the highest late-night pickup demand in the
analysis with 27,593 trips.

Other high-demand late-night zones included:

- West Village
- Lower East Side
- Greenwich Village South
- JFK Airport

## Visualisations

The notebook includes visualisations comparing:

- Trip volumes across peak, off-peak and late-night periods
- Top pickup zones
- Borough demand across time periods

## Known Limitation

One visualisation cell uses the variable `time_period_demand`, which was
retained in the original notebook runtime but is not explicitly assigned
in the saved notebook before that chart is executed.

As a result, that specific chart may require rerunning the preceding SQL
query and assigning its output to `time_period_demand` when running the
notebook from a completely fresh environment.

This does not affect the core ETL pipeline, data cleaning, feature
engineering, dataset integration or SQL analysis demonstrated in the
project.

## Dataset

The project uses NYC Yellow Taxi trip records and the NYC Taxi Zone
lookup dataset.

Large raw datasets are not included directly in this repository.

## Repository Structure

- `nyc_taxi_demand_pipeline.ipynb` — data cleaning, transformation,
  integration, SQL analysis and visualisation
- `README.md` — project documentation

## Academic Context

This project was originally developed as part of university coursework
and is presented here as a technical portfolio project.

## Author

Nikolas Kotsios  
Computer Science Student
