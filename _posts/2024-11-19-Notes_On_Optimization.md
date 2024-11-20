---
math: true
media_subpath: assets/pic/
---



### Lipschitz 

Given a function $f$ is Lipschitz-continuous, intuitively it means that the changes in function value can be bounded by the change in variable:

$$\vert \vert f(x) - f(y) \vert \vert \leq L\vert\vert x - y\vert\vert_2$$

Similarly, we can define the Lipschitz-continuous for the gradient of $f$. Further, if $\nabla f$ is Lipschitz-continuous, then we have the following inequality (1): 

$$\begin{aligned}| f(y) - f(x) - \langle \nabla f(x), y-x\rangle| \leq \frac{L}{2}||x-y||^2\end{aligned}$$

Obviously, we can further conclude the following inequality.

$$\begin{aligned} f(y) & \leq f(x) + \langle \nabla f(x), y-x\rangle +  \frac{L}{2}||x-y||^2 \\  f(y) & \geq f(x) + \langle \nabla f(x), y-x\rangle -  \frac{L}{2}||x-y||^2\end{aligned}$$

Intuitively, the means that **value function $f$ can be upper and lower bounded by the second-order approximation in $x$ ** . This gives us many merits in convergence analysis. For example, in gradient descent, one can choose the next $x_{k+1}$ that minimizes the second-order upper bound. As a result, we have the following inequality to show that the update is a least . In the gradient ascent case, we choose the lower bound to achieve similar results. 

$$\begin{aligned} & x_{k+1} = \arg\min_y f(x_k) + \langle \nabla f(x_k), y - x_k\rangle + \frac{L}{2}||x_k - y||^2  \\ & f(x_{k+1})  \leq  f(x_k) + \langle \nabla f(x_k), x_{k+1} - x_k\rangle + \frac{L}{2}||x_k - x_{k+1}||^2 \leq  f(x_{k+1}) - \frac{L}{2}||\nabla f(x_k)||^2\end{aligned} $$



![image-20241120124906937](a.png)

_Lipschitz-continuous and gradient descent_

To prove (1), as the change of the gradient is upper bounded by the changes of variable, the accumulated change of function value is upper bounded by the square of variable changes during integral. In the detailed proof, the derivation relies on expanding the difference between $f(y)$ and $f(x)$ and write it as the integral of the difference between derivatives.  

<details>
    <summary> Proof</summary>
First we need to write the difference between function value as the integral of derivative. We first consider the simplest case, where $f(x): \mathbb{R} \to \mathbb{R}$. Then we have:


$$\begin{aligned} f(y) - f(x) &= \int_x^y \nabla f(t)dt \\  & =\int_0^1 \nabla f((y-x)u + x)d((y-x)u) + x) \\ &= \int_0^1 \nabla f((y-x)u + x)(y-x)du \end{aligned}$$



Therefore for the $\mathbb{R}^n$ case, we have : 

$$\begin{aligned}f(y) &= f(x) + \int_0^1 \langle \nabla f(x + \tau(y-x)), y-x \rangle d\tau \\ &= f(x) + \langle \nabla f(x), y - x\rangle + \int_0^1 \langle \nabla f(x + \tau(y-x)) - \nabla f(x), y-x \rangle d\tau \end{aligned}$$

Staring from the lefthand side, and utilizing Cauchy-Schwarz inequality in $(a)$, we can complete the proof

$$\begin{aligned} \vert f(y) - f(x) - \langle \nabla f(x), y-x\rangle \vert&= \bigg |\int_0^1  \langle \nabla f(x + \tau(y-x)) - \nabla f(x), y-x \rangle d\tau \bigg | \\ &\leq \int_0^1 \vert \langle \nabla f(x + \tau(y-x)) - \nabla f(x), y-x \rangle\vert d\tau \\ &\overset{(a)}{\leq} \int_0^1\vert\vert \nabla f(x + \tau(y-x)) - \nabla f(x)\vert\vert\cdot \vert\vert y-x\vert\vert d\tau \\ &= \int_0^1L\vert\vert x - y\vert\vert^2\tau d\tau = \frac{L}{2}||x - y||^2\end{aligned}$$
</details>









