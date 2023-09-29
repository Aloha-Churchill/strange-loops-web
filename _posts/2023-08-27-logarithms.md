---
layout: post
title:  Trying to build a better intuition for logarithmic and exponential functions
subtitle: Rabbits and compounding interest and the natural log oh my!
cover-img: /assets/img/logarithms/trees.jpg
thumbnail-img: /assets/img/logarithms/thumb.jpg
tags: [math]
---

# Logarithms

<div style="display: flex; justify-content: center; text-align: center;">
 <div class="image">
    <img src="../assets/img/logarithms/rabbit.jpg" width="500"/>
    <p>Rabbit population dynamics are commonly modeled with logarithms</p>
</div>
</div>

From chipping away slowly at Richard Hamming's book, *The Art of Doing Science and Engineering*, one motif is the importance of understanding the fundamentals of math. Choosing the base function for a modeling task is fundamental to understanding the nature of the problem, and I realized the family of logarithms and exponentials was an area where my intuition was weak. The lockdown lectures by Youtube legend Grant Sanderson, the creator of 3Blue1Brown, were a great starting place.

---

Notes on [Logarithm Fundamentals](https://www.youtube.com/watch?v=cEvgcoyZvB4&list=PLZHQObOWTQDP5CVelJJ1bNDouqrAhVPev&index=7)
* Traditional y-axes are additive (1, 2, 3, ...). If we instead make the y-axis multiplicative (1, 10, 100, ...), then the graphical representation of an exponential function is linear.


* Inverse operations: (addition, subtraction), (multiplication, division), (exponentiation, logarithm)
  * Properties of logarithms have corresponding exponentiation rules
  * The change of base formula $$log_b(a) = \frac{log_c(a)}{log_c(b)}$$ works because "anything additive in the logarithm realm is the same as anything multiplicative in terms of what is inside the parentheses"
* When extending the definition of logarithms to complex numbers, a bit more reasoning has to be done for a simple calculation $$ log_e(1) = 0, e^{2i\pi}, e^{4i\pi}, ... $$
* Extending the idea of complex numbers in logarithms, we can define solutions to logarithms with negative bases and then leverage Euler's formula to solve them.
* The last challenge question was cute, and here's an extended inductive proof showing that the statement is true for the general case of $$ n \geq 2$$.
 
$$
\frac{1}{log_2(100!)} + \frac{1}{log_3(100!)} + ... + \frac{1}{log_{100}(100!)} =? 
$$

Inductive Proof
* Base Case
$$ n = 2 \\
\frac{1}{log_2(2!)} = 1
$$
* Inductive Hypothesis

Assuming 
$$
\frac{1}{log_2(k!)} + \frac{1}{log_3(k!)} + ... + \frac{1}{log_{k}(k!)} = 1 
$$ 
is true for $$n=k, k \geq 2$$

* Recursive Step

Then, for $$n=k+1$$ , we have 
$$
\frac{1}{log_2((k+1)!)} + \frac{1}{log_3((k+1)!)} + ... + \frac{1}{log_{k+1}(k+1)!)} =? 
$$
$$
\frac{log(2)}{log((k+1)!)} + \frac{log(3)}{log((k+1)!)} + ... + \frac{log(k+1)}{log((k+1)!)} =? 
$$
$$
\frac{log(2*3*4*...*(k+1))}{log((k+1)!)} = 1$$

---

Notes on [What makes the natural log "natural"](https://www.youtube.com/watch?v=4PDoT7jtxmw&list=PLZHQObOWTQDP5CVelJJ1bNDouqrAhVPev&index=8)
* Primes and the natural log are related. This part I still don't understand
* Proof that $$ 1 + \frac{1}{2} + \frac{1}{3} + ... $$ is infinite
  * Just group terms in increasing powers of two and show that each is greater than 1/2. This exponential grouping also shows the logarithmic growth of this series
* What is special about $e$? 
  * The most fundamental propert-e ;) is $$\frac{d}{dx} e^x = e^x$$. i.e. the rate of change at a point is equal to the y value at that point.
    * Definition of a derivative: take $$ a^x$$ 
    * $$ a^x \cdot \lim_{h \to 0} \frac{a^h-1}{h} $$ 
    * e is defined to be the number such that this limit is 1 and thus $$e^x$$ is its own derivative
  * Taylor series approach: $$e^x = 1 + x + \frac{x^2}{2!} + ...$$ 
* On the complex plane, the derivative of $$ e^{i\theta}$$ is $$ie^{i\theta} $$, so the slope at that point on the complex unit circle is always a rotation of $$\frac{\pi}{2}$$ of the vector and always of unit length. Here, the base of *e* determines how fast around the origin a point is moving wheras *i* dictates the rotational property (this makes sense when plugging *i* into the Taylor series to see why points don't blow up towards infinity as well).
* So we have $$ \frac{d}{dx}ln(x) = \frac{1}{x} $$ because $$\frac{dy}{dx} = \frac{1}{e^y}$$
  * Therefore, $$1 + \frac{1}{2} + \frac{1}{3} + ... + \frac{1}{N} = ln(N) + \gamma$$ since the integral acts as an approximation for the Riemman sum of the series.
* Important principle: when it benefits a mathematician's, engineer's, or other professional's specific problem to generalize the form, it can benefit an entire community. 


---
Summary
> Fundamentally, when looking at which class of functions to use when modeling a scenario, logarithms and exponentials serve as the basis to problems where there is a *multiplicative relationship between variables*. For example, the distance a train travels at a constant velocity with respect to time, $$d=vt$$ is additive, in that during each time step, a constant amount is added onto the distance. However, charging and discharging a capcitor is intrinsically exponential and the charge can be represented by the general form $$Q=Ae^{-pt} + B$$ because during each time step, the charge changes proportionally to the current charge. It's natural to think of this in terms of the solution to the differential equation: $$V=R\frac{dQ}{dt} + \frac{Q}{C}$$ where $$C, R, V$$ are constants and we are trying to solve for *Q*. This turns out to be a first-order linear non-homogeneous differential equation. As a more basic representation, the general solution to the first order ODE $$y' = ky$$ is $$y=Ce^{kt}$$ and is fundamentally exponential because the rate of change is proportional to the current value. So why would certain processes be intrinsically exponential or logarithmic? One idea is that systems where the ouput of a process becomes the input for the next iteration tend to be exponential/logarithmic in nature due to the relationship between the current value and rate of change. I'd be curious to hear people's encounters with logarithms and exponentials in the wild! If there are any errors or misunderstandings in this post, please feel free to reach out to me (contact information is in about page).


<div style="display: flex; justify-content: center; text-align: center;">
 <div class="image">
    <img src="../assets/img/logarithms/tweet0.png" width="500"/>
    <p>Question Tweet</p>
</div>
</div>