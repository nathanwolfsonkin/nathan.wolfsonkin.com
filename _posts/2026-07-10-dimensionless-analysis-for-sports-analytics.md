---
title: Dimensionless Analysis for Sports Analytics
tags:
 - dimensional analysis
image: /images/blog/2026-07-10/goals-vs-field-length.png
---

The world cup is going on right here in Philadelphia. I figured it would be fun to see how some of the ideas in dimensional analysis that I have been learning about recently are applied in the world of sports analytics. This post is more or less a review of a paper in that space.

Julien Blondeau's work [1] attempts to identify how number of scored goals in field and goal based sports such as soccer and hockey correlate with various parameters of interest. He identifies them as follows:

| Parameter | Symbol | Dimensions |
|------------|-----------|-----------|
| Game Duration | $t_g$ | $T$ |
| Field Length | $l_f$ | $L$ |
| Field Width | $w_f$ | $L$ |
| Goal Width | $w_g$ | $L$ |
| Goal Height | $h_g$ | $L$ |
| Player Velocity | $v_p$ | $LT^{-1}$ |
| Ball Velocity | $v_b$ | $LT^{-1}$ |
| Number of Players | $n_p$ | $-$ |
| Player Radius of Action | $r_p$ | $L$ |
| Number of Goals | $N_g$ | $-$ |

From here the dimensions matrix can be constructed

$$D = \begin{bmatrix} 0 & 1 & 1 & 1 & 1 & 1 & 1 & 0 & 1 & 0 \\ 1 & 0 & 0 & 0 & 0 & -1 & -1 & 0 & 0 & 0 \end{bmatrix}$$

Computing the null space of our dimensional matrix reveals the sets of dimensionless variables. Since our $D$ matrix is $2 \times 9$, we are left with $7$ total dimensionless parameters:

| Symbol | Formula | Interpretation |
|------------|-----------|
| $t_g^*$ | $\frac{t_gv_p}{l_f}$ | Ratio between field length and average distance players will cross in a game |
| $\alpha_f$ | $\frac{w_f}{l_f}$ | Ratio between field length and field width |
| $w_g^*$ | $\frac{w_g}{l_f}$ | Ratio between goal width and field length |
| $\alpha_g^*$ | $\frac{h_g}{w_g}$ | Ratio between goal width and goal height |
| $v_b^*$ | $\frac{v_b}{v_p}$ | Ratio between player velocity and ball velocity |
| $r_p^*$ | $\frac{r_p}{l_f}$ | Ratio between player radius of action and field length |
| $n_p$ | $n_p$ | Number of players |

Blondeau proposes a dimensionless number, $B_k$ which is intended to predict how changing out parameters will alter the number of goals in a game. In the interest of simplicity, I am brushing past some of the math, but please refer to [1] if you're interested. $B_k$ is defined as a ratio between the duration of the game and the time needed to cross the midfield at the representative field veloity, $v_f$. Here, $v_f$ is something approximating a weighted average of player velocity and ball velocity.

Formally, $B_k$ is defined as:

$$B_k = t_g^* \frac{l_f}{l_{mf}} \frac{v_f}{v_p}$$

Supporting equations are as follows:

$$\frac{l_{mf}}{l_f} = 1 - \frac{1}{2} v_b^* w_g^* \sqrt{1+\alpha_g^*}$$

$$\frac{v_f}{v_p} = ( 1 + v_b^* ) \frac{\rho_p}{ 2 v_b^* } (1-\kappa \frac{\rho_p}{v_b^*})$$

$$\rho_p=(n_p-2)\frac{\pi {r_p^*}^2}{\alpha_f} $$

Here, $\kappa$ is a tuning parameter. The important part to recognize here is not the nuances of all of these equations, but rather that we can write $B_k$ purley as a function of the non-dimensional parameters discovered using Buckingham-Pi:

$$B_k = f(t_g^* , \alpha_f, w_g^* , \alpha_g^* , v_b^* , r_p^* , n_p)$$

## Data & Results

Here is the data used for the dimensional parameters (Lengths and times are measured in meters and seconds respectivley):

| Sport | $l_f$ | $w_f$ | $w_g$ | $h_g$ | $v_p$ | $v_b$ | $t_g$ | $n_p$ | $r_p$ | $N_g$ |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| Ice Hockey | 52 | 27.5 | 1.83 | 1.22 | 7.56 | 44.7 | 3600 | 12 | 1.5 | 6.4 |
| Soccer | 105 | 69.5 | 7.32 | 2.44 | 3.79 | 24.7 | 5400 | 22 | 1 | 2.6 |

Based on these numbers, the tuning parameter was altered to maximize the correlation between number of goals, $N_g$, and $B_k$. The best linear correlation found used $\kappa = 99$ and resulted in

$$N_g = 2.04 B_k$$

This is the most important part of the entire paper. The utility of this function is that now proposed ruleset changes could be made to attempt to make the game more exciting. For example, in 2022, the FIFA World Cup had average of $2.69$ goals per game. If the FIFA administration decided that games would be more exciting with one more goal per game, this model tells us that that result can be achieved by reducing field length to just under 90 meters. 

{% include figure.html
  image="/images/blog/2026-07-10/goals-vs-field-length.png"
  width="50%"
  caption="source: [1]"
%}

## Citations
[1] J. Blondeau, “The influence of field size, goal size and number of players on the average number of goals scored per game in variants of football and hockey: the Pi-theorem applied to team sports,” Journal of Quantitative Analysis in Sports, vol. 17, no. 2, pp. 145–154, Jun. 2021, doi: 10.1515/jqas-2020-0009.

