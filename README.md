# Bayesian Statistical Modelling of Water Polo Euro 1999

**Course Project – Bayesian Statistics**  
**MSc in Applied Statistics – Athens University of Economics and Business (AUEB)**  
**Author:** Gerasimos Chatzopoulos

## Overview

This project applies Bayesian modeling to match data from the 1999 European Water Polo Championship. The dataset includes 44 matches played between 12 European national teams. The primary goal is to estimate team strengths, predict match outcomes, and simulate a full league using probabilistic models.

## Objectives

- Estimate attacking and defensive abilities for each team
- Predict win/draw/loss probabilities for selected matches
- Simulate a full league and generate team ranking distributions
- Evaluate model performance using information criteria (e.g. DIC)
- Compare fixed and random effects modeling approaches

## Data Summary

| Variable     | Description                      |
|--------------|----------------------------------|
| `ht`, `at`   | Home and away team indices       |
| `goals1`, `goals2` | Goals scored by each team |
| `K`          | Number of teams (12)             |
| `n`          | Number of matches (44)           |
| `a[k]`, `d[k]` | Attack and defense parameters |

## Modeling Approach

The main framework used is a **Poisson log-linear model** for goal counts, incorporating:

- A global intercept (`μ`)
- Team-specific **attack (`a[k]`)** and **defense (`d[k]`)** parameters
- Sum-to-zero constraints for identifiability

A **Negative Binomial model** was also tested to account for overdispersion, but the **Poisson model outperformed it** based on DIC values.

### Random Effects Analysis

To improve model flexibility, several extensions were evaluated:

- **Fixed Effects**: Treat each match or phase as a fixed categorical variable
- **Random Effects**: Add random intercepts for matches, and phases
- **Random Game Effects** produced the **best model fit**, indicating unobserved game-level variation was important in explaining goal outcomes

## Prediction and Simulation

The model was used to predict outcomes of key semifinal and final matches. Simulated match results closely matched actual outcomes without including those games in the training data.

A **league simulation** was also performed, where all teams played each other twice. The simulation generated:

- Expected points per team
- Average finishing position
- Probability distributions over all ranking positions

The simulated rankings aligned closely with actual tournament results, with the top 4 teams exactly matching in both.

## Conclusion

Bayesian Poisson modeling successfully captured the dynamics of the 1999 European Water Polo Championship. The inclusion of random effects significantly improved model performance. The model produced accurate match predictions and realistic league simulations, demonstrating the value of hierarchical Bayesian models in sports analytics.

---
