# Deep Reinforcement Learning Nanodegree
## Project 2 Report - Continuous Control

### Introduction
This project solves the distributed agent version of the Reacher environment implementing the DDPG algorithm using 20 agents. The Deep Deterministic Policy Gradient (DDPG) algorithm is attractive for this environment as it extends the power of the Deep Q-Network (DQN) algorithm to environments with continuous action spaces (as is the case for the Reacher environemnt).While the DDPG algorithm performs well in solving this environment, it should be noted that several other policy-based algorithms may be suitable as well: Trust Region Policy Optimization (TRPO), Proximal Policy Optimization (PPO), and Asynchronous Advantage Actor Critic (A3C), for example.

### DDPG Algorithm
The DDPG algorithm is an actor-critic method that performs well in environments with a continuous action space, addressing a key short-coming of the DQN algorithm, which can only be applied to discrete action spaces.  Further, the DDPG algorithm is an improvement over the Deterministic Policy Gradient (DPG) algorithm, as the former employs a deep neural network for improved generalization and function approximation.

The DDPG algorithm consists of two neural networks: one an Actor and the other a Critic. The Actor approximates the optimal deterministic policy and thus returns a single action&mdash;the optimal (or, rather, an approximation thereof)&mdash;for each state. The Critic learns how to evaluate the optimal action-value function using actions from the Actor.  The core idea of this algorithm is that the Actor calculates a new target value, which is used to train the action-value function in the Critic.  A schematic of the network architecture is shown, below (it should be noted that that DDPG actually makes use of 4 different neural networks in its implementation: [1] a local actor; [2] a target actor; [3] a local critic; and [4] a target critic.):

<img src="https://nervanasystems.github.io/coach/_images/ddpg.png" alt="DDPG Architecture" title="DDPG Architecture" style="max-width:100%;">

There are two additioonal important features to the algorithm: (1) the use of a replay buffer, just like the DQN; and (2) the use of soft updates as the mechanism to update the weights of the target networks (this is in place of a fixed update after a prescriberd number of time steps, as employed by the DQN).

The following hyperparameters were used to implement the algorithm, described above, and which were also used in the original DDPG paper:

```
BUFFER_SIZE      # replay buffer size
BATCH_SIZE       # minibatch size
GAMMA            # discount factor
TAU              # for soft update of target parameters
LR_ACTOR         # learning rate of the actor 
LR_CRITIC        # learning rate of the critic
WEIGHT_DECAY     # L2 weight decay
```

As noted above, the DDPG model uses both actor and critic networks.  The structure of each in this implementation follows the networks described in the original paper.  To that end, each network consists of 3 fully-connected layers, the first two of which use a ReLU activation function, while the output layer uses a tanh (*i.e.*, to ensure the output falls between -1 and 1, as required by the Reacher environment). The tanh function further ensures a continous output value, ensuring smooth operability in continuous environments.  The critic network does not make use of an activation function in the output layer.

### Training and Results

# Plot of Rewards

The plot, above, shows the agent solved the environment after *XXX* episodes and settles at an average score around *XXX* after 250 episodes.

Training process initially followed the architecture and hyperparameter values from the original paper very closely, though these values did not result in good performance.  Instead, the hyperparameters were tuned to arrive at the following:

```
BUFFER_SIZE  = int(1e5)   # (1e6 in original paper)
BATCH_SIZE   = 128        # (64 in original paper)
GAMMA        = 0.99
TAU          = 1e-3 
LR_ACTOR     = 1e-4 
LR_CRITIC    = 1e-3 
WEIGHT_DECAY = 0          # (1e-2  in original paper)
```

Further, while the original structure of the neural network used 400 and 300 nodes in the first two fully connected layers, respectively, this architecture failed to learn.  Using 256 and 128, however, achieved the results outlined above.

## Future Improvements
A natural extension of this work would be to compare the performance shown here against other algorithms (such as TRPO, PPO and A3C) in the same environment, along with applying multi-agent learning techniques.  The DDPG algorithm used here could also be furthe roptimized, *i.e.*, by further tuning hyperparameters and neural network architecture.
