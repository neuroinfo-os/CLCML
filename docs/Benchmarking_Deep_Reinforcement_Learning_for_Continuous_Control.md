# Benchmarking Deep Reinforcement Learning for Continuous Control
## Yan Duan, Xi Chen, Rein Houthooft, John Schulman, Pieter Abbeel

The article is dedicated to implementation and comparison of a range of reinforcement learning algorithms. Benchmarks and algorithms gould be found at
https://github.com/ rllab/rllab. Authors showed that even some implemented batch algorithms could provide an effective solutions for training DNN.
Nevertheless, none of them are able to cope with more complicated, _hierarchical tasks_. 

### Tasks

#### Basic
Cart-Pole Balancing, Cart-Pole Swing Up, Mountain Car, Acrobot Swing Up, Double Inverted Pendulum Balancing

#### Locomotion Tasks
Six tasks (such. as Swimmer, Walker), for which the main goal is to move forward as quickly as possible.

#### Partially Observable Tasks
- _Limited Sensors_:  only provide positional information is provided. An agent was to learn to infer velocity information in order to recover the full state. Similar tasks have been explored in Gomez & Miikkulainen (1998); Scha ̈fer & Udluft (2005); Heess et al. (2015a); Wierstra et al. (2007).
- _Noisy Observations and Delayed Actions_: sensor noise is simulated through the addition of Gaussian noise to the observations. We also introduce a time delay between taking an action and the action being in effect.
- _System Identification_: the underlying physical model parameters are varied across different episodes (Szita et al., 2003). The agents must learn to generalize across different models, as well as to infer the model parameters from its observation and action history.

Result :  recurrent policies can find better solutions than feedforward policies,  but they are more difficult to train.

#### Hierarchical Tasks
- Locomotion + Food Collection
- Locomotion + Maze
Result : all of implemented algorithms achieve poor performance, even with extensive hyperparameter search and 500 iterations of training.

### Algorithms

#### Batch Algorithms
- REINFORCE 
fast and effective, but prone to converging to local optima
- Truncated Natural Policy Gradient (TNPG) 
outperform other batch algorithms on most tasks
- Reward-Weighted Regression (RWR)
RWR showed fast initial improvement followed by significant slow-down. It can solve only basic tasks.
- Relative Entropy Policy Search (REPS)
REPS is prone to early convergence to local optima in case of continuous states and actions
- Trust Region Policy Optimization (TRPO)
outperform other batch algorithms on most tasks
- Cross Entropy Method (CEM)
 the performance suffers from increasing complicity of system dynamics. In high-dimensional observation tasks it runs out of memory.
- Covariance Matrix Adaption Evolution Strategy (CMA-ES) 

#### Online Algorithms
_Deep Deterministic Policy Gradient (DDPG)_
converges significantly faster on certain tasks due to its greater sample efficiency, but less stable, than batch algorithms. 
However, he latter problem could be solved by rescaling the reward of all tasks by a factor of 0.1. 

#### Recurrent Variants
