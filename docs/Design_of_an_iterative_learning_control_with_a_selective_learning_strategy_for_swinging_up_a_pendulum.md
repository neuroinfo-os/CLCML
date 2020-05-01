# Design of an iterative learning control with a selective learning strategy for swinging up a pendulum
## Jonas Beuchert, Joerg Raisch, and Thomas Seel
## 2018 European Control Conference, June 12-15, 2018.

### Short summary
Authors present an Iterative Learning Control (ILC) algorithm for trajectory tracking in a nonlinear system on a swinging up a pendulum on a cart task.
It was shown, that described ILC algorithm can learned to swing up a pendulum by angle trajectory tracking in six iterations. 
The novelity in the controller design is that it learns on trajectory segments with small tracking errors.

### Task
The pendulum is described with the following secon-order differential equation:


 <img src="https://render.githubusercontent.com/render/math?math=\ddot{y}=c_1(c_2(\ddot(u)*cos(y)+ g*sin(y))-c*\dot{y})">

<img src="https://render.githubusercontent.com/render/math?math=cos(x)">