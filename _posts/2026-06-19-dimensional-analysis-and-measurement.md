---
title: Dimensional Analysis and Measurement
tags:
  - dimensional analysis
---

A few years ago, my lab produced a paper titled "Towards Predicting Collective Performance in Multi-Robot Teams" [1]. I read the paper when I first started my PhD and was immediatley impressed. The paper is fundamentally about developing metrics for analysis for multi-robot teams. I have a similar project I am trying to pursue so I figured it would be important to start from the fundamental works in measurement science. This week, I began reading P. W. Bridgman's work on dimensional analysis [2]. Here are some concepts I have been thinking about in relation to measurements and dimensional analysis.

## Metric Generation
One of the tasks of measurement science is to generate metrics. To understand the utility of this endevor, let's look at an example. Imagine a school locker. If a student claims they want the "best" locker, what does that mean? Well, what is the purpose of a locker? One possible answer is "to effectivley store items." We will define the effectiveness of a locker at storing items as the locker's quality and denote it as $Q$. How do we measure locker quality? A naive solution might be to maximize the internal volume. 

$$Q := whd$$

Here, $w$ is the width, $d$ is the depth, and $h$ is the height. The problem here is that this metric only tells us how much space exists within the locker and not the effectiveness of that space for holding items. Take the lockers in the image below:

{% include figure.html 
   image="/images/blog/2026-06-19/locker.jpeg"
   width="30%"
   caption="source: reddit.com/u/Ceaseless_watcher224"
%}

It might be possible that the tall locker has a greater total volume than the shorter ones, but it likely doesn't store items as effectivley due to its limited width. To develop a suitable metric for locker quality, we need to define some properties. To simplify the problem, let us assume a depth that is reasonable for item storage, $d \gg 0$. We want quality to decrease when height or width approach zero, since that limits a locker's ability to effectivley store items. More formally we can write:

$$\lim_{w \rightarrow 0}Q = - \infty$$
$$\lim_{h \rightarrow 0}Q = - \infty$$

If we had an infinitly large locker, we could store infinite items. Therefore locker quality should approach infinity as the width or heigh approach infinity. More formally:

$$\lim_{w \rightarrow \infty}Q = \infty$$
$$\lim_{h \rightarrow \infty}Q = \infty$$

We should also place some physical constraints on our system. Neither width nor height can be negative. In realistic cases, both of these values will be greater than zero:

$$w > 0$$
$$h > 0$$

Under these constraints, a suitable metric might look like this:

$$Q := log(wh)$$

Now $Q$ satisfies all of our constraints.

This is a somewhat silly example, but it highlights an important concept in measurement science. There exists a disconnect between what we want to know (how well a locker stores items) and what we can physically measure (width, height, etc.). Part of the job of measurement science is to develop the metrics which bridge that gap. 

## Dimensional Analysis Sample Problem

There is a lot of information that can be revealed by knowing about units. P. W. Bridgman goes through some simple examples of dimensional analysis in [2] and it is really enlightening to see just how much information can be attained knowing only the dimensions of the involved quantities. For example assume we want to determine the period of swing of a simple pendulum. The quantities involved are listed as follows: 

| Name of Quantity | Symbol | Dimensions |
|------------|-----------|-----------|
| Time of swing (period) | $t$ | $T$ |
| Length of pendulum | $l$ | $L$ |
| Mass of pendulum | $m$ | $M$ |
| Accelleration due to gravity | $g$ | $LT^{-2}$ |
| Anngular amplitude of swing | $\theta$ | No dimensions |

The objective is to find some function $f$ which computes the swing time using the other quantities. More formally we want to find:

$$t = f(l, m, g, \theta)$$

There are two pieces of fundamental intuition here: 

  1.  We know that the output numerical values must be independent of the units that we use to measure. Meaning that if we were to measure in inches and feet instead of meters, the numerical value that we compute for time should not change. The same applies to all other units. If we decided to use slugs instead of kilograms for measuring mass, the computed number for time should not change, provided that time is still measured in seconds. 
  2. The output of $f$ must be in units of time

Using the second rule we can deduce that $f$ must be independent of mass since its units are unique and cannot cancel out with any other quantities. Therefore:

$$t=f(l,g,\theta)$$

Similarly, $l$ and $g$ must enter the function together such that the dimensions cancel. A solution to this is to divide $l$ and $g$ such that the output units are in time. 

$$t=f\left(\frac{l}{g},\theta\right)$$

Of course this results in units of $T^2$ so the function must use a square root to ensure the output is in units of $T$. The result is that using only knowledge of dimensions and input parameters we can get as close as

$$t = \phi(\theta) \sqrt{\frac{l}{g}}$$

Where $\phi$ is some function which operates on $\theta$ and outputs a dimensionless value. We can compare this to the solution which can be attained from first principles:

$$t = \frac{1}{2\pi}\sqrt{\frac{l}{g}}$$

The result is that using only knowledge of the involved parameters and their dimensions, we can determine almost the entire structure of the resultant relationship. **The real problem here is determining which parameters should be included to compute this relationship.** For certain simple problems, this is somewhat trivial. P.W. Bridgman explains that for more complex settings, such as fluid or thermal relationships, it is not so simple to deduce. 

## Arbitrary Dimensions
Measurments are relative. This is a key, critical insight that is so often forgotten. Assume I want to compare the weights between myself and my wife. We could go to scales and measure ourselves to find the numerical quantity associated with our weight in a particular unit system. For example, I weigh 180 pounds while my wife weighs 120. The actual number here is somewhat arbitrary. If we chose instead of measure in metric units, we would instead say that I weigh 81 kilograms while my wife weighs 54 kilograms. The important idea here is not the numerical quantity, but rather the relationship between the quantities. We can choose whatever reference point we desire as a unit of weight. But no matter what refernce point is chosen, I will still weigh 1.5x my wife's weight. That ratio between our weights is the reality that will exist in any measurment system.

## Primary and Secondary Units
P.W. Bridgman outlines in [2] that physical units exist in two distinct categories, namely primary and secondary dimensions. Primary dimensions are those who are defined with reference to themselves. They are axiomatic in a sense. In total the national institute of standards abd technology recognizes seven primary units:
- Time
- Length
- Mass
- Electrical Current
- Thermodynamic Temperature
- Amount of Substance
- Luminous Intensity

From these seven primary units, all other units can be derived as secondary units. P.W. Bridgman argues that these are somewhat arbitrary. If we decided, for example to use a different set of primary dimensions, that is perfectly acceptable provided that the selected units are also measurable in terms of themselves. Meaning that the relationship between different quantities of a unit can be measured with reference to other measurable quantities of that unit. For example, I can define my own weight in terms of my wife's weight and these are directly measurable quantities.  

Imagine that we used force as defined in newtons as a primary dimension. We know from empical measurments and Euler's first law that:
$$F=ma$$

The usual system of dimensions defines that one newton is equal to one kilogram-meter per second squared:
$$1 N = 1 \frac{Kg*m}{s^2}$$

But if we redefined which dimensions are considered primary, we could come up with a different system. Perhaps in our new unit system, mass is considered a secondary dimension, defined based on $m=\frac{F}{a}$. In this context, we would instead say that the secondary unit known as the kilogram is defined as such:

$$1 Kg = 1 \frac{N*s^2}{m}$$

We can define this because in our new system of measurment, time, distance, and force are considered primary dimensions while mass is considered secondary. The same logic can be applied to, for example, velocity but not viscosity. This is because "it is not at once obvious whether a physical procedure could be set up by which two viscosities could be compared directly with each other without measuring other kinds of quantity.” [Bridgman, 1922, p. 20].