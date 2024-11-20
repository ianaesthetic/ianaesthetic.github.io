---
math: true
---



### Polyak-Lojasiewicz Condition 

#### Unconstrained Case

In the unconstrained case, the objective can be written as $\begin{aligned} \min_{x \in \mathbb{R}^d} f(x)\end{aligned}$. Here we assume the derivative of $f$ is $L-$Lipschitz-continuous: 

$$\begin{aligned} f(y) \leq f(x) + \langle \nabla f(x), y - x\rangle + \frac{L}{2}\end{aligned}||x - y||^2 = D(y, x)$$

We say $f(x)$ meets the Polyak-Lojasiewicz (PL) inequality if the following holds for some $\mu > 0$:

$$\begin{aligned}\frac{1}{2}||\nabla f(x)|| \geq \mu (f(x) - f(x^*))\end{aligned},\forall x$$



For a constant step-size $1/L$, the PL condition guarantees that $f$ can achieve linear global convergence with gradient descent, i.e., $\begin{aligned} x_{k+1} \leftarrow x_k - \frac{1}{L}\nabla f(x_k)\end{aligned}$. The first key idea here depends on the Lipschitz-continuous: Here the step-size $1/L$ originates from choosing the step size that minimize the second order approximation. This choice ensures that the updates from gradient descent are lower bounded by **the square of the norm of the gradient**. 

$$\begin{aligned} & x_{k+1} = \arg\min_y f(x_k) + \langle \nabla f(x_k), y - x_k\rangle + \frac{L}{2}||y-x_k||^2 = \arg\min_y D(x_k, y) \\ & f(x_{k+1}) \leq D(x_k, x_{k+1}) \quad (L-\text{Lipschitz-continuous gradient}) \\  &f(x_{k+1}) \leq f(x_k) + \textcolor{red}{\langle \nabla f(x_k), x_{k+1} - x_k\rangle + \frac{L}{2}||x_{k+1}-x_k||^2}\\& f(x_k) - f(x_{k+1}) \geq \textcolor{red}{\frac{1}{2L}||\nabla f(x_k)||_2^2 } \end{aligned}$$

For the global convergence part, as stated by the PL inequality, **every update of gradient descent will make up at least a constant fraction of the difference between the current value and optimal value**. This ensures the sequence $x_k$ can converges to $x^*$. The whole proof is written as followed.

$$  \begin{aligned} & f(x_k) - f(x_{k+1}) \geq \frac{1}{2L}||\nabla f(x_k)||_2^2 \geq \frac{\mu}{L}(f(x) - f(x^*)) \quad (\text{PL-condition}) \\ & f(x_{k+1}) - f(x^*) \leq (1 - \frac{\mu}{L})(f(x_k) - f(x^*)) \\ & f(x_k) - f(x^*) \leq (1 - \frac{\mu}{L})^k (f(x_0) - f(x^*))\end{aligned}$$



#### Constrained Case

As the constrained case is a special case of proximal optimization, we focus on the following composite function where $f$ has $L$-Lipschitz continuous gradient and $g$ is a convex function:

$$\begin{aligned} \min_x  F(x) =f(x) + g(x)\end{aligned}$$

In the proximal gradient descent, the next $x_{k+1}$ is similarly drawn from a minimization target. 

$$\begin{aligned}x_{k+1} = \arg\min_{y}\left[ f(x_k) + \langle \nabla f(x_k), y - x\rangle + \frac{L}{2}||y-x||^2 + g(y)\right]\end{aligned} $$

As we have $L$-Lipschitz in $f$ we can similarly derive:

$$\begin{aligned}F(x_{k+1}) &= f(x_{k+1}) + g(x_{k+1}) \\ &\leq f(x_k)   +  \langle \nabla f(x_{k} ), x_{k+1} - x_{k}\rangle + \frac{L}{2}||x_{k+1} - x_k^2|| + g(x_{k+1}) \\ &  \leq F(x_{k}) +  \textcolor{red}{\langle \nabla f(x_{k} ), x_{k+1} - x_{k}\rangle + \frac{L}{2}||x_{k+1} - x_k^2|| + g(x_{k+1}) - g(x_k)}\end{aligned}$$

The red part serves the same purpose as that in the unconstrained case. However, instead of having a closed form in the unconstrained case and leading to the square of the gradient due to the derivation of $x_{k+1}$, the proximal case has no closed form. So we write the whole red part and have the following PL condition. The convergence result is then very straightforward.

$$\begin{aligned} &D_g(x; \alpha) = \min_y \left[\langle \nabla f(x_{k} ), y - x_{k}\rangle + \frac{\alpha}{2}||y - x_k||^2 + g(x_{k+1}) - g(x_k) \right] \\ & D_g(x_k; L) \geq \mu(F(x^*) - F(x_{k})) \end{aligned}$$



Reference: 

[1] Karimi H, Nutini J, Schmidt M. Linear convergence of gradient and proximal-gradient methods under the polyak-łojasiewicz condition[C]//Machine Learning and Knowledge Discovery in Databases: European Conference, ECML PKDD 2016, Riva del Garda, Italy, September 19-23, 2016, Proceedings, Part I 16. Springer International Publishing, 2016: 795-811.
