## Introduction

The goal of the project is to train an agent to collect bananas.

A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana.  Thus, the goal of your agent is to collect as many yellow bananas as possible while avoiding blue bananas.

The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around agent's forward direction.  Given this information, the agent has to learn how to best select actions.  Four discrete actions are available, corresponding to:
- **`0`** - move forward.
- **`1`** - move backward.
- **`2`** - turn left.
- **`3`** - turn right.

The task is episodic, and in order to solve the environment, agent must get an average score of +13.


## Implementation
- model.py
  - QNetwork
    - Input layer - 37 which is state space
    - Hidden layers - both 64
    - Output layer - 4 which is action size
  - DuellingQNetwork
    - Input layer - 37 which is state space
    - Hidden layers - both 64
    - Output layer - 4 which is action size
    - Averaging layer - 64 to 1
- dqn_agent.py
  - This file is implemented based on the coding exercise of Deep Q-Learning algorithm.
  - This includes replay buffer and the algorithm to act, learn and take steps for the agent
  - This also involves Double dqn


## Hyper Parameters
The DQN agent uses the following parameters values

```
BUFFER_SIZE = int(1e5)  # replay buffer size
BATCH_SIZE = 64         # minibatch size 
GAMMA = 0.995           # discount factor 
TAU = 1e-3              # for soft update of target parameters
LR = 5e-4               # learning rate 
UPDATE_EVERY = 4        # how often to update the network
```

## Future Ideas

### Prioritized Experience Replay

Prioritized Experience Replay (PER) is a straightforward improvement for the vanilla Deep Q-Network (DQN) algorithm. It is built on top of experience replay buffers, which allow a reinforcement learning (RL) agent to store experiences in the form of transition tuples, usually denoted as (st,at,rt,st+1) with states, actions, rewards, and successor states at some time index t. In contrast to consuming samples online and discarding them thereafter, sampling from the stored experiences means they are less heavily “correlated” and can be re-used for learning.


### Dueling Agents

The Dueling DQN architecture trades on the idea that the evaluation of the Q function implicitly calculates two quantities:
- V(s) — the value of being in state s
- A(s, a) — the advantage of taking action a in state s
### Prioritized Experience Replay

Prioritized Experience Replay (PER) is a straightforward improvement for the vanilla Deep Q-Network (DQN) algorithm. It is built on top of experience replay buffers, which allow a reinforcement learning (RL) agent to store experiences in the form of transition tuples, usually denoted as (st,at,rt,st+1) with states, actions, rewards, and successor states at some time index t. In contrast to consuming samples online and discarding them thereafter, sampling from the stored experiences means they are less heavily “correlated” and can be re-used for learning.


### Dueling Agents

The Dueling DQN architecture trades on the idea that the evaluation of the Q function implicitly calculates two quantities:
- V(s) — the value of being in state s
- A(s, a) — the advantage of taking action a in state s
This has been implemented. Futur work is required to reach optimal harapeters for this network.
