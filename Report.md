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

Experience replay lets online reinforcement learning agents remember and reuse experiences from the past. In prior work, experience transitions were uniformly sampled from a replay memory. However, this approach simply replays transitions at the same frequency that they were originally experienced, regardless of their significance. To replay important transitions more frequently, and therefore learn more efficiently, we use prioritized Experience Replay

### Dueling Agents

Dueling networks utilize two streams: one that estimates the state value function `V(s)`, and another that estimates the advantage for each action `A(s,a)`. These two values are then combined to obtain the desired Q-values.