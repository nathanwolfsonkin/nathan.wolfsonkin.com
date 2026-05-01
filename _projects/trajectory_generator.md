---
title: Vehicle Trajectory Generator
skills: 
  - MATLAB
repo: nathanwolfsonkin/Vehicle-Trajectory-Generation
---

{% include centered_image.html 
   src="/images/personal/trajgen/trajGen.gif" 
   width="80%" %}

{% include section.html %}

This project was an exercise in trajectory generation. Given a starting and ending state, the model generates a fifth-order polynomial to smoothly drive from start to finish. 

The vehicle was designed to begin and end in a stopped state. Additionally, the beginning and ending poses are user-defined. Therefore, it is known a priori that

$$ 
\dot{x}_0 = \dot{y}_0 = \dot{\theta}_0 = \dot{x}_f = \dot{y}_f = \dot{\theta}_f = 0
$$
$$
x_0 = y_0 = \theta_0 = x_f = y_f = \theta_f = constant
$$

From there, the corresponding velocity and acceleration are:

$$ 
x(t) = c_5 t^5 + c_4 t^4 + c_4 t^3 + c_2 t^2 + c_1 t + c_0 
$$

From there, the required velocity and accelleration can be written as:

$$ 
\dot{x}(t) = c_5 5t^4 + c_4 4t^3 + c_3 3t^2 + c_2 2t + c_1 
$$

$$
\ddot{x}(t) = c_5 20t^3 + c_4 12t^2 + c_3 6t + c_2 2
$$

If we predefine a target arrival time, $T$, set the initial time as $t=0$, and assemble everything into a matrix, we obtain:

$$
\begin{bmatrix} c_0 \\ c_1 \\ c_2 \\ c_3 \\ c_4 \\ c_5 \end{bmatrix} = 
\begin{bmatrix} 0 & 0 & 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 2 & 0 & 0 \\ T^5 & T^4 & T^3 & T^2 & T & 1 \\ 5T^4 & 4T^3 & 3T^2 & 2T & 1 & 0 \\ 20T^3 & 12T^2 & 6T & 2 & 0 & 0 \end{bmatrix} 
\begin{bmatrix} x_0 \\ \dot{x}_0 \\ \ddot{x}_0 \\ x_f \\ \dot{x}_f \\ \ddot{x}_f \end{bmatrix}
$$

Here, the output vector contains the coefficients required to generate the smooth polynomial. The exact same process is applied in the $y$-direction. Finally, $\theta$ is computed using the kinematic relationship between linear and angular velocity for the bicycle model:

$$
\theta = \operatorname{atan2}(\dot{y}, \dot{x})
$$
$$
\dot{\theta}
=
\frac{1}{\left(\left(\frac{\dot{y}}{\dot{x}}\right)^2 + 1\right)}
\cdot
\frac{\dot{x} \cdot \ddot{y} - \dot{y} \cdot \ddot{x}}{\dot{x}^2}
$$


With that, the full state trajectory is computed:

$$
X(t) = \begin{bmatrix} x(t) \\ y(t) \\ \theta(t) \\ \dot{x}(t) \\ \dot{y}(t) \\ \dot{\theta}(t) \end{bmatrix}
$$


