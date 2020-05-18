# Learning and Control Using Gaussian Processes
## ACM/IEEE 9th International Conference on Cyber-Physical Systems (ICCPS), 2018
## Achin Jain,Truong Nghiem, Manfred Morari and Rahul Mangharam


### Summary 
The article shows how Gaussian Processes (GP) can be used for learning control-oriented models. To overcome basic challenges, that arise when system controled via machine learning  __Fully black-box models__ are used. Opposed to  __Mix of black-box and physics-based models__, that use NN to model the dynamics only of a sub-system or to model only dynamics uncertanties, this approach implies modelling of the full dynamics of a system. Authors showeed that GP can be efficiently used for 1. making an optimal experiment design if amount of data is limited; 2. formulatinf an optimisation problem for a Model Predictive Control(MPC)  3. online closed-loop controll. 

 
### Terminology
A _Gaussian Process_ is a collection of random variables, any finite number of which have a joint
Gaussian distribution. (Carl Edward Rasmussen and Christopher KI Williams. Gaussian processes for machine learning, volume 1. MIT press Cambridge, 2006.)

The advantages of GP machine learning algorithms claimed in the article are:
1. It provides an estimate of uncertainty or cofidence
2. Allows to work with small datasets
3. Prior knowledge about parameters of the system could be included in GPs


_Optimal experiment design (OED)_: optimisation of data quality collected during experiment within some constraints. This approach allows to minimize amount of data required for taining. 

_Information theoretic approach for OED_ used to design or selectthe best data points, which can explain the behavior of the underlying physical system with GP. To achieve that the sample should be selected  in a way that maximizes infirmation and minimizes uncertainty in some model parameters. 

###






