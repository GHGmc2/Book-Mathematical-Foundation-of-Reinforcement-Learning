# Temporal Difference Methods

## TD learning of state values

- The TD algorithm can be annotated as:
  $$
  \underbrace{v_{t+1}(s_t)}_{\text{new estimate}} = \underbrace{v_t(s_t)}_{\text{current estimate}} - \alpha_t(s_t) \big[ \overbrace{v_t(s_t) - [\underbrace{r_{t+1} + \gamma v_t(s_t+1)}_{\text{TD target }\bar v_t}]}^{\text{TD error }\delta_t} \big]
  $$

  - TD target: $\bar v_t \triangleq r_{t+1} + \gamma v_t(s_{t + 1})$
  - TD error: $\delta_t \triangleq v_t(s_t) - \bar v_t$
    - It reflects the diﬀerence between two time steps.
    - It reflects the diﬀerence between $v_t$ and $v_{\pi}$.
    - The TD error can be interpreted as innovation, which means new information obtained from the experience $(s_t,r_{t+1},s_{t+1})$.

- The TD algorithm in (1) only estimates the state value of a given policy. It will be extended to estimate action values and then search for optimal policies.

- Bellman expectation equation:
  $$
  v_{\pi}(s) = \mathbb E[R + \gamma v_{\pi}(S') | S=s], s \in \mathcal S.
  $$



## TD learning of action values

- TODO



## TD learning of optimal action values: Q-learning

### Algorithm description

- Q-learning can directly estimate optimal action values and hence optimal policies.



### Off-policy vs. on-policy

- There exist two policies in a TD learning task:
  - The **behavior policy** is used to generate experience samples.
  - The **target policy** is constantly updated toward an optimal policy.
- When the behavior policy is the same as the target policy, such kind of learning is called on-policy. When they are diﬀerent, the learning is called oﬀ-policy.
  - Both Sarsa and MC are on-policy.
  - Q-learning is oﬀ-policy.



### Implementation

- Since Q-learning is oﬀ-policy, it can be implemented in an either oﬀ-policy or on-policy fashion.



## A unified viewpoint

- A unified expression:
  $$
  q_{t+1}(s_t, a_t) = q_t(s_t, a_t) - \alpha_t(s_t, a_t)[q_t(s_t, a_t) - \bar q_t]
  $$

  - where $\bar q_t$ is the TD target.

- Diﬀerent TD algorithms have diﬀerent $\bar q_t$: TODO

- All the TD algorithms can be viewed as stochastic approximation algorithms solving the Bellman equation or Bellman optimality equation: TODO

