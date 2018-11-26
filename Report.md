# Continuous Control Project Report

## Deep Deterministic Policy Gradients (DDPG)
In continuous space, policy gradient algorithms are more applicable than value based methods, specifically for systems with high degrees of freedom [1](http://proceedings.mlr.press/v32/silver14.pdf),[2](https://arxiv.org/pdf/1509.02971.pdf). Deterministic policy gradients are computationally efficient for high dimensional action space as it only integrates over state space [1](http://proceedings.mlr.press/v32/silver14.pdf). 

DDPG, implemeted here, is an offline policy method in which two architectures are combined: 1) actor which is utilized to determine the current policy in continuous space and 2) critic to learn the Q-values in a given (state, action) pair. For more details, please take a look at [2](https://arxiv.org/pdf/1509.02971.pdf). 

## Model Architecture
In this projectm, 20 agents Reacher environment were employed. The framework of this project is from [Udacity ddpg-bipedal]( 
https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-pendulum)

We train the network using DDPG algorithm. For the Actor and Critic, we use a three layer MLP with 400 and 300 neurons respectively in hidden layers. The state vector is the 33 dimensional vector used as the input to Actor and Critic.The final layer of Actor has the size of 4, action size. The final layer of Critic is fully connected, with size of 1. We train the network using Adam optimizer.

For stable learning, the following methods were used: gradient clipping to prevent large gradient, soft target update, replay buffer to learn offline, and batch normalization to train the agent in mini batches.

## The Training Parameters and Result:
The parameters for this project are:

BUFFER_SIZE = int(1e5)  # replay buffer size\
BATCH_SIZE = 128        # replay buffer minibatch size\
GAMMA = 0.99            # discount factor\
TAU = 1e-3              # for soft update of target parameters\
LR_ACTOR = 1e-4         # learning rate of the actor for the Adam optimizer \
LR_CRITIC = 1e-4        # learning rate of the critic for the Adam optimizer\
WEIGHT_DECAY = 0.00001  # L2 weight decay used in the Critic Adam optimizer

The reached the average score of 30 at 102 episodes and became stable before 40 episode:
![alt text](https://github.com/AghaAmin/DRLND-P2-Continuous-Control/blob/master/images/result.png)


## 6. Future Work
For the Future, D4PG, TRPO, and PPO will be implemented.
