---
title: Dimensionless Variable Discovery
tags:
 - dimensional analysis
---

I was reading more about dimensional analysis this week. Enjoy.

## Buckingham-Pi Theorem

Buckingham-Pi theorem [1] is fundamentally a process by which the complete set of dimensionless variables can be identified given a set of input parameters which the dimensionless variable depends on. The basic process works as follows:

1. List out all parameters of interest as well as their units
2. Define a matrix, $D$, containing all of the relevant parameters and their exponents
3. Compute the null space of $D$
4. The vectors spanning the null space represent the set of possible dimensionless variables

### Locomotion Example

In locomotion there is a metric called cost of transport. The value of this metric is that it can be used to compare energy efficiency across length scales, weight scales, and modes of locomotion. For example it could be used to compare the energetic efficiency of a hummingbird flying to an elephant walking. Cost of transport, $c$, which is defined as:

$$c = \frac{e}{mgd}$$

Where $e$ represents energy consumed, $mg$ is weight, and $d$ is distance traveled. We can apply Buckingham-Pi theorem to find all possible sets of dimensionless variables for this problem. First we need to list out all parameters of interest along with their units

| Parameter | Symbol | Dimensions |
|------------|-----------|-----------|
| Mass | $m$ | $M$ |
| Energy Consumed | $e$ | $ML^{2}T^{-2}$ |
| Acceleration due to Gravity | $g$ | $LT^{-2}$ |
| Distance Traveled | $d$ | $L$ |

The objective of Buckingham-Pi is to compute all possible sets of exponents ($\alpha$, $\beta$, $\gamma$, $\delta$) such that the result contains no units:

$$m^\alpha e^\beta g^\gamma d^\delta$$

Now we can set up the $D$ matrix:

$$D=\begin{bmatrix} 0 & 2 & 1 & 1 \\ 1 & 1 & 0 & 0 \\ 0 & -2 & -2 & 0 \end{bmatrix} $$

$D$ is defined such that each row represents a dimension and each column a parameter. The elements represent the exponent applied to the dimensions of each parameter.

$$ \begin{array}{c \| c c c c}    & m & e & g & d \\ \hline L & 0 & 2 & 1 & 1 \\ M & 1 & 1 & 0 & 0 \\ T & 0 & -2 & -2 & 0 \end{array} $$

Since each element represents an exponent applied to a parameter, the null space of this matrix represents the linear combination of exponents which results in all exponents resulting in zero. This will reveal the dimensionless variables. The null space for this example is:

$$null(D) = \begin{bmatrix} -1 \\ 1 \\ -1 \\ -1 \end{bmatrix}$$

For this simple example the null space is a single dimension, but that is not the case for all possible cases. In this case, $D$ was constructed such that the order of parameters was $\begin{bmatrix}m & e & g & d\end{bmatrix}$. We can read our null space vector in the same order. This means that $m^{-1}e^{1}g^{-1}d^{-1}$ will result in a dimensionless variable.

$$m^{-1}e^{1}g^{-1}d^{-1} = \frac{e}{mgd} = c$$

We can compare our result to first principles to see that the result truly contains no units. Writing out the units of $c$ it is clear that our result in dimensionless:

$$ c = \frac{e}{mgd} \frac{ML^2T^{-2}}{MLT^{-2}L}$$

Based on our analysis, there is no particular reason to use this version of cost of transport other than convention and simplicity. The same Buckingham-Pi analysis can result in infinite other dimensionless variables provided that they exist on the span as the null space of $D$. Here are a few examples

$$m^{1}e^{-1}g^{1}d^{1} = \frac{mgd}{e} = c^{-1}$$

$$m^{-2}e^{2}g^{-2}d^{-2} = \frac{e^2}{m^2g^2d^2} = c^{2}$$

$$m^{-\pi}e^{\pi}g^{-\pi}d^{\pi} = \frac{e^\pi}{m^\pi g^\pi d^\pi} = c^{\pi}$$

I can't imagine a scenario where it would be useful or practical to represent our dimensionless variable in terms of a $\pi$ exponent, but it's perfectly valid to do so.

## More on Measurement Theory

I read a great document that better explains some of the measurement theory ideas I was writing about last week. Bridgman [2] explained measuring units with respect to itself, Sonin [3] explained this concept more rigorously. He defined that any acceptable primary unit must be capable of performing two physical operations:

1. Equality $\textbf{A} = \textbf{B}$
2. Addition $\textbf{C} = \textbf{A} + \textbf{B}$

Using these purely physical operations, we can define:

1. Comparisons of magnitude
  - If $\textbf{A} + \textbf{B} = \textbf{C}$, then $\textbf{C} > \textbf{A}$
2. Subtraction
  - If $\textbf{A} + \textbf{B} = \textbf{C}$, then $\textbf{A} = \textbf{C} - \textbf{B}$
3. Multiplication by numbers (not other quantities)
  - If $\textbf{B} = \textbf{A} + \textbf{A}  + \textbf{A}$, then $\textbf{B} = 3\textbf{A}$
4. Division by numbers (not other quantities)
  - If $\textbf{A} = \textbf{B} + \textbf{B}  + \textbf{B}$, then $\textbf{A} = \frac{\textbf{B}}{3}$

By these rules, properties such as mass, velocity, force, area, time, and length are viable candidates for primary units. Simultaneously, properties such as color and shape are not possible to quantify in the same way. How does one add a square to a circle?

## Next week

I'll be on vacation next week so no post. My next post will be on Friday, July 9th.

## Citations

[1] E. Buckingham, “On Physically Similar Systems; Illustrations of the Use of Dimensional Equations,” Phys. Rev., vol. 4, no. 4, pp. 345–376, Oct. 1914, doi: 10.1103/PhysRev.4.345.


[2] P. W. Bridgman, Dimensional Analysis. Yale University Press, 1922.


[3] A. A. Sonin, “Department of Mechanical Engineering MIT Cambridge, MA 02139”.



