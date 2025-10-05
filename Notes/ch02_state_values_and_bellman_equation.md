# State Values and Bellman Equation

## Motivating examples

- Return could be used to evaluate policies.
- The returns rely on each other. Bootstrapping (obtain the values of some quantities from themselves)



## State Values

- The expectation (or called expected value or mean) of discounted return $G_t$ is defined as the state-value function or simply state value:
  $$
  v_{\pi} = \mathbb E[G_t | S_t = s]
  $$

- Remarks:

  - It is a function of $s$. It is a conditional expectation with the condition that the state starts from $s$.
  - It is based on the policy $\pi$. Not depend on $t$.
  - The state value is the **mean of all possible returns** that can be obtained starting from a state. If everything ($\pi(a|s), p(r|s,a), p(s′|s,a)$) is deterministic, then state value is the same as return.
  - 区分：reward --> return --> state value



## The Bellman Equation

- The Bellman equation describes the relationship among the values of all states.

- Deriving the Bellman equation (elementwise form): 过程略
  $$
  v_{\pi} = \mathbb E[G_t | S_t = s] \\
  = \mathbb E[R_{t+1} + \gamma G_{t+1} | S_t = s] \\
  = \mathbb E[R_{t+1} | S_t = s] + \gamma E[G_{t+1} | S_t = s] \\
  = \underbrace{\sum_a \pi(a|s) \sum_r p(r|s,a) r}_{\text{mean of immediate rewards}} + \underbrace{\gamma \sum_a \pi(a|s) \sum_{s'} p(s'|s,a) v_{\pi}(s')}_{\text{mean of future rewards}} \\
  = \sum_a \pi(a|s) \left[ \sum_r p(r|s,a) r + \gamma \sum_{s'} p(s'|s,a) v_{\pi}(s') \right], \quad \forall s \in \mathcal{S}.
  $$
  

- Highlights

  - It consists of two terms: the immediate reward term and the future reward term.
  - It's a set of equations: every state has an equation like this.



## Matrix-vector form of Bellman equation

- Rewrite the Bellman equation as:
  $$
  v_{\pi}(s) = r_{\pi}(s) + \gamma \sum_{s'}p_{\pi}(s'|s)v_{\pi}(s') \\
  
  \text{where}\space r_{\pi}(s) \triangleq \sum_a \pi(a | s) \sum_r p(r|s, a)r, \space p_{\pi}(s'|s) \triangleq \sum_a \pi(a|s)p(s'|s, a)
  $$

  - $r_{\pi}(s)$ denotes the mean of the immediate rewards.
  - $p_{\pi}(s'|s)$ is the probability of transitioning from $s$ to $s'$ under policy $\pi$.

- Put all equations for all the states together and rewrite to a matrix-vector form:
  $$
  v_{\pi} = r_{\pi} + \gamma P_{\pi}v_{\pi}
  $$

  - $v_{\pi} = [v_{\pi}(s_1), ..., v_{\pi}(s_n)]^ T \in \mathbb R^n$
  - $r_{\pi} = [r_{\pi}(s_1), ..., r_{\pi}(s_n)]^ T \in \mathbb R^n$
  - $P_{\pi} \in \mathbb R^{n \times n}$, where $[P_{\pi}]_{ij} = p_{\pi}(s_j | s_i)$ is the *state transition matrix*





## Solving state values from the Bellman equation

- Given a policy, finding out the corresponding state values is called *policy evaluation*.



### Closed-form solution

- The closed-form solution is: $v_{\pi} = (I - \gamma P_{\pi})^{-1} r_{\pi}$
  - The matrix $I - \gamma P_{\pi}$ is inevitable.
  - We still need to use numerical algorithms to calculate the matrix inverse.



### Iterative solution

- An iterative solution is: $v_{k+1} = r_{\pi} + \gamma P_{\pi} v_k$
  - We can show that $v_k \rightarrow v_{\pi}, \text{as } k \rightarrow \infty$



## From state value to action value

- State value: the average return the agent can get *starting from a state*.

- Action value: the average return the agent can get *starting from a state and taking an action*. We want to know which action is better.

- Definition: $q_{\pi}(s, a) = \mathbb E[G_t | S_t=s, A_t=a]$

  - $q_{\pi}(s, a)$ is a function of the state-action pair $(s, a)$, depends on $\pi$

- From the properties of conditional expectation, it follows that
  $$
  \underbrace{\mathbb E[G_t | S_t = s]}_{v_{\pi}(s)} = \sum_a \underbrace{\mathbb E[G_t | S_t=s, A_t=a]}_{q_{\pi}(s, a)} \pi(a|s) \\
  \text{Hense, } v_{\pi}(s) = \sum_a \pi(a|s)q_{\pi}(s, a)
  $$

  - 对比公式(2)可得，action-value function:
    $$
    q_{\pi}(s, a) = \sum_r p (r|s, a)r + \gamma \sum_{s'} p (s' | s, a) v_{\pi}(s')
    $$

  - State value and action value are the two sides of the same coin.



### The Bellman equation in terms of action values

- TODO
