The proportional-Integral-Derivative controller widely used in closed-loop control systems. Additionally to current error, it uses error derivative and past errors.

### <img src="https://render.githubusercontent.com/render/math?math=u(t)=K_{p}e(t) %2B K_i \int_{0}^{t} e(\tau)d\tau %2B K_{D}\frac{d}{dt}e(t)">


_u(t)_ - the output of the controller, _e(t)_ - is an error


<img src="https://render.githubusercontent.com/render/math?math=K_{p}, K_{i} , K_{D}"> are constants for proportional, integral and differential parts subsequenly. 

Constants act as filters and their choice depends on a set goal. The proportional filter serves as an all-pass; integral term filters low frequencies and differential term compensate high frequencies. 