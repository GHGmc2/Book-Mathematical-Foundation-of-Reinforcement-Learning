## Ref

 - [Third-party code and materials](https://github.com/MathFoundationRL/Book-Mathematical-Foundation-of-Reinforcement-Learning#third-party-code-and-materials)





## [30分钟了解强化学习的名词脉络](https://www.bilibili.com/video/BV1r3411Q7Rr)

<img src="https://discuss.pytorch.kr/uploads/default/original/2X/b/bba5e3967b5de4634194ee2554d4f6a81709f0f1.jpeg" width=700>



### Fundamental tools

**Ch01**

- Concepts: state, action, reward, return, episode, policy...
- Markov decision process (MDP)



**Ch02**

- One concept: state value
  $$
  v_{\pi}(s) = \mathbb E[G_t | S_t = s]
  $$

- One tool: Bellman equation
  $$
  v_{\pi} = r_{\pi} + \gamma P_{\pi}v_{\pi}
  $$



**Ch03**

- Two concepts: optimal policy $\pi^*$ & optimal state value

- One tool: Bellman optimality equation
  $$
  v = \max_{\pi}(r_{\pi} + \gamma P_{\pi} v) = f(v)
  $$





### Algorithms/Methods

**Ch04: 承上启下**

- Three algorithms
  - Value iteration (VI)
  - Policy iteration (PI)
  - Truncated policy iteration



**Ch05: model-free**

- Algorithms
  - MC Basic
  - MC Exploring Starts
  - MC $\epsilon$-greedy



**Ch06: incremental manner**

- Algorithms
  - Robbins-Monro (RM) algorithm
  - Stochastic gradient descent (SGD)
    - SGD, BGD, MBGD



**Ch07: incremental**

- Algorithms
  - TD learning of state values
  - Sarsa: TD learning of action values
  - Q-learning: TD learning of optimal action values
    - on-policy & off-policy: behavior policy vs. target policy
  - Unified point of view



**Ch08: function representation**

- Algorithms

  - State value estimation with value function approximation (VFA):
    $$
    \min_w J(w) = \mathbb E[v_{\pi}(S) - \hat v (S, w)]
    $$
    

  - Sarsa with VFA

  - Q-learning with VFA

  - Deep Q-learning (DQN)



**Ch09: policy-based**

- Contents

  - Metrics to define  optimal policies:
    $$
    J(\theta) = \bar v_{\pi}, \bar r_{\pi}
    $$
    

  - Policy gradient:
    $$
    \nabla J(\theta) = \mathbb E[\nabla_{\theta} \ln \pi(A | S, \theta)q_{\pi}(S, A)]
    $$
    

  - Gradient-ascent algorithms (REINFORCE):
    $$
    \theta_{t + 1} = \theta_t + \alpha \nabla_{\theta} \ln \pi (a_t | s_t, \theta_t)q_t(s_t, a_t)
    $$



**Ch10: policy-based + value-based**

- Algorithms
  - The simplest actor-critic (QAC)
  - Advantage actor-critic (A2C)
  - Off-policy actor-critic
    - Importance sampling
  - Deterministic actor-critic (DPG)



