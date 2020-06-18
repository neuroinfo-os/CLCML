# Learning and Control Using Gaussian Processes
## ACM/IEEE 9th International Conference on Cyber-Physical Systems (ICCPS), 2018
## Achin Jain,Truong Nghiem, Manfred Morari and Rahul Mangharam


### Summary 
The article shows how Gaussian Processes (GP) can be used for learning control-oriented models. To overcome basic challenges, that arise when system controled via machine learning  __Fully black-box models__ are used. Opposed to  __Mix of black-box and physics-based models__, that use NN to model the dynamics only of a sub-system or to model only dynamics uncertanties, this approach implies modelling of the full dynamics of a system. Authors showeed that GP can be efficiently used for 1. making an optimal experiment design if amount of data is limited; 2. formulatinf an optimisation problem for a Model Predictive Control(MPC)  3. online closed-loop controll. 

The advantages of GP machine learning algorithms claimed in the article are:
1. It provides an estimate of uncertainty or cofidence
2. Allows to work with small datasets
3. Prior knowledge about parameters of the system could be included in GPs 
 
### Gaussian Process for Dynamical systems
A _Gaussian Process(GP)_ is a collection of random variables, any finite number of which have a joint Gaussian distribution. (Carl Edward Rasmussen and Christopher KI Williams. Gaussian processes for machine learning, volume 1. MIT press Cambridge, 2006.) GP in control or optimisation tasks involves the propagation of uncertainty through the model over a finite number of future steps. This results in complecity increase with each step. To achieve prediction accuracy, several methods can be used. In the described model authors replacrd the autoregressive outputs with respective expected values (_ zero-variance method_). 




### Optimal experiment design (OED): optimisation of data quality collected during experiment within some constraints. This approach allows to minimize amount of data required for taining. 

_Information theoretic approach for OED_ used to design or select the best data points, which can explain the behavior of the underlying physical system with GP. To achieve that the sample should be selected  in a way that maximizes information and minimizes uncertainty in some model parameters. 


_Sequential experiment design with Gaussian Processes_ 
1. Features of the system which influence output should be known.
2. Covarience structure of GP is chosen (eg. by assigning prior distribution based on MLE, or manual initialisation). In this article squared exponential kernel waas used.
3. The new control input generates the output and updates the parameters using maximum a posteriori (MAP)

### MODEL PREDICTIVE CONTROL






