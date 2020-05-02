# Design of an iterative learning control with a selective learning strategy for swinging up a pendulum
## Jonas Beuchert, Joerg Raisch, and Thomas Seel
## 2018 European Control Conference, June 12-15, 2018.

### Short summary
Authors present an Iterative Learning Control (ILC) algorithm for trajectory tracking in a nonlinear system. The algorithm is tested on a pendulum on a cart task (classic task in control in engineering). The novelity in the controller design is that (1) it is restricted to learn only on trajectory segments with small tracking errors; and (2) the system's parameters set in a way that gives an opportunity to overcome singularities in plant inversion. 

___Result:___ It was shown, that described ILC algorithm can learned to swing up a pendulum in less, than six iterations. However, the learning process stops if the cart reaches the end of the rail.

### Task
A pendulum rod is placed on a cart pole, which moves along horisontal direction. The moving of a cart influences the angle of the rod. The aim of the task is to make the cart learn how to move in order to swing the rod from downwards to upwards position. 
The pendulum is described with the following second-order differential equation:


 <img src="https://render.githubusercontent.com/render/math?math=\ddot{y}=c_1(c_2(\ddot{u}*cos(y)%2B g*sin(y))-c*\dot{y})">

<img src="https://render.githubusercontent.com/render/math?math=c_{1}=\frac{1}{J_{s}%2Bm*a^{2}}">

<img src="https://render.githubusercontent.com/render/math?math=c_{2}=m*a">

with the following parameters to be controlled:


<img src="https://github.com/neuroinfo-os/CLCML/blob/master/docs/images/pendulum_param.png" height="200px" width="350px" >



### Controller Desesign

The linearizetion of system's differential equation at a general linearization point (<img src="https://render.githubusercontent.com/render/math?math=(y_S, \dot{y_S}, \ddot{y_S})">) results in the following :
<img src="https://render.githubusercontent.com/render/math?math=\ddot{y}= -\alpha_0(y-y_s)-\alpha_1(\dot{y}-\dot{y_S})%2B\beta_2(\ddot{u}-\ddot{u_S})">

<img src="https://render.githubusercontent.com/render/math?math=\alpha_0=-c_1*c_2(-\ddot{u_S}*\sin(y_S)%2Bg*cos(y_S))">


<img src="https://render.githubusercontent.com/render/math?math=\alpha_1=c_1*c_2">


<img src="https://render.githubusercontent.com/render/math?math=\beta_2=c_1*c_2*cos(y_S)">



For learning purposes the system dynamics is discretized at a finite number of time points (k=n). After every trial _j_  parametrs are updated based on the measured input (_u[k]_) and output _y[k]_. The tracking error is used to calculate the next input _u[k+1]_, which is fed into the system.  Here the L-filter to calculate the next input inverts the dynamics.
The general update law has a form:

<img src="https://render.githubusercontent.com/render/math?math=u_{j+1}[k]=Q(q^{-1}(u_j[k] %2B L(q^{-1})*e_j[k]))">, where <img src="https://render.githubusercontent.com/render/math?math=Q(q^{-1}) and L(q^{-1})"> are discrete-time filters, and <img src="https://render.githubusercontent.com/render/math?math=q^{-1}"> is the back-shift operator. 





__There are two main novelties in the algorithm.__ _First,_ __the learning process was restricted to samples with small tracking error by adjusting the L-filter;__ this  garantees that linearization coold approximate the system dynamics. At each trial the smallest index _k_ calculated in a way that absolute tracking value <img src="https://render.githubusercontent.com/render/math?math=|e_j[k]|"> exceeds a threshold <img src="https://render.githubusercontent.com/render/math?math=e_{max}>0">. The input is updated only for these time steps. In other cases cart position is set to decline to zero. 

Thus,  the update law looks like 

<img src="https://github.com/neuroinfo-os/CLCML/blob/master/docs/images/pendulum_update.png" height="200px" width="350px" >

_Second,_ __the coefficients of the learning law are set in a way, that prevents learning from segments, where change of one variable almost does not influence the other.__  In particular this happens, when the rod is in a horizontal position: card's velocity cannot produce a significant change in the rod's angle. 


<img src="https://github.com/neuroinfo-os/CLCML/blob/master/docs/images/pendulum_param2.png" height="200px" width="350px" >


where, _v, d, p_ are positive constants. Parameter _d_ influences where to attenuate coefficients. Other determine slope and shape of the transitions between the restricted and the unmodified segments. 


_Finally,_ authors add  Q-filter into the learning law to filter out unmodelled high frequencies. 




























