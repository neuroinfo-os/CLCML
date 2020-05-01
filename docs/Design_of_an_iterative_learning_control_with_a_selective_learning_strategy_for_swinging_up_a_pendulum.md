# Design of an iterative learning control with a selective learning strategy for swinging up a pendulum
## Jonas Beuchert, Joerg Raisch, and Thomas Seel
## 2018 European Control Conference, June 12-15, 2018.

### Short summary
Authors present an Iterative Learning Control (ILC) algorithm for trajectory tracking in a nonlinear system on a swinging up a pendulum on a cart task.
It was shown, that described ILC algorithm can learned to swing up a pendulum by angle trajectory tracking in six iterations. 
The novelity in the controller design is that it learns on trajectory segments with small tracking errors.

### Task
The pendulum is described with the following second-order differential equation:


 <img src="https://render.githubusercontent.com/render/math?math=\ddot{y}=c_1(c_2(\ddot{u}*cos(y)%2B g*sin(y))-c*\dot{y})">

<img src="https://render.githubusercontent.com/render/math?math=c_{1}=\frac{1}{J_{s}%2Bm*a{2}}">

<img src="https://render.githubusercontent.com/render/math?math=c_{2}=m*a">

with the following parameters to be controlled:
<img src="https://github.com/neuroinfo-os/CLCML/blob/master/docs/images/pendulum_param.png" height="200px" width="350px" >



### Controller Desesign

The linearizetion of system's differential equation at a general linearization point (<img src="https://render.githubusercontent.com/render/math?math=(y_S, \dot{y_S}, \ddot{y_S})">) results in the following :
<img src="https://render.githubusercontent.com/render/math?math=\ddot{y}= -\alpha_0(y-y_s)-\alpha_1(\dot{y}-\dot{y_S})%2B\beta_2(\ddot{u}-\ddot{u_S})">

<img src="https://render.githubusercontent.com/render/math?math=\alpha_0=-c_1*c_2(-\ddot{u_S}*\sin(y_S)%2Bg*cos(y_S))">


<img src="https://render.githubusercontent.com/render/math?math=\alpha_1=c_1*c_2">


<img src="https://render.githubusercontent.com/render/math?math=\beta_2=c_1*c_2*cos(y_S)">




























