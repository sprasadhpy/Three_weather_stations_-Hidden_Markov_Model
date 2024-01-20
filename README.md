![image](https://github.com/sprasadhpy/Three_weather_stations_Hidden_Markov_Model/assets/40602129/39d3424e-834c-4587-88ce-a7d199f52ee7)# Weather Station Data Analysis using EM Algorithm
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


The log likelihood of the given data for learned parameters is:

\colorbox{codegreen} {-45254.5104}

## Learned Parameters

### Hidden State Distribution Probabilities (p(h))

These are the probabilities of starting in each of the three hidden states:

| Hidden State | Probability |
|--------------|-------------|
| State 0      | 0.2996      |
| State 1      | 0.1920      |
| State 2      | 0.5083      |

### Initial State Probability Given Hidden State (p(v₁|h))

These probabilities represent the likelihood of observing the first visible state given each hidden state. Each row corresponds to a hidden state, and each column represents the probability of emitting a particular visible state. The values in the matrix indicate the emission probabilities for the first visible state given each hidden state:

| Hidden State | Visible State 0 | Visible State 1 | Visible State 2 |
|--------------|-----------------|-----------------|-----------------|
| State 0      | 0.1921          | 0.4270          | 0.4611          |
| State 1      | 0.4192          | 0.5729          | 0.3312          |
| State 2      | 0.3886          | 0.0000          | 0.2076          |

### Transition Probabilities (p(vₜ|vₜ₋₁, h))

These matrices represent the probabilities of transitioning from one visible state to another given the current hidden state. There is a separate matrix for each hidden state. Each row in a matrix corresponds to the probabilities of transitioning from the visible state represented by that row to the visible states represented by the columns, given the current hidden state:

**Matrix 1:**

| From \ To | State 0 | State 1 | State 2 |
|-----------|---------|---------|---------|
| State 0   | 0.0597  | 0.3886  | 0.0705  |
| State 1   | 0.1300  | 0.2405  | 0.1367  |
| State 2   | 0.4175  | 0.5453  | 0.5107  |

**Matrix 2:**

| From \ To | State 0 | State 1 | State 2 |
|-----------|---------|---------|---------|
| State 0   | 0.1395  | 0.1484  | 0.4946  |
| State 1   | 0.3237  | 0.5154  | 0.2258  |
| State 2   | 0.4278  | 0.0175  | 0.4372  |

**Matrix 3:**

| From \ To | State 0 | State 1 | State 2 |
|-----------|---------|---------|---------|
| State 0   | 0.8007  | 0.4628  | 0.4348  |
| State 1   | 0.5461  | 0.2439  | 0.6373  |
| State 2   | 0.1545  | 0.4371  | 0.0519  |



## Transition Probability Matrices

These matrices represent the probabilities of transitioning from one visible state to another given the current hidden state. There is a separate matrix for each hidden state. Each row in a matrix corresponds to the probabilities of transitioning from the visible state represented by that row to the visible states represented by the columns, given the current hidden state.


| Observation | Log Posterior (state=0) | Log Posterior (state=1) | Log Posterior (state=2) | Posterior (state=0) | Posterior (state=1) | Posterior (state=2) | Probable Hidden State |
|--------------|-------------------------|-------------------------|-------------------------|---------------------|---------------------|---------------------|-----------------------|
| 0            | -50.5467                | 0                       | -68.2744                | 1.1163e-22          | 1                   | 2.2324e-30          | 1                     |
| 1            | -1.9073e-4              | -82.0105                | -8.5647                 | 0.9998              | 2.4170e-36          | 1.90716e-4          | 0                     |
| 2            | -12.5738                | -104.0388               | -3.4614e-06             | 3.4614e-06           | 6.5542e-46          | 0.9999              | 2                     |
| 3            | -19.7543                | -59.3410                | -2.6349e-09             | 2.6349e-09           | 1.6924e-26          | 0.9999              | 2                     |
| 4            | -12.0428                | -68.3054                | -5.8865e-06             | 5.8865e-06           | 2.1643e-30          | 0.9999              | 2                     |
| 5            | -3.7612e-05             | -72.5706                | -10.1888                | 0.9999              | 3.0407e-32          | 3.7587e-05          | 0                     |
| 6            | -42.7049                | 0                       | -63.3609                | 2.8409e-19          | 1                   | 3.0386e-28          | 1                     |
| 7            | -18.7211                | -80.5536                | -7.4048e-09             | 7.4048e-09           | 1.037e-35           | 0.9999              | 2                     |
| 8            | -12.6637                | -125.0396               | -3.1636e-06             | 3.1636e-06           | 4.9655e-55          | 0.9999              | 2                     |
| 9            | -13.0225                | -84.8230                | -2.2099e-06             | 2.2099e-06           | 1.4514e-37          | 0.9999              | 2                     |

You can analyze these transition probabilities to understand the model's behavior.


The EM algorithm is sensitive to the choice of initial parameters. Different initialization may lead to convergence to different local optima. The likelihood function being optimized may have multiple peaks, and the algorithm could get stuck in one of them based on the initial guess.

Our Initialization Strategy was to perform multiple runs of the EM algorithm with different initializations and choose the result with the highest likelihood. All the initial parameters were randomly sampled from a uniform distribution on [0,1], then normalized such that relevant marginal probabilities summed up to 1. This helped mitigate the impact of converging to a sub-optimal solution.

## Computational Issues

### 1. Numerical Underflow

Numerical underflow was an issue that affected computations in Markov chains, as it deals with small probabilities. Numerical underflow occurs when the product of many small probabilities leads to a value too close to zero, causing a loss of precision and potential inaccuracies in calculations.

#### Dealing with Computational Issues

Instead of working directly with probabilities, we use the logarithm of probabilities. Since probabilities are typically small numbers between 0 and 1, their logarithms are negative. Summing logarithms is computationally more stable than multiplying probabilities.

### 2. Initialization Sensitivity Issues

EM results were sensitive to the initial parameter values.

#### Dealing with Initialization Sensitivity Issues

We used multiple random initializations and chose the results that led to the highest likelihood.

### 3. Numerical Instability in EM Computation

During the computation of the Expectation-Maximization (EM) algorithm, it was observed that some probabilities in matrices had a value of 0. This situation resulted in -infinity when taking the logarithm, causing numerical instability in log-scale computations.

#### Dealing with Numerical Instability

To address the numerical instability, an adjustment was implemented by adding a small positive constant, referred to as epsilon, to the probabilities before taking the logarithm. This adjustment ensured that even extremely small probabilities were represented in a stable manner on the log scale, preventing -infinity issues. After thorough analysis and testing, it was observed that the introduction of the small positive constant (epsilon) did not lead to any significant changes in other calculated values. The adjustment effectively resolved the numerical instability issue without introducing substantial alterations to the overall EM computation results.




When we initialize all the relevant distributions to be uniform, the parameters learned by the EM algorithm will converge to values that maximize the likelihood of the observed data given this uniform initialization. In practical terms, this implies that the algorithm learns parameters that assign equal probabilities to all states. Consequently, it may struggle to effectively differentiate between the components. The algorithm tends to converge to a scenario where each component has precisely equal importance, which becomes evident in the final results. As a result, all the parameter updates become identical in each EM step across all hidden states. Therefore, initializing all relevant distributions as uniform is generally not advisable, as it can hinder the model's ability to capture meaningful data patterns.

## Impact of Uniform Initialization

### Log Likelihood with Uniform Initialization

The log likelihood of the given data for the learned parameters using uniform initialization is: \colorbox{codegreen}{-49473.5473}. This value represents the log-likelihood of the observed data, given the parameters estimated with uniform initialization.

### Learned Parameters with Uniform Initialization
[0.3333]
[0.3333]
[0.3333]

#### Hidden State Distribution Probabilities$


These are the probabilities of starting in each of the three hidden states. In the case of uniform initialization of parameters, we observe that the model has converged to a state where each hidden state is equally likely to be the starting state.

### Initial State Probability Given Hidden State 

[0.3740 0.3740 0.3740]
[0.4040 0.4040 0.4040]
[0.2220 0.2220 0.2220]

These probabilities represent the likelihood of observing the first visible state given each hidden state. Each row corresponds to a hidden state, and each column represents the probability of emitting a particular visible state. The values in the matrix indicate the emission probabilities for the first visible state given each hidden state. Again, we observe that the emission probabilities for the first visible state are the same across all hidden states.


## Transition Probabilities $p(v_t|v_{t-1},h)$


![image](https://github.com/sprasadhpy/Three_weather_stations_Hidden_Markov_Model/assets/40602129/6ab12792-33ca-4366-9990-9af59d8d6925)



These matrices represent the probabilities of transitioning from one visible state to another given the current hidden state. There is a separate matrix for each hidden state. Each row in a matrix corresponds to the probabilities of transitioning from the visible state represented by that row to the visible states represented by the columns, given the current hidden state. Here we observe that there is no distinction between hidden states as all transition probabilities are the same across the hidden states.

In conclusion, **Initializing the EM algorithm with a uniform distribution makes it seem as though there is essentially only one hidden state.**



