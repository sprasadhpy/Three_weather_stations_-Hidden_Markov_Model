# Weather Station Data Analysis using EM Algorithm
 Coursework part of the course COMP0080: GRAPHICAL MODELS

You have the data from three weather stations (meteo1.csv) and you don’t know which data sequences come from which one. You believe that the data for each weather station follow a first-order Markov chain.

## Graphical Model

We begin by creating a graphical model to represent the relationships between the hidden states and observed weather data. The graphical model is illustrated below:

![image](https://github.com/sprasadhpy/Three_weather_stations_Hidden_Markov_Model/assets/40602129/072ca249-2982-4598-8c43-de7c79f000c7)


In this graphical model:
- The circle node labeled 'h' represents the hidden state, which indicates the weather station from which the data is generated.
- The square nodes labeled 'v1' to 'v100' represent the observed weather data sequences.
- Arrows between 'h' and 'v1' to 'v100' indicate dependencies, where the hidden state 'h' influences the observed data.

## Model Parameters

The parameters of the model are as follows:

1. **Initial State Distribution Probabilities (π)**: These probabilities represent the likelihood of starting in each of the three hidden states (weather stations).
2. **Transition Probabilities (A)**: The transition probabilities capture the likelihood of transitioning from one state to another, given the current state. This reflects the Markov property of the data.
3. **Initial State Transition Probability**: This parameter represents the likelihood of transitioning to a specific state as the initial state in the Markov model.

## Steps of the EM Algorithm

The Expectation-Maximization (EM) algorithm for this scenario involves the following steps:

1. **Initialization**:
   - Initialize the parameters of the model, including initial state distribution probabilities, transition probabilities, and initial state transition probability.

2. **E-step (Expectation)**:
   - Compute the expected values of the hidden states (which station generated the data) given the observed data and the current parameter estimates.
   - Calculate the probability or likelihood of the hidden data given the observed data and the current parameter estimates.

3. **M-step (Maximization)**:
   - Update the parameters of the model to maximize the expected log-likelihood obtained in the E-step.
   - Specifically, update the initial state distribution probabilities, transition probabilities, and initial state transition probability in the Markov model.

4. **Convergence Check**:
   - Evaluate the change in the log-likelihood or the parameters between successive iterations.
   - Check if the algorithm has converged to a stable solution.

5. **Iteration**:
   - Repeat the E-step and M-step until convergence or until a predefined stopping criterion is met.
   - Monitor the change in the log-likelihood or the parameter values between iterations to assess convergence.



In this repository, we discuss a modeling approach based on a set of observed sequences denoted as $V = \{v_{1:T}^n, n = 1, \ldots, N\}$, each having the same length T. We assume that the data in these sequences is independent and identically distributed (i.i.d). Therefore, we can express the probability of observing the entire set $V$ as:

$$
p(V) = \prod_{n} p(v_{1:T}^n)
$$


We have defined a model to describe the generation of a single sequence denoted as $v_{1:T}$. This model takes into account the hidden states, denoted as $H$, which play a crucial role in the generation process.In our modeling framework, $H$ represents the hidden states associated with the sequences, providing valuable information about the underlying structure and dynamics.


