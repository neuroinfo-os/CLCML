# Controlling statistical moments of stochastic dynamical networks
## PHYSICAL REVIEW E 94, 012306 (2016)
## Dmytro Bielievtsov, Josef Ladenbauer, and Klaus Obermayer
### _DOI: 10.1103/PhysRevE.94.012306_


The aim of the work is to explore how the first and second statistical moments of stochastic dynamical networks can be controlled by interfering only with a subset of nodes. The described approach, known as _pinning control_ (or _clamping control_), consists of the following steps:
1. Description of first and second statistical moments of a system;
2.
   * Identification of moments' subsets which can steer the whole system in a desired state;
   * Identification of original nodes corresponding to described moments' subsets;
3. Feedback controller design. 


### Step 1
The network is described by the following equation: 
<img src="https://render.githubusercontent.com/render/math?math=\dot{x}=f(t,x) %2B M\eta(t) ">
f(t,x) is a direct graph of the system with N nodes, and M is a constant noise mixing matrix. The moment system (MS) described by the following equations:

<img src="https://render.githubusercontent.com/render/math?math=\dot{\mu}=f(t,\mu) %2B\frac{1}{2}\nabla\nabla f(t,\mu)C  ">

<img src="https://render.githubusercontent.com/render/math?math=\dot{C}=\nabla f(t,\mu)C %2B C \nabla f(t,\mu) 2B% Q ">

where  <img src="https://render.githubusercontent.com/render/math?math=\nabla f(t,\mu)"> is the Jacobian of f and Q is the total noise covariance matrix. 


### Step 2
A subset K of the vertex set I := {1,...,N} for the system is a set of switching nodes, if the network is guaranteed to converge to a solution with SN are forced to attain the values of one of the solution when t tends to infinity. For that the following requirements should be sutisfied:
1. __Assumption 1__  For all initial conditions state of the system stays within a ball of finite radius as time tends to infinity.
2. __Assumption 2__ the Jacobian matrix of f(t, x_i, x_I) is strictly negative definite.

### Step 3











