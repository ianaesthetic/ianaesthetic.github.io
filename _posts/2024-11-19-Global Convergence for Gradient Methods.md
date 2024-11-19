---
math: true
---



### Polyak-Lojasiewicz Condition 

#### Unconstrained Case

In the unconstrained case, the objective can be written as $\begin{aligned} \min_{x \in \mathbb{R}^d} f(x)\end{aligned}$. Here we assume the derivative of $f$ is $L-$Lipschitz-continuous: 

$$\begin{aligned} f(y) \leq f(x) + \langle \nabla f(x), y - x\rangle + \frac{L}{2}\end{aligned}||x - y||^2 = g(y, x)$$

We say $f(x)$ meets the Polyak-Lojasiewicz (PL) inequality if the following holds for some $\mu > 0$:

$$\begin{aligned}\frac{1}{2}||\nabla f(x)|| \geq \mu (f(x) - f(x^*))\end{aligned},\forall x$$



For a constant step-size $1/L$, the PL condition guarantees that $f$ can achieve linear global convergence with gradient descent, i.e., $\begin{aligned} x_{k+1} \leftarrow x_k - \frac{1}{L}\nabla f(x_k)\end{aligned}$. The first key idea here depends on the Lipschitz-continuous: Here the step-size $1/L$ originates from choosing the step size that minimize the second order approximation. This choice ensures that the updates from gradient descent are lower bounded by **the square of the norm of the gradient**. 

$$\begin{aligned} & x_{k+1} = \arg\min_y g(x_k, y) \\ & f(x_{k+1}) \leq g(x_k, x_{k+1}) \quad (L-\text{Lipschitz-continuous gradient}) \\ & f(x_k) - f(x_{k+1}) \geq \frac{1}{2L}||\nabla f(x_k)||_2^2  \end{aligned}$$

For the global convergence part, as stated by the PL inequality, **every update of gradient descent will make up at least a constant fraction of the difference between the current value and optimal value**. This ensures the sequence $x_k$ can converges to $x^*$. The whole proof is written as followed.

$$  \begin{aligned} & f(x_k) - f(x_{k+1}) \geq \frac{1}{2L}||\nabla f(x_k)||_2^2 \geq \frac{\mu}{L}(f(x) - f(x^*)) \quad (\text{PL-condition}) \\ & f(x_{k+1}) - f(x^*) \leq (1 - \frac{\mu}{L})(f(x_k) - f(x^*)) \\ & f(x_k) - f(x^*) \leq (1 - \frac{\mu}{L})^k (f(x_0) - f(x^*))\end{aligned}$$

