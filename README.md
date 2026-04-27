# Hyperuniformity in terms of stochastic processes

Consider a stochastic process $\varphi(\mathbf{x}):\Omega \to \mathbb{R}$ where $\Omega \subset \mathbb{R}^d$. Its autocovariance; considering $\mathbf{x}_t$ to be the time factor vector; is given by
$$
\begin{aligned}
    R_{\varphi}(\mathbf{x}_1 - \mathbf{x}_2)
    &= \text{cov}[\varphi(\mathbf{x}_1), \varphi(\mathbf{x}_2)] \\
    &= \mathbb{E}[(\varphi(\mathbf{x}_1) - \mathbb{E}[\varphi(\mathbf{x}_1)])(\varphi(\mathbf{x}_2) - \mathbb{E}[\varphi(\mathbf{x}_2)])] \\
    &= \mathbb{E}[\varphi(\mathbf{x}_1)\varphi(\mathbf{x}_2)] - \mathbb{E}[\varphi(\mathbf{x}_1)]\mathbb{E}[\varphi(\mathbf{x}_2)]
\end{aligned}
$$

The spectral density is given by the Fourier transform of this autocovariance function
$$
\begin{aligned}
    \widehat{R}_\varphi(\mathbf{f})
    &= S_\varphi(\mathbf{f}) \\
    &= |\widehat{\varphi}(\mathbf{f})|^2
\end{aligned}
$$
where $\mathbf{f}$ is the wave frequency vector.

The process $\varphi(\mathbf{x})$ is said to be hyperuniform if
$$\lim_{|\mathbf{k}| \to 0} \widehat{R}_\varphi(\mathbf{f}) = 0$$

Formulating Hyperuniformity in stochastic terms could lead to some new results through a Markovian analysis. Maybe it is worth looking into.

# Cahn-Hillard equation in terms of stochastic process

The standard Cahn-Hillard equation is purely deterministic. However, converting this partial differential equation to a stochastic partial differential equation might allow us to invoke the central limit theorem to make the solution converge to a Gaussian random field.

Another benefit one can think of is the addition of noise in a SPDE which could better mimic a real-world scenario where fluctuations between atoms are present due to brownian motion.

For a stochastic process $\varphi:\Omega \times [0,T] \to \mathbb{R}$ with $\Omega \subset \mathbb{R}^d$ ,the Cahn-Hillard equation from the paper has the form of a conservation law
$$
\frac{\partial \varphi}{\partial t} = - \nabla \cdot \mathbf{j}(x,y)
$$
where the flux, $\mathbf{j}(x,y) = (1/\epsilon) \nabla \mu$, and $\mu = 72\varphi^3 - 36\varphi - \epsilon^2 \nabla^2\varphi$

Adding the white noise $\xi$ proved a bit challenging to me. On one hand the most studied SPDE, the stochastic heat equation given by
$$
\frac{\partial u}{\partial t} = \nabla^2 u + \xi
$$
adds the white noise to the entire PDE directly; but intuition says that it should be added to the flux. 

Some discussion is required for this. Reference used for this section was Wikipedia page for Cahn-Hillard equation and Stochastic PDE. John Walsh's "An Introduction to SPDEs" has been helpful as well.

# The Code

For practical purposes I am going to use the standard Cahn-Hillard equation since the stochastic one needs some work.