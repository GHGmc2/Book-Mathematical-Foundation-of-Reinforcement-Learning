# Basic Concepts



## State and action

- State: the agent's status of the agent with respect to the environment
- State space: the set of all states
- Action: 
- Action space of a state



## State transition

- When taking an action, the agent may move from one state to another. Such a process is called state transition.

- State transition describes the interaction with the environment.
- In general, state transitions can be *stochastic* and must be described by conditional probability distributions $p(s'|s, a)$



## Policy

- A Policy tells the agent what actions to take at a state.
- Mathematically, policies can be described by conditional probabilities.



## Reward

- After executing an action at a state, the agent obtains a reward, denoted as $r$, as feedback from the environment.
- The reward is a function of the state $s$ and action $a$.
- Reward can be interpreted as a human-machine interface, with which we can guide the agent to behave as what we expect.
- The reward transition could be stochastic $p(r|s, a)$



## Trajectories, returns, and episodes

- A trajectory is a state-action-reward chain.
- The **return** of this trajectory is the sum of all the **rewards** collected along the trajectory. Return could be used to evaluate policies.
- Discounted return
  - A trajectory may be infinite.
  - discount rate $\gamma \in (0, 1)$
    - removes the stop criterion and allows for infinitely long trajectories.
    - can be used to adjust the emphasis placed on near- or far-future rewards.
- Episode: the agent may stop at some terminal states. The resulting trajectory is called an episode (or a trial).
  - An episode is usually assumed to be a finite trajectory.




## Markov decision processes

Key elements of MDP:

- Sets
  - State: the set of states $\mathcal S$
  - Action: the set of actions $\mathcal A(s)$ is associated for state $s \in \mathcal S$
  - Reward: the set of rewards $\mathcal R(s, a)$
- Probability distribution (or called system model)
  - State transition probability: at state $s$, taking action $a$, the probability to transit to state $s'$ is $p(s'|s, a)$
  - Reward probability: at state $s$, taking action $a$, the probability to get reward $r$ is $p(r| s, a)$
- Policy: at state $s$, the probability to choose action $a$ is $\pi(a | s)$
- *Markov property*: memoryless property. The next state or reward depends merely on the current state and action and is independent of the previous ones.
- Once the policy in an MDP is fixed, the MDP degenerates into an Markov processes (MP).



