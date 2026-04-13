# Modeling Urban Traffic Flow Using NYC Taxi Data

This project models the relationship between traffic density and vehicle speed using NYC taxi data. Inspired by classical traffic flow theory, I analyze how increasing demand affects system efficiency and identify a critical density threshold where traffic flow is maximized.

<p align="center">
  <img src="https://github.com/lukaszamora/Traffic-Flow-Modeling/blob/main/2%20-%20plot.png" alt=""/>
</p>

## Objectives

- Model the relationship between density and speed  
- Compare linear and nonlinear traffic models  
- Compute traffic flow as a function of density  
- Identify the critical density where throughput peaks  

## Dataset

- [NYC Yellow Taxi Trip Data](https://www.kaggle.com/datasets/marcbrandner/tlc-trip-record-data-yellow-taxi?resource=download&select=yellow_tripdata_2022-08.parquet)  
- Timeframe: August to October 2022  

## Data Preparation

- Aggregated trips by hour  
- Computed:
  - average trip distance  
  - average trip duration  
- Estimated speed as distance divided by duration  
- Defined density as hourly trip count  

Note: Density is a normalized trip-density proxy rather than a direct measure of physical road occupancy.

## Traffic Modeling

### Speed-Density Relationship

Observed data shows that speed decreases as density increases, indicating congestion effects.

### Linear Model

A classical linear model was tested:

$$ v(\rho) = v_{max} (1 - \rho). $$

This model did not align well with observed data, suggesting that the relationship is nonlinear.

### Nonlinear Model (Underwood)

An exponential model was fitted:

$$ v(\rho) = v_f * e^{-k\rho}. $$ 

This model better captured the asymptotic decline in speed as density increased.

## Flow Modeling

Traffic flow is defined as:

$$ q(\rho) = \rho · v(\rho). $$

Using the fitted nonlinear model, flow was computed across density values.

## Key Result

- Critical density ≈ 0.36  
- Maximum flow ≈ 16.87  

Flow increases with density up to this threshold, then declines as congestion reduces system efficiency.

## Key Findings

- Speed decreases nonlinearly with increasing density  
- Linear models do not adequately capture real-world traffic behavior  
- Nonlinear modeling provides a better fit to observed data  
- Traffic systems exhibit a critical threshold beyond which efficiency declines  
- Increasing demand does not always increase throughput  

## Tools Used

- Python  
- Pandas  
- NumPy  
- Matplotlib  
- SciPy  

## Summary

This project demonstrates how differential-equation-inspired models can be applied to real-world data to understand complex system behavior. The results highlight the nonlinear dynamics of urban traffic and the existence of an optimal operating range for system efficiency.
