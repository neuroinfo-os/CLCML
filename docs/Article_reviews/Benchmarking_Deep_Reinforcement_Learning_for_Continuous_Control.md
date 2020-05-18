---
layout: page
title: About
---


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
- _Limited Sensors_:  only positional information is provided. An agent is to learn to infer velocity information in order to recover the full state.
- _Noisy Observations and Delayed Actions_: adding Gaussian noise to the observations.
- _System Identification_: the underlying physical model parameters are varied across episodes, so agent has to generilize.

__Result__ :  recurrent policies can find better solutions than feedforward policies,  but they are more difficult to train.

#### Hierarchical Tasks
- Locomotion + Food Collection
- Locomotion + Maze
__Result__ : all of implemented algorithms achieve poor performance, even with extensive hyperparameter search and 500 iterations of training.

### Algorithms

#### Batch Algorithms

- __REINFORCE__ estimates the gradient of expected return:
<p align="center">
 <img src="https://render.githubusercontent.com/render/math?math=\hat{\Delta_{\sigma\mu(\pi_{\sigma})}}=\frac{1}{NT}\sum_{i=1}^{N}\sum_{t=0}^{T}\delta_{\sigma}log \pi(a_{i}^{t}|s_{t}^{i},\theta)(R_{t}^{i}-b_{t}^{i})">, where 
 
 
 <img src="https://render.githubusercontent.com/render/math?math=R_{t}^{i}=\sum_{t^{\prime}=t}^{T}\gamma_{t-t^{\prime}}r_{t}^{i}"> 
 and b is a policy baseline, that reduces varience. 
</p>

__Result__ fast and effective, but prone to converging to local optima. 

- __Truncated Natural Policy Gradient (TNPG)__
It adds computation of the ascent direction provides a small change in a policy distribution. 

<p align="center">
 <img src="https://render.githubusercontent.com/render/math?math=I(\theta^-1)\Delta_{\sigma\mu(\pi_{\sigma})}"> .
 </p>
   
 
  
 The step is choosen as :
<img src="https://render.githubusercontent.com/render/math?math=\alpha=\sqrt{\delta_{KL}(\Delta_{\sigma\mu(\pi_{\sigma})^T}  I(\theta)^{-1}\Delta_{\sigma\mu(\pi_{\sigma})^{-1}})}">
Then authors  replace ∇θη(πθ) and I(θ) by their empirical estimates.

__Result__ Outperforms other batch algorithms on most tasks. 


- __Reward-Weighted Regression (RWR)__
RWR allows to avoid manual setting of learning rate. Each iteration algorithm optimizes a lower bound of the log-expected return with argmax of <img src="https://render.githubusercontent.com/render/math?math=\ell(\theta)">. Where

<p align="center">
<img src="https://render.githubusercontent.com/render/math?math=\ell(\theta)=\frac{1}{NT}\sum_{i=1}^{N}\sum_{t=0}^{T}\delta_{\sigma}log \pi(a_{i}^{t}|s_{t}^{i},\theta)p(R_{t}^{i}-b_{t}^{i})">, 
 
 where p is a function that transforms raw returns to nonnegative value. 
</p>
 
__Result__ RWR showed fast initial improvement followed by significant slow-down. It can solve only basic tasks.


- __Relative Entropy Policy Search (REPS)__
The aim is to lessen the loss of information per iteration. At each iteration all trajectories are collected and then argmin of dual parameters are found to maximize information for updated parameters.


__Result__  REPS is prone to early convergence to local optima in case of continuous states and actions


- __Trust Region Policy Optimization (TRPO)__
The algorithm is similar to TNPG, but adds _surrogate loss_ which leads to more precise control of the expected policy improvment. Detailed description of the algorithm could be found at [Schulman, J., Levine, S., Abbeel, P., Jordan, M. I., and Moritz, P. Trust region policy optimization. In ICML, pp. 1889–1897, 2015a].

__Result__  Outperform other batch algorithms on most tasks along with TNPG.


- __Cross Entropy Method (CEM)__
CEM explores directly in the policy parameter space, opposed to learning via stochastic actions. For that at each step i. N pertrubations of policy parameter are produced; ii new iteration performed; iii the top q-quantile parameters are used to compute the mean and a new covariance matrix. 

 __Result__  CEM suffers from increasing complicity of system dynamics. Moreover, in high-dimensional observation tasks it runs out of memory.
 
 
- __Covariance Matrix Adaption Evolution Strategy (CMA-ES)__
Similar to CEM, but estimates the covariance matrix using information about the corelations between consecutive updates.

#### Online Algorithms
_Deep Deterministic Policy Gradient (DDPG)_
The algorithm improves the policy during environment exploration. For stability issues two target networks  are used: critic NN and the policy  NN. Authors applie gradient descent to the policy within  a minibatch from a replay pool; then The critic is trained via gradient descent on the l2 loss of the Bellman error. 

__Result__  converges significantly faster on certain tasks due to its greater sample efficiency, but less stable, than batch algorithms. 
However, he latter problem could be solved by rescaling the reward of all tasks by a factor of 0.1. 

#### Recurrent Variants
All aforementioned algorithms were implemented as recurrent policies. 
