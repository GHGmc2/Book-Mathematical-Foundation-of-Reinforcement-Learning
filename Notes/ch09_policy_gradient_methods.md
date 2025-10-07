# Policy Gradient Methods

- policy function methods (or called policy gradient methods)



## Basic idea

- Policies can be represented by parameterized functions: $\pi(a | s,\theta)$
  - The function can be, for example, a neural network, whose input is $s$, output is the probability to take each action, and parameter is $\theta$.
  - The function representation is also sometimes written as $\pi(a, s, \theta), \pi_{\theta}(a|s)$ or $\pi_{\theta}(a, s)$.
- Diﬀerences between tabular and function representations:
  - In the function case, a policy $\pi$ is optimal if it can maximize certain scalar metrics.
  - In the function case, we need to calculate the value of $\pi(a|s, \theta)$ given the function structure and the parameter.
  - In the function case, a policy $\pi$ can only be updated by changing the parameter $\theta$.
- The basic idea of the policy gradient:
  - metrics (or objective functions) to define optimal policies: $J(\theta)$, which can define optimal policies.
  - gradient-based optimization algorithms to search for optimal policies: $\theta_{t+1} = \theta_t + \alpha \nabla_{\theta}J(\theta_t)$



## Metrics for defining optimal policies

- average state value or simply called average value: $\bar v_{\pi}$

- average one-step reward or simply average reward: $\bar r_{\pi}$ 
- Summary
  - The two metrics are equivalent (not equal) to each other.
  - Specifically, in the discounted case where $\gamma < 1$, it holds that $\bar r_{\pi} = (1 - \gamma) \bar v_{\pi}$.




## Gradients of the metrics

- The expression of the gradient:
  $$
  \nabla_{\theta} J(\theta) = \sum_{s \in \mathcal S} \eta(s) \sum_{a \in \mathcal A} \nabla_{\theta} \pi(a|s, \theta)q_{\pi}(s, a)
  $$

  - $J(\theta)$ can be $\bar v_{\pi}, \bar r_{\pi}$ or $\bar v_{\pi}^0$.
  -  "=" may denote strict equality, approximation, or proportional to.
  - $\eta$ is a distribution or weight of the states.

- A compact form expressed in terms of expectation:
  $$
  \nabla_{\theta} J(\theta) = \mathbb E_{S \sim \eta, A \sim \pi} [\nabla_{\theta} \ln \pi(A|S, \theta) q_{\pi}(S, A)]
  $$

  - we can use samples to approximate the gradient.
  - It is required by $\ln \pi(a|s, \theta)$ that $\pi(a|s, \theta) > 0$, this can be achieved by using softmax functions.



## Monte Carlo policy gradient (REINFORCE)

- deterministic policy gradient (DPG)

- the first policy gradient algorithm to find optimal policies

  1. The gradient-ascent algorithm maximizing $J(\theta)$ is:
     $$
     \theta_{t+1} = \theta_t + \alpha \nabla_{\theta} J(\theta) \\
     = \theta_t + \alpha \mathbb E[\nabla_{\theta} \ln \pi(A|S, \theta_t) q_{\pi}(S, A)]
     $$

  2. Since the true gradient is unknown, we can replace it by a stochastic one:
     $$
     \theta_{t+1} = \theta_t + \alpha \nabla_{\theta} \ln \pi(a_t | s_t,\theta_t) q_{\pi}(s_t, a_t)
     $$

  3. Furthermore, since $q_{\pi}$ is unknown, it can be replaced by an estimate:
     $$
     \theta_{t+1} = \theta_t + \alpha \nabla_{\theta} \ln \pi(a_t | s_t,\theta_t) q_t(s_t, a_t)
     $$

- If $q_{\pi}(s_t,a_t)$ is estimated by Monte Carlo estimation, the algorithm has a specifics name, REINFORCE.

- policy gradient methods are on-policy.

