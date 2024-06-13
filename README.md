# Bandit Algorithms for Stationary and Non-Stationary Environments
## FOR REINFORCEMENT LEARNING ASSIGNMENT ONE
### By Adejoke Adeoye and Cephas Acquah Forson
-----------------------------------------------------------------------------------------
## Overview
This repository contains implementations of various multi-armed bandit algorithms and experiments designed to compare their performance in both stationary and non-stationary environments.

## Algorithms Implemented
1. **Greedy with Non-Optimistic Initial Values** algorithm initializes the action value estimates to 0 and selects the action with the highest estimated value at each step. It uses an incremental implementation of the simple average method to update the estimates.

2. **Epsilon-Greedy with Fixed Step Size** algorithm selects a random action with probability ϵ and the best-known action with probability 1−ϵ. The action value estimates are updated with a fixed step size.

3. **Optimistic Initial Values with Greedy Approach** algorithm starts with optimistic initial values for the action value estimates to encourage exploration. It then selects the action with the highest estimated value greedily at each step.

4. **Gradient Bandit Algorithm with Variable Alpha** algorithm maintains preference values for each action and uses a softmax function to select actions. The preference values are updated based on a learning rate αα, which is varied to find the optimal performance.


## Part 1: Stationary Environment
1. **Stationary Setup**: We initialized a 10-armed bandit with normally distributed rewards. We generate 10 means, μi (for i =1, …, 10), from a normal distribution N(0,1) for each of 1000 bandit problems
2. **Optimal Hyperparameters**: We Identified the best alpha for the Gradient Bandit to be 0.2 and the best epsilon for the Epsilon-Greedy algorithm to be 0.02 using average rewards.
3. **Algorithms Comparison**: We evaluate the performance of all four algorithms using the identified best hyperparameters.

## Part 2: Non-Stationary Environment
1. **Non-Stationary Setup**: We implement gradual drift of 0.001 random drift, mean-reverting changes of 0.01 about the 0.5 mean, and abrupt changes in the reward distributions.
2. **Algorithms  Comparison**: We evaluate the performance of the algorithms in non-stationary environments, focusing on the distribution of average rewards after a large number of steps (20,000).

## Repository Structure
- `DSCI_6650_RL_ASS_ONE_ADEJOKE_FORSON.ipynb`: Contains the the complete code in a notebook format.

## Instructions for Running the Code
Ensure you have Python 3.x and install the required libraries using:
```sh
pip install numpy matplotlib seaborn
```
Open the notebook in code editor and run all chunks.


## Results and Analysis
The experiments generate plots and box plots that visualize:
1. The average reward over time for different values of alpha and epsilon.
2. The comparison of average rewards for Greedy, Epsilon-Greedy, Optimistic Greedy, and Gradient Bandit algorithms in both stationary and non-stationary environments.
3. And the distribution of rewards in non-stationary environments, highlighting the adaptability of each algorithm to different rates of change.

## Summary Analysis of Non-Stationary Environments
We compare the performance of three bandit algorithms under different rates of change:
1. **Optimistic Greedy**
2. **Epsilon-Greedy with Fixed Step Size**
3. **Epsilon-Greedy with Decreasing Step Size (Simple Average Estimator)**

### Gradual Drift Changes
- **Optimistic Greedy** exhibits high variability in rewards, with a wider spread compared to the epsilon-greedy algorithms. The optimistic initial values help in exploration early on but may not adapt well to the gradual drift.
- **Epsilon-Greedy with Fixed Step Size** shows a more stable distribution of rewards, indicating better adaptation to gradual changes. The fixed exploration rate helps maintain a balance between exploration and exploitation.
- **Epsilon-Greedy with Decreasing Step Size** performs similarly to the fixed step size variant but with slightly higher variability. The decreasing exploration rate can lead to less adaptation over time.

### Mean-Reverting Changes
- **Optimistic Greedy** shows high variability and a wider spread of rewards. It struggles to maintain performance as the environment reverts to the mean.
- **Epsilon-Greedy with Fixed Step Size** demonstrates a more concentrated reward distribution, suggesting effective adaptation to mean-reverting changes.
- **Epsilon-Greedy with Decreasing Step Size** shows a higher spread in rewards compared to the fixed step size variant, indicating some difficulty in adapting to mean-reverting changes as exploration decreases over time.

### Abrupt Changes
- **Optimistic Greedy** experiences the highest variability in rewards among the three algorithms. The sudden changes in the environment pose significant challenges.
- **Epsilon-Greedy with Fixed Step Size** exhibits better stability in reward distribution. The constant exploration helps the algorithm to quickly adapt to abrupt changes.
- **Epsilon-Greedy with Decreasing Step Size** shows similar performance to the fixed step size variant but with slightly more variability.

## Conclusion
The **Epsilon-Greedy with Fixed Step Size** algorithm demonstrates the most stable and favorable performance across different non-stationary conditions, making it the preferable choice for environments where adaptability is crucial.

________________________________________________________________________________________________________________________________
