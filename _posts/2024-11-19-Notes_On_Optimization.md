### Lipschitz 

Given a function $f$ is Lipschitz-continuous, intuitively it means that the changes in function value can be bounded by the change in variable:

$$\vert \vert f(x) - f(y) \vert \vert \leq L\vert\vert x - y\vert\vert_2$$

Similarly, we can define the Lipschitz-continuous for the gradient of $f$. Further, if $f'$ is Lipschitz-continuous, then we have,





Lemma: 

$$$$



<details>Small techniques: consider $f(x): \mathbb{R} \to \mathbb{R}$, then we have:

$$\begin{aligned} f(y) - f(x) &= \int_x^y f'(t)dt \\  & =\int_0^1 f'((y-x)u + x)d((y-x)u) + x) \\ &= \int_0^1 f'((y-x)u + x)(y-x)du \end{aligned}$$



Therefore for the $\mathbb{R}^n$ case, we have : 

$$\begin{aligned}f(y) = f(x) + \int_0^1 \langle f'(x + \tau(y-x)), y-x \rangle d\tau \\ &= \end{aligned}$$
</details>



Small techniques: consider $f(x): \mathbb{R} \to \mathbb{R}$, then we have:

$$\begin{aligned} f(y) - f(x) &= \int_x^y f'(t)dt \\  & =\int_0^1 f'((y-x)u + x)d((y-x)u) + x) \\ &= \int_0^1 f'((y-x)u + x)(y-x)du \end{aligned}$$



Therefore for the $\mathbb{R}^n$ case, we have : 

$$\begin{aligned}f(y) = f(x) + \int_0^1 \langle f'(x + \tau(y-x)), y-x \rangle d\tau \\ &= \end{aligned}$$