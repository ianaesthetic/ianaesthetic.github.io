---
math: true
---



### Lipschitz 

Given a function $f$ is Lipschitz-continuous, intuitively it means that the changes in function value can be bounded by the change in variable:

$$\vert \vert f(x) - f(y) \vert \vert \leq L\vert\vert x - y\vert\vert_2$$

Similarly, we can define the Lipschitz-continuous for the gradient of $f$. Further, if $f'$ is Lipschitz-continuous, then we have the following inequality: 

$$\begin{aligned}| f(y) - f(x) - \langle f'(x), y-x\rangle| \leq \frac{L}{2}||x-y||^2\end{aligned}$$

Obviously, we can further conclude:

$$\begin{aligned} f(y) & \leq f(x) + \langle f'(x), y-x\rangle +  \frac{L}{2}||x-y||^2 \\  f(y) & \geq f(x) + \langle f'(x), y-x\rangle -  \frac{L}{2}||x-y||^2\end{aligned}$$

<details>Small techniques: consider $f(x): \mathbb{R} \to \mathbb{R}$, then we have:

$$\begin{aligned} f(y) - f(x) &= \int_x^y f'(t)dt \\  & =\int_0^1 f'((y-x)u + x)d((y-x)u) + x) \\ &= \int_0^1 f'((y-x)u + x)(y-x)du \end{aligned}$$



Therefore for the $\mathbb{R}^n$ case, we have : 

$$\begin{aligned}f(y) = f(x) + \int_0^1 \langle f'(x + \tau(y-x)), y-x \rangle d\tau \\ &= \end{aligned}$$
</details>



Small techniques: consider $f(x): \mathbb{R} \to \mathbb{R}$, then we have:

$$\begin{aligned} f(y) - f(x) &= \int_x^y f'(t)dt \\  & =\int_0^1 f'((y-x)u + x)d((y-x)u) + x) \\ &= \int_0^1 f'((y-x)u + x)(y-x)du \end{aligned}$$



Therefore for the $\mathbb{R}^n$ case, we have : 

$$\begin{aligned}f(y) &= f(x) + \int_0^1 \langle f'(x + \tau(y-x)), y-x \rangle d\tau \\ &= f(x) + \langle f'(x), y - x\rangle + \int_0^1 \langle f'(x + \tau(y-x)) - f'(x), y-x \rangle d\tau \end{aligned}$$

$$\begin{aligned} \vert f(y) - f(x) - \langle f'(x), y-x\rangle \vert&= \bigg |\int_0^1  \langle f'(x + \tau(y-x)) - f'(x), y-x \rangle d\tau \bigg | \\ &\leq \int_0^1 \vert \langle f'(x + \tau(y-x)) - f'(x), y-x \rangle\vert d\tau \\ &\overset{(a)}{\leq} \int_0^1\vert\vert f'(x + \tau(y-x)) - f'(x)\vert\vert\cdot \vert\vert y-x\vert\vert d\tau \\ &= \int_0^1L\vert\vert x - y\vert\vert^2\tau d\tau = \frac{L}{2}||x - y||^2\end{aligned}$$



















