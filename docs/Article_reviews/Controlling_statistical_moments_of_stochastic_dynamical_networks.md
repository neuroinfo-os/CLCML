# Controlling statistical moments of stochastic dynamical networks
## PHYSICAL REVIEW E 94, 012306 (2016)
## Dmytro Bielievtsov, Josef Ladenbauer, and Klaus Obermayer
### _DOI: 10.1103/PhysRevE.94.012306_


The aim of the work is to explore how the first and second statistical moments of stochastic dynamical networks can be controlled by interfering only with a subset of nodes. The approach was demonstrated on a stochastic Hopfield network and a stochastic whole brain network model of 66 nodes obtained human diffusion imaging and functional magnetic resonance imaging data at rest.The simulations were performed using Python with the libraries “SciPy” and “Theano”. 


The described approach, known as _pinning control_ (or _clamping control_), consists of the following steps:
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

<img src="https://render.githubusercontent.com/render/math?math=\dot{C}=\nabla f(t,\mu)C %2B C \nabla f(t,\mu) %2B Q ">

where  <img src="https://render.githubusercontent.com/render/math?math=\nabla f(t,\mu)"> is the Jacobian of f and Q is the total noise covariance matrix. 


### Step 2
 A subset K of the vertex set I := {1,...,N} for the system is a set of __switching nodes__(SN), if the network is guaranteed to converge to a solution with SN are forced to attain the values of one of the solution when t tends to infinity. For that the following requirements should be sutisfied:
1. __Assumption 1__  For all initial conditions state of the system stays within a ball of finite radius as time tends to infinity.
2. __Assumption 2__ the Jacobian matrix of f(t, x_i, x_I) is strictly negative definite.
If assumtions fullfilled that the set of SNs is identical to the __feedback vertex set (FVS)__ of the graph of the system. 

The set of SNs (<img src="https://render.githubusercontent.com/render/math?math=K^*">) consists of the means and variances of the nodes in K and  the covariances between these nodes and all others:

<img src="https://render.githubusercontent.com/render/math?math=K^*=\{\mu_i, C_{i,j}, C_{j,i}: j\in K, i\in I\}">


### Step 3

The goal of this step is to  design a stochastic feedback controller wich drives the system to a target metastable space in the moments space. 

 Linear feedback controller is described as:

<img src="https://render.githubusercontent.com/render/math?math=u_K (t, x_J (t) ):=\[\mu_g (t)+ C^{\frac{1}{2}}_g (t)\nu_g (t)\] %2B W(t)^T x_J (t)">

where
<img src="https://render.githubusercontent.com/render/math?math=[\mu_g (t)+ C^{\frac{1}{2}}_g (t)\nu_g (t)\] )">  is an
uncorrelated Gaussian process with mean and covariance <img src="https://render.githubusercontent.com/render/math?math=\mu_g (t), C_g (t)"> . W(t) ia a feedback weighting matrix to be determined with:

<img src="https://render.githubusercontent.com/render/math?math=W(t)=C^{-1}_{JJ}C^*_{JK}(t) )"> 

Taking pinning into account yields:

<img src="https://render.githubusercontent.com/render/math?math=\dot{\mu_J}=f_J %2B \frac{1}{2}\nabla\nabla f_JC"> ,




<img src="https://render.githubusercontent.com/render/math?math=\dot{C_JJ}=\nabla_J f_JC_JJ %2B C_JJ\nabla_J f^T_J  %2B Q_JJ %2B \nabla_K f_JC_KJ %2B C_KJ \nabla_K F^T_J)"> 


NOTE! The descibed control system depends on a state vector <img src="https://render.githubusercontent.com/render/math?math=x_J(t)"> evaluated at  <img src="https://render.githubusercontent.com/render/math?math=x-\mu">. This implies full observability of the system!  




