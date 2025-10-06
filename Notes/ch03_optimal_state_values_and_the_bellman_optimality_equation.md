# Optimal State Values and the Bellman Optimality Equation

## Optimal State Values and optimal policies

- Definition: a policy $\pi^*$ is optimal if $v_{\pi^*}(s) \ge v_{\pi}(s)$ for **all** $s \in \mathcal S$  and for any other policy $\pi$.
- The state values of $\pi^*$ are the optimal state values.



## The Bellman Optimality Equation (BOE)

- Elementwise form:
  $$
  v(s) = \max_{\pi} \sum_a \pi(a|s) \big(\sum_r p(r | s, a)r + \gamma \sum_{s'} p(s' | s, a)v(s')  \big) , s \in \mathcal S \\
  = \max_{\pi} \sum_a \pi(a|s) q(s, a), s \in \mathcal S
  $$

- Matrix-vector form ($\max_{\pi}$ is performed elementwise):
  $$
  v = \max_{\pi} (r_{\pi} + \gamma P_{\pi}v)
  $$

- Let $f(v) = \max_{\pi}(r_{\pi} + \gamma P_{\pi}v)$, then the BOE becomes
  $$
  v = f(v)
  $$
  

  - where $[f(v)]_s = \max_{\pi} \sum_a \pi(a|s) q(s, a)$



### Maximization of the right-hand side of the BOE

- Considering that $\sum_a \pi(a | s) = 1$, we have:
  $$
  v(s) = \max_{\pi} \sum_a \pi(a|s) q(s, a) \\
  = \max_{a \in \mathcal A(s)} q(s, a)
  $$

  - where the optimality is archieved when
    $$
    \pi(a|s) = 
    \begin{cases} 
    1 & a = a^* \\
    0 & a \neq a^*
    \end{cases}
    $$

  - where $a^* = \text{argmax}_a q(s, a)$

- The optimal policy $\pi(s)$ is the one that selects the action that has the greatest value of $q(s,a)$.



### Contraction mapping theorem

- Contraction mapping (or contractive function): $f$ is a contraction mapping if $|| f(x_1) - f(x_2)|| \leq \gamma ||x_1 - x_2 ||$
  - where $\gamma \in (0, 1)$, $|| \cdot ||$ can be any vector norm.
- Contraction Mapping Theorem: for any equation that has the form of $x = f(x)$, if $f$ is a contraction mapping, then
  - **Existence**: there exists a fixed point $x^*$ satisfying $f(x^*) = x^*$.
  - **Uniqueness**: The fixed point $x^*$ is unique.
  - **Algorithm**: Consider a sequence $\{x_k\}$ where $x_{k+1} = f(x_k)$, then $x_k \rightarrow x^*$ as $k \rightarrow \infty$. Moreover, the convergence rate is exponentially fast.



### Contraction property of the right-hand side of the BOE

- Contraction property of BOE: $f(v)$ is a contraction mapping satisfying $||f(v_1) - f(v_2)|| \leq \gamma ||v_1 - v_2||$, where $\gamma$ is the discount rate.



## Solving an optimal policy from the BOE

- For the BOE $v = f(v) = \max_{\pi}(r_{\pi} + \gamma P_{\pi}v)$, there always **exists** a solution $v^*$ and the solution is **unique**. The solution could be solved iteratively by
  $$
  v_{k+1} = f(v_k) = \max_{\pi}(r_{\pi} + \gamma P_{\pi}v_k)
  $$

  - This sequence ${v_k}$ converges to $v^*$ exponentially fast given any initial guess $v_0$. The convergence rate is determined by $\gamma$.
  - The algorithm is called the **value iteration algorithm**.

- Optimality of $v^*$ and $\pi^*$: the solution $v^*$ is the optimal state value, and $\pi^*$ is an optimal policy.

- Greedy optimal policy: for any $s \in \mathcal S$, the deterministic greedy policy is an optimal policy for solving the BOE:
  $$
  \pi^*(a | s) = 
  \begin{cases}
  1 & a = a^*(s) \\
  0 & a \neq a^*(s)
  \end{cases}
  $$

  - Here, $a^*(s) = \text{argmax}_a q^*(a, s)$,
  - $q^*(s, a) \triangleq \sum_r p(r | s, a)r + \gamma \sum_{s'} p(s' | s, a)v^*(s')$.



## Factors the influence optimal policies

- Three factors:

  - the immediate reward $r$

  - the discount rate $\gamma$

  - the system model $p(s' | s, a), p(r|s, a)$

- Optimal Policy Invariance: the optimal policies are invariant to the aﬃne transformation of the reward signals.

